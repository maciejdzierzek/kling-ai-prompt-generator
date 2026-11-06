# Kling AI Prompt Templates

Ready-to-use templates organized by use case. Replace bracketed placeholders with specific content.

Kling 4.0 templates come first. Syntax below is for the app (`@Image1`). In the API use your own `@id`, and in the CLI use `图片1`, `视频1`, `音频1` and `<<<element_id>>>` - see `api-and-cli.md`.

## Kling 4.0: Omni Reference Templates

Declare what every asset is for. Without a role, the model guesses.

### Basic Structure (official)

```
[Asset Roles]
@Image1 defines [what]; preserve its [which traits].
@Image2 defines [what]; preserve its [which traits]. Reference the [motion / camera path / pacing] of @Video1.

[Overall Settings]
Scene and texture: [concrete surfaces, light]; visual style: [style]; camera tone: [handheld / locked off].

[Sequence of Events]
0-[X]s: [visuals + action + emotion]
[X]-[Y]s: [camera movement + additional details]
[Y]s-end: [closing shot]

[Audio]
[Dialogue in quotes], [ambient sound], [music or "no background music"], [sound effects].
```

### Character in a Scene

```
@Image1 defines the scene. Preserve its spatial layout, furnishings, and lighting.
@Image2 defines the [character]. Preserve [their] facial features, hairstyle, and clothing.
The [character] [action], [second action], and [resolving action].
```

### Motion Transfer From a Video

```
Reference the [fighting moves / dance / gestures] and timing in @Video1. Use @Image1 as the character design reference. Reference only the motion from the video; do not carry over its people or scene.
```

### Camera Move Transfer

```
Reference the camera path and pacing of @Video1. Replace the subject with [the product] in @Image1 and the background with @Image2.
```

### Creative Recreation

```
Replace the [subject] in @Video1 with [the subject] from @Image1. Keep everything else unchanged, including the background composition, camera movements, lighting, shadows, audio, and video duration. Ensure the replacement integrates naturally into the original footage.
```

### Storyboard to Film

```
Reference the character design in @Image1 and use the storyboard in @Image2 as the director-approved sequence of shots, framing, camera paths, screen direction, and emotional progression for this scene. Recreate the finished [style] frames described in each storyboard panel. Do not render the storyboard itself. Avoid pencil-sketch textures, grids, title bars, annotations, and director's notes.
```

### One-Sentence Exploration

```
[Who] [does what], [emotion or tone].
```

Kling expands this with storyline, blocking and camera moves. Good for a first result, then add detail.

## Kling 4.0: Keyframes Templates

Keyframes entry: images only, up to 10 in total. For keyframes plus reference assets, use Omni Reference. Not on Flash, except a single first frame.

### First Frame

```
Use @Image1 as the first frame. [Describe what happens next, in order.]
```

### First and Last Frame

```
Use @Image1 as the first frame ([state A]) and @Image2 as the last frame ([state B]). Generate a [N]-second video showing [the process], in a [style] style. The final frame matches @Image2 exactly.
```

### Single Continuous Shot Between Two Frames

```
Use @Image1 as the first frame and @Image2 as the last frame. The entire video is one continuous [lateral tracking] shot, with no cuts, angle changes, or scene changes.
```

### Last Frame Only

```
Use @Image1 as the last frame. [Describe what happens before it, and how the scene arrives at this composition.]
```

### Middle Keyframes on a Timeline

```
0-[X]s | Keyframe 1: Strictly match @Image1. [What happens, and how the camera arrives.]
[X]-[Y]s | Keyframe 2: Hard cut to @Image2. [What happens.]
[Y]-[Z]s | Keyframe 3: [Describe the connection to the previous node.] Match @Image3.
```

## Kling 4.0: Video Editing Templates

Always write `Edit`, because `Reference` can route the job to generation. Keep one intent per generation.

### Targeted Change

```
Edit @Video1. Change [what] to [what]. Keep everything else unchanged.
```

### Replace Subject and Scene

```
Edit @Video1. Replace the environment and characters throughout with those in @Image1.
```

### Remove an Element

```
Edit @Video1 to remove [the foreground person]. Keep everything else unchanged, including the background, other subjects, camera movement, lighting, composition, and video duration. Seamlessly reconstruct the areas previously obscured, with natural, consistent details.
```

### Style Change Only

```
Edit @Video1. Replace the video's style with the [felt] style of @Image1. Preserve the original composition, shots, and actions. Change only the style; do not alter [characters' clothing, scene elements, or the event sequence].
```

### Replace a Spoken Line

```
Edit @Video1. Replace the final line, "[old line]", with "[new line]". Keep everything else unchanged.
```

Add `Keep the audio exactly identical to the original video. Do not add any new sounds.` when the sound has to stay.

## Kling 4.0: Dialogue and Language

Write dialogue in the target language, inside quotation marks. Keep the rest in English.

### One Speaker

```
[Character description] speaks directly to camera in [natural, clear, slightly slow] [language], [warm and sincere]: "[line in that language]" No background music, no subtitles.
```

### Several Speakers

```
Exactly [2] people. [Person A, position] says in [language]: "[line]" After a short pause, [Person B, position] answers in [language]: "[line]"
Audio: each person has a distinct voice. When one person is speaking, the others remain silent. No interruptions or overlapping dialogue. All dialogue has clear vocals, with lip movements synchronized. Subtle [room] ambience. No background music.
```

### With a Voice Reference

In the app, upload the voice profile. In the API, add a `voice` input:

```
Use @image_1 as the character reference. [Action]. [She] [says] in English using @1: "[line]"
```

The voice sets the timbre; Kling generates the speech. To lip-sync your own audio file, use Avatar 2.0.

## Kling 4.0: On-Screen Text

### Text in the Scene

```
[Surface or object] shows the text "[EXACT TEXT]" in [font character], [color], [position]. The text stays clear, correctly spelled, and attached to the same position throughout.
```

### Burned-In Subtitles

```
Burned-in [English] subtitles, bottom-center inside the title-safe area, positioned 10% above the lower edge. One or two lines maximum. [Rounded cream panel with dark bold lettering], high contrast, stable placement. Subtitles appear and disappear exactly with each spoken line.
```

Without this, write `no subtitles`: the model may add them by default.

## Kling 4.0: Long-Form Brief

Kling's long official examples use the blocks below, for hero shots of 15-30s. It is a pattern from their examples, not a required format; use only the blocks that change the result.

```
SCENE CONTEXT: EXACTLY [1] CHARACTER - NO DUPLICATES. [What happens in one or two sentences.]
ACTIVE REFERENCES: @Image1 controls [what]. @Image2 controls [what].
LOCATION MAP: [Where things sit on screen, which side the camera stays on, direction of travel.]
FIRST FRAME AND SPATIAL BLOCKING: [Exact opening positions.]
FORMAT MODE: [N] seconds, [one continuous shot / X shots with hard cuts at A, B, C seconds]. [No fades, dissolves, speed ramps.]
OPTICS: [Equivalent focal length, field of view, distance to subject, depth of field.]
CAMERA: [How a real operator moves: handheld sway, delayed reframing, speed. Which camera moves happen when.]
ACTION TIMING: 0.0-[X]s: [action]. [X]-[Y]s: [action].
PHYSICS: [Weight, inertia, contact, what reacts to what.]
LIGHTING: [Key source and direction. What stays protected.]
AUDIO: [Ambience, sound effects tied to actions, music or "no music".] [Dialogue in quotes.]
CHARACTER ACTING: [Observable behavior: gaze, breath, gesture, irregular blinks.]
STYLE: [Genre, texture, palette in percentages, film grain, "no digital sharpening".]
QUALITY: [What must stay consistent: identity, geometry, logos, hands.]
POSITIVE CONSTRAINTS: Exactly one [X] throughout. [State what must be true, not what to avoid.]
```

**Realism habits from these examples:** a human operator with visible imperfection instead of a stabilized camera, one motivated light source, and specific texture language such as `old-photograph softness, organic film grain, restrained contrast, no digital sharpening`.

---

## Image-to-Video Templates (motion-only prompts)

For a Kling 3.0 image-to-video slot, or the first-frame path on 4.0. On 4.0, prefix with `Use @Image1 as the first frame.`

### Product Animation (Static Camera)

```
Subtle glow pulsation on [product], gentle ambient light shifting across surfaces. Faint reflection movement. Camera remains completely static. Background stable and unchanged. Minimal motion, premium feel.
```

### Product Rotation

```
[Product] slowly rotates 45 degrees clockwise, then returns to original position. Soft studio lighting with subtle highlight sweep across surface. Static camera, dark background unchanged. Smooth, continuous motion.
```

### Portrait Animation

```
Subject's hair moves gently as if touched by soft breeze. Subtle eye movement, natural micro-expressions. Clothing fabric shifts slightly. Camera static, background completely fixed. Cinematic lighting unchanged.
```

### Holographic/Tech UI

```
Subtle holographic scanning effect on [element], gentle glow pulsation, faint scan line moving across surface. Ambient light intensity shifting slowly. Static camera. All text labels and UI elements remain absolutely fixed and unchanged. Dark background stable.
```

### Nature Scene

```
Leaves sway gently in breeze, water surface ripples softly, clouds drift slowly in background. Birds fly across distant sky. Camera remains static. Warm natural lighting. Peaceful, continuous motion.
```

### Logo Animation (Minimal)

```
Subtle light reflection passes across [logo/text], gentle ambient glow pulsation. Logo and all text remain completely fixed and unchanged in position and shape. Background static. Elegant, minimal motion.
```

---

## Avatar 2.0 Templates

Avatar 2.0 uses your provided audio for lip-sync, body language, and expression. Prompts are short - tone and energy framing, not scene direction. Keep them under 50 words.

### Corporate Presenter (Narration)

```
Professional presenter, calm and confident, soft natural smile.
Minimal hand gestures, occasional natural emphasis.
Steady eye contact with camera. Slight breathing movement.
Soft studio lighting, neutral background.
```

### Energetic Explainer (YouTube-style)

```
Enthusiastic creator speaking to camera, expressive face.
Active hand gestures, head movement to emphasize key points.
Warm lighting, plain background.
Energy: high but controlled, conversational pace.
```

### Singer / Music Performance

```
Vocal performer, eyes closed during emotional phrases, head tilts with phrasing.
Hand gestures match musical dynamics.
Stage lighting with subtle backlight.
Posture: confident, full body present in frame.
```

### Educational / Documentary Narrator

```
Thoughtful presenter, measured pace.
Subtle facial reactions to content, occasional gestural emphasis.
Soft directional lighting, slight depth in background.
Calm, intellectual energy.
```

### Quick Setup Checklist for Avatar 2.0

1. Source image: face clearly visible, neutral or slight expression, even lighting, no extreme angle
2. Audio: clean recording or AI-generated TTS (ElevenLabs etc.), no background music behind speech (music OK if the performance IS music)
3. Officially listed lip-sync languages: **EN, JA, KO, ZH**. In practice the model syncs to whatever audio you provide - **field-confirmed working with Polish ElevenLabs audio** and likely other Latin-script languages. Try unlisted languages instead of assuming they won't work.
4. Duration: up to 5 minutes single continuous generation, covers all scenarios (narration, song, advertising, storytelling)
5. Optional tone/style prompt - 20-50 words framing energy and gesture level

---

## Multi-Shot Storyboard Templates (VIDEO 3.0, also fine on 4.0)

### Short Narrative (4 shots, ~12s)

```
Shot 1 (3s): [Wide establishing shot description, time of day, weather]. Camera: static.
Shot 2 (3s): [Medium shot of main character, action begins]. Camera: slow push in.
Shot 3 (3s): [Close-up on face or detail, reaction]. Camera: static.
Shot 4 (3s): [Resolution - character walks away / reaches destination / completes action]. Camera: [tracking / pull back].
```

### Product Launch (3 shots, ~10s)

```
Shot 1 (3s): [Product on surface, wide studio shot]. Dramatic lighting from above. Camera: static.
Shot 2 (4s): [Camera orbits slowly around product, highlighting [key feature]]. Studio lighting.
Shot 3 (3s): [Close-up macro on [signature detail]: texture, logo, finish]. Camera: slow dolly in, then hold.
[Speaker: Narrator] "[tagline]" in a confident, clear voice. Background: soft ambient hum.
```

### Social Media Hook (3 shots, ~9s)

```
Shot 1 (2s): [Attention-grabbing close-up of result / final state]. Camera: fast push in.
Shot 2 (4s): [The process / journey / transformation]. Camera: tracking.
Shot 3 (3s): [Final reveal, return to result]. Camera: pull back to wide.
```

---

## Text-to-Video Templates (VIDEO 3.0)

### Cinematic Portrait

```
Setting: [location with specific atmospheric detail, time of day, light quality].
Subject: [Age] [gender] with [hair description] and [clothing], [expression] expression.
Action: First [initial state], then [main action], finally [resolving gesture].
Camera: [slow push in / static medium shot / gentle orbit]. 35mm lens, shallow depth of field.
Style: Cinematic, film grain, [mood].
```

### Product Commercial

```
Setting: [product] on [surface material] pedestal in [environment with specific details].
Action: Camera slowly orbits clockwise around product. [Specific feature] catches light, creating [reflection/highlight type]. [Secondary element] in soft focus background.
Camera: smooth orbit, 270-degree arc, then settles to front-facing.
Style: Studio lighting with [light quality]. Premium advertisement aesthetic.
```

### Action Scene (Sequential)

```
Setting: [environment with specific atmospheric detail].
Subject: [character description].
Action: First [setup action], then [peak action with physics detail], finally [landing/resolution].
Camera: [wide establishing for setup] / [tracking shot for peak action] / [static for resolution].
Style: [time of day] lighting. Motion blur on fast elements. Dust/particles in air.
```

### Talking Head with Audio (VIDEO 3.0)

*For talking-head content longer than 15s, or driven by your own audio file, use Avatar 2.0 instead - see Avatar 2.0 Templates section above. Kling 4.0 goes up to 30s with its own generated speech.*

```
Setting: [Person description] in [setting with specific background details].
Action: Speaks directly to camera with natural hand gestures.
Camera: Medium close-up, static, slight breathing movement.
[Speaker: [Name/role]] "[dialogue - 1-2 sentences]" in a [warm/confident/excited] voice with [accent].
Background ambient: [office sounds / cafe sounds / none].
Style: Soft studio lighting, shallow depth of field.
```

### Atmospheric Loop

```
Setting: [Scene with primary motion element and atmospheric context].
Action: [Primary element] [cyclical motion]. [Secondary element] moves slowly in background. [Atmospheric effect: fog drifts / dust particles float / light rays shift]. All elements return to approximate starting position.
Camera: Static, locked off.
Style: Peaceful ambient mood, [lighting keyword].
```

---

## Camera Movement Vocabulary

### Supported Movements
- `static camera` / `locked off shot` - no movement
- `slow push in` / `dolly in` - camera moves toward subject
- `pull back` / `dolly out` - camera moves away from subject
- `pan left/right` - horizontal rotation
- `tilt up/down` - vertical rotation
- `orbit` / `arc shot` - circular movement around subject
- `tracking shot` - follows moving subject
- `crane up/down` - vertical camera movement
- `low angle looking up` - dramatic upward perspective
- `POV shot` - first-person perspective
- `shot-reverse-shot` - dialogue coverage between two subjects

### Movement Modifiers
- `slow` / `gentle` / `subtle` - reduced speed
- `smooth` / `fluid` - no jerky motion
- `gradual` - progressive change
- `snap` / `whip` - fast, abrupt movement

---

## Style Keywords

### Lighting
`cinematic lighting`, `studio lighting`, `golden hour`, `soft diffused light`, `dramatic shadows`, `rim light`, `backlit`, `neon glow`, `natural daylight`, `overcast flat light`, `candlelight`

### Atmosphere
`foggy`, `misty`, `dusty`, `rainy`, `snowy`, `sunny`, `overcast`, `moody`, `ethereal`, `hazy`

### Visual Style
`photorealistic`, `cinematic`, `film grain`, `shallow depth of field`, `bokeh`, `high contrast`, `desaturated`, `vibrant colors`, `noir`, `hyperrealistic`, `4K sharp`

### Lens/Camera
`35mm lens`, `wide angle`, `telephoto`, `anamorphic`, `fisheye`, `macro`, `50mm portrait`, `85mm shallow DOF`

---

## Negative Instructions

**Kling 4.0:** do not use a long list. Per the official guide, negatives can increase the chance of errors. Only two are truly necessary:

```
No subtitles. No background music.
```

Use them when you don't want these things, since the model may add them by default. For styles, add one targeted exclusion, for example `no photorealistic textures` on animation.

**Older models, when the interface shows a negative prompt field:**

```
distortion, morphing, warping, glitching, artifacts, blurry, low quality, text changes, logo deformation, unnatural movement, jerky motion, flickering, color shifting, face distortion
```

This list is a working convention, not an official one. The new API has no separate negative field for 3.0 or 4.0.

---

## Audio Prompts (VIDEO 3.0, 2.6, Avatar 2.0)

For Kling 4.0, see "Kling 4.0: Dialogue and Language" above.

### Dialogue with Speaker Attribution

The format Kling documents for 3.0 pairs the character with the line:
```
Mom (softly, in a surprised tone): Wow, I didn't expect this plot at all.
```

This bracket format is not in Kling's guides, but it has worked in our productions on 3.0 Omni and 4.0:
```
[Speaker: Character Name] "[text]" in a [adjective] [male/female] voice with [accent].
```

### Multilingual Dialogue (VIDEO 3.0)
```
[Speaker: Character] "[Japanese text here]" in a natural conversational tone.
```

### Sound Effects
```
Add [sound: footsteps / door closing / glass breaking / rain] synchronized with [action].
```

### Ambient
```
Background ambient: [environment: city traffic at night / forest birds morning / office hum / heavy rain].
```

### Music
```
[Genre] music playing softly in background, [tempo: upbeat / slow / dramatic].
```

### Voice Control (VIDEO 2.6 / 3.0)

Voice Control (launched 2025-12-16, [official release note](https://kling.ai/release-note/release-notes/7trhudk78j)) creates a custom voice from a 5-30s audio sample and binds it to characters via `[Character] @VoiceName` syntax.

```
[Livestream Host] @Sweet Female Voice: "This top is a trending must-have!"
```

Multi-character dialogue:
```
[Teacher] @Intellectual Female Voice: "Turn to page 20."
[Student] @Teen Male Voice: "Okay, teacher!"
```

**Notes:**
- Currently supports Chinese and English only (with bidirectional cross-language delivery)
- Up to 200 voices in your library
- Use 5-30s clean reference audio: single speaker, neutral emotion, low background noise
- Pricing: +2 credits/sec on top of base video generation

### Voice Reference vs Avatar 2.0 - which to use

| You want... | Use |
|-------------|-----|
| Consistent voice across many generations | Voice reference (Kling 4.0, not Flash) or Voice Control (VIDEO 2.6 / 3.0) |
| Mouth moving to your own audio file | Avatar 2.0 |
| Long-form (1-5 min) talking content | Avatar 2.0 |
| Multi-character scene with native dialogue | Kling 4.0, or VIDEO 3.0 + Voice Control |

---

## Quick Reference: Common Mistakes

| Avoid | Use Instead |
|-------|-------------|
| "interesting motion" | "slow 45-degree rotation" |
| "moves around" | "orbits clockwise, returns to start" |
| "nice lighting" | "soft rim light from upper left" |
| "camera does something" | "camera: slow push in over 5 seconds" |
| "text visible" | "all text remains fixed and unchanged" |
| Long continuous motion | Motion with clear endpoint |
| One prompt for 6 elements | Multi-shot storyboard |
| Generic "character speaks" | Name the speaker and quote the line |
| "premium look" | Side backlight, blurred background, matte grain |
| Asset ID with no role | "@Image1 defines the scene; preserve its layout" |
| "Reference @Video1" for an edit | "Edit @Video1. Change X to Y. Keep everything else unchanged." |
| "move naturally" | "walks with confident stride, arms swinging" |
