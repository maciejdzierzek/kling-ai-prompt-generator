# Kling API and CLI Reference

For anyone automating Kling rather than using the app. Checked 2026-11-06 against the [API docs](https://kling.ai/document-api/guides/get-started/overview) and live declarations of `kling-cli` 0.2.3 (MCP 1.3.3).

**Trust order when sources disagree:** what the live `kling who_am_i` declares for your account, then the API endpoint reference, then user guides, then release notes. Kling's pages are not consistent with each other (see "Known contradictions").

---

## Model IDs

| Model | API ID | CLI ID | Duration | Resolution | Aspect ratio |
|---|---|---|---|---|---|
| Kling 4.0 | `kling-4.0` | `kling-video-v4_0` | 3-30s | 720p, 1080p | 21:9, 16:9, 1:1, 9:16, adaptive |
| Kling 4.0 Flash | `kling-4.0-flash` | `kling-video-v4_0_flash` | 3-20s | 720p | 21:9, 16:9, 1:1, 9:16, adaptive |
| Kling 3.0 Turbo | `kling-3.0-turbo` | `kling-video-v3_0_turbo` | 3-15s | 720p, 1080p | 16:9, 1:1, 9:16 |
| Kling 3.0 | `kling-v3` | `kling-video-v3_0` | 3-15s | 720p, 1080p, 4K | 16:9, 1:1, 9:16 |
| Kling 3.0 Omni | `kling-v3-omni` | `kling-video-v3_0_omni` | 3-15s | 720p, 1080p, 4K | 16:9, 1:1, 9:16 |
| Kling O1 | `kling-video-o1` | `kling-video-o1` | 3-10s | 720p, 1080p | 16:9, 1:1, 9:16 |
| Kling 2.6 | `kling-v2-6` | `kling-video-v2_6` | 5s, 10s | 720p, 1080p | 16:9, 1:1, 9:16 |
| Kling 2.5 Turbo | `kling-v2-5-turbo` | `kling-video-v2_5` | 5s, 10s | 720p, 1080p | 16:9, 1:1, 9:16 |

**Not in the CLI:** Avatar, Lip Sync, Multi-element Video Editing. Motion Control exists in the CLI for 2.6 and 3.0 only.

---

## API

Base URL: `https://api-singapore.klingai.com`. Auth: `Authorization: Bearer ${KLING_API_KEY}`. Async: create a task, then query it; do not resubmit while waiting.

| Task | Endpoint | Accepts |
|---|---|---|
| Text to video | `POST /text-to-video/kling-4.0` | `prompt`, `settings` |
| Keyframes | `POST /image-to-video/kling-4.0` | `first_frame`, `middle_frame`, `last_frame` |
| Omni Reference | `POST /omni-video/kling-4.0` | all of the above + `refer_image`, `feature_video`, `base_video`, `element`, `voice` |

Flash uses the same paths with `kling-4.0-flash`, without `middle_frame`, `last_frame` and `voice`.

### `contents` types (Omni)

| Type | Meaning |
|---|---|
| `prompt` | Required. `text` field |
| `first_frame`, `middle_frame`, `last_frame` | Keyframes. Put `first_frame` first and `last_frame` last in `contents` |
| `refer_image` | Reference image. Scene, style, character |
| `feature_video` | Video to **reference** (motion, camera, style) |
| `base_video` | Video to **edit**. At most 1 per request |
| `element` | `element_id` + `id` |
| `voice` | `voice_id` + `id`. At most 3. System presets or Custom Voice |

**The type decides the job.** Use `feature_video` to reference a video and `base_video` to edit it; the prompt's wording ("Edit" versus "Reference") should match.

Give each asset an `id`, then refer to it as `@id` in the prompt. Example: `"id": "image_1"` is `@image_1`. A voice with `"id": "1"` is `@1`.

### `settings`

| Field | Values | Default | Notes |
|---|---|---|---|
| `resolution` | `720p`, `1080p` | `1080p` | 4K coming soon |
| `aspect_ratio` | `21:9`, `16:9`, `9:16`, `1:1`, `adaptive` | `adaptive` | Beats the prompt when set. **Not accepted** on `/image-to-video/kling-4.0` |
| `duration` | integer, 3-30 | prompt, then base video length, then 10 | Beats the prompt when set. Sets the billing |
| `audio` | `native`, `original` | `native` | `original` keeps the input's sound and cannot be combined with `voice` |

### Limits

- **Prompt:** 8,000 tokens, expressed as 26,000 English or 11,000 non-English characters. Mixed text must satisfy `E/26000 + N/11000 <= 1`. Kling 3.0: 3,072 characters, 2,500 recommended.
- **Images:** jpg, jpeg, png; ≤30 MB; at least 300 px each side; 2:5-5:2. Max 10.
- **Videos:** mp4, mov; ≤300 MB; 700-4553 px; ≤8,294,400 pixels; 2:5-5:2; 24-60 fps. Each and total 3-30s. **Output is 24 fps.**
- **Total:** 15 inputs across images, videos, elements and voices.

### Other

- Video links expire, so store results. The official Kling skill states 30 days of retention.
- The older API stays available: "no current plans for deprecation" (2026-07-15). New paths use API key auth.
- Create voices with `POST /v1/general/custom-voices`. Avatar is `POST /v1/videos/avatar/image2video`.
- The API changelog, not the release notes, is where the API status of a model lands.

---

## CLI (`kling` 0.2.3)

Install: `npm i -g @klingai/cli-global`. Start with `kling who_am_i` to see the models, arguments and input slots your account can use. `kling account` shows credits. Every submission costs credits, and a job takes minutes (6 min for 20s at 1080p, our test).

```bash
kling text_to_video  --model kling-video-v4_0 --duration 10 --resolution 1080p "Prompt" --poll=600
kling image_to_video --model kling-video-v4_0 --image first.png --tailImage last.png --duration 6 --resolution 1080p --prompt "Prompt" --poll=600
kling image_to_video --model kling-video-v4_0 --input first_image=a.png --input keyframe_1=b.png --input tail_image=c.png --prompt "Prompt"
kling omni_ref_video --model kling-video-v4_0 --image ref.png --video motion.mp4 "图片1 ... 视频1 ..."
kling omni_ref_video --model kling-video-v4_0 --image ref.png --audio voice.mp3 --enable_audio true "图片1 ... 音频1 ..."
```

`--input` cannot be combined with `--image` / `--tailImage` on `image_to_video`.

**Reference syntax in the CLI prompt:** `图片1` = `image_1`, `视频1` = `video_1`, `音频1` = `audio_1`, and an Element is `<<<id>>>` plus an entry in `--elements`. An English prompt with these tokens worked for us **(our test)**. Whether `@Image1` also works in the CLI is untested.

**Where 4.0 differs by command:**

| Command | References | Keyframes | Elements | Audio control |
|---|---|---|---|---|
| `text_to_video` | no | no | no | not exposed |
| `image_to_video` | no | `first_image`, `tail_image`, `keyframe_1..10` (10 images max) | no | not exposed |
| `omni_ref_video` | `image_1..10`, `video_1..5`, `audio_1..3` | **no slots** | up to 7 | `enable_audio`, `keepOriginalSound` |

**Defaults that catch people out:**

- `resolution` is **720p**, unlike the API's 1080p
- `prefer_multi_shots` must stay `true` on `omni_ref_video`. Ask for a single take in the prompt
- Only one of `enable_audio` and `keepOriginalSound` may be true. `enable_audio false` exists here, though the API documents no silent mode for 4.0. Untested
- `aspect_ratio: auto` needs at least one image or video
- The model is billed per second and input video is included, which the CLI requires you to tell the user

**Motion Control:** `kling motion_control` with `kling-video-v3_0` or `kling-video-v2_6`. `motionDirection`: `motion_direction` follows the video (source 3-30s); `image_direction` follows the image (3-10s only).

**Elements:** `kling element_create --name N --description D --tag TAG --cover front.png --secondary side.png`, or `--video` instead. `--voice` takes an optional .mp3.

---

## Known contradictions in Kling's own sources

| Topic | Source A | Source B | What to do |
|---|---|---|---|
| 4K on 4.0 | Release note table, User Guide, capability map: listed | API manual: "4K output is coming soon"; enum 720p/1080p; no price | Treat as not available through API and CLI |
| 10-bit HDR | Spec tables: listed | Same page's text: "coming soon" | Treat as not available |
| Flash first/last frame | Capability map: YES | User Guide, API manual, API endpoint, CLI: first frame only | First frame only |
| Audio upload | CLI help example: `使用音频2的音乐` (use the music in audio 2) | User Guide and API manual: voice only, no music or sound effects | Voice only, until tested |
| Audio on 4.0 | User Guide and API: always on, no toggle in the app | CLI: `enable_audio` true or false | Assume sound is on, and budget for it |
| `audio_N` in the CLI | CLI help example: a character speaks "according to audio 1" | Docs and our test: timbre only | Kling generates the speech itself |
| Keyframes + references | App: entries "cannot be combined" | API: `/omni-video` takes both. App Omni also offers keyframes | Use Omni Reference, not the Keyframes entry |

---

## Unverified

- How the CLI's `omni_ref_video` distinguishes an edit from a reference: it has one `video_N` slot type, while the API has `base_video` and `feature_video`
- Whether `enable_audio false` gives a silent 4.0 clip in the CLI
- Whether `--aspect_ratio` on `image_to_video` is honored, since the API endpoint rejects a separate field
