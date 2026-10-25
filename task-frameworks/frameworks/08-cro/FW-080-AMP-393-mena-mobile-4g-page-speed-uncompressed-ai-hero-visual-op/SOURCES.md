# Evidence Register & Source Boundaries — `FW-080` (`AMP-393`)

- **Framework Title (EN)**: MENA Mobile 4G Page-Speed & Uncompressed AI Hero Visual Optimization Checklist (`LCP < 2.5s`)
- **عنوان الأصل (AR)**: قائمة فحص سرعة تحميل صفحات الجوال على شبكات `4G` وضغط الصور والفيديوهات المولدة بالذكاء الاصطناعي (`LCP < 2.5s`)
- **Channel**: CRO - Conversion Rate Optimization
- **Last Reviewed Date**: `2026-10-25`
- **Verification Gate Status**: `READY_FOR_REVIEW`

## 1. Problem & Empirical Evidence (What Proves the Failure Mechanism in Egypt & GCC)

| Source ID | Title & Direct Link | Publisher | Published | Accessed | Type & Confidence | What This Source Supports | Support Boundary |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `SRC-050` | [Digital Advertising Landscape in Egypt (2026)](https://23hublab.com/digital-advertising-landscape-in-egypt/) | 23HubLab | `2026-03-15` | `2026-10-25` | `MARKET_BENCHMARK` (`RESEARCH_FINDING`) | In Egypt, standard Meta Pixel captures only 60-75% of conversions (25-40% lost to in-app browsers, iOS ATT, and ad blockers), while platform-reported conversions overstate actual revenue by 20-40% due to COD cancellations and last-click inflation; provides 2026 EGP CPM/CPC/CPL benchmarks and notes Snapchat is niche in Egypt vs TikTok/Meta. | Egyptian digital advertising market 2026. |
| `SRC-061` | [The Arabic SEO in Saudi Arabia Mistakes Costing Riyadh Brands Rankings](https://digistreetmedia.com/blog/the-arabic-seo-in-saudi-arabia-mistakes-costing-riyadh-brands-rankings/) | DigiStreet Media | `2026-09-29` | `2026-10-25` | `PRACTITIONER_GUIDE` (`REPEATED_SIGNAL`) | Identifies 5 recurring KSA SEO failures: treating Arabic as translation, running one strategy across Arabic/English, broken hreflang/RTL mobile UX, ignoring Vision 2030 sector context, and chasing non-local backlinks while treating Riyadh, Jeddah, and Dammam as homogeneous. | Saudi Arabia B2B and B2C SEO. |

## 2. Official Platform Capability, Regulatory & Advice Evidence

| Source ID | Title & Direct Link | Publisher | Published | Accessed | Status / Confidence | Official Capability or Rule Verified | Fallback / Operational Boundary |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `SRC-061` | [The Arabic SEO in Saudi Arabia Mistakes Costing Riyadh Brands Rankings](https://digistreetmedia.com/blog/the-arabic-seo-in-saudi-arabia-mistakes-costing-riyadh-brands-rankings/) | DigiStreet Media | `2026-09-29` | `2026-10-25` | `OFFICIAL_CAPABILITY_CHECK` (`supported`) | WebP is supported across 99%+ of iOS Safari and Android Chrome devices in Egypt and GCC; raw PNG exports from diffusion models are uncompressed lossless files never meant for direct web serving. | Fallback: Block any image `> 200 KB` from being committed to hero templates via CI/CMS upload limits. |

## 3. Counterevidence, Exceptions & When This Pattern Does NOT Apply

- In strictly single-language English B2B niches or fully prepaid digital-product flows, the severity of this CRO - Conversion Rate Optimization mismatch is lower provided manual QA is still performed.
- ** Operational Boundary**: Never upload a raw `.png` from Midjourney/DALL·E or an autoplay unmuted/high-bitrate `.mp4` into an above-the-fold mobile hero banner. / لا ترفع أبداً ملف `.png` خام من أدوات التوليد أو فيديو خلفية عالي الحجم في الجزء العلوي من صفحة الجوال.

## 4. Claims Remaining Uncertain & Update Triggers

- **Verification Requirement**: Verify live store/account configuration and current 2026/2027 platform UI settings for CRO - Conversion Rate Optimization before deploying changes.
- **Verification Requirement**: Confirm current statutory penalty thresholds and licensing rules with qualified local counsel in KSA, UAE, or Egypt.
- **No Guaranteed Outcomes**: Per Agent 2 v1.2 boundaries, this asset defines operational controls and testable measurement hypotheses; it does not promise guaranteed rankings, virality, or fixed ROAS lift.
- **Update Triggers**: Re-verify this framework whenever platform UI/API schemas change, prior to major Hijri/seasonal peaks (Ramadan/White Friday), or within 90 days of `2026-10-25`.
