---
name: kling-ai
description: >
  This skill should be used when the user wants to create AI-generated video with Kling AI - including animating an image, generating video from a text prompt, writing or improving Kling prompts, choosing between Kling models (V3, O3, O1, 2.6, 2.5 Turbo), setting up multi-shot storyboards, using motion control, applying voice cloning, or troubleshooting generation issues. Also applies when the user asks about Kling credits, pricing, or platform alternatives. Trigger phrases include: "Kling", "animate this image", "image to video", "text to video", "AI video generation", "cinematic prompt", "how do I make an AI video".
---

# Kling AI Video Generation

## Platform Access

Primary interface: **app.klingai.com/global**

Alternative platforms with Kling integration: Higgsfield, Pollo.ai, Fal.ai, Media.io, Artlist, Vidful.ai, Scenario, BasedLabs, LetzAI

---

## Quick Start: Animate an Image in 60 Seconds

1. Go to **app.klingai.com/global** → AI Videos → Image to Video
2. Select **Video 3.0 (V3)**
3. Upload your image
4. Write a short motion prompt - describe only what moves, not the whole scene:
   ```
   Subtle breeze moves through hair. Eyes blink naturally. Camera static.
   ```
5. Set duration: **5s** for loops, **10-15s** for narrative
6. Generate at **1080p Standard** mode (saves credits, same prompt quality as Professional)

That's it. For model selection, advanced prompting, and multi-shot workflows - read on.

---

## Model Lineup (as of February 2026)

| Model | Best For | Resolution | Audio | Max Duration |
|-------|----------|------------|-------|--------------|
| **Video 3.0 (V3)** | Multi-shot storytelling, cinematic control | 1080p | Yes (5 languages) | 15s |
| **Video 3.0 Omni (O3)** | Reference-based consistency, voice cloning, 4K | 4K / 60fps | Yes (5 languages) | 15s |
| **Video O1** | Complex scenes, character consistency, editing | 1080p | No | 10s |
| **Video 2.6** | Audio-visual sync, dialogue (EN/CN) | 1080p | Yes (EN/CN) | 10s |
| **Video 2.5 Turbo** | Fast drafts, simple scenes | 1080p | No | 10s |
| **2.6 Motion Control** | Motion transfer from reference video | 1080p | Optional | 30s |

## Model Selection Guide

**Choose Video 3.0 (V3) when:**
- Need multi-shot sequences (up to 6 shots in one generation)
- Want first-and-last-frame control for seamless transitions
- Want native multilingual audio (EN, ZH, JA, KO, ES)
- Working from text or image prompts (prompt-first workflow)
- Need videos up to 15 seconds with narrative structure

**Choose Video 3.0 Omni (O3) when:**
- Have a reference video or image to anchor character identity
- Need voice cloning from a reference clip
- Require 4K resolution or 60fps for fast-paced content (60fps requires Pro plan)
- Editing or remixing existing footage
- Need the strongest subject consistency across shots

**Choose O1 when:**
- Complex multi-element scenes with the older pipeline
- Video-to-video editing tasks in pre-3.0 workflows

**Choose 2.6 when:**
- Need synchronized audio specifically in English or Chinese only

**Choose 2.5 Turbo when:**
- Rapid prototyping before committing credits to a 3.0 generation
- Simple 3-4-element scenes without audio needs

**Choose 2.6 Motion Control when:**
- Have a reference video with exact motion you want to transfer to a character

---

## Core Workflows

### Image-to-Video

1. Navigate to **AI Videos - Image to Video**
2. Select model (V3 or O3 recommended)
3. Upload image (min 300x300px, max 10MB, JPG/PNG/WEBP)
4. Write a motion-focused prompt - describe only what moves, not the image content (the scene already exists in your image)
5. Optionally set an end frame (new in 3.0) to control where motion resolves
6. Set duration (5s for loops/social, up to 15s for narrative)
7. Set aspect ratio to match source image
8. Generate

### Text-to-Video

1. Navigate to **AI Videos - Text to Video**
2. Select model (V3 for prompt-driven, O3 for reference-driven)
3. Write prompt in this structured order: **Scene - Characters - Action - Camera - Audio & Style**
4. For 3.0: optionally use multi-shot mode to define each shot separately
5. Set duration (3-15s for V3/O3), aspect ratio, and quality
6. Generate at 1080p for drafts; use 4K (O3 only) for final output

### Multi-Shot Storyboard (3.0 Only)

The biggest new workflow in Kling 3.0. Instead of one continuous clip, you direct a complete scene sequence in a single generation pass.

1. Enter **Custom Storyboard mode** in the V3/O3 interface
2. Define up to 6 shots - for each shot specify: duration, camera movement, composition, and subject action
3. Keep 4-6 shots for a 10-15 second video (more than 6 shots in under 10 seconds feels rushed)
4. Use Elements 3.0 or reference images to maintain character consistency across shots
5. Generate

**Example multi-shot prompt structure:**
```
Shot 1 (3s): Wide establishing shot of rain-slicked Tokyo street at night, neon reflections on pavement. Camera: static.
Shot 2 (4s): Medium shot - young woman in red coat emerges from subway exit, looks around. Camera: slow push in.
Shot 3 (3s): Close-up on her face, raindrops on cheek, determined expression. Camera: static.
Shot 4 (5s): She walks toward camera into the crowd. Camera: tracking shot from behind.
```

### First and Last Frame Control (3.0 Only)

Define exactly where a video starts and ends visually.

- **Start + End frames:** Full control over composition and motion arc
- **End frame only:** Guide how motion resolves without fixing the start
- Upload reference images for either or both frames

Use this to create near-seamless loops by matching the end frame composition to the start.

### Elements 3.0 - Subject Consistency

Reference specific subjects or objects using the `@element_name` syntax:

1. In the V3/O3 interface, open the **Elements panel** and upload a reference image
2. Give it a name in the name field (e.g., `hero_character`)
3. In your prompt, reference it as `@hero_character walks through the market`

Elements can be reused across separate generations, enabling a consistent visual library of characters and objects. O3 has the strongest implementation - use for commercial work where identity must stay locked.

### Motion Control (2.6)

1. Navigate to **Motion Control**
2. Upload character image (full/half body with background)
3. Upload reference video (3-30s) or select from library
4. Set character orientation: `image` (max 10s) or `video` (max 30s)
5. Add optional text prompt for atmosphere/style
6. Generate

---

## Language of Prompts

Always write Kling prompts in **English**, regardless of the language the user is writing in. Kling was trained predominantly on English-language descriptions, and English prompts produce significantly better and more predictable results than prompts in other languages.

The workflow is:
- Communicate with the user in their language (Polish, German, French, etc.)
- Write all Kling prompts in English

If the user writes their prompt in Polish or another language, translate it to English before presenting the final version they should paste into Kling. Explain this briefly if it's not obvious.

Exception: when using the native audio features (V3/O3), dialogue text in the `[Speaker: Name] "text"` syntax should be in the target language (e.g., Polish dialogue for a Polish-language video). The surrounding prompt structure should still be in English.

---

## Prompt Engineering

### The Director's Mindset

Kling 3.0 understands **cinematic intent**. The key shift: stop writing prompts like image captions, start directing like a DoP (Director of Photography). Think of each prompt as a mini-screenplay:

**Scene setting - Camera direction - Subject action**

### Structured Prompt Formula

```
[Scene/Environment] + [Characters/Subjects] + [Sequential Actions] + [Camera Movement] + [Audio & Style]
```

For 3.0, you can describe **sequential actions**: "First she looks up, then turns toward the window, finally smiles." Previous models couldn't handle this reliably - 3.0 can.

### Model-Specific Guidance

| Model | Prompt Length | Max Elements | Key Pattern |
|-------|---------------|--------------|-------------|
| V3 / O3 | 100-200 words | 6-7 | Sequential actions, multi-shot |
| O1 | 60-100 words | 5-7 | Clear element descriptions |
| 2.6 | 50-80 words | 5-7 | Include audio instructions |
| 2.5 Turbo | 40-60 words | 3-4 | Keep it simple |

### Essential Prompt Rules

1. **Specify camera behavior explicitly** - Without it, camera will improvise unpredictably
2. **Add motion endpoints** - "then settles back" or "returns to starting position" prevents 99% of generation hangs
3. **Use spatial language** - "left to right", "toward camera", "background depth"
4. **Be hyper-specific about setting** - "cyberpunk alleyway at midnight, neon reflections on wet pavement" beats "a street"
5. **One main action per shot** - Use multi-shot for complexity, not a single overloaded prompt
6. **Use negative prompts** - Explicitly tell the model what to avoid

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

- **1080p for all drafts** - saves credits, same prompt quality
- **4K (O3 only) for final deliverables** - switch only when prompt is locked in
- **30fps** for most content; **60fps** for dance, sport, fast action (Kling 3.0, requires Pro plan)

---

## Prompt Templates

See `references/prompt-templates.md` for ready-to-use templates organized by use case.

---

## Common Issues & Solutions

| Issue | Cause | Solution |
|-------|-------|----------|
| Generation stuck at 99% | Open-ended motion | Add endpoint: "then stops", "returns to start" |
| Unwanted camera movement | No camera instruction | Add "static camera" or specific movement |
| Text/elements changing | AI interpretation | Repeat "fixed", "unchanged", "static" multiple times |
| Character morphing across shots | Identity drift | Use O3 with Elements 3.0 and reference images. Rewrite prompt from scratch rather than retrying with same settings. |
| Artifacts on hands/faces | Model limitation | Simplify scene, reduce duration, use O3 |
| Multi-shot feels disjointed | No shared style anchor | Define visual style once at start, use @element refs |
| Audio desync | Missing speaker attribution | Use `[Speaker: Name] "dialogue"` format |

---

## Settings Reference

**Duration:** 5s (loops/social), up to 15s (V3/O3 narrative), 10s (O1/2.6)

**Aspect Ratios:** 16:9 (landscape), 9:16 (vertical/mobile), 1:1 (square)

**Quality modes:**
- Standard mode (~10 credits/5s) - for drafts and iteration
- Professional mode (~35 credits/5s) - for finals (requires paid plan)

**V3 vs O3:** Same generation quality - O3 adds 4K, reference-based control, voice cloning. Both cost the same per generation.

---

## Credits & Pricing (2026)

**Free tier:** 66 credits/day (expire in 24h, watermarked output)

**Paid plans:**

| Plan | Monthly | Credits/mo | ~Videos/mo (Pro mode, 5s) |
|------|---------|------------|---------------------------|
| Standard | ~$10 | 660 | ~18 |
| Pro | ~$37 | 3,000 | ~85 |
| Premier | ~$92 | 8,000 | ~230 |
| Ultra | ~$180 | 26,000 | ~740 |

Annual plans: ~34% discount. Additional credit packs available from $5 (330 credits).

All paid plans include: watermark removal, Professional mode access, 1080p output, priority processing.

**Audio surcharge:** Audio-enabled generation (Kling 2.6 with native audio) costs approximately 5x more credits than silent generation (~50 credits/5s standard, ~100 credits/5s professional).

---

## Audio Features (V3, O3, and 2.6)

**Languages for native audio:** Chinese, English, Japanese, Korean, Spanish (V3/O3); English + Chinese only (2.6)

**Audio types:** speech/dialogue, narration, singing/rap, sound effects, ambient

**Speaker attribution syntax (critical for accurate lip-sync):**
```
[Speaker: Character Name] "[dialogue]" in a [tone/emotion] [accent] voice.
Add [sound: footsteps / rain / door closing] when [action occurs].
Background ambient: [environment description].
```

**Voice cloning (O3 only):** Upload an audio clip (min 3s) as part of an Element. O3 binds the voice profile to the character's element_id, reusable across generations. In the prompt, reference the character via `@element_name` - voice follows automatically.
