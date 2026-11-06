# Kling AI Pricing Reference

Three separate billing systems - do not mix them up:

| | Currency | Where | Verified |
|---|---|---|---|
| **Subscription / in-app** | credits | kling.ai app and `kling` CLI, Basic to Ultra+ plans | **2026-11-06** (public page, fetched) |
| **API, Kling 4.0 and Flash** | Flagship Units, ~$0.157 list | kling.ai/dev/pricing, per second of billed duration | **2026-11-06** (public page, fetched) |
| **API, all other models** | General Units, $0.14 list | kling.ai/dev/pricing, per second of output | **2026-11-06** (public page, fetched) |

Pricing changes - verify before quoting figures to anyone.

---

## API resource packages

**Flagship and General Units cannot be swapped.** Flagship packages are "available only for Kling 4.0 and Kling 4.0 Flash". General packages "are not compatible with Kling 4.0 or Kling 4.0 Flash". To call Kling 4.0, you need a Flagship pack or an account cash balance above zero.

| Type | Package | Price | List | Units | Price per Unit | Validity | Concurrency |
|---|---|---|---|---:|---|---|---:|
| Flagship | Trial | $9 | $10 | 64 | $0.1413 | 30 days | 5 |
| Flagship | Trial | $90 | $100 | 637 | $0.1413 | 30 days | 5 |
| Flagship | Standard 1 | $500 | $510 | 3,250 | $0.15386 | 180 days | 20 |
| Flagship | Standard 2 | $2,000 | $2,060 | 13,135 | $0.15229 | 180 days | 20 |
| Flagship | Standard 3 | $8,000 | $8,420 | 53,640 | $0.14915 | 180 days | 20 |
| General | Trial | $9.80 | $14 | 100 | $0.098 | 30 days | 5 |
| General | Trial | $98 | $140 | 1,000 | $0.098 | 30 days | 5 |
| General | Standard 1 | $700 | - | 5,000 | $0.14 | 180 days | 20 |
| General | Standard 2 | $2,100 | - | 15,000 | $0.14 | 180 days | 20 |
| General | Standard 3 | $3,780 | $4,200 | 30,000 | $0.126 | 180 days | 20 |
| General | Standard 4 | $5,670 | $6,300 | 45,000 | $0.126 | 180 days | 20 |
| General | Standard 5 | $7,560 | $8,400 | 60,000 | $0.126 | 180 days | 20 |

Trial packs: first purchase discounted, up to 5 purchases. No rollover or extension. Kling does not publish a Flagship list price per Unit; **~$0.157 is derived** from the list prices above ($510 / 3,250). All USD figures for 4.0 below use it. Larger custom packages go through Business Inquiry.

---

## API rate card (Units per second)

Transcribed from [kling.ai/dev/pricing](https://kling.ai/dev/pricing) and [billing rules](https://kling.ai/document-api/pricing/base/video) on **2026-11-06**.

### Kling 4.0 and Flash (Flagship Units)

| Model | Configuration | 720p | 1080p | 4K |
|---|---|---|---|---|
| **Kling 4.0** | no input video | 1.0 U (~$0.157) | 1.5 U (~$0.235) | n/a |
| **Kling 4.0** | with input video | 0.6 U (~$0.094) | 0.9 U (~$0.141) | n/a |
| **Kling 4.0 Flash** | no input video | 0.6 U (~$0.094) | n/a | n/a |
| **Kling 4.0 Flash** | with input video | 0.4 U (~$0.063) | n/a | n/a |

**Billed duration rule. Read this before quoting anything with a video input:**

| Case | Billed duration |
|---|---|
| No input video | Output duration |
| Input ≤ output | Output × 2 |
| Input > output | Input + output |

Input video includes reference videos, videos being edited, and the videos of video character Elements. The API returns `usage.output_duration` and `input_duration`.

**Worked examples (Kling 4.0, 1080p, list price):**

| Job | Billed | Units | Approx. cost |
|---|---:|---:|---:|
| 10s, no video | 10s | 15 U | $2.35 |
| 30s, no video | 30s | 45 U | $7.06 |
| 10s with a 5s reference video | 20s | 18 U | $2.82 |
| 10s edit of a 10s video | 20s | 18 U | $2.82 |
| 10s with a 30s reference video | 40s | 36 U | $5.65 |

### Older models (General Units)

| Model | Configuration | 720p | 1080p | 4K |
|---|---|---|---|---|
| **Kling 3.0 Turbo** | with Native Audio (only config listed) | 0.8 U ($0.112) | 1.0 U ($0.14) | n/a |
| **Kling 3.0** | no Native Audio | 0.6 U ($0.084) | 0.8 U ($0.112) | 3.0 U ($0.42) |
| **Kling 3.0** | with Native Audio | 0.9 U ($0.126) | 1.2 U ($0.168) | 3.0 U ($0.42) |
| **Kling 3.0** | Motion Control | 0.9 U ($0.126) | 1.2 U ($0.168) | n/a |
| **Kling 3.0 Omni** | no reference video, no Native Audio | 0.6 U ($0.084) | 0.8 U ($0.112) | 3.0 U ($0.42) |
| **Kling 3.0 Omni** | no reference video, with Native Audio | 0.8 U ($0.112) | 1.0 U ($0.14) | 3.0 U ($0.42) |
| **Kling 3.0 Omni** | with reference video, no Native Audio | 0.9 U ($0.126) | 1.2 U ($0.168) | 3.0 U ($0.42) |
| **Kling O1** | no reference video | 0.6 U ($0.084) | 0.8 U ($0.112) | n/a |
| **Kling O1** | with reference video | 0.9 U ($0.126) | 1.2 U ($0.168) | n/a |
| **Kling 2.6** | no Native Audio | 0.3 U ($0.042) | 0.5 U ($0.07) | n/a |
| **Kling 2.6** | with Native Audio, no voice reference | n/a | 1.0 U ($0.14) | n/a |
| **Kling 2.6** | with Native Audio, with voice reference | n/a | 1.2 U ($0.168) | n/a |
| **Kling 2.6** | Motion Control | 0.5 U ($0.07) | 0.8 U ($0.112) | n/a |
| **Kling 2.5 Turbo** | no Native Audio | 0.3 U ($0.042) | 0.5 U ($0.07) | n/a |

### Other capabilities

| Capability | Billing | 720p | 1080p |
|---|---|---|---|
| Avatar | per second | 0.4 U ($0.056) | 0.8 U ($0.112) |
| Multi-element Video Editing | per 5 seconds | 3 U | 5 U |
| Lip Sync | per 5 seconds | 0.5 U, independent of resolution | |
| TTS | per request | 0.05 U | |
| Face Recognition | per request | 0.05 U | |
| Text to Audio / Video to Audio | per request | 0.25 U | |
| Custom Voice | per request | 0.05 U | |
| Image Recognition | per request | 0.1 U | |
| Effects | varies by template | see Effects Pricing List | |

The solution APIs (AI Apparel Replicator, Goods Studio, Video Commerce) have their own per-second rates on the pricing page. They are outside this skill's scope.

### What this means in practice

Cheapest per second **with sound**:

| Resolution | Cheapest first |
|---|---|
| 720p | Flash ~$0.094 · Turbo and Omni $0.112 · VIDEO 3.0 $0.126 · Kling 4.0 ~$0.157 |
| 1080p | Turbo and Omni $0.14 · VIDEO 3.0 $0.168 · Kling 4.0 ~$0.235 |
| 4K | VIDEO 3.0 and Omni $0.42 |

- **Video input never saves money on 4.0.** The rate falls by 40% but billed time at least doubles.
- **4K is a cliff on 3.0:** a 10s 4K clip is $4.20. Lock the prompt at 720p or 1080p first.
- **Audio costs extra on VIDEO 3.0:** silent 1080p is $0.112/s, with native audio $0.168/s (+50%).
- **Avatar is the cheapest per second of any video model:** $0.056/s at 720p. A 60s talking-head at 720p is ~$3.40.

### Reading any third-party or aggregator price

Third-party providers (fal.ai, PiAPI, kie.ai) and aggregators (e.g. OpenRouter) set their own prices and expose their own model IDs. A headline per-second or per-clip figure from any of them is a **base rate, not the bill**: the actual charge moves with resolution, duration, aspect ratio and whether audio or video input is on. Read the response's own usage/cost field after a real call rather than trusting a table.

---

## Subscription Plans (verified 2026-11-06)

Now public on [the membership page](https://kling.ai/app/membership/membership-plan). The plan line-up changed since the May audit: **Premier has four sizes, and Ultra was replaced by Ultra+**.

| Plan | Monthly list | First month | Renews at | Yearly | Credits/month | Elements |
|------|---:|---:|---:|---:|---:|---:|
| **Basic** | $0 | - | - | - | none listed | 30 |
| **Standard** | $10 | $6.99 | $8.80 | $79.20 | 660 | 50 |
| **Pro** | $37 | $25.99 | $32.56 | $293.04 | 3,000 | 150 |
| **Premier 8K** | $92 | $64.99 | $80.96 | $728.64 | 8,000 | 150 |
| **Premier 18K** | $207 | $144.99 | $181.99 | $1,639.99 | 18,000 | 150 |
| **Premier 28K** | $322 | $225.99 | $283.99 | $2,550.99 | 28,000 | 150 |
| **Premier 38K** | $428 | $299.99 | $376.99 | $3,389.99 | 38,000 | 150 |
| **Ultra+** | $619 | $432.99 | $544.99 | $4,902.99 | 57,000 | 500 |

**Team Plan** (web only): $98 per seat a month, or $73 per seat billed yearly. 10,000 credits per seat a month. The page shows 30,000 team credits per month at its default seat count.

**What a credit costs.** The page's "100 Credits = $1.06" for Standard is the **first-month** price. After that:

| Plan | Per 100 credits, renewing monthly | Per 100 credits, yearly (page figure) |
|---|---:|---:|
| Standard | $1.33 | $1.00 |
| Pro | $1.09 | $0.81 |
| Premier 18K | $1.01 | $0.76 |
| Ultra+ | $0.96 | $0.72 |

Renewal figures are derived from the prices in the table above.

---

## Critical: Basic Tier Limitation

⚠️ **Basic (free) tier: generated content is NOT for commercial use.**

To unlock commercial use, the user must be on Standard or higher.

---

## Features by Plan (verified 2026-11-06)

| Feature | Basic | Standard | Pro | Premier | Ultra+ |
|---------|-------|----------|-----|---------|-------|
| VIDEO 2.6 Voice Control | - | Free | Free | Free | Free |
| Element AI Multi-Shot | - | 3 daily uses | 3 daily uses | 3 daily uses | 3 daily uses |
| 1080p/4K Video Generation | - | ✓ | ✓ | ✓ | ✓ |
| Max videos per generation | 1 | 4 | 4 | 4 | 4 |
| Commercial use of output | ✗ | ✓ | ✓ | ✓ | ✓ |
| Brand watermark removal | - | ✓ | ✓ | ✓ | ✓ |
| Priority access to new features | - | - | ✓ | ✓ | ✓ |
| Beta test invite | - | - | - | - | ✓ |

Unlisted in this table but on the page: daily free credits for subscribers, unlimited task queue, fast-track generation.

**"1080p/4K Video Generation" is a plan benefit, not a promise about a model.** It does not mean 4K works on Kling 4.0: see the status table in `SKILL.md`.

---

## Confirmed Credit Costs

Kling does not publish a per-model credit table. The app shows an estimate before each generation - always check there.

| Item | Cost | Source |
|------|------|--------|
| Kling 4.0, 1080p | **15 credits/sec** | **Our test:** 300 credits for 20s through the CLI (`creditsConsumed`), 2026-10-22 |
| 4K generation (VIDEO 3.0 series) | **30 credits/sec** | [Cinema-Grade Native 4K release note, 2026-04-23](https://kling.ai/release-note/release-notes/z8zeqsxwol) |
| Lip Sync | 5 credits for 5s, 10 credits for 10s | [Lip sync guide, 2025-11-24](https://kling.ai/quickstart/ai-lip-sync-guide) |
| Voice Control surcharge | +2 credits/sec on top of base video gen | [Voice Control release note, 2025-12-16](https://kling.ai/release-note/release-notes/7trhudk78j) - the membership page lists VIDEO 2.6 Voice Control as free on paid plans |

**Unverified:** credit rates for Kling 4.0 at 720p, Flash, and any model outside the table.

At 15 credits/sec, a second of Kling 4.0 at 1080p costs about $0.11-0.20 depending on plan: a Standard plan's 660 credits buy 44 seconds a month.

---

## Third-party resellers and aggregators

Kling models are also resold via fal.ai, PiAPI, kie.ai, Higgsfield and OpenRouter, among others. **Their pricing and model coverage are their own, not Kling's.** Their status for 4.0 was not verified for this skill - see "Reading any third-party or aggregator price" above before quoting anything.

---

## Sources

- **Membership plans:** https://kling.ai/app/membership/membership-plan
- **Official API rate card and packages:** https://kling.ai/dev/pricing
- **API billing rules:** https://kling.ai/document-api/pricing/base/video
- **Kling API documentation:** https://kling.ai/document-api/guides/get-started/overview
- **Kling release notes (feature/pricing announcements):** https://kling.ai/release-note

**Last verified:** 2026-11-06, all three price lists (public pages).

**Caveat:** Subscription prices and discounts shift with promo cycles. Always check the live estimate in the Kling app before quoting cost for a specific deliverable.
