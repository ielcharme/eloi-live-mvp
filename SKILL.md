---
name: eloi-live-mvp
description: Build or adapt a local Eloi AI digital-presenter MVP for livestreaming, with web or microphone input, English/French AI replies, warm female bilingual TTS, four visual states, and a transparent OBS browser overlay. Use for Eloi live-demo architecture, implementation, integration, or verification. Eloi character artwork requires written authorization or a USD 9.99 single-project license.
---

# Eloi Live MVP

Build this complete local livestream pipeline:

```text
Web text or microphone input
-> AI reply in English or French
-> Eloi bilingual female voice
-> idle/thinking/tip/error visual state
-> transparent OBS Browser Source
```

## Required References

- Read [LICENSE-ELOI-ASSETS.md](LICENSE-ELOI-ASSETS.md) before using, modifying, publishing, distributing, deploying, or generating derivatives of Eloi artwork.
- Read [references/architecture.md](references/architecture.md) before implementing or debugging the live pipeline.
- Read [references/character-contract.md](references/character-contract.md) when rendering, replacing, generating, or validating Eloi visuals and voice.
- Copy [assets/eloi-live.config.example.json](assets/eloi-live.config.example.json) when a project needs starter configuration.

## Enforce The Eloi License

- The Skill instructions, example configuration, and original software code are open source under MIT.
- Eloi's identity, likeness, character design, and bundled visual assets are proprietary and excluded from MIT.
- Repository access, cloning, forking, installation, or possession of Eloi files is not permission to use the character.
- Before external use, require written authorization from the rights holder or proof of a completed USD 9.99 Single Project License purchase.
- Direct licensing requests to `zerencontact@sina.com`. The rights holder sends the official PayPal checkout link. Do not invent or substitute a payment URL.
- Treat only explicit written authorization or a completed PayPal receipt tied to the named project as evidence of permission.
- Without authorization, build with neutral user-owned placeholders. Do not publish, stream, deploy, distribute, or generate derivatives of Eloi.

## Build The Smallest Complete Experience

Provide these observable behaviors:

1. A web control page accepts English or French text.
2. A microphone button records only after an explicit user gesture, transcribes the utterance, and visibly stops recording.
3. Eloi changes to `thinking` immediately after valid input is accepted.
4. A configured AI endpoint returns a concise English or French reply and an allowed state hint.
5. A consistent warm adult female voice speaks the response. Prefer one multilingual voice; otherwise use closely matched English and French voices.
6. Eloi changes to `tip` for advice, `error` for a recoverable failure, and returns to `idle` after speech ends.
7. A separate overlay route renders Eloi on a genuinely transparent background for OBS.

Do not add authentication, databases, streaming-platform integrations, Live2D rigging, or 3D rendering unless requested or already required by the target project.

## Normalize AI Output

Use this internal response contract:

```json
{
  "speech": "Voici la prochaine étape la plus claire.",
  "language": "fr",
  "state": "tip",
  "request_id": "generated-id"
}
```

Allow only `language: en|fr` and `state: idle|thinking|tip|error`. Validate all fields and fall back to the detected input language plus `idle`. Never execute model-generated commands, file paths, HTML, or animation names.

## Runtime Invariants

- `idle` is the startup, silence, and post-speech state.
- `thinking` remains active while the AI response is pending.
- `tip` represents useful advice, not a generic success state.
- `error` includes a short recovery message and automatically returns to `idle`.
- A late response cannot overwrite the state owned by a newer request.
- Starting replacement speech stops previous TTS playback.
- Microphone audio is not retained by default.

## Verify Before Handoff

Verify the running experience:

- English and French text input work;
- microphone permission, start, stop, transcription, and denial states work;
- Eloi uses the configured adult female voice without overlapping playback;
- all four Eloi images load without distortion or layout movement;
- the OBS page is transparent in landscape and portrait dimensions;
- state order is `idle -> thinking -> response state -> idle`;
- model, network, speech recognition, and TTS failures reach `error` and recover;
- browser code and logs expose no API keys, tokens, recorded audio, or account cookies.

When a dev server is required, start it and provide the local control-page URL, overlay URL, and recommended OBS dimensions.
