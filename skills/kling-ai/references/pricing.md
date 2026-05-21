# Kling AI Pricing Reference

**Verified against the official pricing page** at [kling.ai](https://kling.ai) (subscription plans tab) on **2026-05-21**. Pricing changes - verify in the Kling dashboard before quoting figures to anyone.

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

## API / Third-Party Pricing

VIDEO 3.0 series and Avatar 2.0 are also available via:

- **fal.ai** - per-generation USD pricing, no monthly commitment. Avatar 2.0 has its own model card.
- **PiAPI** - usage-based, includes Avatar 2.0 access
- **kie.ai** - Avatar 2.0 specifically
- **Higgsfield** - bundled with their own model offering

Use these when you don't want a Kling subscription or need API access for integration. Pricing is per minute of generated video, billed in USD, no Kling credits involved.

---

## Sources

- **Official Kling pricing page:** [kling.ai](https://kling.ai) (subscription tab, after login)
- **Kling API documentation:** https://kling.ai/document-api/quickStart/productIntroduction/overview
- **Kling release notes (feature/pricing announcements):** https://kling.ai/release-note
- **fal.ai Kling model pages:** https://fal.ai/models?keyword=kling

**Last verified against Kling pricing page:** 2026-05-21

**Caveat:** Subscription prices and discounts shift frequently with promo cycles. Credit-to-video conversion math holds for 720p but changes at 1080p and 4K. Always check the live estimate in the Kling app before quoting cost for a specific deliverable.
