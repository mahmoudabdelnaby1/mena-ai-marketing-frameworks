# End-to-End Worked Example & Failure Recovery — `FW-022` (`AMP-070`)

- **Framework**: MENA Healthcare & Pharmaceutical Paid Search Eligibility & Regulatory Routing Aid
- **العنوان بالعربية**: أداة القرار الإعلاني للقطاع الصحي والدوائي في الأسواق العربية (قيود `Google AI Mode` وتصاريح `SFDA / MOH / EDA`)
- **Selected Artifact Type**: `DECISION_AID`
- **Disclaimer**: *All scenarios, brand names, SKU codes, and metrics below are original, realistic illustrative examples for MENA practitioner training and are never represented as verified client outcomes.*

## 1. Realistic Sample Brief / Input (`المدخلات وموجز الحالة العملية`)

- **Advertiser**: Multi-branch Dermatology & Aesthetic Clinic in Riyadh and Dubai.
- **Problem**: Agency tried to run Google Search ads with headlines containing prescription injectable brand names and pitched 'Google AI Mode Pharma Ads' for a new hair-loss treatment; 18 of 20 ads were disapproved for `Restricted drug terms` and missing DHA/MOH permit disclosures.

## 2. Initial Generated / Completed Output (`المخرج الأولي عند تطبيق الأداة`)

- **Compliant Routing & Copy Restructure**:
  - Removed prescription drug brand names from Google Search headlines and pinned the clinic's official service category (`عيادة جلدية وليزر وعناية بالشعر`).
  - Added mandatory license footer pin:
    - Riyadh Campaign: `"ترخيص وزارة الصحة السعودية رقم: [MOH-XXXX]"`
    - Dubai Campaign: `"تصريح هيئة الصحة بدبي رقم: [DHA-AD-XXXX]"`

## 3. Human Review & Localization/Technical Edits (`المراجعة البشرية والتعديلات الرقابية والتقنية`)

1. **Landing Page Audit (`AMP-176`)**: Replaced `"علاج نهائي ومضمون 100% لتساقط الشعر"` on the landing page with `"جلسات عناية متخصصة بفروة الرأس تحت إشراف أطباء جلدية مرخصين"`.
2. **Expectation Alignment**: Clarified in the media plan that Google AI Mode pharma ad inventory is not enabled for Arab jurisdictions, shifting budget to standard High-Intent Arabic/English Search + Google Maps Local Pack.

## 4. Final Reviewed Example Outcome (`النتيجة النهائية الجاهزة للتنفيذ`)

- `100%` of clinic Search ads approved in Riyadh and Dubai with visible `MOH` and `DHA` permit numbers and zero restricted-drug policy violations.

## 5. What Can Go Wrong & Specific Correction / Fallback (`حالة الفشل المحتملة وخطة الإنقاذ والبديل`)

- **Common Failure Mode (`ما الذي قد يسير بشكل خاطئ؟`)**:
  A copywriter uses leetspeak or spacing tricks (`بـ.ـوتـ.ـوكس` or `B.o.t.o.x`) to bypass Google Ads' automated prescription drug filter; Google's policy system flags the account for `Circumventing Systems`, suspending the entire ad account permanently.
- **Specific Correction & Non-AI / Platform Fallback (`الإصلاح المحدد والبديل الآمن`)**:
  Never use obfuscation or character insertion to bypass medical ad filters (`Circumventing Systems` is a fatal account ban); remove restricted drug terms completely and apply for official Google Healthcare certification where eligible.
