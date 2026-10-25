# End-to-End Worked Example & Failure Recovery — `FW-054` (`AMP-282`)

- **Framework**: Cross-Border MENA Creator Permit Decision Matrix (UAE Media Council Permit vs. KSA GAMR Mawthooq vs. Egypt Tax/SCM)
- **العنوان بالعربية**: أداة القرار لتراخيص المؤثرين العابرة للحدود بين الإمارات (مجلس الإمارات للإعلام) والسعودية (`موثوق`) ومصر
- **Selected Artifact Type**: `DECISION_AID`
- **Disclaimer**: *All scenarios, brand names, SKU codes, and metrics below are original, realistic illustrative examples for MENA practitioner training and are never represented as verified client outcomes.*

## 1. Realistic Sample Brief / Input (`المدخلات وموجز الحالة العملية`)

- **Campaign**: Regional Tourism & Retail App flying 3 creators (1 Saudi, 1 Egyptian, 1 Emirati) to Dubai for a 4-day paid brand shoot, followed by a 3-day shoot in Riyadh.

## 2. Initial Generated / Completed Output (`المخرج الأولي عند تطبيق الأداة`)

- **Permit Routing Plan**:
  1. **Dubai Leg (`UAE Media Council`)**:
     - Emirati creator: Verified active UAE Media Council Advertiser Permit displayed in bio.
     - Visiting Saudi & Egyptian creators: Registered under the partner Dubai talent agency for **UAE Visiting Advertiser Permits (`تصريح معلن زائر`)** 14 days prior to travel (holding a Saudi `Mawthooq` license does NOT exempt a creator filming ads in Dubai from UAE Media Council rules!).
  2. **Riyadh Leg (`KSA GAMR`)**:
     - Saudi creator: Verified active `Mawthooq` license (`AMP-281`).
     - Visiting Emirati & Egyptian creators: Contracted and cleared directly through the licensed Riyadh advertising agency under GAMR visiting/agency sponsorship rules.

## 3. Human Review & Localization/Technical Edits (`المراجعة البشرية والتعديلات الرقابية والتقنية`)

1. **Added 14-Day Lead Time Gate**: Blocked flight ticket booking until permit numbers for both legs were issued and logged in the production tracker.
2. **Tax Withholding & E-Invoice Check (Egypt)**: Confirmed the Egyptian creator's contract includes their Egyptian Tax Registration Number (`رقم التسجيل الضريبي`) and electronic invoice (`الفاتورة الإلكترونية`) compliance.

## 4. Final Reviewed Example Outcome (`النتيجة النهائية الجاهزة للتنفيذ`)

- All 3 creators cleared with jurisdiction-specific permits for both the UAE and KSA shoots 10 days before departure, with zero cross-border permit violations.

## 5. What Can Go Wrong & Specific Correction / Fallback (`حالة الفشل المحتملة وخطة الإنقاذ والبديل`)

- **Common Failure Mode (`ما الذي قد يسير بشكل خاطئ؟`)**:
  A Dubai agency books a famous Saudi creator (who holds a valid KSA `Mawthooq` license) to film paid restaurant & mall ads inside Dubai without obtaining a UAE Media Council Visiting Advertiser Permit, assuming `Mawthooq` is valid across the GCC.
- **Specific Correction & Non-AI / Platform Fallback (`الإصلاح المحدد والبديل الآمن`)**:
  Enforce the **Jurisdiction Independence Rule**: `KSA Mawthooq != UAE Media Council Permit`. Always verify the permit required by (a) the country where the creator is physically filming/residing AND (b) the country where the ad is targeted.
