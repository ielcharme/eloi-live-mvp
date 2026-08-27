# Zerendo Live MVP

**English** | [Francais](README.fr.md)

An open-source Codex Skill for building a reactive AI presenter experience with web or microphone input, English/French Zerendo replies, bilingual speech, four visual states, and a transparent OBS output.

Zerendo remains the AI reasoning layer. **Eloi** is the default visual presenter and can be replaced with another authorized character pack.

## Important: Eloi requires a paid license

The code and Skill instructions in this repository are licensed under MIT. **Eloi's identity, likeness, character design, and images are not covered by the MIT License.**

Before using Eloi in a video, livestream, website, application, advertisement, product, or social-media channel, you must obtain either:

- written authorization from the rights holder; or
- a **USD 9.99 Single Project License**.

Contact: [zerencontact@sina.com](mailto:zerencontact@sina.com)

Suggested email subject: `Eloi License - [Project Name]`

Identify the project, product, website, application, or channel that will use Eloi. The rights holder will send the official payment link through the existing ZEREN PayPal integration. The license becomes valid only after PayPal confirms completed payment.

Cloning, forking, or installing this repository does not authorize use of Eloi. Read [LICENSE-ELOI-ASSETS.md](LICENSE-ELOI-ASSETS.md) for the complete terms.

## Runtime flow

```text
Web text / microphone
-> Zerendo reply
-> English/French female TTS
-> Eloi idle/thinking/tip/error
-> transparent OBS Browser Source
```

## MVP capabilities

- English and French text input;
- microphone input after an explicit user gesture;
- adapter for an existing Zerendo endpoint;
- warm adult female bilingual voice;
- `idle`, `thinking`, `tip`, and `error` visual states;
- real alpha transparency for OBS;
- replaceable adapters for STT, TTS, model backend, and presenter packs.

## Installation

Copy the `zerendo-live-mvp` folder into your Codex Skills directory, then invoke:

```text
$zerendo-live-mvp Build a transparent OBS-ready Zerendo experience with Eloi as the presenter.
```

Without a valid Eloi license, use neutral images you own or another properly licensed presenter pack.

## Main files

- `SKILL.md`: core Skill instructions;
- `references/architecture.md`: adapters, events, state machine, and OBS contract;
- `references/character-contract.md`: Eloi identity, voice, and visual behavior;
- `assets/zerendo-live.config.example.json`: starter configuration;
- `assets/eloi-*.png`: proprietary Eloi visual assets.

## Licenses

- Code, instructions, and configuration: [MIT](LICENSE)
- Eloi identity and visual assets: [Eloi proprietary asset license](LICENSE-ELOI-ASSETS.md)

This license template is not legal advice.
