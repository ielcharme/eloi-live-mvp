# Zerendo Live MVP Architecture

## Component Boundary

```text
Input UI
  text | microphone
        |
        v
Input adapter / optional speech-to-text
        |
        v
Live controller -----> avatar state store
        |
        v
Zerendo adapter -----> policy and response normalizer
        |                         |
        v                         v
TTS adapter ----------------> audio player
        |                         |
        +-------------> presenter pack / transparent overlay
```

Keep adapters small enough to replace independently:

- `input`: text submission and explicit microphone capture.
- `stt`: browser or server transcription; absent in text-only mode.
- `zerendo`: calls an existing backend or a configured model endpoint.
- `tts`: converts normalized `speech` and `language` into playable audio using the presenter's configured voice.
- `presenter`: declares identity, voice profile, and the four state assets without changing Zerendo's response contract.
- `avatar`: maps approved presenter states to local transparent images.
- `transport`: direct HTTP for a single page; WebSocket or SSE only when a separate control page and OBS overlay must stay synchronized.

## Suggested Event Shape

```json
{
  "id": "evt_01",
  "type": "user.text",
  "source": "web",
  "language": "fr",
  "text": "Explique-moi cette campagne.",
  "created_at": "2026-08-27T20:00:00Z"
}
```

Supported MVP event types:

- `user.text`
- `user.speech.transcript`
- `zerendo.reply.started`
- `zerendo.reply.completed`
- `zerendo.reply.failed`
- `tts.started`
- `tts.completed`
- `tts.failed`

Generate event and request IDs locally. Ignore unknown event types.

## Zerendo Adapter

Inspect the target project before choosing the endpoint. Convert its result into:

```ts
type ZerendoLiveReply = {
  speech: string;
  language: "en" | "fr";
  state: "idle" | "thinking" | "tip" | "error";
  request_id: string;
};
```

Keep spoken replies short by default. If the source answer is long, speak a concise summary and leave the full answer in the control UI. Preserve citations in the control UI when the underlying Zerendo answer provides them; do not read raw URLs aloud.

## State Controller

Use a deterministic state machine rather than allowing arbitrary model output:

```text
idle
  -> thinking                 accepted input
thinking
  -> idle | tip              normalized reply ready
thinking
  -> error                   model or network failure
idle | tip
  -> idle                    TTS completed
error
  -> idle                    recovery timeout or new input
```

Use the latest request ID as the state owner. A late response with a different ID must be discarded.

## Browser And OBS Contract

- Set `html`, `body`, and the app root to transparent backgrounds.
- Do not render instruction text, controls, or debugging information in overlay mode.
- Keep controls on a separate route or hide them behind `?mode=control`.
- Keep the character anchored to the bottom center with a stable box and `object-fit: contain`.
- Preserve alpha transparency in source PNG files.
- Normalize the presenter's rendered height instead of assuming identical source-canvas dimensions.
- Recommended initial OBS dimensions: `1920x1080` landscape and `1080x1920` portrait.
- Provide a query parameter such as `?scale=0.9` only when the implementation validates and clamps it.

## Failure Behavior

Map failures to a safe local response:

- microphone denied: stop capture, show the control-page error, keep avatar usable by text;
- transcription failed: `error`, then return to `idle`;
- Zerendo unavailable: speak only if a pre-approved local fallback exists;
- TTS failed: show the text reply and recover to `idle`;
- missing image: render `idle` if available, otherwise a transparent empty stage with a control-page error.

Never expose stack traces, credentials, raw prompts, or provider payloads in the OBS overlay.
