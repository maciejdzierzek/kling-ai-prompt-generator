# Kling AI Pricing Reference

Two separate billing systems - do not mix them up:

| | Currency | Where | Verified |
|---|---|---|---|
| **Subscription / in-app** | credits | kling.ai app, Basic-Ultra plans | 2026-05-21 (dashboard, needs login) |
| **API** | Units, `1 Unit = $0.14` | kling.ai/dev/pricing, per second of output | **2026-08-04** (public page, fetched) |

Pricing changes - verify before quoting figures to anyone.

---

## API rate card (Units per second of output)

Transcribed from [kling.ai/dev/pricing](https://kling.ai/dev/pricing) on **2026-08-04**. `1 Unit = $0.14` list price. Billing is **per second**, and the rate depends on model x resolution x whether native audio and video input are enabled.

### Flagship models

| Model | Configuration | 720p | 1080p | 4K |
|---|---|---|---|---|
| **Kling 3.0 Turbo** | with Native Audio (only config listed) | 0.8 U ($0.112) | 1.0 U ($0.14) | n/a |
| **Kling 3.0** | no Native Audio | 0.6 U ($0.084) | 0.8 U ($0.112) | 3.0 U ($0.42) |
| **Kling 3.0** | Native Audio, no Voice Control | 0.9 U ($0.126) | 1.2 U ($0.168) | 3.0 U ($0.42) |
| **Kling 3.0 Omni** | no video input, no Native Audio | 0.6 U ($0.084) | 0.8 U ($0.112) | 3.0 U ($0.42) |
| **Kling 3.0 Omni** | no video input, with Native Audio | 0.8 U ($0.112) | 1.0 U ($0.14) | 3.0 U ($0.42) |
| **Kling 3.0 Omni** | with video input, no Native Audio | 0.9 U ($0.126) | 1.2 U ($0.168) | 3.0 U ($0.42) |

### Other models

| Model | Billing | 720p | 1080p |
|---|---|---|---|
| Motion Control | per second | 0.9 U ($0.126) | 1.2 U ($0.168) |
| Avatar | per second | 0.4 U ($0.056) | 0.8 U ($0.112) |
| Effects | varies by template | see Effects Pricing List | n/a |

### What this means in practice

- **4K is a cliff:** flat 3.0 U/s ($0.42) on every model that offers it - 2.5x the priciest 1080p rate and 5x the cheapest. A 10s 4K clip is $4.20. Lock the prompt at 720p/1080p first.
- **Turbo is the cheapest 3.0-class option with sound:** $0.14/s at 1080p vs. $0.168/s for VIDEO 3.0 with audio. It has **no 4K tier**.
- **Audio and video input each cost extra.** Silent 1080p on VIDEO 3.0 is $0.112/s; add native audio and it is $0.168/s (+50%).
- **Avatar is the cheapest per second of anything** - $0.056/s at 720p. A 60s talking-head at 720p is ~$3.40.
- Kling also sells prepaid resource packages (180-day validity, no rollover, 20 concurrency on the tier visible on the page) and custom/enterprise packages via inquiry.

### Reading any third-party or aggregator price

Third-party providers (fal.ai, PiAPI, kie.ai) and aggregators (e.g. OpenRouter) set their own prices and expose their own model IDs. A headline per-second or per-clip figure from any of them is a **base rate, not the bill**: the actual charge moves with resolution, duration, aspect ratio and whether audio or video input is on. Read the response's own usage/cost field after a real call rather than trusting a table - a cheaper-looking model can end up more expensive than a pricier one once resolution and duration are set.

---

## Subscription Plans (verified 2026-05-21)

| Plan | List price | Discounted | Credits/month | Implied 720p videos/mo | Element quota |
|------|-----------|------------|---------------|-------|--------|
| **Basic (Free forever)** | $0 | - | 0 (login to earn daily credits) | - | 30 |
| **Standard** | $10 | **$6.99** (up to 30% off) | 660 | 33 | 50 |
| **Pro** | $37 | **$25.99** (up to 30% off) | 3,000 | 150 | 150 |
| **Premier** | $92 | **$64.99** (up to 29% off) | 8,000 | 400 | 150 |
| **Ultra** (NEW) | $180 | **$127.99** (up to 29% off) | 26,000 | 1,300 | 500 |

**Credit math:** Roughly 20 credits per 720p video at standard quality (660 ÷ 33). At 1080p / 4K costs scale up. Specific confirmed costs below.

---

## Critical: Basic Tier Limitation

⚠️ **Basic (free) tier: "Generated content is NOT for commercial use"**

Users on the free tier cannot use generated videos commercially. This is a hard restriction listed on the official pricing page. To unlock commercial use, the user must be on Standard or higher.

---

## Features by Plan (verified 2026-05-21)

| Feature | Basic | Standard | Pro | Premier | Ultra |
|---------|-------|----------|-----|---------|-------|
| Login monthly credits | - | ✓ | ✓ | ✓ | ✓ |
| VIDEO 2.6 Voice Control | - | **FREE** | **FREE** | **FREE** | **FREE** |
| VIDEO O1 Element AI Multi-Shot | - | 3 daily uses | 3 daily uses | 3 daily uses | 3 daily uses |
| Daily Free Credits for Subscribers | - | ✓ | ✓ | ✓ | ✓ |
| Queue unlimited tasks | - | ✓ | ✓ | ✓ | ✓ |
| Fast-track generation | - | ✓ | ✓ | ✓ | ✓ |
| 1080p Video Generation | - | ✓ | ✓ | ✓ | ✓ |
| Image upscaling | - | ✓ | ✓ | ✓ | ✓ |
| Brand watermark removal | - | ✓ | ✓ | ✓ | ✓ |
| Video extension | - | ✓ | ✓ | ✓ | ✓ |
| Commercial use of output | ✗ | ✓ | ✓ | ✓ | ✓ |
| Priority access to new features | - | - | ✓ | ✓ | ✓ |
| Beta test invite | - | - | - | - | ✓ |

**Counter-intuitive but confirmed:** Voice Control is included **free** in all paid subscription tiers - it's not a per-second surcharge for subscribers. (The "+2 credits/sec" figure that appears in the Voice Control release note likely refers to API / pay-as-you-go billing outside the subscription model.)

---

## Confirmed Hard Numbers (from official release notes)

| Item | Cost | Source |
|------|------|--------|
| 4K generation (VIDEO 3.0 series) | **30 credits/sec** | [Cinema-Grade Native 4K release note, 2026-04-23](https://kling.ai/release-note/release-notes/z8zeqsxwol) |
| Voice Control (pay-as-you-go) | +2 credits/sec on top of base video gen | [Voice Control release note, 2025-12-16](https://kling.ai/release-note/release-notes/7trhudk78j) - included free for subscribers per current pricing page |
| 720p video (standard, ~5s) | ~20 credits | Derived: Standard plan = 660 credits → 33 videos |

---

## Approximate Credit Cost per Model (estimates, verify in app)

The Kling pricing page does not break credit cost down per model explicitly. Approximations based on the 720p baseline:

| Model / Output | Approximate cost | Notes |
|-------|------------------|-------|
| **720p standard** | ~20 credits per 5s clip | Derived from plan ratios |
| **1080p standard** | higher than 720p | Verify in app |
| **VIDEO 3.0 series (4K)** | **30 credits/sec (confirmed)** | Native 4K |
| **Avatar 2.0** | scales with duration | Verify in app for current rate |
| **Voice Control surcharge (API)** | **+2 credits/sec (confirmed)** | Free for subscribers per pricing page |

For exact per-model credit costs, the Kling app shows an estimate before each generation - always check there.

---

## Annual Plans

The discounted prices shown above ($6.99/$25.99/etc.) are presented as "Subscribe Special Offer" rates with monthly renewal at "Next monthly renewal" prices (e.g., Standard renews at $8.80/month). For longer commitments, the Kling dashboard offers annual billing - check current discount in app.

---

## Third-party resellers and aggregators

VIDEO 3.0 series and Avatar 2.0 are also available via:

- **fal.ai** - per-generation USD pricing, no monthly commitment. Avatar 2.0 has its own model card.
- **PiAPI** - usage-based, includes Avatar 2.0 access
- **kie.ai** - Avatar 2.0 specifically
- **Higgsfield** - bundled with their own model offering
- **OpenRouter** and similar aggregators - expose Kling model IDs next to competing video models; note that video models are not returned by the default model list endpoint on some aggregators, and video prices are often absent from their API metadata entirely

Use these when you don't want a Kling subscription or need API access for integration. **Their pricing is their own, not Kling's** - see "Reading any third-party or aggregator price" above before quoting anything.

---

## Sources

- **Official Kling pricing page:** [kling.ai](https://kling.ai) (subscription tab, after login)
- **Official API rate card:** https://kling.ai/dev/pricing
- **Kling API documentation:** https://kling.ai/document-api/quickStart/productIntroduction/overview
- **Kling release notes (feature/pricing announcements):** https://kling.ai/release-note
- **fal.ai Kling model pages:** https://fal.ai/models?keyword=kling

**Last verified:** API rate card 2026-08-04 (public page) · subscription plans 2026-05-21 (dashboard, login required)

**Caveat:** Subscription prices and discounts shift frequently with promo cycles. Credit-to-video conversion math holds for 720p but changes at 1080p and 4K. Always check the live estimate in the Kling app before quoting cost for a specific deliverable.
