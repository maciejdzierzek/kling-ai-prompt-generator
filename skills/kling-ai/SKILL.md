---
name: kling-ai
description: This skill should be used when the user wants to create AI-generated video with Kling AI - including animating an image, generating video from a text prompt, building a talking AI avatar from one photo + audio, writing or improving Kling prompts, choosing between Kling models (VIDEO 3.0, VIDEO 3.0 Omni, Avatar 2.0, 2.6, 2.5 Turbo, VIDEO 3.0 Motion Control), setting up multi-shot storyboards via the Canvas Agent, using Element Reference for character consistency, applying Voice Control or voice cloning, or troubleshooting generation issues. Also applies when the user asks about Kling credits, pricing, or platform alternatives. Trigger phrases include "Kling", "animate this image", "image to video", "text to video", "AI video generation", "talking avatar", "AI presenter", "lip sync video", "cinematic prompt", "how do I make an AI video".
---

# Kling AI Video Generation

Source-of-truth for the facts in this skill: the official Kling release notes at [kling.ai/release-note](https://kling.ai/release-note). When numbers, durations, credit costs, or language lists matter for a deliverable, verify them there before quoting.

## Platform Access

Primary interface: **app.klingai.com/global** (or **kling.ai/app**)

Alternative platforms with Kling integration: Higgsfield, Pollo.ai, Fal.ai, Media.io, Artlist, Vidful.ai, Scenario, BasedLabs, LetzAI, PiAPI, kie.ai

---

## Quick Start: Animate an Image in 60 Seconds

1. Go to **app.klingai.com/global** - AI Videos - Image to Video
2. Select **VIDEO 3.0** (or **VIDEO 3.0 Omni** if you have reference images / video elements to anchor identity)
3. Upload your image
4. Write a short motion prompt - describe only what moves, not the whole scene:
   ```
   Subtle breeze moves through hair. Eyes blink naturally. Camera static.
   ```
5. Set duration: **5s** for loops/social, **10-15s** for narrative (3.0 supports up to 15s)
6. Set output: 1080p Standard for drafts; switch to **native 4K** only for finals (4K costs ~30 credits/sec)

That's it. For model selection, advanced prompting, avatars, and multi-shot workflows - read on.

---

## Model Lineup (as of May 2026)

| Model | Best For | Resolution | Audio | Max Duration | Released |
|-------|----------|------------|-------|--------------|----------|
| **VIDEO 3.0** | Cinematic storytelling, multi-shot, native audio, multilingual dialogue | up to 4K | Yes (5 langs) | 15s | 2026-01-31 |
| **VIDEO 3.0 Omni** | VIDEO 3.0 capabilities + video element reference + element voice control | up to 4K | Yes (5 langs) | 15s | 2026-01-31 |
| **VIDEO 3.0 Motion Control** | Motion transfer with high facial consistency, including occlusions and multi-angle | 1080p | Optional | 30s | 2026-03-04 |
| **Avatar 2.0** | Talking avatars from 1 image + 1 audio file, up to 5 minutes | 1080p / 48fps | Lip-sync to provided audio | 5 min | 2025-12-04 |
| **Kling 2.6** | Older Native Audio pipeline (EN+ZH), good fast/budget option | 1080p | EN + ZH | 10s | 2025-12-03 |
| **Kling 2.5 Turbo** | Fastest, simplest scenes, draft work | 1080p | No | 10s | earlier |

**Important clarification on the 3.0 Series:** "Kling 3.0" is a *series name*, not a single model. It contains **VIDEO 3.0** (upgrade path from VIDEO 2.6) and **VIDEO 3.0 Omni** (upgrade path from the older VIDEO O1). Both share the new unified multimodal training framework; Omni adds video element reference and element voice control. Third-party reviews sometimes merge them into one - the official release notes do not.

## Model Selection Guide

**Choose VIDEO 3.0 when:**
- Text-to-video or image-to-video from prompts/images you already have
- Need multi-shot sequences (3.0 introduced multi-shot - 2.6 did not have it)
- Want native multilingual audio (Chinese, English, Japanese, Korean, Spanish) with dialects/accents
- Need start-frame + element reference, or multi-character coreference (3+ characters)
- Working up to 15s, flexible duration
- Default choice for prompt-driven work

**Choose VIDEO 3.0 Omni when:**
- Have a reference **video** (not just images) to anchor character/scene
- Want to add voice to specific elements (Element Voice Control)
- Need the strongest cross-shot consistency for commercial work
- Same other capabilities as VIDEO 3.0 (text-to-video, image-to-video, native audio, multi-shot, 15s)

**Choose VIDEO 3.0 Motion Control when:**
- Have a reference action video and want to transfer the motion to your character
- Need high facial consistency across angles/emotions/occlusions
- Need up to 30s of motion-controlled output (vs. 15s on regular 3.0)
- Built on 2.6 Motion Control, now with facial element binding

**Choose Avatar 2.0 when:**
- Need a talking-head video (presenter, explainer, music performance)
- Have one image of the person and an audio track (recorded or AI-generated)
- Need duration up to 5 minutes (much longer than VIDEO 3.0's 15s)
- The face/voice IS the content - camera and scene are secondary

**Choose Kling 2.6 when:**
- Need synchronized native audio in English or Chinese with the older pipeline
- Lower credit budget than 3.0

**Choose 2.5 Turbo when:**
- Rapid prototyping, simple 3-4 element scenes, no audio needs

---

## Core Workflows

### Image-to-Video

1. Navigate to **AI Videos - Image to Video**
2. Select **VIDEO 3.0** (or VIDEO 3.0 Omni for reference-heavy work)
3. Upload image (min 300x300px, max 10MB, JPG/PNG/WEBP)
4. Write a motion-focused prompt - describe only what moves (the scene already exists in your image)
5. Optionally set an end frame to control where motion resolves
6. Set duration (5s for loops/social, up to 15s for narrative)
7. Set aspect ratio to match source image
8. Render at 1080p first to verify; switch to 4K only for final delivery

### Text-to-Video

1. Navigate to **AI Videos - Text to Video**
2. Select VIDEO 3.0
3. Write prompt in this structured order: **Scene - Characters - Action - Camera - Audio & Style**
4. Optionally use multi-shot mode to define each shot separately
5. Set duration (3-15s), aspect ratio, quality
6. Render at 1080p for review; 4K only for final

### Talking Avatar (Avatar 2.0)

The headline feature of Avatar 2.0: one image + one audio file → talking avatar with synchronized expressions, body language, and hand gestures. Up to 5 minutes of continuous output for any scenario (knowledge sharing, song performance, advertising, storytelling).

1. Navigate to **AI Avatar** (or via fal.ai / PiAPI / kie.ai API endpoints)
2. Upload a reference image - good lighting, face clearly visible
3. Upload an audio track - speech, narration, singing. Recorded or AI-generated (e.g., ElevenLabs)
4. Optional: short text prompt for tone or framing (e.g., "calm professional presenter, minimal gestures")
5. Generate

**What 2.0 improved over 1.0:**
- Enhanced performance and motion quality - body movements, gestures, expressions, camera angles
- Stable, clear hand movements (the main fix vs. 1.0's notorious hand artifacts)
- Up to **5 minutes** of continuous output for any scenario

**Note on languages:** Kling officially lists multilingual support for Avatar 2.0 as **English, Japanese, Korean, Chinese**. However, the model lip-syncs to whatever audio file you provide - it uses your audio as the reference, not just trained-language detection. Field-tested confirmation: **Polish audio (e.g., ElevenLabs-generated) works** and produces correct lip-sync. Other non-listed languages will likely work too. Practical guidance: don't tell the user "your language isn't supported" - if they have a good audio file, try it. Worst case the sync is slightly off and a paid generation is wasted; best case (most common) it works perfectly.

**When NOT to use Avatar 2.0:** When you need full scene control (complex cinematography, environment, camera moves) - use VIDEO 3.0 talking-head workflow instead. Avatar 2.0 is purpose-built for face/voice content with a relatively static framing.

### Multi-Shot Storyboard (VIDEO 3.0)

Multi-shot was introduced in the 3.0 generation - VIDEO 2.6 did not support it. Instead of one continuous clip, direct a complete scene sequence in a single generation pass.

Two ways to use it:
- **Implicit multi-shot:** Describe a scene in natural prompt language - the model recognizes cinematic structure (shot-reverse-shot, cross-cutting dialogue, voice-over) and adjusts camera angles automatically.
- **Custom multi-shot:** Explicitly define each shot with its own subject, action, camera, duration.

**Example custom multi-shot prompt structure:**
```
Shot 1 (3s): Wide establishing shot of rain-slicked Tokyo street at night, neon reflections on pavement. Camera: static.
Shot 2 (4s): Medium shot - young woman in red coat emerges from subway exit, looks around. Camera: slow push in.
Shot 3 (3s): Close-up on her face, raindrops on cheek, determined expression. Camera: static.
Shot 4 (5s): She walks toward camera into the crowd. Camera: tracking shot from behind.
```

### Kling Canvas Agent (one-click storyboard)

Launched 2026-01-29 - an AI orchestrator on top of the Kling generation models that automates the storyboard production pipeline:

- **Continuous shot creation** - upload an element, get consistent storyboard images and videos across many shots
- **Multi-angle storyboard expansion** - from one reference image, generate multiple angles/perspectives
- **Script creation** - feed a story outline; Canvas Agent expands it into a structured storyboard script
- **Reverse prompt suggestions** - feed it a video or image; it extracts visual style and core elements as a high-quality prompt
- **Batch generation** - parallel processing of multiple prompts
- **E-commerce image set** - from one product photo, generate Main + Model + Scene images

When the user needs more than a single clip - a complete short film with consistent characters, or a multi-asset deliverable - Canvas Agent is the right starting point.

### First and Last Frame Control (VIDEO 3.0)

Define exactly where a video starts and ends visually.

- **Start + End frames:** Full control over composition and motion arc
- **End frame only:** Guide how motion resolves without fixing the start
- Upload reference images for either or both frames

Use this to create near-seamless loops by matching the end frame composition to the start.

### Element Reference (character/scene consistency)

Kling's official mechanism for keeping subjects, items, and scenes consistent across shots is the **Element** system (sometimes called Element Library or Element Reference). Third-party reviews call this "Character LoRA" - the user-facing feature in Kling is named **Element**.

**How it works (VIDEO 3.0 / Omni):**
1. Open the Element panel
2. Upload reference image(s) for the subject - multi-image references work, and Omni also accepts a video as an element
3. Name the element (e.g., `@protagonist`)
4. Reference it in prompts via the element chip or the `@element_name` syntax
5. Reusable across multiple generations - the Element Library persists

For commercial work where identity must stay locked across many shots, this is the recommended approach.

### Voice Control (VIDEO 2.6 / 3.0)

Launched in VIDEO 2.6 on 2025-12-16 as a separate feature from generic Native Audio. Voice Control extracts the timbre from your uploaded audio sample into a reusable **Voice Embedding**, then binds it to characters via the `[Character] @VoiceName` syntax.

**Key facts (verify before quoting):**
- Upload a **5-30s clean clip** (single speaker, neutral emotion, low noise) to train a voice
- Up to **200 voices** in your library
- Syntax: `[Subject] @VoiceName` in the prompt - e.g., `[Livestream Host] @Sweet Female Voice: "This top is a trending must-have!"`
- Multi-character dialogue: each character can have its own `@VoiceName`
- Currently supports **Chinese and English only** for voice creation/use, with **bidirectional Chinese-English cross-language** delivery (a voice trained in one can perform in the other)
- Pricing: **+2 credits/sec** on top of base video generation

This is what you want when you need a consistent IP voice or brand persona across many videos. For one-off talking-head content with audio you already have, **Avatar 2.0** is a different tool entirely.

### Motion Control (VIDEO 3.0)

Current Motion Control is the **VIDEO 3.0 Motion Control** model (launched 2026-03-04), an upgrade over VIDEO 2.6 Motion Control (Dec 2025).

1. Navigate to **Motion Control**
2. Upload reference action video and target character image
3. Click "Bind Facial Element to Enhance Facial Consistency" below the character image - bind an existing element or create a new one
4. Optionally upload additional images/short video to enrich multi-angle expression data
5. Set duration (up to 30s)
6. Generate

**What 3.0 Motion Control adds over 2.6:** facial element binding for high facial consistency across angles, emotions, and even occlusions (hands, props in front of face). Element Binding requires the character orientation to match the video orientation.

---

## Language of Prompts

Always write Kling prompts in **English**, regardless of the language the user is writing in. Kling was trained predominantly on English and Chinese; English prompts produce significantly better and more predictable results than prompts in less-represented languages.

The workflow is:
- Communicate with the user in their language (Polish, German, French, etc.)
- Write all Kling prompts in English

If the user writes their prompt in Polish or another language, translate it to English before presenting the final version they should paste into Kling. Explain this briefly if it's not obvious.

**Exception:** when using Native Audio features (VIDEO 3.0), dialogue text inside `[Speaker: Name] "text"` syntax should be in the target language. VIDEO 3.0 supports Chinese, English, Japanese, Korean, Spanish with dialects and accents. The surrounding prompt structure should still be in English.

**For Avatar 2.0:** language is determined by the audio file you upload, not by the prompt. The framing prompt itself stays English.

---

## Prompt Engineering

### The Director's Mindset

Kling 3.0 understands **cinematic intent**. The key shift: stop writing prompts like image captions, start directing like a DoP (Director of Photography). Think of each prompt as a mini-screenplay:

**Scene setting - Camera direction - Subject action**

### Structured Prompt Formula

```
[Scene/Environment] + [Characters/Subjects] + [Sequential Actions] + [Camera Movement] + [Audio & Style]
```

VIDEO 3.0 handles **sequential actions** reliably: "First she looks up, then turns toward the window, finally smiles." Use this for any action that has phases.

### Model-Specific Guidance

| Model | Prompt Length | Max Elements | Key Pattern |
|-------|---------------|--------------|-------------|
| VIDEO 3.0 / 3.0 Omni | 100-200 words | 6-7 | Sequential actions, multi-shot, native audio |
| Avatar 2.0 | 20-50 words (framing only) | 1-2 | Tone/energy descriptor; audio does the work |
| 2.6 | 50-80 words | 5-7 | Include audio instructions (EN/ZH) |
| 2.5 Turbo | 40-60 words | 3-4 | Keep it simple |

### Essential Prompt Rules

1. **Specify camera behavior explicitly** - Without it, camera will improvise unpredictably
2. **Add motion endpoints** - "then settles back" or "returns to starting position" prevents the stuck-at-99% generation hang
3. **Use spatial language** - "left to right", "toward camera", "background depth"
4. **Be hyper-specific about setting** - "cyberpunk alleyway at midnight, neon reflections on wet pavement" beats "a street"
5. **One main action per shot** - Use multi-shot for complexity, not a single overloaded prompt
6. **Use negative prompts** - Explicitly tell the model what to avoid
7. **Validate at 1080p before 4K** - 4K is ~30 credits/sec; iterate cheaper first

### Keeping Elements Static

```
All [element] must remain absolutely fixed and unchanged throughout.
[element] stays completely static. No movement on [element].
```

For critical logos or text: generate without text, add as a post-production overlay.

### Loop-Friendly Prompts

```
Subtle [motion type], gentle oscillation, returns to starting position.
Breathing effect, slow pulse, cyclical movement.
```

With 3.0: use first/last frame control with matching compositions. Post-process with 0.3-0.5s cross-dissolve.

### Resolution Workflow

- **1080p for iteration** - same prompt quality as 4K, fraction of the credits
- **4K (VIDEO 3.0 series, launched 2026-04-23) for final deliverables** - 30 credits/sec, native (not upscaled), preserves reference consistency, lighting, color
- **30fps** for most content; higher framerates available on 3.0 for fast action

---

## Prompt Templates

See `references/prompt-templates.md` for ready-to-use templates organized by use case (image-to-video, multi-shot, text-to-video, Avatar 2.0, audio).

---

## Common Issues & Solutions

| Issue | Cause | Solution |
|-------|-------|----------|
| Generation stuck at 99% | Open-ended motion | Add endpoint: "then stops", "returns to start" |
| Burning credits on bad prompts | Going to 4K too early | Always iterate at 1080p first; only render 4K once prompt is locked |
| Unwanted camera movement | No camera instruction | Add "static camera" or specific movement |
| Text/elements changing | AI interpretation | Repeat "fixed", "unchanged", "static" multiple times |
| Character morphing across shots | Identity drift | Use VIDEO 3.0 Omni with Element Reference (multi-image/video). Rewrite prompt from scratch rather than retrying with same settings. |
| Artifacts on hands/faces | Model limitation | Simplify scene, reduce duration, use 4K with 3.0 |
| Avatar 2.0 lip-sync looks off | Difficult audio (noise, multi-speaker, distorted) | Use a clean single-speaker audio source; check current docs for language support |
| Avatar 2.0 body too static / too active | No framing prompt | Add a one-line tone/energy descriptor: "calm presenter, minimal gestures" or "energetic performer, full body movement" |
| Voice Control sounds wrong | Bad reference audio | Use 5-30s clean clip, single speaker, neutral emotion, low background noise |
| Multi-shot feels disjointed | No shared style anchor | Define visual style once at start, use Element Reference for people/items |
| Audio desync | Missing speaker attribution | Use `[Speaker: Name] "dialogue"` format, or with Voice Control `[Character] @VoiceName` |

---

## Settings Reference

**Duration:**
- VIDEO 3.0 / Omni: 5-15s (flexible)
- VIDEO 3.0 Motion Control: up to 30s
- Avatar 2.0: up to 5 minutes
- 2.6 / 2.5 Turbo: 5-10s

**Aspect Ratios:** 16:9 (landscape), 9:16 (vertical/mobile), 1:1 (square)

**Quality / Output:**
- Standard mode - for drafts
- Professional mode - for finals (requires paid plan)
- Native 4K - VIDEO 3.0 series only, at ~30 credits/sec, launched 2026-04-23

---

## Credits & Pricing

See `references/pricing.md` for plan structure, per-feature inclusions, credit costs per model, and third-party API providers (fal.ai, PiAPI, kie.ai). Pricing changes frequently.

**Key facts (verified against the official pricing page 2026-05-21):**
- 5 subscription tiers: Basic (free), Standard ($6.99), Pro ($25.99), Premier ($64.99), Ultra ($127.99)
- **Basic/free tier output cannot be used commercially** - hard restriction; user must be on Standard+ for commercial use
- **Voice Control is FREE for all paid subscribers** (the "+2 credits/sec" rate applies to API / pay-as-you-go use, not subscription)
- VIDEO O1 Element AI Multi-Shot: 3 daily free uses on every paid plan
- 4K generation: 30 credits/sec (VIDEO 3.0 series)
- 720p baseline: ~20 credits per 5s clip

---

## Audio Features

### Native Audio (VIDEO 3.0 / Omni)

Languages supported (per official 3.0 release note): **Chinese, English, Japanese, Korean, Spanish**, with **dialects and accents**. Multi-character coreference (3+ characters) and per-character voice precision.

**Speaker attribution syntax (critical for accurate lip-sync in T2V/I2V workflows):**
```
[Speaker: Character Name] "[dialogue]" in a [tone/emotion] [accent] voice.
Add [sound: footsteps / rain / door closing] when [action occurs].
Background ambient: [environment description].
```

### Native Audio (VIDEO 2.6)

Chinese and English only. Same speaker-attribution syntax.

### Voice Control (VIDEO 2.6 / 3.0)

A separate, more advanced feature. See the Voice Control section above. Currently Chinese-English only; +2 credits/sec.

### Avatar 2.0

Uses your provided audio directly - no voice cloning or attribution syntax needed. Lip-sync is automatic.

---

## Verification & Sources

When facts in this skill matter for a deliverable (credit pricing, language lists, duration limits), verify against the current Kling state:

- **Official release notes index:** https://kling.ai/release-note
- **Specific release notes referenced in this skill:**
  - Cinema-Grade Native 4K (2026-04-23): https://kling.ai/release-note/release-notes/z8zeqsxwol
  - VIDEO 3.0 Motion Control (2026-03-04): https://kling.ai/release-note/release-notes/4titicw2vg
  - Kling 3.0 Era / VIDEO 3.0 + 3.0 Omni rollout (2026-01-31): https://kling.ai/release-note/release-notes/whbvu8hsip
  - Kling Canvas Agent (2026-01-29): https://kling.ai/release-note/release-notes/s568cuscq1
  - Voice Control in VIDEO 2.6 (2025-12-16): https://kling.ai/release-note/release-notes/7trhudk78j
  - Kling AI Avatar 2.0 (2025-12-04): https://kling.ai/release-note/release-notes/9bbqv0a76z
- **Official API documentation:** https://kling.ai/document-api/quickStart/productIntroduction/overview
- **Pricing:** https://kling.ai/dev/pricing or app dashboard after login
- **Third-party API providers** (different pricing, current model coverage): fal.ai, PiAPI, kie.ai
