# Motion Control Examples

Motion Control mode lets you define precise camera paths using Kling's trajectory interface. These examples describe the camera movements to set up - use them as reference when configuring the Motion Control panel.

---

## Slow Orbit Around Subject

**Use case:** Products, characters, architectural details - anything that benefits from showing multiple angles.

**Camera path setup:** Draw a curved arc from left to right, keeping the subject centered. Set speed to 30-40% for smooth motion.

**Prompt to pair with:**
```
Professional sneaker on neutral pedestal. Camera orbits slowly clockwise 90 degrees, highlights travel across mesh texture. Static environment, studio lighting unchanged. Smooth, fluid motion. Duration: 10s.
```

**Expected result:** The camera follows the defined arc while the product stays centered in frame. Light creates moving highlights on the surface texture.

---

## Push In to Face

**Use case:** Portraits, emotional close-ups, dramatic reveals.

**Camera path setup:** Draw a straight line from current position toward the subject's face. Use a gentle curve if you want slight vertical rise during approach. Speed 25-35%.

**Prompt to pair with:**
```
Young man with short hair looks toward horizon, thoughtful expression. Gradual camera push in toward face, ending in medium close-up. Soft side lighting, shallow depth of field. Cinematic feel. Duration: 5s.
```

**Expected result:** Camera smoothly closes the distance to the subject. Background gradually blurs more as camera moves closer. Works best when the starting frame has enough space around the subject.

---

## Ken Burns - Landscape Pan

**Use case:** Still landscape photos, documentary-style content, travel visuals.

**Camera path setup:** Draw a slow horizontal pan from one side of the frame to the other. Keep the path nearly straight with very slight curve. Low speed (20-25%) for a proper Ken Burns feel.

**Prompt to pair with:**
```
Wide mountain landscape at golden hour. Camera slowly pans from left edge to right, revealing valley and river in background. Warm amber light on peaks. No subject movement, purely camera driven. Duration: 10s. Aspect ratio: 16:9.
```

**Expected result:** Camera glides across the scene revealing detail progressively. 10-second duration prevents the pan from feeling rushed.

> **Tip:** Motion Control works best when the camera path is simple and deliberate. Complex multi-direction paths often produce less stable results than a single clean arc or line.
