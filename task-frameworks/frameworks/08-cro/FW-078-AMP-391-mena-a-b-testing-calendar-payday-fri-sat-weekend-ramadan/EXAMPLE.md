# End-to-End Worked Example & Failure Recovery — `FW-078` (`AMP-391`)

- **Framework**: MENA A/B Testing Calendar & Payday / Fri-Sat Weekend / Ramadan Cycle Decision Aid
- **العنوان بالعربية**: أداة قرار ضبط مدة اختبارات `A/B Testing` في مصر والخليج (مراعاة دورة الرواتب `25–30 الشهر`، عطلة الجمعة والسبت، ومواسم رمضان)
- **Selected Artifact Type**: `DECISION_AID`
- **Disclaimer**: *All scenarios, brand names, SKU codes, and metrics below are original, realistic illustrative examples for MENA practitioner training and are never represented as verified client outcomes.*

## 1. Realistic Sample Brief / Input (`المدخلات وموجز الحالة العملية`)

- **Store**: Riyadh Electronics Store testing Variation A (`Free Shipping over 300 SAR`) vs. Variation B (`10% Off Coupon`).
- **Previous Flawed Test**: Ran Variation A from `18–22 October` (pre-payday trough, CVR `1.4%`), then switched the site to Variation B from `26–30 October` (Saudi salary week, CVR `2.9%`) and concluded Variation B 'doubled conversion rate'.

## 2. Initial Generated / Completed Output (`المخرج الأولي عند تطبيق الأداة`)

- **Audit Verdict**: **`INVALID SEQUENTIAL TEST (Confounded by KSA 27th October Salary Surge)`**
- **Re-Run Valid Concurrent Protocol**:
  - Launched a 50/50 concurrent split (`Variation A` vs. `Variation B` running simultaneously on the exact same days) for **14 full days (`18 Oct – 31 Oct`)**, covering both the pre-payday week and the salary week across two full `Fri/Sat` weekends.

## 3. Human Review & Localization/Technical Edits (`المراجعة البشرية والتعديلات الرقابية والتقنية`)

1. **Segmented Results by Payday Window**: The valid 14-day concurrent test revealed that `Variation A (Free Shipping Threshold)` actually beat `Variation B` by `+11%` in net margin during payday week (`26–31 Oct`), whereas `Tabby/Tamara Installment Highlight` drove higher conversion during the mid-month trough (`18–24 Oct`).
2. **Locked Minimum Sample Gate**: Added a hard rule in the VWO/Optimizely runbook: zero winner declarations under `14 days` and `350 conversions/arm`.

## 4. Final Reviewed Example Outcome (`النتيجة النهائية الجاهزة للتنفيذ`)

- Established a 14-day concurrent A/B testing SOP anchored to KSA/Egypt payday and Fri/Sat weekend cycles, eliminating false-positive bandit switches.

## 5. What Can Go Wrong & Specific Correction / Fallback (`حالة الفشل المحتملة وخطة الإنقاذ والبديل`)

- **Common Failure Mode (`ما الذي قد يسير بشكل خاطئ؟`)**:
  An e-commerce manager runs a checkout test during the last 5 days of Sha'ban and continues it into the first 5 days of Ramadan (`AMP-125`), when hourly traffic shifts completely from daytime (`12 PM–5 PM`) to post-Iftar/Suhoor (`9 PM–3 AM`).
- **Specific Correction & Non-AI / Platform Fallback (`الإصلاح المحدد والبديل الآمن`)**:
  Never span a single A/B test across a major **Regime Boundary** (`Sha'ban -> Ramadan`, `Ramadan -> Eid`, or `Normal Week -> White Friday`); close pre-season tests before the regime shift and run dedicated in-season tests.
