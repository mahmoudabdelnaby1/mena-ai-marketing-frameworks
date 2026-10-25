# Evidence Register & Source Boundaries — `FW-060` (`AMP-288`)

- **Framework Title (EN)**: Anti-Coupon-Leak Influencer Attribution & Unique Landing-Page / Cart-Link Workflow
- **عنوان الأصل (AR)**: مسار عمل قياس عائد المؤثرين ومنع تسرب أكواد الخصم الثابتة (`Promo Code Cannibalization`) لزيارات الدفع العضوية
- **Channel**: Influencer Marketing
- **Last Reviewed Date**: `2026-10-25`
- **Verification Gate Status**: `READY_FOR_REVIEW`

## 1. Problem & Empirical Evidence (What Proves the Failure Mechanism in Egypt & GCC)

| Source ID | Title & Direct Link | Publisher | Published | Accessed | Type & Confidence | What This Source Supports | Support Boundary |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `SRC-045` | [How GA4 Classifies AI Traffic for Arab Websites: What Saudi, UAE and Egyptian Sites Lose (2026 Study)](https://voctos.net/ga4-ai-traffic-arab-markets/) | VOCTOS | `2026-10-18` | `2026-10-25` | `EMPIRICAL_AUDIT` (`RESEARCH_FINDING`) | GA4's AI Assistant channel (launched 13 May 2026) misses 96.9% of AI search citations (which come from Google AI Overviews and AI Mode and land in Organic Search), sends ChatGPT links with rel='noreferrer' or WhatsApp shares to Direct, and sends Perplexity, Claude, HUMAIN Chat (KSA), Fanar (Qatar), and Gulf marketplaces (amazon.sa, noon.com) to Referral. | Based on GA4 channel rules, StatCounter Sep 2026 Arab market data, and Delta Medical Labs KSA case study. |
| `SRC-050` | [Digital Advertising Landscape in Egypt (2026)](https://23hublab.com/digital-advertising-landscape-in-egypt/) | 23HubLab | `2026-03-15` | `2026-10-25` | `MARKET_BENCHMARK` (`RESEARCH_FINDING`) | In Egypt, standard Meta Pixel captures only 60-75% of conversions (25-40% lost to in-app browsers, iOS ATT, and ad blockers), while platform-reported conversions overstate actual revenue by 20-40% due to COD cancellations and last-click inflation; provides 2026 EGP CPM/CPC/CPL benchmarks and notes Snapchat is niche in Egypt vs TikTok/Meta. | Egyptian digital advertising market 2026. |

## 2. Official Platform Capability, Regulatory & Advice Evidence

| Source ID | Title & Direct Link | Publisher | Published | Accessed | Status / Confidence | Official Capability or Rule Verified | Fallback / Operational Boundary |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `SRC-045` | [How GA4 Classifies AI Traffic for Arab Websites: What Saudi, UAE and Egyptian Sites Lose (2026 Study)](https://voctos.net/ga4-ai-traffic-arab-markets/) | VOCTOS | `2026-10-18` | `2026-10-25` | `OFFICIAL_CAPABILITY_CHECK` (`supported`) | All major MENA e-commerce platforms support start/end timestamps on coupon codes and URL-parameter discount auto-application. | Fallback: Always set an explicit end date (`+72 hours` from post time) when creating any influencer promo code. |

## 3. Counterevidence, Exceptions & When This Pattern Does NOT Apply

- In strictly single-language English B2B niches or fully prepaid digital-product flows, the severity of this Influencer Marketing mismatch is lower provided manual QA is still performed.
- ** Operational Boundary**: Never pay creator commission or evaluate influencer ROAS on `Total Orders Using Promo Code X` without splitting `Click-Verified Influencer Sessions` vs. `Zero-Click Checkout Code Paste`. / لا تقم أبداً بحساب عمولة المؤثر أو تقييم عائده الإعلاني بناءً على «إجمالي الطلبات التي استخدمت الكود» دون فصل «الزيارات القادمة فعلياً من رابط المؤثر» عن «لصق الكود في صفحة الدفع من زوار محركات البحث».

## 4. Claims Remaining Uncertain & Update Triggers

- **Verification Requirement**: Verify live store/account configuration and current 2026/2027 platform UI settings for Influencer Marketing before deploying changes.
- **Verification Requirement**: Confirm current statutory penalty thresholds and licensing rules with qualified local counsel in KSA, UAE, or Egypt.
- **No Guaranteed Outcomes**: Per Agent 2 v1.2 boundaries, this asset defines operational controls and testable measurement hypotheses; it does not promise guaranteed rankings, virality, or fixed ROAS lift.
- **Update Triggers**: Re-verify this framework whenever platform UI/API schemas change, prior to major Hijri/seasonal peaks (Ramadan/White Friday), or within 90 days of `2026-10-25`.
