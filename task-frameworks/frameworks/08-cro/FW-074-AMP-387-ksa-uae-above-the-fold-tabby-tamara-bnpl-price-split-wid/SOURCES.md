# Evidence Register & Source Boundaries — `FW-074` (`AMP-387`)

- **Framework Title (EN)**: KSA & UAE Above-the-Fold Tabby & Tamara BNPL Price-Split Widget Checklist
- **عنوان الأصل (AR)**: قائمة فحص وضع شارات تقسيط «تابي» و«تمارا» (`Tabby & Tamara`) بجوار السعر مباشرة أعلى طية صفحة المنتج في السعودية والإمارات
- **Channel**: CRO - Conversion Rate Optimization
- **Last Reviewed Date**: `2026-10-25`
- **Verification Gate Status**: `READY_FOR_REVIEW`

## 1. Problem & Empirical Evidence (What Proves the Failure Mechanism in Egypt & GCC)

| Source ID | Title & Direct Link | Publisher | Published | Accessed | Type & Confidence | What This Source Supports | Support Boundary |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `SRC-081` | [Conversion Rate Optimization for UAE E-Commerce (2026)](https://soluvide.com/blog/conversion-rate-optimization-uae-ecommerce-2026) | Soluvide | `2026-02-19` | `2026-10-25` | `PRACTITIONER_GUIDE` (`REPEATED_SIGNAL`) | Shows how Cash on Delivery (COD) and Buy Now Pay Later (Tabby and Tamara) reduce checkout friction and lift AOV in UAE/GCC e-commerce. | UAE and GCC e-commerce CRO. |
| `SRC-082` | [Tabby vs Tamara Shopify UAE 2026: BNPL Comparison](https://www.huptechweb.com/blogs/tabby-vs-tamara-shopify-uae-bnpl-2026) | Huptech Web | `2026-06-25` | `2026-10-25` | `MARKET_BENCHMARK` (`REPEATED_SIGNAL`) | Documents BNPL representing ~14% of UAE e-commerce checkout and compares Tabby vs Tamara placement, approval behavior, and merchant fees on Shopify. | UAE and KSA Shopify BNPL checkout optimization. |

## 2. Official Platform Capability, Regulatory & Advice Evidence

| Source ID | Title & Direct Link | Publisher | Published | Accessed | Status / Confidence | Official Capability or Rule Verified | Fallback / Operational Boundary |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `SRC-082` | [Tabby vs Tamara Shopify UAE 2026: BNPL Comparison](https://www.huptechweb.com/blogs/tabby-vs-tamara-shopify-uae-bnpl-2026) | Huptech Web | `2026-06-25` | `2026-10-25` | `OFFICIAL_CAPABILITY_CHECK` (`supported`) | Huptech and Soluvide 2026 UAE/KSA CRO studies confirm ~14% BNPL checkout share and highlight PDP above-the-fold installment visibility as a primary conversion and AOV driver. | Fallback: If third-party widget JS slows down mobile LCP (`AMP-393`), use the lightweight zero-JS Liquid/HTML box above and lazy-load the modal script on click. |

## 3. Counterevidence, Exceptions & When This Pattern Does NOT Apply

- In strictly single-language English B2B niches or fully prepaid digital-product flows, the severity of this CRO - Conversion Rate Optimization mismatch is lower provided manual QA is still performed.
- ** Operational Boundary**: Do not display static image screenshots of Tabby/Tamara that show a fixed or wrong installment number when the shopper switches product size/variant price! / لا تضع صورة ثابتة لتابي وتمارا تعرض رقماً خاطئاً عند تغيير مقاس أو خيار المنتج؛ استخدم الودجت الديناميكي الذي يقسم السعر الفعلي على 4 تلقائياً.

## 4. Claims Remaining Uncertain & Update Triggers

- **Verification Requirement**: Verify live store/account configuration and current 2026/2027 platform UI settings for CRO - Conversion Rate Optimization before deploying changes.
- **Verification Requirement**: Confirm current statutory penalty thresholds and licensing rules with qualified local counsel in KSA, UAE, or Egypt.
- **No Guaranteed Outcomes**: Per Agent 2 v1.2 boundaries, this asset defines operational controls and testable measurement hypotheses; it does not promise guaranteed rankings, virality, or fixed ROAS lift.
- **Update Triggers**: Re-verify this framework whenever platform UI/API schemas change, prior to major Hijri/seasonal peaks (Ramadan/White Friday), or within 90 days of `2026-10-25`.
