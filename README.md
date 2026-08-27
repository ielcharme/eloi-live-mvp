# Eloi Live MVP

**English** | [Français](README.fr.md)

An open-source Codex Skill for building **Eloi as an AI digital presenter for livestreaming**. Viewers or operators can interact through web text or a microphone; Eloi answers in English or French, speaks with a warm female voice, changes visual state automatically, and appears on a transparent OBS layer.

## How it works

```text
Web text / microphone
-> AI reply in English or French
-> Eloi bilingual female voice
-> idle / thinking / tip / error
-> transparent OBS Browser Source
```

## Important: Eloi requires a paid license

The software and Skill instructions are licensed under MIT. **Eloi's identity, likeness, character design, and images are proprietary and are not covered by MIT.**

Before using Eloi in a livestream, video, website, application, advertisement, product, or social-media channel, obtain either:

- written authorization from the rights holder; or
- a **USD 9.99 Single Project License**.

Contact: [zerencontact@sina.com](mailto:zerencontact@sina.com)

Suggested subject: `Eloi License - [Project Name]`

Describe the project or channel that will use Eloi. The rights holder will send the official PayPal checkout link. The license becomes valid only after PayPal confirms completed payment.

Cloning, forking, or installing this repository does not grant permission to use Eloi. See [LICENSE-ELOI-ASSETS.md](LICENSE-ELOI-ASSETS.md) for complete terms.

## MVP capabilities

- English and French text interaction;
- microphone input after explicit user action;
- connection to a configurable AI endpoint;
- warm adult female bilingual speech;
- automatic `idle`, `thinking`, `tip`, and `error` states;
- transparent OBS overlay for landscape or portrait livestreams;
- replaceable STT, AI, and TTS adapters.

## Installation

Copy `eloi-live-mvp` into your Codex Skills directory, then invoke:

```text
$eloi-live-mvp Build an English/French Eloi digital presenter for a transparent OBS livestream.
```

Without a valid Eloi license, use neutral images you own while building the technical pipeline.

## Main files

- `SKILL.md`: Eloi livestream implementation instructions;
- `references/architecture.md`: adapters, events, state machine, and OBS contract;
- `references/character-contract.md`: Eloi identity, voice, and visual behavior;
- `assets/eloi-live.config.example.json`: starter configuration;
- `assets/eloi-*.png`: proprietary Eloi visual assets.

## Licenses

- Software, instructions, and configuration: [MIT](LICENSE)
- Eloi identity and visual assets: [Eloi proprietary asset license](LICENSE-ELOI-ASSETS.md)

This license template is not legal advice.
