# Evidence Register & Source Boundaries — `FW-052` (`AMP-240`)

- **Framework Title (EN)**: COD Serial-Returner Exclusion & Prepaid-Upgrade Win-Back Decision Aid (Egypt & KSA)
- **عنوان الأصل (AR)**: أداة قرار استبعاد «كثيري رفض استلام طلبات COD» وتحويلهم للدفع المسبق في حملات استعادة العملاء (`Win-Back`)
- **Channel**: Email Marketing
- **Last Reviewed Date**: `2026-10-25`
- **Verification Gate Status**: `READY_FOR_REVIEW`

## 1. Problem & Empirical Evidence (What Proves the Failure Mechanism in Egypt & GCC)

| Source ID | Title & Direct Link | Publisher | Published | Accessed | Type & Confidence | What This Source Supports | Support Boundary |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `SRC-050` | [Digital Advertising Landscape in Egypt (2026)](https://23hublab.com/digital-advertising-landscape-in-egypt/) | 23HubLab | `2026-03-15` | `2026-10-25` | `MARKET_BENCHMARK` (`RESEARCH_FINDING`) | In Egypt, standard Meta Pixel captures only 60-75% of conversions (25-40% lost to in-app browsers, iOS ATT, and ad blockers), while platform-reported conversions overstate actual revenue by 20-40% due to COD cancellations and last-click inflation; provides 2026 EGP CPM/CPC/CPL benchmarks and notes Snapchat is niche in Egypt vs TikTok/Meta. | Egyptian digital advertising market 2026. |
| `SRC-052` | [E-commerce Growth in Egypt vs. Saudi Arabia vs. UAE](https://23hublab.com/e-commerce-growth-in-egypt-vs-saudi-arabia-vs-uae/) | 23HubLab | `2026-05-01` | `2026-10-25` | `MARKET_BENCHMARK` (`RESEARCH_FINDING`) | Contrasts Egypt's high raw volume and high COD return risk with KSA/UAE higher AOV and digital payment adoption; highlights underexploited Egyptian Arabic SEO vs paid-only dependence. | MENA e-commerce structural comparison. |
| `SRC-086` | [Common Mistakes When Using AI in B2B Sales and Marketing](https://founderz.com/blog/common-mistakes-ai-b2b-sales-marketing/) | Founderz | `2026-08-15` | `2026-10-25` | `PRACTITIONER_GUIDE` (`REPEATED_SIGNAL`) | Automating B2B outreach and lead generation on top of uncleaned CRM data or without sales-marketing ICP alignment amplifies errors and lengthens the sales cycle. | B2B AI marketing and CRM automation. |

## 2. Official Platform Capability, Regulatory & Advice Evidence

| Source ID | Title & Direct Link | Publisher | Published | Accessed | Status / Confidence | Official Capability or Rule Verified | Fallback / Operational Boundary |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `SRC-052` | [E-commerce Growth in Egypt vs. Saudi Arabia vs. UAE](https://23hublab.com/e-commerce-growth-in-egypt-vs-saudi-arabia-vs-uae/) | 23HubLab | `2026-05-01` | `2026-10-25` | `OFFICIAL_CAPABILITY_CHECK` (`supported`) | In COD-heavy markets (Egypt merchant-measured payment mix from recent order records; KSA 15–30% COD), initial order creation (`Placed Order`) does not equal revenue collection; courier RTO status must update CRM profile properties. | Fallback: Filter all win-back and VIP segments by `Financial Status == Paid` (which for COD only triggers after courier cash collection). |

## 3. Counterevidence, Exceptions & When This Pattern Does NOT Apply

- In strictly single-language English B2B niches or fully prepaid digital-product flows, the severity of this Email Marketing mismatch is lower provided manual QA is still performed.
- ** Operational Boundary**: Never define a 'High-Value / VIP Customer' in Klaviyo, HubSpot, Salla, or Zid using `Total Placed Orders` (`إجمالي الطلبات`)—always filter by `Fulfilled / Delivered & Collected Orders` (`الطلبات المكتملة والمسلمة`). / لا تعرّف شريحة «العملاء المميزين VIP» بناءً على «إجمالي الطلبات المسجلة»؛ بل اعتمد حصرياً على «الطلبات المكتملة والمحصّلة فعلياً».

## 4. Claims Remaining Uncertain & Update Triggers

- **Verification Requirement**: Verify live store/account configuration and current 2026/2027 platform UI settings for Email Marketing before deploying changes.
- **Verification Requirement**: Confirm current statutory penalty thresholds and licensing rules with qualified local counsel in KSA, UAE, or Egypt.
- **No Guaranteed Outcomes**: Per Agent 2 v1.2 boundaries, this asset defines operational controls and testable measurement hypotheses; it does not promise guaranteed rankings, virality, or fixed ROAS lift.
- **Update Triggers**: Re-verify this framework whenever platform UI/API schemas change, prior to major Hijri/seasonal peaks (Ramadan/White Friday), or within 90 days of `2026-10-25`.
