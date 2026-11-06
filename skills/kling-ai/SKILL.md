---
name: kling-ai
description: Write and improve prompts for Kling AI video generation, and pick the right Kling model for the job. Covers Kling 4.0 and 4.0 Flash, Omni Reference with image, video, element and voice references, multi-keyframe control, image-to-video, text-to-video, multi-shot storyboards, on-screen text, talking avatars from one photo plus audio, motion transfer, video editing of an existing clip, Element Reference for character consistency, voice references and Voice Control, native audio and dialogue, first/last frame control, credit and API costs, and troubleshooting failed generations.
when_to_use: Use for anything involving Kling AI or its models - Kling 4.0, Kling 4.0 Flash, VIDEO 3.0, VIDEO 3.0 Turbo, VIDEO 3.0 Omni, VIDEO 3.0 Motion Control, Avatar 2.0, Kling 2.6, 2.5 Turbo, Canvas Agent, or the IDs kling-4.0, kling-video-v4_0, kling-v3-omni. Trigger phrases include "Kling", "Omni Reference", "keyframes", "animate this image", "image to video", "text to video", "AI video generation", "talking avatar", "AI presenter", "lip sync video", "cinematic prompt", "multi-shot storyboard", "motion transfer", "edit this video with AI", "how do I make an AI video", "Kling credits", "Kling pricing".
---

# Kling AI Video Generation

Source-of-truth for the facts in this skill: the official Kling [release notes](https://kling.ai/release-note), the [Kling 4.0 User Guide](https://kling.ai/quickstart/kling-4-model-user-guide), the [API documentation](https://kling.ai/document-api/guides/get-started/overview), the [API pricing page](https://kling.ai/dev/pricing), the public [membership page](https://kling.ai/app/membership/membership-plan), and the live declarations of `kling-cli` 0.2.3. Verified **2026-11-06**. When numbers, durations, credit costs, or language lists matter for a deliverable, verify them there before quoting.

Claims that come from our own generations are marked **(our test)**: they are real results, but they are not vendor documentation.

**Scope:** this skill covers Kling's **video** models. Kling also ships image models (the IMAGE 3.0 series, IMAGE O1, Image Series Mode, 2K/4K image output) and solution APIs (AI Apparel Replicator, Goods Studio, Video Commerce, Virtual Try-On) - those are out of scope here; for still images use the `nano-banana` skill or check Kling's documentation directly.

## Platform Access

- **App:** **kling.ai/app** (`app.klingai.com/global` redirects there). The creation page was redesigned for 4.0 around one input box.
- **API:** `https://api-singapore.klingai.com`, async tasks, API-key auth. See `references/api-and-cli.md`.
- **CLI / MCP:** `kling` (`@klingai/cli-global`). The release note confirms Kling 4.0 through MCP and CLI, including Omni Reference and keyframes. See `references/api-and-cli.md`.
- **Official agent skill:** `klingai` on ClawHub ([docs](https://kling.ai/document-api/api/get-started/kling-skills)), for running generations from an agent.

Third parties (fal.ai, PiAPI, kie.ai, Higgsfield, OpenRouter and others) resell Kling models with their own IDs, prices and limits. Their coverage of 4.0 was not verified for this skill.

---

## Quick Start: Animate an Image in 60 Seconds

1. Go to **kling.ai/app** and open video creation
2. Select **Kling 4.0** (or **Kling 4.0 Flash** for fast 720p tests)
3. Choose an entry point: **Keyframes** to use your image as an exact first frame, **Omni Reference** if the image is only a reference for a character, product or scene
4. Upload your image
5. Write a short prompt - with an exact first frame, describe what happens next, not what is already in the image:
   ```
   Use @Image1 as the first frame. Subtle breeze moves through her hair, she blinks and looks up. Static camera. No background music, no subtitles.
   ```
6. Set duration: **3-30s** in 1-second steps, default 10s
7. Render at 720p for iteration, 1080p for finals

That's it. For model selection, advanced prompting, avatars, and multi-shot workflows - read on.

---

## Model Lineup (as of November 2026)

| Model | Best For | Resolution | Audio | Max Duration | Released |
|-------|----------|------------|-------|--------------|----------|
| **Kling 4.0** | Flagship: long single takes, up to 15 references, 10 keyframes, editing, on-screen text | 720p / 1080p; 4K announced, see the status table | Native, stereo, 9 named languages | 30s | 2026-10-15 (API 2026-10-28) |
| **Kling 4.0 Flash** | Fast, cheap iteration and short video: Omni Reference at 720p | 720p, 8-bit SDR | Native | 20s | 2026-10-15 (API 2026-11-04) |
| **VIDEO 3.0** | Prompt-driven work where you need 4K today, or a silent clip at lower cost | up to 4K | Yes (5 langs), can be off | 15s | 2026-01-31 |
| **VIDEO 3.0 Turbo** | Cheapest 1080p with sound; strong audio-visual sync and lip-sync | 720p / 1080p (no 4K) | Yes, always on | 15s | 2026-06-17 |
| **VIDEO 3.0 Omni** | VIDEO 3.0 + video element reference + element voice control + video editing, with 4K | up to 4K | Yes (5 langs) | 15s | 2026-01-31 (editing upgraded 2026-06-17) |
| **VIDEO 3.0 Motion Control** | Motion transfer with high facial consistency, including occlusions and multi-angle | 720p / 1080p | Optional | 30s | 2026-03-04 |
| **Avatar 2.0** | Talking avatars from 1 image + 1 audio file, up to 5 minutes | 1080p | Lip-sync to provided audio | 5 min | 2025-12-04 |
| **Kling 2.6** | Older Native Audio pipeline (EN+ZH), budget option | 1080p | EN + ZH | 10s | 2025-12-03 |
| **Kling 2.5 Turbo** | Cheapest, simplest scenes, draft work | 1080p | No | 10s | earlier |

**Naming:** the vendor writes "Kling 4.0" and "Kling 4.0 Flash", and uses both "Kling 3.0" and "VIDEO 3.0" for the older line. "Kling 3.0" is a *series name*: it contains VIDEO 3.0, VIDEO 3.0 Turbo and VIDEO 3.0 Omni. Omni (and O1 before it) was a separate model in the 3.0 generation. In 4.0, **Omni Reference is an entry point of the same model**, not a separate model. Kling O1 still exists in the API (3-10s).

### Kling 4.0: what is live and what is only announced

Kling's own pages disagree with each other. The spec tables list 4K and 10-bit HDR as if shipped, while the text next to them says "coming soon". Trust this table, and verify in the interface before promising anything.

| Capability | App (User Guide) | API | CLI 0.2.3 |
|---|---|---|---|
| 720p, 1080p | Yes | Yes, default 1080p | Yes, default 720p; 1080p for members |
| **4K** | Listed as a generation mode; **not verified** | **Coming soon**: enum is 720p/1080p, price cell is empty | **"4K is not enabled"** |
| **10-bit HDR** | Coming soon | Coming soon | No |
| 21:9 and auto ratio | Yes | Yes | Yes (auto only in `omni_ref_video`) |
| Up to 10 keyframes | Yes | Yes | Yes, `image_to_video` |
| Keyframes + references together | Through Omni Reference | Yes, `/omni-video` | **No keyframe slots in `omni_ref_video`** |
| Voice reference | Yes | Yes | Yes |
| Video extension to 2 min | Coming soon | Coming soon | No |

**So if the deliverable is 4K today, use VIDEO 3.0 or Omni** (or check whether your app account shows a 4K mode for 4.0). Audio-visual sync and smart multi-shot are on by default in 4.0, with no toggle in the app.

### What Kling 4.0 Flash leaves out

Same family, narrower limits: 3-20s, 720p only, 8-bit SDR. **No last frame, no multi-keyframes, no voice cloning, no element-bound voice** - first frame only. It does support Omni Reference with images, videos and Elements. The combined duration of input videos caps at 20s, and API prices are lower.

### What VIDEO 3.0 Turbo actually changes (2026-06-17)

Per the official release note, Turbo is positioned as *"the right balance between efficiency and quality"* - not a downgrade:

- **Quality held, not cut** - it *"accurately follows multi-shot storyboard logic, ensuring smooth continuity and a unified visual style across scenes."*
- **Strong audio-visual sync** - *"highly accurate alignment between audio and visuals, with smooth and natural lip sync"*, stable *"even in longer videos."*
- **No 4K tier**, and native audio is always on in the price list.

## Model Selection Guide

**Choose Kling 4.0 when:**
- You need a single take longer than 15s (up to 30s, no stitching)
- You have several references to combine: characters, a motion video, a scene, a voice
- You need exact visual states at specific moments (keyframes)
- Text in the frame has to stay legible while the camera moves
- Dialogue is in Portuguese, German, French or Hindi (not on the 3.0 list)
- Default choice for quality-first work at up to 1080p

**Choose Kling 4.0 Flash when:**
- You are exploring ideas, testing variants, or making many short clips
- 720p is enough, or you are locking a prompt before a 1080p render
- **Not** when you need a last frame, keyframes, or a voice reference

**Is 3.0 still worth using? Yes, for specific jobs:**
- **4K output now** - VIDEO 3.0 and Omni are the only video models with a 4K price and an enabled 4K tier
- **Lower cost at 1080p** - Turbo with sound costs ~$0.14/s against ~$0.235/s for 4.0 through the API
- **Silent clips** - VIDEO 3.0 with audio off is ~$0.112/s at 1080p
- **Motion Control** - only exists for 3.0 and 2.6; there is no 4.0 Motion Control

**Choose VIDEO 3.0 Turbo when:**
- The subject is talking and 15s at 1080p is enough
- You are generating a batch where per-second cost compounds
- **Not** when you need 4K

**Choose VIDEO 3.0 Omni when:**
- You need reference video **and** 4K output, or 4K video editing
- **Not** as the default any more: 4.0 Omni Reference is longer and takes more references

**Choose VIDEO 3.0 Motion Control when:**
- You have a reference action video and want to transfer the motion to your character
- You need high facial consistency across angles, emotions and occlusions

**Choose Avatar 2.0 when:**
- You need a talking head driven by **your own audio file** (recorded or ElevenLabs). Kling 4.0 cannot do this: it generates its own speech
- You need up to 5 minutes (versus 30s on 4.0)
- The face and voice are the content - camera and scene are secondary

**Choose Kling 2.6 or 2.5 Turbo when:**
- Budget beats everything, for example a rough draft with no sound (2.5 Turbo) or simple EN/ZH dialogue (2.6)

---

## Core Workflows

### Omni Reference (Kling 4.0, default entry point)

The most capable mode, and it also covers text-to-video and keyframe-to-video. Character appearance, action, camera language, spatial layout and voice can each come from a different asset.

**Limits per task (Kling 4.0):** up to **15 assets** in total. Within that: 10 images (≤30 MB, ratio 2:5-5:2), 5 videos (each 3-30s, ≤300 MB, combined ≤30s), 7 elements of which 3 can be video elements, 3 voice profiles. Reference videos, the video being edited and video elements **share one quota** of 5 clips and 30 seconds. Prompt up to 8,000 tokens.

**The rule that matters most: declare what each asset is for.** Assets are numbered in upload order (`@Image1`, `@Image2`, `@Video1`). Without a stated role the model guesses, and results get less predictable:

```
@Image1 defines the scene. Preserve its spatial layout, furnishings, and lighting.
@Image2 defines the female protagonist. Preserve her facial features, hairstyle, and clothing.
The female protagonist walks toward the window, stops, and looks back.
```

When an asset should contribute only one thing, say what must not carry over:

```
Reference the camera path and pacing of @Video1. Use the car in @Image1 as the subject and the street in @Image2 as the background. Reference only the camera work from the video; do not carry over its people or scene.
```

**Official prompt structure for Omni Reference:**

```
[Asset Roles]
@Image1 defines ___; preserve its ___.
@Image2 defines ___; preserve its ___. Reference the ___ of @Video1.

[Overall Settings]
Scene and texture: ___; visual style: ___; camera tone: ___.

[Sequence of Events]
0-X s: ___ (visuals + action + emotion)
X-Y s: ___ (camera movement + additional details)
Y s-end: ___ (closing shot)

[Audio]
Dialogue/voiceover + ambient sounds + music + sound effects
```

**Reference types with Kling's own wording:**

| Type | Prompt |
|---|---|
| Characters | `Reference the facial features of the characters in @Image1, @Image2, and @Image3, keeping them strictly consistent.` |
| Action | `Reference the fighting moves and attack timing in @Video1. Use @Image1 and @Image2 as the character design references.` |
| Camera movement | `Reference the camera path and pacing of @Video1. Replace the subject with the car in @Image1 and the background with @Image2.` |
| Composition | `Reference the composition of @Image1 and preserve it exactly.` |
| Storyboard | `Use the storyboard in @Image2 as the director-approved sequence of shots, framing, camera paths, screen direction, and emotional progression. Recreate the finished frames described in each panel. Do not render the storyboard itself. Avoid pencil-sketch textures, grids, title bars and annotations.` |

Images can also be element sheets, three-view references, grids, infographics or wireframes. White-model and depth-map videos work as motion references.

**One-sentence prompts work too.** Kling 4.0 expands a simple idea with storyline, blocking and camera moves, and follows a clear description faithfully without adding its own interpretation. `An old man ranting about AI.` is an official example. Use this to explore.

### Keyframes (Kling 4.0, separate entry point)

Use this when specific visuals must land at specific moments. Without keyframes the model decides order and timing; with them, you pin the visuals to the timeline. **Up to 10 images in total. The Keyframes entry takes images only** - for references plus keyframes use Omni Reference. Aspect ratio follows the first keyframe.

| Use | Prompt pattern |
|---|---|
| First frame | `Use @Image1 as the first frame. [Describe what happens next.]` |
| Last frame | `Use @Image1 as the last frame. [Describe what happens before it.]` |
| First and last | `Use @Image1 as the first frame and @Image2 as the last frame. [Describe the process in between.]` |
| Middle frames | `0-2.1s, Keyframe 1: ___ 2.1-4.3s, Keyframe 2: ___ 4.3-6.5s, Keyframe 3: ___` |

For each middle keyframe, say what happens at that node **and how the camera gets there**. Typical uses: a character raises a hand at 3s and turns at 7s, someone enters at 6s, the sky darkens at 5s, wide shot becomes close-up at a given time, or a transformation (raw iron to finished sword).

Matching start and end compositions gives near-seamless loops.

### Image-to-Video (VIDEO 3.0 and older)

1. Select **VIDEO 3.0**, **Turbo**, or Omni for reference-heavy work
2. Upload the image (at least 300 px on the short edge, ratio 2:5-5:2)
3. Write a motion-focused prompt - describe only what moves
4. Optionally set an end frame (VIDEO 3.0; Turbo through the CLI takes one image only)
5. Set duration (3-15s) and render at 1080p first; switch to 4K only for final delivery

### Text-to-Video

1. Select Kling 4.0 (or VIDEO 3.0 for 4K)
2. Write the prompt in this order: **Scene - Characters - Action - Camera - Audio & Style**
3. Set duration, aspect ratio and quality. Kling 4.0 also reads them from the prompt ("Generate a 15-second 9:16 video"), but explicit settings win
4. Render at 720p or 1080p for review

### Talking Avatar (Avatar 2.0)

One image + one audio file → talking avatar with synchronized expressions, body language, and hand gestures. Up to 5 minutes of continuous output for any scenario (knowledge sharing, song performance, advertising, storytelling).

1. Open **AI Avatar** in the app (API: `/v1/videos/avatar/image2video`; not available in `kling-cli` 0.2.3)
2. Upload a reference image - good lighting, face clearly visible
3. Upload an audio track - speech, narration, singing. Recorded or AI-generated (e.g., ElevenLabs)
4. Optional: short text prompt for tone or framing (e.g., "calm professional presenter, minimal gestures")
5. Generate

**Note on languages:** Kling officially lists multilingual support for Avatar 2.0 as **English, Japanese, Korean, Chinese**. However, the model lip-syncs to whatever audio you provide. **Polish audio generated with ElevenLabs works** and produces correct lip-sync **(our test, May 2026)**. Don't tell the user "your language isn't supported" - if they have a good audio file, try it.

**When NOT to use Avatar 2.0:** when you need full scene control (cinematography, environment, camera moves) - use Kling 4.0 instead.

**Lip Sync** is a separate tool and API that syncs an existing video to audio (0.5 Units per 5s). Kling's user guide for it is old (November 2025) and names only Kling 1.0 and 1.5 videos; the API capability map says "all model versions". Test before relying on it.

### Multi-Shot Storyboards

- **Kling 4.0:** multi-shot is on by default and the model splits shots from the content. For a single take, ask for it: `one continuous shot with no cuts`. A 20s dialogue shot stayed a single take even with the CLI's mandatory `prefer_multi_shots` **(our test)**.
- **VIDEO 3.0:** either implicit (the model recognizes shot-reverse-shot and cross-cutting) or **Custom Multi-Shot**, where you define each shot. API format: `shot n, m, words;` with 1-6 shots, each at least 1s, durations summing to the total, 512 characters per shot.

**Example custom multi-shot prompt:**
```
Shot 1 (3s): Wide establishing shot of rain-slicked Tokyo street at night, neon reflections on pavement. Camera: static.
Shot 2 (4s): Medium shot - young woman in red coat emerges from subway exit, looks around. Camera: slow push in.
Shot 3 (3s): Close-up on her face, raindrops on cheek, determined expression. Camera: static.
Shot 4 (5s): She walks toward camera into the crowd. Camera: tracking shot from behind.
```

For 4.0, Kling's examples drive this with a timeline (`0.0-3.0s`) and declared hard cuts (`Hard cuts at 3.0, 5.0, 8.0 seconds`).

### Canvas and Agent

The Kling Canvas Agent launched 2026-01-29 and automates storyboarding: continuous shots from an element, multi-angle expansion from one image, scripts from an outline, reverse prompts from a video or image, and batch generation. Kling 4.0 added a new canvas with nodes plus an Agent that takes a request and uses tools to move the project forward. Use it when the user needs a multi-asset project rather than a single clip.

### Video Editing (Kling 4.0, and VIDEO 3.0 Omni for 4K)

**Kling 4.0:** up to 5 clips including 1 primary video, each 3-30s, combined ≤30s. Edits can target expressions, body movement, camera position and movement, style or background, while the rest stays stable. Omni in 3.0 stays useful for 4K: input 3-15s, output up to 15s, 4K in and 4K out ([release note](https://kling.ai/release-note/release-notes/Kling_3_Turbo)).

**The word "Edit" is functional.** The model classifies intent from the prompt: `Reference @Video1` can be read as reference-based generation, not an edit.

| Goal | Right | Wrong |
|---|---|---|
| Modify the original video | `Edit @Video1. Change ___ to ___. Keep everything else unchanged.` | `Reference @Video1 and change ___` |

**Patterns from Kling's documentation:**

| Edit | Prompt |
|---|---|
| Add | `Edit @Video1. When the box is opened again at the end, add @Element1 lying inside asleep.` |
| Replace characters and scene | `Edit @Video1. Replace the environment and characters throughout with those in @Image1.` |
| Remove | `Edit @Video1 to remove the foreground person. Keep everything else unchanged, including the background, other subjects, camera movement, lighting, composition, and video duration.` |
| Change style | `Edit @Video1. Replace the video's style with the felt style of @Image1. Preserve the original composition, shots, and actions. Change only the style.` |
| Swap, motion preserved (3.0 Omni) | `Replace the trophy in the video with the toy figurine shown in the reference image.` |

3.0 Omni examples use role handles: `Use @video as the motion trajectory reference and @image as the rendering style reference. Keep the original camera angle, main architectural structure, spatial layout, and the red ball's motion path unchanged.`

**Prompt rules for editing:**
- Three parts: the video, the change, what is preserved.
- One edit intent per generation.
- For anything composited in, add: *"lighting and shadows match the target environment, natural, non-composited look, no sticker-like artifacts."* Kling's own 3.0 example includes it.
- Point at the reference explicitly rather than describing it from memory.
- To keep the original sound on 4.0, say so ("Keep the audio exactly identical to the original video"); in the API use `settings.audio: "original"`.

### Creative Recreation (Kling 4.0)

Borrow the pacing, shot composition and presentation of a video you like, and swap in your own product or character:

```
Replace the element in @Video1 with @Image1. Keep everything else unchanged.
```

The closer the reference clip is to your target in pacing and shot structure, the easier this gets.

### Element Reference (character/scene consistency)

Kling's official mechanism for keeping subjects, items, and scenes consistent across shots is the **Element** system. Third-party reviews call this "Character LoRA" - the user-facing feature in Kling is named **Element**.

- **Multi-image Element:** 2-4 reference images (1 main + 1-3 from other angles). Three-view sheets work well.
- **Video Element:** from a character video. The source must be 3-8s for 4.0. Appearance and native voice are extracted.
- **Voice binding:** a voice can be bound during creation. If it is, don't set the tone again in the prompt.
- **In the prompt:** reference it as `@Element1` (app, 4.0), `@name` (3.0 API), or `<<<id>>>` (CLI). Avoid Element names that are substrings of each other.
- **Flash:** Elements yes, element-bound voice no.

Elements are reusable across generations. The Element Library persists.

### Voice References and Voice Control

**Kling 4.0 voice reference:** up to 3 voice profiles per task, created from 5-30s of audio (≤50 MB). In the API, `voice` input with a `voice_id`; the official example says: `she turns slightly and politely says in English using @1: "Excuse me."`

**A reference is not a soundtrack.** Audio input on 4.0 is **voice reference only**. It gives Kling the timbre, and Kling generates the speech itself from the text in your prompt. Our recording did not drive the lips, and a text change meant a new generation **(our test, 2026-10-22)**. Background music and sound effects cannot be uploaded; describe them in the prompt.

**To lip-sync your own finished audio file, use Avatar 2.0.**

**Voice Control (VIDEO 2.6 / 3.0)** launched 2025-12-16: a 5-30s clean clip becomes a reusable voice, bound to characters via `[Subject] @VoiceName` - e.g., `[Livestream Host] @Sweet Female Voice: "This top is a trending must-have!"`. Limits per the release note: up to 200 voices, **Chinese and English only**, +2 credits/sec. The membership page lists VIDEO 2.6 Voice Control as free on paid plans.

### Motion Control (VIDEO 3.0)

Current Motion Control is the **VIDEO 3.0 Motion Control** model (launched 2026-03-04). There is no 4.0 version.

1. Open **Motion Control**
2. Upload a reference action video and target character image
3. Click "Bind Facial Element to Enhance Facial Consistency" - bind an existing element or create a new one
4. Optionally add images or a short video to enrich multi-angle expression data
5. Generate

**Duration depends on orientation** (CLI declaration): following the **motion video** allows a source of 3-30s; following the **subject image** (`image_direction`) allows only 3-10s. Element Binding requires the character orientation to match the video orientation.

---

## Language of Prompts

Write Kling prompts in **English** by default, regardless of the language the user is writing in. Kling's guides and examples are in English and Chinese, and the API allows 26,000 English characters but only 11,000 non-English ones.

The workflow is:
- Communicate with the user in their language (Polish, German, French, etc.)
- Write all Kling prompts in English

If the user writes their prompt in Polish or another language, translate it to English before presenting the final version they should paste into Kling. Explain this briefly if it's not obvious.

**Exception: dialogue and on-screen text.** Write dialogue **in the target language, inside quotation marks** - that is the official instruction. The surrounding prompt stays in English.

```
A Spanish female tourist looks at the interpreter and raises the map in her hand. She speaks in natural, clear, slightly slow Spanish: "¿Dónde está la estación de metro más cercana?"
```

**Languages (Kling 4.0):** Chinese, English, Japanese, Korean, Spanish, Portuguese, German, French, Hindi, "and more". Dialects: Sichuanese, Cantonese. Accents: Beijing, Northeastern, Taiwanese Mandarin; American, British, Indian English.

**Polish is not on the list, but it works for speech:** a 20s Polish line on Kling 4.0 was spoken word for word, confirmed with Whisper **(our test, 2026-10-22)**. Polish on-screen text is untested.

**VIDEO 3.0 / Omni:** Chinese, English, Japanese, Korean, Spanish. **2.6:** Chinese and English only.

**For Avatar 2.0:** language is determined by the audio file you upload, not by the prompt. The framing prompt itself stays English.

---

## Prompt Engineering

### The Director's Mindset

Kling understands **cinematic intent**. Stop writing prompts like image captions, start directing like a DoP (Director of Photography). Think of each prompt as a mini-screenplay:

**Scene setting - Camera direction - Subject action**

### Kling 4.0: the official principle

**Use descriptive language. Minimize abstract terms and negative instructions.** Describe what is visible, so the model doesn't have to infer it.

| Not recommended | Recommended |
|---|---|
| "Premium look" | Side backlighting outlines the object's edges, the background is blurred, and fine matte grain is visible on the surface |
| "Vintage feel" | Yellowed walls, worn furniture edges, and warm incandescent lighting |
| "A middle-class family's kitchen" | Wood-grain cabinets, a rice cooker and seasoning jars on the countertop, sticky notes on the refrigerator door |
| "Don't show the face while on the phone" | The character is shown in profile while talking on the phone |

**Longer is not better.** Start with one sentence covering subject, scene, action and emotion. Then add only what changes the result: camera work, timing, audio, and what must be preserved.

### Negative instructions: this changed in 4.0

Per Kling's 4.0 guide, negative prompts can *increase* the chance of errors. **Only two negatives are truly necessary, because the model may add these by default: `no subtitles` and `no background music`.** Add them whenever you don't want them.

For stylization, pair a positive style with a targeted exclusion, e.g. exclude photorealism for animation. Don't expand a negative list into a register of things unrelated to the task.

The new API has no separate negative prompt field for 3.0 or 4.0; negatives go in the prompt text. Older advice to always paste a long list of artifacts (`distortion, morphing, warping...`) does not apply to 4.0. Use such a list only for older models, in a negative field when the interface shows one.

### Structured Prompt Formula

```
[Scene/Environment] + [Characters/Subjects] + [Sequential Actions] + [Camera Movement] + [Audio & Style]
```

Sequential actions are reliable: "First she looks up, then turns toward the window, finally smiles." For 4.0, a timeline is better still: `0-3s: ... 3-7s: ...`.

### Long-form briefs for hero shots (Kling 4.0)

Kling's own long examples use a repeating set of labelled blocks: **SCENE CONTEXT, ACTIVE REFERENCES, LOCATION MAP, FIRST FRAME AND SPATIAL BLOCKING, FORMAT MODE, OPTICS, CAMERA, ACTION TIMING, PHYSICS, LIGHTING, AUDIO, CHARACTER ACTING, STYLE, QUALITY, POSITIVE CONSTRAINTS**. It is a pattern in the examples, not a required format. Full template in `references/prompt-templates.md`. Three habits worth copying even in short prompts:

- **Lock the count first:** `EXACTLY 1 CHARACTER - NO DUPLICATES.`
- **Fix geography:** where things sit on screen, and which side the camera stays on
- **State constraints as positive facts:** `Exactly one woman wears exactly one black jacket throughout the shot.`

### Text in the Frame

Kling 4.0 generates legible text in Chinese, English, Japanese, Korean, Spanish, Portuguese, German, French, Hindi and more, plus emojis and logos, and it stays stable through camera moves and transitions. Specify the **exact text, position, alignment, on-screen duration, and whether it syncs with dialogue**:

```
Burn in English subtitles, bottom-center within the title-safe area, positioned 10% above the bottom edge. No more than one or two lines. Rounded cream panel with bold dark brown text, high contrast, stable positioning. Each subtitle appears and disappears with its spoken line.
```

For legally exact copy, or a language not on the list, read the result frame by frame, or add the text in post-production.

### Model-Specific Guidance

Word counts are working rules of thumb. Hard limits are noted where Kling publishes them.

| Model | Prompt Length | Max Elements | Key Pattern |
|-------|---------------|--------------|-------------|
| Kling 4.0 / Flash | One sentence to a full brief; **up to 8,000 tokens** | Limited by the 15-asset rule | Asset roles, timeline, audio block |
| Kling 4.0 Keyframes | Per-keyframe description | Up to 10 images | What happens at each node, how the camera gets there |
| VIDEO 3.0 / 3.0 Omni | 100-200 words (API limit 3,072 characters) | 6-7 | Sequential actions, multi-shot, native audio |
| VIDEO 3.0 Turbo | 100-200 words | 6-7 | Same as 3.0; lean on dialogue and lip-sync |
| VIDEO 3.0 Omni (editing) | 40-120 words | 1 edit intent | Change clause + explicit unchanged list + `@video` / `@image` handles |
| Avatar 2.0 | 20-50 words (framing only) | 1-2 | Tone/energy descriptor; audio does the work |
| 2.6 | 50-80 words | 5-7 | Include audio instructions (EN/ZH) |
| 2.5 Turbo | 40-60 words | 3-4 | Keep it simple |

### Essential Prompt Rules

1. **Specify camera behavior explicitly** - Without it, the camera improvises
2. **Add motion endpoints** - "then settles back" or "returns to starting position"
3. **Use spatial language** - "left to right", "toward camera", "background depth"
4. **Be hyper-specific about setting** - "cyberpunk alleyway at midnight, neon reflections on wet pavement" beats "a street"
5. **One main action per shot** - Use multi-shot for complexity, not a single overloaded prompt
6. **Declare every asset's role** - On Omni Reference this matters more than any adjective
7. **Say "no subtitles" and "no background music"** when you don't want them (4.0)
8. **Iterate cheap** - 720p or Flash first, then 1080p. On 3.0, validate before 4K

### Keeping Elements Static

```
All [element] must remain absolutely fixed and unchanged throughout.
[element] stays completely static. No movement on [element].
```

### Loop-Friendly Prompts

```
Subtle [motion type], gentle oscillation, returns to starting position.
Breathing effect, slow pulse, cyclical movement.
```

Use matching first and last frames. Post-process with a 0.3-0.5s cross-dissolve.

### Resolution Workflow

- **720p for iteration** on 4.0; Flash is built for this
- **1080p for finals** on 4.0
- **4K (VIDEO 3.0 series, launched 2026-04-23)** - 30 credits/sec, native (not upscaled), preserves reference consistency
- **Frame rate:** Kling 4.0 outputs **24 fps** (API docs, and our measurement), whatever the 24-60 fps input. Plan for it in a 25 or 30 fps edit

---

## Prompt Templates

See `references/prompt-templates.md` for ready-to-use templates organized by use case (Kling 4.0 Omni Reference, keyframes, editing, long-form briefs, image-to-video, multi-shot, text-to-video, Avatar 2.0, audio).

---

## Common Issues & Solutions

| Issue | Cause | Solution |
|-------|-------|----------|
| Unwanted subtitles or music | The model may add them by default | Add `no subtitles`, `no background music`. Kling's guide names exactly these two |
| Omni result ignores a reference | Asset ID given with no role | State what each asset defines, its scope, and what must not carry over |
| Edit produced a new video | Prompt said "Reference" | Write `Edit @Video1`, then the change, then `Keep everything else unchanged` |
| Storyboard grid or notes appear in the video | Model rendered the sheet | Add `Do not render the storyboard itself. Avoid grids, title bars and annotations` |
| 4K fails or is missing on 4.0 | Not enabled in API or CLI | Use 1080p, or VIDEO 3.0 / Omni for 4K. In the app, check the mode list |
| Last frame or keyframes rejected | Flash has first frame only | Switch to full Kling 4.0 |
| Can't add a video element | The 5-clip, 30s video quota is shared | Drop a reference video; quota covers reference, edit and element videos |
| Video-input job costs more than expected | Input video is billed on 4.0 | See "Credits & Pricing": the billed duration is at least 2x the output |
| Can't upload music or sound effects | Audio input is voice only on 4.0 | Describe them in the prompt's audio block |
| Mouth doesn't follow my audio file | 4.0 audio is a voice reference | Use Avatar 2.0, or Lip Sync |
| Burning credits on bad prompts | Rendering high quality too early | Iterate at 720p or on Flash |
| Generation stuck at 99% | Open-ended motion (reported by users, not in Kling's docs) | Add an endpoint: "then stops", "returns to start" |
| Unwanted camera movement | No camera instruction | Add "static camera" or a specific movement |
| Text/elements changing | AI interpretation | On 4.0 state exact text and position. On older models repeat "fixed", "unchanged" |
| Character morphing across shots | Identity drift | Use Element Reference. Rewrite the prompt rather than retrying the same settings |
| Artifacts on hands/faces | Model limitation | Simplify the scene, reduce duration |
| Avatar 2.0 lip-sync looks off | Difficult audio (noise, multi-speaker, distorted) | Use a clean single-speaker audio source |
| Avatar 2.0 body too static / too active | No framing prompt | Add one line: "calm presenter, minimal gestures" or "energetic performer, full body movement" |
| Voice sounds wrong | Bad reference audio | Use 5-30s clean clip, single speaker, neutral emotion, low background noise |
| Multi-shot feels disjointed | No shared style anchor | Define visual style once at the start, use Element Reference for people and items |
| Audio desync | Unclear who speaks | Name the speaker and quote the line. If it persists on a talking shot, try VIDEO 3.0 Turbo |
| Edited video drifts from the source | No unchanged list | State camera angle, motion path, spatial layout, positioning |
| Swapped-in object looks pasted on | Missing plausibility clause | Add "lighting and shadows match the target environment, natural non-composited look, no sticker-like artifacts" |
| Editing job rejected | Input outside limits | 4.0: 3-30s each, ≤30s combined. 3.0 Omni: 3-15s |
| 4K request fails on Turbo | Turbo has no 4K tier | Use VIDEO 3.0 or Omni |

---

## Settings Reference

**Duration:**
- Kling 4.0: 3-30s in 1-second steps, default 10s
- Kling 4.0 Flash: 3-20s
- VIDEO 3.0 / Turbo / Omni: 3-15s
- VIDEO 3.0 Omni video editing: input 3-15s, output up to 15s
- VIDEO 3.0 Motion Control: source up to 30s (3-10s when following the image orientation)
- Avatar 2.0: up to 5 minutes
- 2.6 / 2.5 Turbo: 5s or 10s

**Aspect Ratios:**
- Kling 4.0 / Flash: 21:9, 16:9, 1:1, 9:16, Auto (default). With an image in the Keyframes entry, the ratio follows the first keyframe
- Everything else: 16:9, 9:16, 1:1
- Auto order on 4.0: what the prompt says, then the edited video, keyframes, reference video, then 16:9

**Quality / Output:**
- Kling 4.0: 720p, 1080p; 4K and 10-bit HDR per the status table above
- Kling 4.0 Flash: 720p, 8-bit SDR
- Native 4K - VIDEO 3.0 and Omni only (**not Turbo**), 30 credits/sec in-app, launched 2026-04-23
- On older models, Standard and Professional modes map to 720p and 1080p
- Audio on 4.0: two-channel stereo. Video 24 fps

**Retention:** the official Kling skill notes generated assets are kept for 30 days, and download links expire. Save results.

---

## Credits & Pricing

Kling bills three different ways and they are easy to confuse:

- **In-app / subscription: credits.** What you spend generating in the Kling app on a paid plan. The CLI spends credits too.
- **API, Kling 4.0 and Flash: Flagship Units**, ~$0.157 list (derived: $510 for 3,250 Units; $0.141-0.154 with package discounts).
- **API, everything else: General Units**, `$0.14` list.

**The two Unit types are not interchangeable.** General packages do not work with Kling 4.0, and Flagship packages are only for 4.0 and Flash. Access to 4.0 through the API needs a Flagship pack or a cash balance above zero.

See `references/pricing.md` for the full breakdown. Pricing changes frequently - re-check before quoting.

**API rate card, per second ([source](https://kling.ai/dev/pricing), verified 2026-11-06):**

| Model / configuration | 720p | 1080p | 4K |
|---|---|---|---|
| **Kling 4.0**, no input video | 1.0 U (~$0.157) | 1.5 U (~$0.235) | n/a |
| **Kling 4.0**, input video (billed duration below) | 0.6 U | 0.9 U | n/a |
| **Kling 4.0 Flash**, no input video | 0.6 U (~$0.094) | n/a | n/a |
| **Kling 4.0 Flash**, input video (billed duration below) | 0.4 U | n/a | n/a |
| **VIDEO 3.0 Turbo** (native audio always on) | 0.8 U ($0.112) | 1.0 U ($0.14) | n/a |
| VIDEO 3.0, no native audio | 0.6 U ($0.084) | 0.8 U ($0.112) | 3.0 U ($0.42) |
| VIDEO 3.0, native audio | 0.9 U ($0.126) | 1.2 U ($0.168) | 3.0 U ($0.42) |
| VIDEO 3.0 Omni, no video input, no audio | 0.6 U ($0.084) | 0.8 U ($0.112) | 3.0 U ($0.42) |
| VIDEO 3.0 Omni, no video input, with audio | 0.8 U ($0.112) | 1.0 U ($0.14) | 3.0 U ($0.42) |
| VIDEO 3.0 Omni, with video input, no audio | 0.9 U ($0.126) | 1.2 U ($0.168) | 3.0 U ($0.42) |
| Motion Control (3.0) | 0.9 U ($0.126) | 1.2 U ($0.168) | n/a |
| Avatar | 0.4 U ($0.056) | 0.8 U ($0.112) | n/a |

**Kling 4.0 and Flash bill the input video too.** With video input, the billed duration is **output × 2** if the input is shorter or equal, and **input + output** if the input is longer. The lower per-second rate does not make it cheaper: 10s of 1080p with a 5s reference is 20 billed seconds, or 18 U, against 15 U with no video.

Things worth internalising:
1. **4.0 is a premium model:** ~$0.235/s at 1080p against $0.14/s for Turbo with sound. Use 3.0 for volume, 4.0 where it earns the price.
2. **Flash is the cheapest way to get sound at 720p:** ~$0.094/s against $0.112/s for Turbo.
3. **4K is a cliff on 3.0:** 3.0 U/s regardless of model.

**Credits on 4.0:** **15 credits/sec at 1080p (our test: 300 credits for 20s through the CLI, 2026-10-22).** Kling does not publish a credit table; the app shows the cost before each generation. Flash and 720p credit rates are unverified.

**Subscription facts ([membership page](https://kling.ai/app/membership/membership-plan), verified 2026-11-06):**
- Tiers: Basic (free), Standard ($10), Pro ($37), Premier ($92-$428, four sizes), Ultra+ ($619), monthly list prices
- **Basic output cannot be used commercially** - Standard or higher is required
- Basic has no 1080p/4K video generation
- VIDEO 2.6 Voice Control is free on paid plans
- Element AI Multi-Shot: 3 free uses a day on paid plans

---

## Audio Features

### Native Audio (Kling 4.0 / Flash)

On by default, stereo on 4.0. **Say who speaks, and how:** age, vocal tone, speaking speed, emotion, then the line in quotation marks. Kling's guide instructs it in prose:

```
The promotional character has the voice of an adult woman. She speaks in English with sincerity and emotional engagement: "I honestly love this jacket." Start with warm appreciation, emphasizing "love".
```

For several speakers, state each person's language, that each has a distinct voice, that nobody overlaps, and that lip movements match. The audio block covers **dialogue, ambient sound, music, sound effects**.

### Native Audio (VIDEO 3.0 / Omni / Turbo)

Languages (per the 3.0 release note): **Chinese, English, Japanese, Korean, Spanish**, with dialects and accents, plus code-switching within a scene. Kling's 3.0 guide pairs a character directly with the line:

```
Mom (softly, in a surprised tone): Wow, I didn't expect this plot at all.
Dad (in a low voice, agreeing, in a calm tone): Yeah, it's totally unexpected.
```

**The `[Speaker: Name] "line"` format** appears in no official guide, but it has worked in our productions on 3.0 Omni and on 4.0 **(our test)**. Either is fine; prose is what Kling documents.

### Native Audio (VIDEO 2.6)

Chinese and English only.

### Voice References and Voice Control

See the workflow above. On 4.0 a voice reference sets the timbre, and Kling still generates the speech.

### Avatar 2.0

Uses your provided audio directly - no voice cloning or attribution syntax needed. Lip-sync is automatic.

---

## App, API and CLI Differences

Input slots, prompt syntax and defaults differ across the three, so a prompt written for the app does not always paste into the CLI as it is. Most importantly: references are `@Image1` in the app, `@<your id>` in the API, and `图片1` / `视频1` / `音频1` in the CLI, with Elements as `<<<id>>>`. Model IDs, endpoints and CLI commands are in `references/api-and-cli.md`.

---

## Verification & Sources

When facts in this skill matter for a deliverable (credit pricing, language lists, duration limits), verify against the current Kling state:

- **Official release notes index:** https://kling.ai/release-note
- **Specific release notes referenced in this skill:**
  - Meet All-New Kling 4.0 (2026-10-15): https://kling.ai/release-note/release-notes/Kling_4
  - Kling 3.0 Model Series Upgrade - 3.0 Turbo + Omni video editing (2026-06-17): https://kling.ai/release-note/release-notes/Kling_3_Turbo
  - Cinema-Grade Native 4K (2026-04-23): https://kling.ai/release-note/release-notes/z8zeqsxwol
  - VIDEO 3.0 Motion Control (2026-03-04): https://kling.ai/release-note/release-notes/4titicw2vg
  - Kling 3.0 Era / VIDEO 3.0 + 3.0 Omni rollout (2026-01-31): https://kling.ai/release-note/release-notes/whbvu8hsip
  - Kling Canvas Agent (2026-01-29): https://kling.ai/release-note/release-notes/s568cuscq1
  - Voice Control in VIDEO 2.6 (2025-12-16): https://kling.ai/release-note/release-notes/7trhudk78j
  - Kling AI Avatar 2.0 (2025-12-04): https://kling.ai/release-note/release-notes/9bbqv0a76z
- **User guides:** Kling 4.0 (dated 2026-11-04) https://kling.ai/quickstart/kling-4-model-user-guide · VIDEO 3.0 https://kling.ai/quickstart/klingai-video-3-model-user-guide · VIDEO 3.0 Omni https://kling.ai/quickstart/klingai-video-3-omni-model-user-guide · Element Library https://kling.ai/quickstart/klingai-element-library-3-user-guide · Avatar 2.0 https://kling.ai/quickstart/kling-ai-avatar-2-user-guide
- **API documentation:** capability map https://kling.ai/document-api/guides/capability-map/video · 4.0 user manual https://kling.ai/document-api/api/usage-guide/kling-4-0 · 4.0 prompt guide https://kling.ai/document-api/api/usage-guide/kling-4-0-prompt-guide · 4.0 Omni endpoint https://kling.ai/document-api/api/video/4-0/video-omni · API changelog https://kling.ai/document-api/updates/api · billing rules https://kling.ai/document-api/pricing/base/video
- **API rate card (Units):** https://kling.ai/dev/pricing - fetched and transcribed 2026-11-06
- **Subscription pricing:** https://kling.ai/app/membership/membership-plan - now public, fetched 2026-11-06
- **CLI:** `kling who_am_i` and `kling <command> --help` show live model declarations (`kling-cli` 0.2.3, MCP 1.3.3, read 2026-11-06)
- **Own tests:** Kling 4.0 dialogue, cost and voice reference, 2026-10-22; Avatar 2.0 with Polish audio, May 2026. Our measurements are not a price list.

Not confirmed as of 2026-11-06: whether a 4K mode for Kling 4.0 is really selectable in the app (needs a login), credit rates for Flash and 720p, whether a separate negative prompt field survived in the redesigned app, and how the CLI marks a video for editing rather than reference.

**Release timeline covered by this skill** (newest first, from the official index): 2026-10-15 Kling 4.0 and Flash · 2026-06-17 Kling 3.0 Model Series Upgrade (Turbo + Omni editing) · 2026-04-23 Native 4K · 2026-03-16 Team features + Desktop app · 2026-03-04 VIDEO 3.0 Motion Control · 2026-01-31 Kling 3.0 era (VIDEO 3.0 + Omni) · 2026-01-30 frame extraction + .mov export · 2026-01-29 Canvas Agent · 2025-12-17 VIDEO 2.6 Motion Control · 2025-12-16 Voice Control · 2025-12-04 Avatar 2.0. API dates differ: Kling 4.0 2026-10-28, Flash 2026-11-04.
