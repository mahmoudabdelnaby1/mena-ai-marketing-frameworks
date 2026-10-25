# Evidence Register & Source Boundaries — `FW-076` (`AMP-389`)

- **Framework Title (EN)**: Bilingual Landing Page RTL CSS Mirroring, Directional Icon & Sticky-CTA Collision Checklist
- **عنوان الأصل (AR)**: قائمة فحص الانعكاس الكامل لواجهات اليمين لليسار (`RTL CSS Mirroring`) واتجاه الأسهم ومنع تصادم الأزرار العائمة في الجوال
- **Channel**: CRO - Conversion Rate Optimization
- **Last Reviewed Date**: `2026-10-25`
- **Verification Gate Status**: `READY_FOR_REVIEW`

## 1. Problem & Empirical Evidence (What Proves the Failure Mechanism in Egypt & GCC)

| Source ID | Title & Direct Link | Publisher | Published | Accessed | Type & Confidence | What This Source Supports | Support Boundary |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `SRC-038` | [We Audited 20 Salla and Zid Stores: The SEO Defaults Saudi Merchants Inherit (2026)](https://voctos.net/salla-zid-store-seo-audit/) | VOCTOS | `2026-10-08` | `2026-10-25` | `EMPIRICAL_AUDIT` (`RESEARCH_FINDING`) | Audit of 20 Saudi stores (10 Salla, 10 Zid): 60% of sampled Salla sitemap URLs (88/146) redirected or returned 410; 6/6 Salla English pages canonicalized to Arabic; 9/10 Zid stores lacked Sitemap in robots.txt; 0/10 Salla stores had Brand in Product JSON-LD; 8/11 English pages kept Arabic-script titles. | Sample of 20 live Saudi stores audited on 2 Oct 2026. |
| `SRC-061` | [The Arabic SEO in Saudi Arabia Mistakes Costing Riyadh Brands Rankings](https://digistreetmedia.com/blog/the-arabic-seo-in-saudi-arabia-mistakes-costing-riyadh-brands-rankings/) | DigiStreet Media | `2026-09-29` | `2026-10-25` | `PRACTITIONER_GUIDE` (`REPEATED_SIGNAL`) | Identifies 5 recurring KSA SEO failures: treating Arabic as translation, running one strategy across Arabic/English, broken hreflang/RTL mobile UX, ignoring Vision 2030 sector context, and chasing non-local backlinks while treating Riyadh, Jeddah, and Dammam as homogeneous. | Saudi Arabia B2B and B2C SEO. |
| `SRC-065` | [Top Arabic Content Writing Mistakes Hurting Your SEO Rankings](https://www.aiqalam.com/en/blog/top-arabic-content-writing-mistakes-hurting-your-seo-rankings) | AI Qalam | `2026-10-24` | `2026-10-25` | `PRACTITIONER_GUIDE` (`REPEATED_SIGNAL`) | Documents poor RTL text alignment, unnatural AI phrasing, and morphological keyword stuffing in Arabic content. | Arabic SEO content writing. |

## 2. Official Platform Capability, Regulatory & Advice Evidence

| Source ID | Title & Direct Link | Publisher | Published | Accessed | Status / Confidence | Official Capability or Rule Verified | Fallback / Operational Boundary |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `SRC-061` | [The Arabic SEO in Saudi Arabia Mistakes Costing Riyadh Brands Rankings](https://digistreetmedia.com/blog/the-arabic-seo-in-saudi-arabia-mistakes-costing-riyadh-brands-rankings/) | DigiStreet Media | `2026-09-29` | `2026-10-25` | `OFFICIAL_CAPABILITY_CHECK` (`supported`) | CSS Logical Properties are supported across 98%+ of modern mobile and desktop browsers; JS carousels (Swiper/Slick) still require explicit `dir='rtl'` / `rtl: true` attributes. | Fallback: Test every `/ar/` landing page on a real mobile screen by swiping through the product gallery and opening the cart drawer. |

## 3. Counterevidence, Exceptions & When This Pattern Does NOT Apply

- In strictly single-language English B2B niches or fully prepaid digital-product flows, the severity of this CRO - Conversion Rate Optimization mismatch is lower provided manual QA is still performed.
- ** Operational Boundary**: Do not mirror universal non-directional icons (checkmarks `✓`, clock faces, play buttons `▶` on standard media players, or brand logos) when mirroring directional UI arrows! / لا تقم بعكس الأيقونات العالمية غير الاتجاهية (مثل علامة الصح `✓` أو عقارب الساعة أو شعار العلامة التجارية)؛ العكس يقتصر على أسهم الاتجاه والخطوات والتقدم.

## 4. Claims Remaining Uncertain & Update Triggers

- **Verification Requirement**: Verify live store/account configuration and current 2026/2027 platform UI settings for CRO - Conversion Rate Optimization before deploying changes.
- **Verification Requirement**: Confirm current statutory penalty thresholds and licensing rules with qualified local counsel in KSA, UAE, or Egypt.
- **No Guaranteed Outcomes**: Per Agent 2 v1.2 boundaries, this asset defines operational controls and testable measurement hypotheses; it does not promise guaranteed rankings, virality, or fixed ROAS lift.
- **Update Triggers**: Re-verify this framework whenever platform UI/API schemas change, prior to major Hijri/seasonal peaks (Ramadan/White Friday), or within 90 days of `2026-10-25`.
