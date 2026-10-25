# Evidence Register & Source Boundaries — `FW-085` (`AMP-443`)

- **Framework Title (EN)**: GA4 AI Search & Regional AI Assistant Attribution Workflow (Capturing the 96.9% in Organic Search + Custom Regex for Perplexity, Claude & HUMAIN Chat)
- **عنوان الأصل (AR)**: مسار عمل تتبع إحالات محركات الذكاء الاصطناعي في `GA4` (رصد الـ `96.9%` المسجلة داخل البحث العضوي + فصل `Perplexity` و`Claude` و`HUMAIN Chat` من الإحالات)
- **Channel**: Marketing Automation
- **Last Reviewed Date**: `2026-10-25`
- **Verification Gate Status**: `READY_FOR_REVIEW`

## 1. Problem & Empirical Evidence (What Proves the Failure Mechanism in Egypt & GCC)

| Source ID | Title & Direct Link | Publisher | Published | Accessed | Type & Confidence | What This Source Supports | Support Boundary |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `SRC-045` | [How GA4 Classifies AI Traffic for Arab Websites: What Saudi, UAE and Egyptian Sites Lose (2026 Study)](https://voctos.net/ga4-ai-traffic-arab-markets/) | VOCTOS | `2026-10-18` | `2026-10-25` | `EMPIRICAL_AUDIT` (`RESEARCH_FINDING`) | GA4's AI Assistant channel (launched 13 May 2026) misses 96.9% of AI search citations (which come from Google AI Overviews and AI Mode and land in Organic Search), sends ChatGPT links with rel='noreferrer' or WhatsApp shares to Direct, and sends Perplexity, Claude, HUMAIN Chat (KSA), Fanar (Qatar), and Gulf marketplaces (amazon.sa, noon.com) to Referral. | Based on GA4 channel rules, StatCounter Sep 2026 Arab market data, and Delta Medical Labs KSA case study. |

## 2. Official Platform Capability, Regulatory & Advice Evidence

| Source ID | Title & Direct Link | Publisher | Published | Accessed | Status / Confidence | Official Capability or Rule Verified | Fallback / Operational Boundary |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `SRC-045` | [How GA4 Classifies AI Traffic for Arab Websites: What Saudi, UAE and Egyptian Sites Lose (2026 Study)](https://voctos.net/ga4-ai-traffic-arab-markets/) | VOCTOS | `2026-10-18` | `2026-10-25` | `OFFICIAL_CAPABILITY_CHECK` (`supported`) | VOCTOS Oct 2026 audit proved that GA4's default AI Assistant channel misses Perplexity, Claude, and regional tools, while 96.9% of measured AI search clicks come via Google Organic Search (AI Overviews / AI Mode). | Fallback: Use GA4 Custom Channel Groups (which evaluate retroactively!) placed above `Referral`. |

## 3. Counterevidence, Exceptions & When This Pattern Does NOT Apply

- In strictly single-language English B2B niches or fully prepaid digital-product flows, the severity of this Marketing Automation mismatch is lower provided manual QA is still performed.
- ** Operational Boundary**: Never show a client GA4's default `AI Assistant` channel row (`e.g., 45 sessions`) and tell them 'that is 100% of your AI search traffic'—that omits 96.9% of AI citations coming through Google `AI Overviews` / `AI Mode` + `Perplexity`/`Claude`/`HUMAIN`! / لا تعرض للعميل صف قناة `AI Assistant` الافتراضي في GA4 وتخبره أن هذا هو إجمالي زيارات الذكاء الاصطناعي؛ لأن ذلك يغفل 96.9% من النقرات القادمة عبر `AI Overviews` في البحث العضوي بالإضافة إلى `Perplexity` و`Claude` و`HUMAIN Chat`!

## 4. Claims Remaining Uncertain & Update Triggers

- **Verification Requirement**: Verify live store/account configuration and current 2026/2027 platform UI settings for Marketing Automation before deploying changes.
- **Verification Requirement**: Confirm current statutory penalty thresholds and licensing rules with qualified local counsel in KSA, UAE, or Egypt.
- **No Guaranteed Outcomes**: Per Agent 2 v1.2 boundaries, this asset defines operational controls and testable measurement hypotheses; it does not promise guaranteed rankings, virality, or fixed ROAS lift.
- **Update Triggers**: Re-verify this framework whenever platform UI/API schemas change, prior to major Hijri/seasonal peaks (Ramadan/White Friday), or within 90 days of `2026-10-25`.
