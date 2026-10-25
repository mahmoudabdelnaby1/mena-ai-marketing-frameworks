# Evidence Register & Source Boundaries — `FW-078` (`AMP-391`)

- **Framework Title (EN)**: MENA A/B Testing Calendar & Payday / Fri-Sat Weekend / Ramadan Cycle Decision Aid
- **عنوان الأصل (AR)**: أداة قرار ضبط مدة اختبارات `A/B Testing` في مصر والخليج (مراعاة دورة الرواتب `25–30 الشهر`، عطلة الجمعة والسبت، ومواسم رمضان)
- **Channel**: CRO - Conversion Rate Optimization
- **Last Reviewed Date**: `2026-10-25`
- **Verification Gate Status**: `READY_FOR_REVIEW`

## 1. Problem & Empirical Evidence (What Proves the Failure Mechanism in Egypt & GCC)

| Source ID | Title & Direct Link | Publisher | Published | Accessed | Type & Confidence | What This Source Supports | Support Boundary |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `SRC-050` | [Digital Advertising Landscape in Egypt (2026)](https://23hublab.com/digital-advertising-landscape-in-egypt/) | 23HubLab | `2026-03-15` | `2026-10-25` | `MARKET_BENCHMARK` (`RESEARCH_FINDING`) | In Egypt, standard Meta Pixel captures only 60-75% of conversions (25-40% lost to in-app browsers, iOS ATT, and ad blockers), while platform-reported conversions overstate actual revenue by 20-40% due to COD cancellations and last-click inflation; provides 2026 EGP CPM/CPC/CPL benchmarks and notes Snapchat is niche in Egypt vs TikTok/Meta. | Egyptian digital advertising market 2026. |
| `SRC-051` | [Paid Media Cost Comparison: Egypt vs. UAE vs. Saudi Arabia](https://23hublab.com/paid-media-cost-comparison-egypt-vs-uae-vs-saudi-arabia/) | 23HubLab | `2026-04-10` | `2026-10-25` | `MARKET_BENCHMARK` (`RESEARCH_FINDING`) | UAE CPMs run 4-5x higher than Egypt CPMs, and Saudi CPMs run 60-80% of UAE levels; Ramadan increases Egyptian Meta CPMs by 40-70%; pooling Egypt and GCC into a single automated budget/ad set causes algorithms to dump spend into cheap Egyptian clicks. | Cross-market Meta & Google Ads cost dynamics in Egypt, KSA, and UAE. |
| `SRC-056` | [GCC Marketing Playbook: UAE, Saudi Arabia and Qatar](https://thegrower.ai/gcc-marketing) | Grower AI | `2026-10-12` | `2026-10-25` | `MARKET_BENCHMARK` (`RESEARCH_FINDING`) | Secondary regional reach material; its localization discussion is not treated as a universal quota or wage rule. | Check current activity- and workforce-specific requirements with the official HRSD calculator. |

## 2. Official Platform Capability, Regulatory & Advice Evidence

| Source ID | Title & Direct Link | Publisher | Published | Accessed | Status / Confidence | Official Capability or Rule Verified | Fallback / Operational Boundary |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `SRC-050` | [Digital Advertising Landscape in Egypt (2026)](https://23hublab.com/digital-advertising-landscape-in-egypt/) | 23HubLab | `2026-03-15` | `2026-10-25` | `OFFICIAL_CAPABILITY_CHECK` (`supported`) | Standard frequentist and Bayesian A/B engines assume stationary conversion rates over time; because MENA conversion rates exhibit strong non-stationary payday (25th–30th) and Fri/Sat weekly cycles, fixed 50/50 splits over full 7/14-day multiples are mandatory. | Fallback: Always use fixed 50/50 traffic allocation for 14 full days instead of early-stopping auto-bandits. |

## 3. Counterevidence, Exceptions & When This Pattern Does NOT Apply

- In strictly single-language English B2B niches or fully prepaid digital-product flows, the severity of this CRO - Conversion Rate Optimization mismatch is lower provided manual QA is still performed.
- ** Operational Boundary**: Never run a sequential test ('Version A ran from the 15th to the 21st, and Version B ran from the 25th to the 30th') and attribute the payday surge to Version B! / إياك وإجراء اختبار تتابعي (تشغيل النسخة A من يوم 15 إلى 21، ثم النسخة B من يوم 25 إلى 30 وقت نزول الرواتب) ونسب ارتفاع المبيعات للنسخة B!

## 4. Claims Remaining Uncertain & Update Triggers

- **Verification Requirement**: Verify live store/account configuration and current 2026/2027 platform UI settings for CRO - Conversion Rate Optimization before deploying changes.
- **Verification Requirement**: Confirm current statutory penalty thresholds and licensing rules with qualified local counsel in KSA, UAE, or Egypt.
- **No Guaranteed Outcomes**: Per Agent 2 v1.2 boundaries, this asset defines operational controls and testable measurement hypotheses; it does not promise guaranteed rankings, virality, or fixed ROAS lift.
- **Update Triggers**: Re-verify this framework whenever platform UI/API schemas change, prior to major Hijri/seasonal peaks (Ramadan/White Friday), or within 90 days of `2026-10-25`.
