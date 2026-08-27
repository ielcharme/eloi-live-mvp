---
name: zerendo-live-mvp
description: Build or adapt a local Zerendo reactive-avatar MVP with a replaceable visual presenter, web or microphone input, English/French replies, bilingual TTS, four visual states, and a transparent OBS browser overlay. Use for Zerendo live-demo architecture, implementation, integration, presenter-pack replacement, or verification. The default Eloi character artwork requires separate authorization or a USD 9.99 single-project license.
---

# Zerendo Live MVP

Create a working local experience with this pipeline:

```text
Web text or microphone input
-> Zerendo response
-> English/French TTS
-> idle/thinking/tip/error state controller
-> replaceable presenter pack
-> transparent OBS browser source
```

Zerendo is the reasoning layer. The default visual presenter is Eloi, using a warm adult female bilingual voice. Keep the presenter pack replaceable so a licensed or user-owned character can be substituted without changing the Zerendo adapter.

## Read The Relevant References

- Read [LICENSE-ELOI-ASSETS.md](LICENSE-ELOI-ASSETS.md) before copying, rendering, modifying, publishing, distributing, deploying, or generating derivatives of an Eloi character image.
- Read [references/architecture.md](references/architecture.md) before designing, scaffolding, integrating, or debugging the live pipeline.
- Read [references/character-contract.md](references/character-contract.md) whenever rendering, replacing, generating, or validating Eloi visuals.
- Copy [assets/zerendo-live.config.example.json](assets/zerendo-live.config.example.json) when a project needs a starter configuration.

## Enforce The Presenter License Boundary

- The Skill instructions and code are open source under MIT. The Eloi identity, likeness, design, and bundled visual assets are excluded from MIT.
- Public repository access, cloning, installation, or possession of the image files is not permission to use Eloi.
- Before using Eloi visuals outside repository evaluation, require written authorization from the rights holder or evidence of a completed USD 9.99 single-project character license purchase.
- Direct authorization and license requests to `zerencontact@sina.com`. Paid licenses use the existing first-party ZEREN PayPal checkout; do not invent or substitute a PayPal account or URL.
- Treat only a completed PayPal receipt tied to the named project, or explicit written authorization, as evidence. Do not claim payment or authorization has been verified without user-provided evidence. Do not collect payment credentials.
- If authorization is absent, build the technical MVP with neutral user-owned placeholders or another properly licensed presenter pack. Do not render, publish, distribute, deploy, or generate derivatives of Eloi.
- The repository owner may use Eloi assets in the official repository, documentation, previews, and first-party projects as the rights holder.

## Preserve The Product Boundary

- Treat Zerendo as the reasoning layer and Eloi as the default visual presenter. Keep input, speech recognition, TTS, avatar state, and OBS rendering behind replaceable adapters.
- Reuse the producer/event/consumer idea from GPT-vup only as an architectural reference. Do not copy its unmaintained runtime, old OpenAI/LangChain dependencies, platform scraping, credentials, or VTube Studio assumptions into a new implementation.
- Prefer an existing Zerendo endpoint when the target project already has one. Inspect its current contract first and wrap it with an adapter instead of coupling the overlay to the backend response shape.
- This MVP does not authorize posting, sending messages, joining live rooms, using stored browser sessions, or changing production accounts.

## Build The Smallest Complete Experience

Provide these observable behaviors:

1. A text field submits English or French input.
2. A microphone control records only after an explicit user gesture, transcribes the utterance, and visibly stops recording.
3. Eloi switches to `thinking` while Zerendo is generating a reply.
4. Zerendo returns concise spoken English or French plus a state hint.
5. A consistent warm adult female voice speaks the response. Prefer one multilingual voice; otherwise use closely matched `en` and `fr` voices.
6. Eloi switches to `tip` for advice or a useful conclusion, `error` for a recoverable failure, and returns to `idle` when speech ends.
7. The overlay renders on a genuinely transparent page suitable for an OBS Browser Source.

Do not add authentication, databases, streaming-platform integrations, Live2D rigging, or 3D rendering unless the user requests them or the existing project already requires them.

## Use A Stable Response Contract

Normalize model output before it reaches TTS or the renderer:

```json
{
  "speech": "Voici la prochaine etape la plus claire.",
  "language": "fr",
  "state": "tip",
  "request_id": "generated-id"
}
```

Allow only `language: en|fr` and `state: idle|thinking|tip|error`. Validate and fall back to the detected input language plus `idle`. Never execute model-generated commands, file paths, HTML, presenter IDs, or animation names.

## State And Audio Invariants

- `idle` is the startup, silence, and post-speech state.
- `thinking` begins immediately after accepted input and remains active while the response is pending.
- `tip` is a positive information state, not a generic success screen.
- `error` must include a short user-readable recovery message and automatically return to `idle`.
- Cancel stale requests so an older response cannot overwrite a newer avatar state.
- Stop previous TTS before playing a replacement response.
- Do not record or retain microphone audio by default. Log only request metadata unless the user explicitly requests recordings.

## Verify Before Handoff

Verify the actual running experience, not only source files:

- text input works in English and French;
- microphone permission, start, stop, and denial states are handled;
- TTS uses the configured adult female voice and finishes without overlapping playback;
- all four Eloi images load without distortion or layout movement;
- the browser background is transparent at desktop and portrait OBS sizes;
- state order is `idle -> thinking -> response state -> idle`;
- network, speech recognition, model, and TTS failures reach `error` and recover;
- no API keys, tokens, recorded audio, or account cookies are exposed to browser code or logs.

When a dev server is needed, start it and provide the local URL plus recommended OBS Browser Source dimensions.
