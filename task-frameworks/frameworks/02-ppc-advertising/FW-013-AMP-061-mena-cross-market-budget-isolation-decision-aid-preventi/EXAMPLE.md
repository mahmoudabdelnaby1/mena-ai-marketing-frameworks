# End-to-End Worked Example & Failure Recovery — `FW-013` (`AMP-061`)

- **Framework**: MENA Cross-Market Budget Isolation Decision Aid (Preventing the 4–5x Egypt vs. GCC CPM Arbitrage Trap)
- **العنوان بالعربية**: أداة قرار فصل الميزانيات الإعلانية بين مصر والخليج (منع فخ التهام الميزانية بسبب فارق الـ CPM البالغ 4–5 أضعاف)
- **Selected Artifact Type**: `DECISION_AID`
- **Disclaimer**: *All scenarios, brand names, SKU codes, and metrics below are original, realistic illustrative examples for MENA practitioner training and are never represented as verified client outcomes.*

## 1. Realistic Sample Brief / Input (`المدخلات وموجز الحالة العملية`)

- **Advertiser**: Regional D2C Modest Fashion Brand shipping to UAE, Saudi Arabia, and Egypt.
- **Total Monthly Budget**: `$30,000/month` (`$1,000/day`).
- **Previous Mistake**: Ran 1 global Meta Advantage+ Shopping Campaign (`Maximize Conversions`) targeting `UAE + KSA + Egypt` together. Result: `88%` of budget (`$26,400`) was spent in Egypt (where AOV was `$28` with `32%` COD returns), while UAE (`$145` AOV) received only `3%` of spend.

## 2. Initial Generated / Completed Output (`المخرج الأولي عند تطبيق الأداة`)

- **Isolated Campaign Architecture (`$1,000/day` Total)**:
  - **Campaign 1 (`KSA_ASC_SAR`)**: `$500/day` (50% budget) | Currency: `SAR` (incl. 15% VAT) | Creative: Saudi Khaleeji + Tamara/Tabby badge.
  - **Campaign 2 (`UAE_ASC_AED`)**: `$300/day` (30% budget) | Currency: `AED` (incl. 5% VAT) | Creative: Bilingual English/Gulf + Tabby/Apple Pay.
  - **Campaign 3 (`EGY_ASC_EGP`)**: `$200/day` (20% budget) | Currency: `EGP` | Bidding: Value-adjusted for Net Delivered COD orders (`AMP-062`).

## 3. Human Review & Localization/Technical Edits (`المراجعة البشرية والتعديلات الرقابية والتقنية`)

1. **Catalog Feed Separation**: Linked each of the 3 campaigns to its country-specific catalog feed (`SAR`, `AED`, `EGP`) so dynamic product overlays never display `EGP` prices to Dubai shoppers or `AED` prices to Cairo shoppers.
2. **Ad Set Minimums Check**: Confirmed each isolated campaign generates `>65` conversions/week, clearing Meta's learning-phase threshold without cross-country cannibalization.

## 4. Final Reviewed Example Outcome (`النتيجة النهائية الجاهزة للتنفيذ`)

- 3 Country-Isolated Campaigns live with locked daily caps (`KSA: $500/d`, `UAE: $300/d`, `EGY: $200/d`), localized currencies, and zero cross-border CPM arbitrage leakage.

## 5. What Can Go Wrong & Specific Correction / Fallback (`حالة الفشل المحتملة وخطة الإنقاذ والبديل`)

- **Common Failure Mode (`ما الذي قد يسير بشكل خاطئ؟`)**:
  A media buyer separates Egypt and UAE into two Ad Sets inside the SAME Meta Campaign with Advantage+ Campaign Budget (`CBO`) turned ON; CBO still shifts 85% of the campaign budget into the Egypt Ad Set.
- **Specific Correction & Non-AI / Platform Fallback (`الإصلاح المحدد والبديل الآمن`)**:
  Enforce isolation at the **Campaign level** (or disable Campaign Budget Optimization and lock Ad Set daily budgets explicitly)—never rely on CBO across countries with >30% CPM divergence.
