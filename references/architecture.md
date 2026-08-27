# Eloi Live MVP Architecture

## Component Boundary

```text
Control page
  text | microphone
        |
        v
Input adapter / optional speech-to-text
        |
        v
Live controller -----> Eloi state store
        |
        v
AI adapter ----------> response normalizer
        |                         |
        v                         v
TTS adapter ----------------> audio player
        |                         |
        +----------------> transparent Eloi overlay
```

Keep each adapter replaceable:

- `input`: text submission and explicit microphone capture.
- `stt`: browser or server transcription; absent in text-only mode.
- `assistant`: calls the configured AI backend.
- `tts`: converts normalized speech into Eloi's configured English/French voice.
- `avatar`: maps the four approved Eloi states to transparent local images.
- `transport`: direct HTTP for one page; WebSocket or SSE only when the control page and OBS overlay must stay synchronized.

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
- `assistant.reply.started`
- `assistant.reply.completed`
- `assistant.reply.failed`
- `tts.started`
- `tts.completed`
- `tts.failed`

Generate request and event IDs locally. Ignore unknown event types.

## AI Adapter

Inspect the target project's current endpoint and convert its result into:

```ts
type EloiLiveReply = {
  speech: string;
  language: "en" | "fr";
  state: "idle" | "thinking" | "tip" | "error";
  request_id: string;
};
```

Keep spoken replies concise. If the source answer is long, speak a short summary and retain the full text in the control page. Keep citations visible in the control page and do not read raw URLs aloud.

## State Controller

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

The latest request ID owns the state. Discard any late response with a different ID.

## Browser And OBS Contract

- Set `html`, `body`, and the app root to transparent backgrounds.
- Keep controls and debug information off the overlay route.
- Anchor Eloi to the bottom center with a stable stage and `object-fit: contain`.
- Preserve alpha transparency in source PNG files.
- Normalize rendered height because source canvas dimensions vary slightly.
- Start with `1920x1080` landscape and `1080x1920` portrait OBS dimensions.

## Failure Behavior

- microphone denied: stop capture, show a control-page error, and keep text input available;
- transcription failed: show `error`, then return to `idle`;
- AI backend unavailable: use `error` unless a pre-approved local fallback exists;
- TTS failed: keep the written reply visible and recover to `idle`;
- image missing: fall back to `idle`, or show an empty transparent stage with a control-page error.

Never expose stack traces, credentials, raw prompts, or provider payloads in the OBS overlay.
