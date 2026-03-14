# Text-to-Video Examples

Ready-to-use T2V prompts. Each example includes notes on generation behavior.

---

## Cinematic Portrait

**Use case:** Character scenes, storytelling, social content with a human subject.

```
35-year-old woman with dark wavy hair and a cream linen blouse, thoughtful expression. Standing in a sunlit cafe near a window. Slowly turns head toward camera, subtle smile forms. Cinematic lighting from left side, shallow depth of field. Camera: slow push in. 35mm lens aesthetic. Duration: 5s.
```

**Expected result:** Camera slowly moves toward the subject as she turns. Background stays softly blurred. The push-in motion combined with the head turn creates a natural, cinematic feel.

---

## Product Commercial

**Use case:** E-commerce, advertising, product showcase without a source image.

```
Matte black watch on dark slate pedestal in minimalist studio. Camera slowly orbits clockwise around product, brushed metal bezel catches light creating sharp specular highlight. Leather strap in soft focus foreground. Studio lighting with soft diffused key light from upper right. Premium advertisement aesthetic. Duration: 10s. Aspect ratio: 16:9.
```

**Expected result:** Smooth orbit shot around the product. Light creates a moving highlight on the metal surface. 10-second duration gives the orbit time to complete without rushing.

---

## Atmospheric Loop

**Use case:** Ambient backgrounds, intro sequences, mood pieces.

```
Foggy mountain valley at blue hour. Pine trees in foreground sway gently in wind, wisps of fog drift slowly through middle ground, distant peaks barely visible. Light rays shift subtly between clouds. Motion returns to approximate starting position. Peaceful ambient mood. Camera: static, locked off. Duration: 10s. Aspect ratio: 16:9.
```

**Expected result:** Multiple layers of gentle motion create depth. The static camera keeps the scene grounded. "Returns to starting position" encourages motion that loops reasonably well.

---

## Talking Head with Audio (Model 2.6)

**Use case:** Explainer content, social video with speech, product announcements. Requires Kling 2.6 for audio support.

```
Professional woman in her 40s, dark blazer, speaks directly to camera in modern open office with blurred background. Natural hand gestures matching speech rhythm. Soft studio lighting, medium close-up, static camera.
[Speaker: Female presenter] "This feature saves our team four hours every week." in a warm, confident voice.
Background ambient: quiet office hum. Duration: 5s.
```

**Expected result:** Subject speaks the indicated dialogue. Lip sync quality varies - works best with short sentences. Ambient sound adds realism.

> **Tip:** Keep dialogue to 1-2 short sentences for best sync results.
