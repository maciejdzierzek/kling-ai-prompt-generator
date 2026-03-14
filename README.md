# Kling AI Prompt Generator - Claude Skill

> A Claude skill for generating professional Kling AI video prompts.
> Works with Claude.ai, Claude Desktop, and Claude Code.
> Supports Image-to-Video, Text-to-Video, Multi-Shot Storyboards, and Motion Control workflows.

[![Live Generator](https://img.shields.io/badge/Live_Generator-maciejdzierzek.com-blue)](https://maciejdzierzek.com/narzedzia/generator-kling-ai)
[![Claude Skill](https://img.shields.io/badge/Claude-Skill-orange)](https://claude.ai)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

---

## What is this?

A skill for Claude that helps you write professional Kling AI video prompts - structured, model-aware, and ready to paste. Instead of guessing what works, Claude asks clarifying questions and builds the prompt following Kling's cinematic conventions.

Works with **Claude.ai** (web), **Claude Desktop**, and **Claude Code** - all three support the same skill format via the Customize > Skills panel.

Developed and used daily in production by [Maciej Dzierżek](https://maciejdzierzek.com) - consultant, trainer, and creator from Poland who works with Kling AI professionally.

**Try the interactive web version (no installation needed):** [maciejdzierzek.com/narzedzia/generator-kling-ai](https://maciejdzierzek.com/narzedzia/generator-kling-ai)

---

## Features

- **4 generation modes:** Image-to-Video, Text-to-Video, Multi-Shot Storyboard (3.0 only), Motion Control
- **Model-aware:** Covers the full Kling lineup - V3, O3, O1, 2.6, 2.5 Turbo - with model-specific prompt length and element limits
- **Camera movement vocabulary:** 10 named movements (static, dolly, orbit, tracking, crane, POV...) with speed modifiers
- **Motion endpoint pattern:** Adds "returns to starting position" / "then settles" to prevent the stuck-at-99% generation hang
- **Audio prompts:** Speaker attribution syntax for lip-synced dialogue, SFX, ambient, and voice cloning (O3)
- **Sequential action support:** 3.0-specific "first / then / finally" action structure for multi-step scenes
- **Elements 3.0 reference tagging:** `@element_name` syntax for cross-shot subject consistency
- **6 ready-to-use templates:** Product, portrait, atmospheric loop, commercial, talking head, action scene
- **Always outputs English prompts:** Regardless of the language you describe your scene in

---

## Installation

### Claude.ai and Claude Desktop (all plans, including free)

1. Download **[kling-ai-prompt-generator-skill.zip](kling-ai-prompt-generator-skill.zip)** from this repository (click → Download raw file)
2. In Claude.ai or Claude Desktop: go to **Customize > Skills** → click **"+"** → **"Upload a skill"**
3. Upload the ZIP file and toggle the skill on

Claude will automatically use the skill when you describe a Kling AI video task. Available on Free, Pro, Max, Team, and Enterprise plans.

> **Note:** Skills require code execution to be enabled. If you don't see the Skills section, go to **Settings > Capabilities** and enable "Code execution and file creation" first.

### Claude Code (CLI) - via plugin marketplace

```bash
/plugin marketplace add maciejdzierzek/kling-ai-prompt-generator
/plugin install kling-ai-prompt-generator@maciejdzierzek-kling-ai-prompt-generator
```

No download needed - installs directly from this GitHub repository.

### Claude Code (CLI) - manual install

```bash
mkdir -p ~/.claude/skills/kling-ai
cp skills/kling-ai/SKILL.md ~/.claude/skills/kling-ai/SKILL.md
```

For project-specific use:
```bash
mkdir -p /your-project/.claude/skills/kling-ai
cp skills/kling-ai/SKILL.md /your-project/.claude/skills/kling-ai/SKILL.md
```

Reload Claude Code. The skill activates automatically.

### Interactive web generator (no installation)

Use directly at: [maciejdzierzek.com/narzedzia/generator-kling-ai](https://maciejdzierzek.com/narzedzia/generator-kling-ai)

No API key, no registration, no data sent to servers. Works entirely in your browser.

---

## Usage

Describe what you want to create - Claude will identify the right mode and build the prompt:

```
Create a Kling AI prompt for an image-to-video animation of my product photo.
The product is a perfume bottle and I want subtle light reflections moving.
```

```
I need a text-to-video prompt for a cinematic portrait of a woman in a cafe.
She should slowly turn toward the camera. Using Kling V3.
```

Use a template as starting point:

```
Load the "Product Commercial" Kling AI template and adapt it for a matte black watch.
```

For multi-shot sequences:

```
I want to create a 4-shot storyboard in Kling 3.0 for a product launch video.
The product is headphones. Approximate total duration 12 seconds.
```

---

## Prompt Structure

### Image-to-Video

```
[MOTION DESCRIPTION - what moves, not what exists].
[STATIC ELEMENTS: what must remain fixed].
Camera: [MOVEMENT]. Duration: [5/10/15]s. Aspect ratio: [16:9/9:16/1:1].
```

### Text-to-Video

```
Setting: [ENVIRONMENT + TIME OF DAY + ATMOSPHERE].
Subject: [CHARACTER/OBJECT DESCRIPTION].
Action: First [INITIAL STATE], then [MAIN ACTION], finally [RESOLUTION].
Camera: [MOVEMENT + LENS]. Style: [VISUAL KEYWORDS].
[AUDIO if using V3/O3/2.6]. Duration: [5-15]s.
```

### Multi-Shot Storyboard (V3/O3 only)

```
Shot 1 ([Xs]): [Wide establishing shot]. Camera: static.
Shot 2 ([Xs]): [Medium shot, action begins]. Camera: slow push in.
Shot 3 ([Xs]): [Close-up, reaction or detail]. Camera: static.
Shot 4 ([Xs]): [Resolution]. Camera: tracking / pull back.
```

### Audio Speaker Attribution (V3, O3, 2.6)

```
[Speaker: Character Name] "[dialogue]" in a [warm/confident/excited] [male/female] voice with [accent].
Add [sound: footsteps / rain / door closing] when [action].
Background ambient: [environment description].
```

---

## Examples

See [examples/](examples/) for ready-to-use prompts with notes on expected results:

- [examples/image-to-video.md](examples/image-to-video.md) - Product animation, portrait animation, nature loop, logo animation
- [examples/text-to-video.md](examples/text-to-video.md) - Cinematic portrait, product commercial, atmospheric loop, talking head with audio
- [examples/motion-control.md](examples/motion-control.md) - Orbit, push in, Ken Burns pan - with camera path setup notes

---

## Models

| Model | Best For | Prompt Length | Max Duration | Audio |
|-------|----------|---------------|--------------|-------|
| **Video 3.0 (V3)** | Multi-shot narrative, sequential actions | 100-200 words | 15s | EN, ZH, JA, KO, ES |
| **Video 3.0 Omni (O3)** | Reference-based consistency, 4K, voice cloning | 100-200 words | 15s | EN, ZH, JA, KO, ES |
| **Video O1** | Complex scenes, older pipeline | 60-100 words | 10s | No |
| **Video 2.6** | Audio-visual sync (EN/CN only) | 50-80 words | 10s | EN + ZH |
| **2.5 Turbo** | Fast drafts, simple scenes | 40-60 words | 10s | No |
| **2.6 Motion Control** | Precise camera trajectory from reference video | Short | 30s | Optional |

**When to use V3 vs O3:** Same generation quality. O3 adds 4K resolution, 60fps, reference-based subject consistency, and voice cloning. Use V3 for prompt-driven work; O3 when you have a reference image or video to anchor identity.

---

## About the Author

Built by [Maciej Dzierżek](https://maciejdzierzek.com) - consultant, trainer, and creator based in Poland. He helps businesses implement AI in their workflows through training, consulting, and hands-on tools.

- Website: [maciejdzierzek.com](https://maciejdzierzek.com)
- All AI tools: [maciejdzierzek.com/narzedzia](https://maciejdzierzek.com/narzedzia)

---

## License

MIT - use freely, attribution appreciated. See [LICENSE](LICENSE).
