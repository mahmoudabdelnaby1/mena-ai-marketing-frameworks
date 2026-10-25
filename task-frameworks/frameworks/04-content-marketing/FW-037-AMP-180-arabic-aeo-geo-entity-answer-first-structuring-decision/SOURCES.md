# Evidence Register & Source Boundaries — `FW-037` (`AMP-180`)

- **Framework Title (EN)**: Arabic AEO / GEO Entity & Answer-First Structuring Decision Aid (Beyond the `llms.txt` Myth)
- **عنوان الأصل (AR)**: أداة القرار لهيكلة المحتوى العربي لمحركات إجابات الذكاء الاصطناعي (`AEO / GEO` — بدلاً من وهم ملف `llms.txt`)
- **Channel**: Content Marketing
- **Last Reviewed Date**: `2026-10-25`
- **Verification Gate Status**: `READY_FOR_REVIEW`

## 1. Problem & Empirical Evidence (What Proves the Failure Mechanism in Egypt & GCC)

| Source ID | Title & Direct Link | Publisher | Published | Accessed | Type & Confidence | What This Source Supports | Support Boundary |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `SRC-045` | [How GA4 Classifies AI Traffic for Arab Websites: What Saudi, UAE and Egyptian Sites Lose (2026 Study)](https://voctos.net/ga4-ai-traffic-arab-markets/) | VOCTOS | `2026-10-18` | `2026-10-25` | `EMPIRICAL_AUDIT` (`RESEARCH_FINDING`) | GA4's AI Assistant channel (launched 13 May 2026) misses 96.9% of AI search citations (which come from Google AI Overviews and AI Mode and land in Organic Search), sends ChatGPT links with rel='noreferrer' or WhatsApp shares to Direct, and sends Perplexity, Claude, HUMAIN Chat (KSA), Fanar (Qatar), and Gulf marketplaces (amazon.sa, noon.com) to Referral. | Based on GA4 channel rules, StatCounter Sep 2026 Arab market data, and Delta Medical Labs KSA case study. |

## 2. Official Platform Capability, Regulatory & Advice Evidence

| Source ID | Title & Direct Link | Publisher | Published | Accessed | Status / Confidence | Official Capability or Rule Verified | Fallback / Operational Boundary |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `SRC-045` | [How GA4 Classifies AI Traffic for Arab Websites: What Saudi, UAE and Egyptian Sites Lose (2026 Study)](https://voctos.net/ga4-ai-traffic-arab-markets/) | VOCTOS | `2026-10-18` | `2026-10-25` | `OFFICIAL_CAPABILITY_CHECK` (`supported`) | VOCTOS Oct 2026 study confirmed 96.9% of measured AI search citations in studied Saudi sites route through Google Search (AI Overviews / AI Mode) and that `llms.txt` is ignored by crawlers. | Fallback: Prioritize Google/Bing indexation, server-rendered HTML tables, and JSON-LD entity markup. |

## 3. Counterevidence, Exceptions & When This Pattern Does NOT Apply

- In strictly single-language English B2B niches or fully prepaid digital-product flows, the severity of this Content Marketing mismatch is lower provided manual QA is still performed.
- ** Operational Boundary**: Do not pay vendors promising 'Guaranteed #1 ChatGPT ranking in 48 hours via `llms.txt`' (`AMP-561`). / لا تدفع لأي جهة تدعي «ضمان المركز الأول في ChatGPT خلال 48 ساعة عبر تركيب ملف `llms.txt`» (`AMP-561`).

## 4. Claims Remaining Uncertain & Update Triggers

- **Verification Requirement**: Verify live store/account configuration and current 2026/2027 platform UI settings for Content Marketing before deploying changes.
- **Verification Requirement**: Confirm current statutory penalty thresholds and licensing rules with qualified local counsel in KSA, UAE, or Egypt.
- **No Guaranteed Outcomes**: Per Agent 2 v1.2 boundaries, this asset defines operational controls and testable measurement hypotheses; it does not promise guaranteed rankings, virality, or fixed ROAS lift.
- **Update Triggers**: Re-verify this framework whenever platform UI/API schemas change, prior to major Hijri/seasonal peaks (Ramadan/White Friday), or within 90 days of `2026-10-25`.
