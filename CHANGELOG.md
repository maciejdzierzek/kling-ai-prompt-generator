# Changelog

All notable changes to the Kling AI Prompt Generator skill and plugin are documented here.

The format follows [Keep a Changelog](https://keepachangelog.com/en/1.1.0/), and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [1.1.0] - 2026-05-21

This release was rewritten against Kling's **official release notes** at [kling.ai/release-note](https://kling.ai/release-note) (fetched via headless browser) and the **official pricing page** (verified from a 2026-05-21 dashboard screenshot). Earlier drafts relied on third-party reviews and contained factual errors. All facts in this entry are sourced from official Kling pages - URLs cited in `SKILL.md` and `references/pricing.md`.

### Added (post-release-notes review, from official pricing page + field testing)

- **Basic (free) tier commercial-use restriction documented** - free output cannot be used commercially; Standard+ required.
- **Pricing structure verified against live Kling pricing page** (Basic / Standard $6.99 / Pro $25.99 / Premier $64.99 / Ultra $127.99) with credit allotments, Element creation quotas, and per-plan feature matrix.
- **Voice Control is FREE for paid subscribers** - the "+2 credits/sec" figure in the Voice Control release note applies to API / pay-as-you-go pricing, not subscription tiers. Corrected in SKILL.md and pricing.md.
- **Element AI Multi-Shot: 3 daily free uses** across all paid plans (per pricing page).
- **Avatar 2.0 multilingual reality check** - officially listed as EN/JA/KO/ZH, but the model lip-syncs to any audio file provided. **Field-confirmed working with Polish ElevenLabs audio.** Skill now guides users to try non-listed languages rather than refusing them.
- **720p credit baseline** - derived from official plan ratios: ~20 credits per 5s 720p clip.

### Added (new features documented for the first time)

- **VIDEO 3.0 Series** section split into two distinct models per official lineup:
  - **VIDEO 3.0** (upgrade path from VIDEO 2.6) - text/image/start-end-frame to video, native audio, multi-shot, 15s, EN/ZH/JA/KO/ES + dialects, multi-character coreference (3+).
  - **VIDEO 3.0 Omni** (upgrade path from VIDEO O1) - all of VIDEO 3.0 plus video element reference and element voice control.
- **VIDEO 3.0 Motion Control** section (released 2026-03-04) - facial element binding, high consistency across angles/emotions/occlusions, up to 30s.
- **Avatar 2.0** section (released 2025-12-04) - one image + one audio file → up to 5-minute talking avatar. Confirmed: enhanced motion quality, stable hand movements (the main fix vs 1.0).
- **Kling Canvas Agent** section (released 2026-01-29) - AI orchestrator: one-click storyboard, multi-angle expansion, reverse prompt suggestions, script creation, batch generation.
- **Voice Control** section (released 2025-12-16, VIDEO 2.6) - custom Voice Embeddings, `[Character] @VoiceName` syntax, up to 200 voices, +2 credits/sec.
- **Native 4K** (released 2026-04-23) - VIDEO 3.0 series, 30 credits/sec, native (not upscaled), preserves reference consistency.
- **Element Reference** (formerly miscalled "Character LoRA") - Kling's official naming for cross-shot identity consistency. Multi-image references, plus video references on Omni.
- **Avatar 2.0 prompt templates** in `references/prompt-templates.md` - presenter, energetic explainer, singer, narrator.
- **`references/pricing.md`** - dedicated reference with confirmed pricing facts vs. third-party estimates clearly separated.
- **`evals/evals.json`** - trigger accuracy eval suite for the skill-creator framework.
- **`.claude-plugin/marketplace.json`** - the repo now serves as both plugin source and marketplace catalog. Marketplace name: `maciejdzierzek` (reusable for future skills like nano-banana).
- **Verification & Sources section** in SKILL.md - links every major claim back to its release note URL.
- **CHANGELOG.md** (this file).

### Changed (corrections + updates)

- **Frontmatter `description`** - extended to cover avatars, Voice Control, Element Reference, Canvas Agent, and new trigger phrases ("talking avatar", "AI presenter", "lip sync video"). Length: ~820 chars.
- **Common Issues table** expanded with Avatar 2.0, Voice Control, and 4K-iteration troubleshooting.
- **`plugin.json` description** updated to mention VIDEO 3.0, Avatar 2.0, Element Reference, Voice Control.
- **README.md** - Features list rewritten, Models table refreshed against official sources, Avatar 2.0 example added.
- **Marketplace install command** is now `/plugin install kling-ai-prompt-generator@maciejdzierzek` (shorter, allows reusing the marketplace name for future skills).

### Fixed (corrections from official source verification)

- **VIDEO 3.0 + VIDEO 3.0 Omni are separate models, not one merged "Kling 3.0".** Earlier draft of this release consolidated them based on third-party reviews. Official release note (2026-01-31) lists them as distinct models with different upgrade paths and capability sets.
- **Native 4K release date** corrected to **2026-04-23** (it was a separate later release, not part of the January 3.0 launch as third-party reviews suggested). Confirmed cost: 30 credits/sec.
- **Motion Control** updated to include **VIDEO 3.0 Motion Control** (2026-03-04) as current; VIDEO 2.6 Motion Control (2025-12-17) is the older variant.
- **Avatar 2.0 details** corrected - the official release note does not split "5 min musical / 1 min narration"; it states "complete 5-minute videos" covering all scenarios. Language-list claims softened to "verify in current docs" since the release note does not enumerate lip-sync language support.
- **Voice Control language coverage** corrected to **Chinese + English only** (third-party reviews incorrectly extended this to EN/ZH/JA/KO).
- **Audio languages** for Native Audio in VIDEO 3.0 confirmed against official source: Chinese, English, Japanese, Korean, Spanish, plus dialects and accents.

### Removed

- **"Omni One architecture"** terminology - third-party invention, not in official notes. Replaced with Kling's official "unified multimodal training framework".
- **"Character LoRA"** terminology - third-party invention. Replaced with official **Element / Element Reference / Element Library** vocabulary.
- **"Draft Mode 5-20x cheaper"** claims - this feature is mentioned in third-party reviews but does not appear in any official release note I could verify. Removed from SKILL.md to avoid propagating an unverified claim. (If a future Kling release note confirms it, add back with citation.)
- **"AI Editor 7-in-1 Multi-Modal Editor"** - third-party claim, not in any official release note verified for this version. Removed.
- **Kling 2.6 Pro as a separate Artlist-exclusive model row** - the official release notes describe 2.6 as a single model with Native Audio; the "2.6 Pro" naming appears in third-party (Artlist) marketing. Demoted to a note rather than a separate lineup row.
- Pricing tables from the main SKILL.md - moved to `references/pricing.md`.
- Stray OneDrive sync-conflict files (`SKILL-MacBook Pro...md`, conflict ZIP).

### Source verification notes

This release was researched and verified against Kling's **official release notes** at [kling.ai/release-note](https://kling.ai/release-note), fetched via headless browser (Playwright) since the site is a JS-rendered SPA. Specific release notes referenced - URLs are cited in the SKILL.md "Verification & Sources" section.

Third-party sources (Atlas Cloud, Higgsfield, MindStudio, Flowith, Cybernews, fal.ai model cards) were used only where official Kling notes did not provide a specific detail, and are clearly marked as "third-party estimate" in `references/pricing.md`. When the two sources conflicted, the official Kling release note wins.

Things NOT verified against official source and therefore left as estimates or omitted:
- Specific pricing tier dollar amounts (Standard/Pro/Premier/Ultra) - third-party data only
- Avatar 2.0 lip-sync language list - left generic ("strong for Chinese and English, others may show drift")
- Approximate credit costs for Kling 2.5 Turbo, Kling 2.6 - third-party estimates only

Verify against the Kling dashboard before quoting any of these to clients.

## [1.0.1] - 2026-03-14

### Added
- Initial plugin packaging for Claude Code marketplace distribution.
- `.claude-plugin/plugin.json` manifest.
- `examples/` folder with image-to-video, text-to-video, and motion-control example prompts.
- README.md with installation paths for Claude.ai, Claude Desktop, and Claude Code.

### Changed
- Repackaged the skill as a Claude Code plugin (previously distributed as a standalone SKILL.md).

## [1.0.0] - 2026-02

### Added
- First public release of the Kling AI Prompt Generator skill.
- SKILL.md covering Image-to-Video, Text-to-Video, Multi-Shot Storyboards (3.0), Motion Control workflows.
- Model lineup: Video 3.0 (V3), Video 3.0 Omni (O3), Video O1, Video 2.6, Video 2.5 Turbo, 2.6 Motion Control.
- `references/prompt-templates.md` with templates for product animation, portrait, holographic UI, nature scene, logo, multi-shot narrative, cinematic portrait, product commercial, action scene, talking head, atmospheric loop.
- English-prompt policy (always translate user prompts to English before pasting into Kling).
- Speaker attribution syntax for audio (V3/O3/2.6).
- Voice cloning workflow (O3 only).

[1.1.0]: https://github.com/maciejdzierzek/kling-ai-prompt-generator/releases/tag/v1.1.0
[1.0.1]: https://github.com/maciejdzierzek/kling-ai-prompt-generator/releases/tag/v1.0.1
[1.0.0]: https://github.com/maciejdzierzek/kling-ai-prompt-generator/releases/tag/v1.0.0
