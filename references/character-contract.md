# Eloi Presenter Contract

## License Gate

The Eloi images and identity are proprietary assets, even when distributed inside the open-source Skill repository. Read [the Eloi Character Asset License](../LICENSE-ELOI-ASSETS.md) before using them. Repository access allows evaluation only; external use requires written authorization from the rights holder or a completed USD 9.99 single-project license purchase.

If proof is unavailable, use neutral placeholders or another properly licensed presenter pack while implementing the pipeline. Do not create Eloi derivatives, publish the bundled images, or present Eloi in an OBS output.

## Canonical Identity

Use [the canonical turnaround](../assets/eloi-turnaround.png) as the strongest visual reference.

- Name: Eloi.
- Age presentation: 29-year-old French woman from Lyon.
- Role: lifestyle creator and client/content operations professional; warm, practical, trustworthy, and never hard-selling.
- Hair: medium-brown, naturally wavy, shoulder length, with a soft side part.
- Eyes: warm brown.
- Face: oval structure, natural skin texture, restrained makeup, and an authentic friendly smile.
- Rendering: photorealistic cinematic natural daylight with a clean French lifestyle aesthetic.

Do not change facial structure, apparent age, hair silhouette, body proportions, skin tone, or realism level without explicit approval. Do not publish the redacted `Eloi_conver.png` source or use it as a public asset.

## Canonical MVP Outfit

- white ribbed fitted top;
- light-gray knit cardigan;
- charcoal high-waisted straight trousers;
- white minimalist sneakers when feet are visible.

Wardrobe selection must not change Eloi's face, hair, age presentation, or body proportions.

## Four Runtime States

Use the bundled transparent images:

| State | Asset | Meaning |
| --- | --- | --- |
| `idle` | `../assets/eloi-idle.png` | attentive listening, silence, normal completion |
| `thinking` | `../assets/eloi-thinking.png` | request in progress |
| `tip` | `../assets/eloi-tip.png` | advice, useful conclusion, recommendation |
| `error` | `../assets/eloi-error.png` | calm, recoverable failure or unavailable service |

Render all states inside one stable bottom-anchored stage. Normalize display height with CSS because the source canvases vary slightly. Use crossfades or subtle transforms that do not shift Eloi's face or overall scale.

## Voice Contract

- adult female voice with a warm, clear, natural register;
- fluent English and French pronunciation;
- calm pace, light French warmth, and restrained commercial delivery;
- one multilingual voice is preferred for identity consistency;
- avoid childlike, exaggerated, synthetic, or aggressive sales voices.

## Motion Restraint

For the PNG MVP, allow only subtle presentational motion:

- slow breathing-scale movement;
- very small vertical float;
- short state crossfade;
- optional eye blink only when implemented with a real layered asset.

Do not fake lip sync by rapidly scaling the whole face or image. Accurate speaking animation requires a layered Live2D model, viseme frames, or a rigged 3D avatar and belongs to a later phase.
