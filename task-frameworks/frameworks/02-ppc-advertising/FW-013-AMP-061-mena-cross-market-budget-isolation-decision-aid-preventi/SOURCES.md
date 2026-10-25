# Evidence Register & Source Boundaries — `FW-013` (`AMP-061`)

- **Framework Title (EN)**: MENA Cross-Market Budget Isolation Decision Aid (Preventing the 4–5x Egypt vs. GCC CPM Arbitrage Trap)
- **عنوان الأصل (AR)**: أداة قرار فصل الميزانيات الإعلانية بين مصر والخليج (منع فخ التهام الميزانية بسبب فارق الـ CPM البالغ 4–5 أضعاف)
- **Channel**: Pay-Per-Click (PPC) Advertising
- **Last Reviewed Date**: `2026-10-25`
- **Verification Gate Status**: `READY_FOR_REVIEW`

## 1. Problem & Empirical Evidence (What Proves the Failure Mechanism in Egypt & GCC)

| Source ID | Title & Direct Link | Publisher | Published | Accessed | Type & Confidence | What This Source Supports | Support Boundary |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `SRC-050` | [Digital Advertising Landscape in Egypt (2026)](https://23hublab.com/digital-advertising-landscape-in-egypt/) | 23HubLab | `2026-03-15` | `2026-10-25` | `MARKET_BENCHMARK` (`RESEARCH_FINDING`) | In Egypt, standard Meta Pixel captures only 60-75% of conversions (25-40% lost to in-app browsers, iOS ATT, and ad blockers), while platform-reported conversions overstate actual revenue by 20-40% due to COD cancellations and last-click inflation; provides 2026 EGP CPM/CPC/CPL benchmarks and notes Snapchat is niche in Egypt vs TikTok/Meta. | Egyptian digital advertising market 2026. |
| `SRC-051` | [Paid Media Cost Comparison: Egypt vs. UAE vs. Saudi Arabia](https://23hublab.com/paid-media-cost-comparison-egypt-vs-uae-vs-saudi-arabia/) | 23HubLab | `2026-04-10` | `2026-10-25` | `MARKET_BENCHMARK` (`RESEARCH_FINDING`) | UAE CPMs run 4-5x higher than Egypt CPMs, and Saudi CPMs run 60-80% of UAE levels; Ramadan increases Egyptian Meta CPMs by 40-70%; pooling Egypt and GCC into a single automated budget/ad set causes algorithms to dump spend into cheap Egyptian clicks. | Cross-market Meta & Google Ads cost dynamics in Egypt, KSA, and UAE. |
| `SRC-052` | [E-commerce Growth in Egypt vs. Saudi Arabia vs. UAE](https://23hublab.com/e-commerce-growth-in-egypt-vs-saudi-arabia-vs-uae/) | 23HubLab | `2026-05-01` | `2026-10-25` | `MARKET_BENCHMARK` (`RESEARCH_FINDING`) | Contrasts Egypt's high raw volume and high COD return risk with KSA/UAE higher AOV and digital payment adoption; highlights underexploited Egyptian Arabic SEO vs paid-only dependence. | MENA e-commerce structural comparison. |

## 2. Official Platform Capability, Regulatory & Advice Evidence

| Source ID | Title & Direct Link | Publisher | Published | Accessed | Status / Confidence | Official Capability or Rule Verified | Fallback / Operational Boundary |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `SRC-051` | [Paid Media Cost Comparison: Egypt vs. UAE vs. Saudi Arabia](https://23hublab.com/paid-media-cost-comparison-egypt-vs-uae-vs-saudi-arabia/) | 23HubLab | `2026-04-10` | `2026-10-25` | `OFFICIAL_CAPABILITY_CHECK` (`supported`) | 23HubLab 2026 benchmarks document a 4–5x CPM gap between UAE/KSA and Egypt; automated budget optimizers prioritize lowest-cost auctions when countries are pooled. | Fallback: Separate campaigns by CPM/country tier at the campaign level. |

## 3. Counterevidence, Exceptions & When This Pattern Does NOT Apply

- In strictly single-language English B2B niches or fully prepaid digital-product flows, the severity of this Pay-Per-Click (PPC) Advertising mismatch is lower provided manual QA is still performed.
- ** Operational Boundary**: Do not split cities within the same country into micro-budgets if total daily spend cannot support ~50 conversions/week per campaign—isolate by country/CPM tier first. / لا تقم بتفتيت الميزانية الصغيرة جداً بين عشرات المدن داخل الدولة الواحدة إذا لم تكفِ لتحقيق 50 تحويلاً أسبوعياً؛ افصل أولاً على مستوى الدول/شرائح الـ CPM.

## 4. Claims Remaining Uncertain & Update Triggers

- **Verification Requirement**: Verify live store/account configuration and current 2026/2027 platform UI settings for Pay-Per-Click (PPC) Advertising before deploying changes.
- **Verification Requirement**: Confirm current statutory penalty thresholds and licensing rules with qualified local counsel in KSA, UAE, or Egypt.
- **No Guaranteed Outcomes**: Per Agent 2 v1.2 boundaries, this asset defines operational controls and testable measurement hypotheses; it does not promise guaranteed rankings, virality, or fixed ROAS lift.
- **Update Triggers**: Re-verify this framework whenever platform UI/API schemas change, prior to major Hijri/seasonal peaks (Ramadan/White Friday), or within 90 days of `2026-10-25`.
