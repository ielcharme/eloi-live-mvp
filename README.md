# Eloi Live MVP

<p align="center">
  <img src="assets/eloi-turnaround.png" alt="Eloi digital presenter reference sheet" width="920">
</p>

<p align="center"><strong>Build Eloi as an English/French AI digital presenter for OBS livestreams.</strong></p>

<p align="center"><strong>English</strong> · <a href="README.fr.md">Français</a></p>

> [!IMPORTANT]
> This repository is a **Codex Skill**, not a finished livestream application. It gives Codex the architecture, character rules, assets, state logic, and verification checklist needed to build or adapt an Eloi livestream experience in your project.

> [!WARNING]
> The software is MIT-licensed, but **Eloi's identity and images are proprietary**. External use requires written authorization or a **USD 9.99 Single Project License**. See [Eloi image licensing](#eloi-image-licensing).

## In one sentence

An operator or viewer types or speaks, an AI produces an English or French reply, Eloi speaks it with a warm female voice, her visual state changes automatically, and OBS receives a transparent character layer.

## How a live interaction works

```text
Viewer or operator
      │
      ├── types in the web control page
      └── speaks through the microphone
                    │
                    ▼
          Speech-to-text, if needed
                    │
                    ▼
           Configured AI endpoint
          English or French reply
                    │
          ┌─────────┴─────────┐
          ▼                   ▼
  Eloi visual state      Female bilingual TTS
 idle/thinking/tip/error       │
          └─────────┬─────────┘
                    ▼
       Transparent OBS Browser Source
```

## Eloi's four live states

<table>
  <tr>
    <th width="25%">Idle</th>
    <th width="25%">Thinking</th>
    <th width="25%">Tip</th>
    <th width="25%">Error</th>
  </tr>
  <tr>
    <td><img src="assets/eloi-idle.png" alt="Eloi idle state" width="210"></td>
    <td><img src="assets/eloi-thinking.png" alt="Eloi thinking state" width="210"></td>
    <td><img src="assets/eloi-tip.png" alt="Eloi tip state" width="210"></td>
    <td><img src="assets/eloi-error.png" alt="Eloi error state" width="210"></td>
  </tr>
  <tr>
    <td>Listening, waiting, or finished speaking.</td>
    <td>The AI is preparing a response.</td>
    <td>Eloi is giving advice or a useful conclusion.</td>
    <td>A recoverable service or input problem occurred.</td>
  </tr>
</table>

The four PNG files contain real alpha transparency and are intended for a bottom-anchored OBS overlay.

## What this Skill helps Codex build

- a web control page for English and French text input;
- microphone capture after an explicit user action;
- optional speech-to-text;
- an adapter for your chosen AI endpoint;
- warm adult female English/French text-to-speech;
- deterministic `idle`, `thinking`, `tip`, and `error` transitions;
- a separate transparent route for OBS Browser Source;
- recovery behavior for microphone, network, AI, and TTS failures.

It does not include a hosted AI service, API credits, streaming-platform accounts, Live2D rigging, or a finished 3D model.

## Quick start

### 1. Install the Skill

Copy this folder to your Codex Skills directory:

```text
~/.codex/skills/eloi-live-mvp
```

### 2. Ask Codex to build the experience

```text
$eloi-live-mvp Build an English/French Eloi digital presenter with text input,
microphone input, female bilingual TTS, automatic visual states, and a
transparent OBS overlay.
```

### 3. Connect your AI and voice services

Start from [the example configuration](assets/eloi-live.config.example.json):

```json
{
  "assistant": {
    "endpoint": "/api/assistant/reply",
    "replyLanguages": ["en", "fr"]
  },
  "speech": {
    "preferredVoiceGender": "female",
    "preferredVoiceMode": "single-multilingual-voice"
  },
  "overlay": {
    "transparent": true
  }
}
```

Codex should adapt the endpoint and provider settings to the target project instead of exposing API keys in browser code.

### 4. Add the overlay to OBS

Use the generated overlay URL as an **OBS Browser Source**.

- Landscape starting size: `1920 × 1080`
- Portrait starting size: `1080 × 1920`
- Background: transparent
- Character position: bottom center

## Eloi image licensing

The repository uses two separate license layers:

| Material | License |
| --- | --- |
| Skill instructions, example configuration, and original software code | [MIT License](LICENSE) |
| Eloi identity, likeness, character design, and `assets/eloi-*.png` | [Proprietary Eloi Asset License](LICENSE-ELOI-ASSETS.md) |

Before using Eloi in a livestream, video, website, application, advertisement, product, or social-media channel, obtain either:

1. written authorization from the rights holder; or
2. a **USD 9.99 Single Project License**.

**Licensing contact:** [zerencontact@sina.com](mailto:zerencontact@sina.com)<br>
**Suggested subject:** `Eloi License - [Project Name]`

Describe the project, product, website, application, or channel that will use Eloi. The rights holder will send the official PayPal checkout link. The license becomes active only after PayPal confirms completed payment.

Cloning, downloading, forking, or installing this repository does **not** grant permission to publish or commercially use Eloi.

## Repository map

```text
eloi-live-mvp/
├── SKILL.md                              Codex workflow and safeguards
├── README.md                            English documentation
├── README.fr.md                         French documentation
├── LICENSE                              MIT software license
├── LICENSE-ELOI-ASSETS.md               Eloi image license
├── agents/openai.yaml                   Skill display metadata
├── assets/
│   ├── eloi-turnaround.png              Canonical visual reference
│   ├── eloi-idle.png                    Normal listening state
│   ├── eloi-thinking.png                AI processing state
│   ├── eloi-tip.png                     Advice state
│   ├── eloi-error.png                   Recoverable error state
│   └── eloi-live.config.example.json    Starter configuration
└── references/
    ├── architecture.md                  Runtime and OBS architecture
    └── character-contract.md            Eloi identity and voice rules
```

## Character and implementation references

- [Eloi character and voice contract](references/character-contract.md)
- [Live architecture and state machine](references/architecture.md)
- [Complete Eloi asset license](LICENSE-ELOI-ASSETS.md)

This license template is not legal advice.
