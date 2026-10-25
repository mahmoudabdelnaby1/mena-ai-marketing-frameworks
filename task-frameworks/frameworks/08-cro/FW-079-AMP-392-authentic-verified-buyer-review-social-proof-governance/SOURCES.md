# Evidence Register & Source Boundaries — `FW-079` (`AMP-392`)

- **Framework Title (EN)**: Authentic Verified-Buyer Review & Social Proof Governance Checklist (Eliminating Fake AI Review Widgets)
- **عنوان الأصل (AR)**: قائمة فحص حوكمة التقييمات وإثباتات الثقة الاجتماعية (`Social Proof` — منع ودجات التقييمات الوهمية المولدة بالذكاء الاصطناعي)
- **Channel**: CRO - Conversion Rate Optimization
- **Last Reviewed Date**: `2026-10-25`
- **Verification Gate Status**: `READY_FOR_REVIEW`

## 1. Problem & Empirical Evidence (What Proves the Failure Mechanism in Egypt & GCC)

| Source ID | Title & Direct Link | Publisher | Published | Accessed | Type & Confidence | What This Source Supports | Support Boundary |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `SRC-044` | [False Discounts in Arab Markets: What Saudi, UAE and Egyptian Law Say Before White Friday](https://voctos.net/false-discount-advertising-law-arab-markets-white-friday/) | VOCTOS | `2026-10-22` | `2026-10-25` | `LEGAL_ANALYSIS` (`RESEARCH_FINDING`) | Fake reference prices violate law across all 3 markets: KSA fines up to SAR 1,000,000 and requires a Ministry of Commerce discount license + old/new price tag; Egypt Law 181/2018 fines EGP 50,000 to EGP 2,000,000; UAE fines AED 100,000. | Read from primary statutory texts on 22 Oct 2026. |
| `SRC-061` | [The Arabic SEO in Saudi Arabia Mistakes Costing Riyadh Brands Rankings](https://digistreetmedia.com/blog/the-arabic-seo-in-saudi-arabia-mistakes-costing-riyadh-brands-rankings/) | DigiStreet Media | `2026-09-29` | `2026-10-25` | `PRACTITIONER_GUIDE` (`REPEATED_SIGNAL`) | Identifies 5 recurring KSA SEO failures: treating Arabic as translation, running one strategy across Arabic/English, broken hreflang/RTL mobile UX, ignoring Vision 2030 sector context, and chasing non-local backlinks while treating Riyadh, Jeddah, and Dammam as homogeneous. | Saudi Arabia B2B and B2C SEO. |

## 2. Official Platform Capability, Regulatory & Advice Evidence

| Source ID | Title & Direct Link | Publisher | Published | Accessed | Status / Confidence | Official Capability or Rule Verified | Fallback / Operational Boundary |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `SRC-044` | [False Discounts in Arab Markets: What Saudi, UAE and Egyptian Law Say Before White Friday](https://voctos.net/false-discount-advertising-law-arab-markets-white-friday/) | VOCTOS | `2026-10-22` | `2026-10-25` | `OFFICIAL_CAPABILITY_CHECK` (`supported`) | Regional consumer laws prohibit fabricated reviews and false popularity indicators; Google Search Central also issues manual actions if `aggregateRating` JSON-LD is populated with non-genuine or scraped reviews. | Fallback: If a brand-new product has `0` reviews yet, hide the star counter (`عرض: منتج جديد`) and highlight the official warranty and Saudi Business Center verification badge until the first 3 real buyer reviews arrive. |

## 3. Counterevidence, Exceptions & When This Pattern Does NOT Apply

- In strictly single-language English B2B niches or fully prepaid digital-product flows, the severity of this CRO - Conversion Rate Optimization mismatch is lower provided manual QA is still performed.
- ** Operational Boundary**: Never import scraped AliExpress/Amazon reviews translated by AI into Arabic onto your store, and never run random-timer 'X from Jeddah just bought this' popups. / لا تقم أبداً باستيراد تقييمات مترجمة آلياً من مواقع خارجية (`AliExpress / Amazon`) وادعاء أنها لعملاء متجرك، ولا تشغل نوافذ إشعارات الشراء العشوائية الوهمية.

## 4. Claims Remaining Uncertain & Update Triggers

- **Verification Requirement**: Verify live store/account configuration and current 2026/2027 platform UI settings for CRO - Conversion Rate Optimization before deploying changes.
- **Verification Requirement**: Confirm current statutory penalty thresholds and licensing rules with qualified local counsel in KSA, UAE, or Egypt.
- **No Guaranteed Outcomes**: Per Agent 2 v1.2 boundaries, this asset defines operational controls and testable measurement hypotheses; it does not promise guaranteed rankings, virality, or fixed ROAS lift.
- **Update Triggers**: Re-verify this framework whenever platform UI/API schemas change, prior to major Hijri/seasonal peaks (Ramadan/White Friday), or within 90 days of `2026-10-25`.
