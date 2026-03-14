# Kling AI Prompt Templates

Ready-to-use templates organized by use case. Replace bracketed placeholders with specific content.

## Image-to-Video Templates

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

## Text-to-Video Templates

### Cinematic Portrait

```
[Age] [gender] with [hair description] and [clothing], [expression] expression. Standing in [location]. [Action: slowly turns head toward camera / looks up / subtle smile forms]. Cinematic lighting from [direction], shallow depth of field. Camera: [slow push in / static medium shot / gentle orbit]. 35mm lens aesthetic.
```

### Product Commercial

```
[Product] on [surface material] pedestal in [setting]. Camera slowly orbits around product, [specific detail] catches light creating [reflection type]. [Secondary element] in soft focus background. Studio lighting with [light quality]. Premium advertisement aesthetic. 10 seconds.
```

### Action Scene

```
[Subject] [specific action with clear start and end point] in [environment]. [Weather/atmosphere]. Camera: [tracking shot following subject / wide establishing then push in]. Motion blur on fast elements. [Time of day] lighting. Dust/particles visible in air.
```

### Talking Head (2.6 with Audio)

```
[Person description] speaks directly to camera in [setting]. Says "[dialogue up to 2 sentences]" in [warm/professional/excited] [male/female] voice. Subtle hand gestures matching speech rhythm. Natural eye contact with camera. Soft studio lighting, blurred background. Medium close-up, static camera.
```

### Atmospheric Loop

```
[Scene description] with [primary motion element]. [Secondary element] moves slowly in background. Subtle [atmospheric effect: fog drifts / dust particles float / light rays shift]. Motion returns to approximate starting position. Peaceful ambient mood. Static camera.
```

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

### Movement Modifiers
- `slow` / `gentle` / `subtle` - reduced speed
- `smooth` / `fluid` - no jerky motion
- `gradual` - progressive change

## Style Keywords

### Lighting
`cinematic lighting`, `studio lighting`, `golden hour`, `soft diffused light`, `dramatic shadows`, `rim light`, `backlit`, `neon glow`, `natural daylight`

### Atmosphere
`foggy`, `misty`, `dusty`, `rainy`, `snowy`, `sunny`, `overcast`, `moody`, `ethereal`

### Visual Style
`photorealistic`, `cinematic`, `film grain`, `shallow depth of field`, `bokeh`, `high contrast`, `desaturated`, `vibrant colors`, `noir`

### Lens/Camera
`35mm lens`, `wide angle`, `telephoto`, `anamorphic`, `fisheye`, `macro`

## Negative Prompt Suggestions

Add to negative prompt field when available:

```
distortion, morphing, warping, glitching, artifacts, blurry, low quality, text changes, logo deformation, unnatural movement, jerky motion
```

## Multi-Shot Storyboard Templates (3.0 Only)

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

## Text-to-Video Templates (Updated for 3.0)

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

### Talking Head with Audio (V3/O3)

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

## Style Keywords

### Lighting
`cinematic lighting`, `studio lighting`, `golden hour`, `soft diffused light`, `dramatic shadows`, `rim light`, `backlit`, `neon glow`, `natural daylight`, `overcast flat light`, `candlelight`

### Atmosphere
`foggy`, `misty`, `dusty`, `rainy`, `snowy`, `sunny`, `overcast`, `moody`, `ethereal`, `hazy`

### Visual Style
`photorealistic`, `cinematic`, `film grain`, `shallow depth of field`, `bokeh`, `high contrast`, `desaturated`, `vibrant colors`, `noir`, `hyperrealistic`, `4K sharp`

### Lens/Camera
`35mm lens`, `wide angle`, `telephoto`, `anamorphic`, `fisheye`, `macro`, `50mm portrait`, `85mm shallow DOF`

## Negative Prompt Suggestions

Add to negative prompt field when available:

```
distortion, morphing, warping, glitching, artifacts, blurry, low quality, text changes, logo deformation, unnatural movement, jerky motion, flickering, color shifting, face distortion
```

## Audio Prompts (V3, O3, and 2.6)

### Dialogue with Speaker Attribution
```
[Speaker: Character Name] "[text]" in a [adjective] [male/female] voice with [accent].
```

### Multilingual Dialogue (V3/O3 only)
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

### Voice Cloning Prompt (O3 only)
```
[Speaker: @reference_voice] "[dialogue text]" - use reference voice characteristics.
```

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
| Generic "character speaks" | `[Speaker: Name] "text"` with attribution |
| "move naturally" | "walks with confident stride, arms swinging" |
