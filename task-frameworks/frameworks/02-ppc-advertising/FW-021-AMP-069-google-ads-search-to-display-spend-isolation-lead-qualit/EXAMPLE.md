# End-to-End Worked Example & Failure Recovery — `FW-021` (`AMP-069`)

- **Framework**: Google Ads Search Campaign Channel Allocation & Lead Quality Review
- **العنوان بالعربية**: مراجعة توزيع القنوات وجودة العملاء المحتملين في حملات البحث على Google Ads
- **Selected Artifact Type**: `DECISION_AID`
- **Disclaimer**: *All scenarios, brand names, SKU codes, and metrics below are original, realistic illustrative examples for MENA practitioner training and are never represented as verified client outcomes.*

## 1. Realistic Sample Brief / Input (`المدخلات وموجز الحالة العملية`)

- **Advertiser**: Dubai & Riyadh Luxury Off-Plan Real Estate Brokerage (`$15,000/month` Google Search budget).
- **Problem**: Campaign had `Include Google Display Network` enabled under `Maximize Conversions`. After adding a simple 2-field lead form, Display Expansion consumed `44%` of the Search budget (`$6,600`), generating `310` spam/accidental mobile-game leads (`0` actual property buyers).

## 2. Initial Generated / Completed Output (`المخرج الأولي عند تطبيق الأداة`)

- **Audit & Action Plan**:
  1. Unchecked `Include Google Display Network` and `Include Google Search Partners` across all 6 Arabic and English Search campaigns.
  2. Demoted raw `Form_Submit` to `Secondary (Observation Only)` and promoted `CRM_Verified_Phone_Qualified_Lead` (via HubSpot/GCLID offline import) to `Primary Conversion Action`.

## 3. Human Review & Localization/Technical Edits (`المراجعة البشرية والتعديلات الرقابية والتقنية`)

1. **Added Negative Placement Exclusion**: Added mobile app category exclusions at the Account level (`Content Suitability -> Excluded placements -> All Mobile Apps`) as a second firewall for PMax campaigns.
2. **Phone Input Validation**: Added Saudi/UAE mobile OTP verification (`+966 5...` / `+971 5...` normalized per `AMP-388`) before firing the primary lead event.

## 4. Final Reviewed Example Outcome (`النتيجة النهائية الجاهزة للتنفيذ`)

- Document the selected channel settings and compare subsequent qualified outcomes with the prior baseline; this illustrative example does not establish a guaranteed allocation or result.

## 5. What Can Go Wrong & Specific Correction / Fallback (`حالة الفشل المحتملة وخطة الإنقاذ والبديل`)

- **Common Failure Mode (`ما الذي قد يسير بشكل خاطئ؟`)**:
  A practitioner accepts Google Ads' inline 'Recommendations (`التوصيات`)' auto-apply suggestion `'Add Display Expansion to get more conversions at a similar CPA'`, which silently re-enables Display Network on Search campaigns.
- **Specific Correction & Non-AI / Platform Fallback (`الإصلاح المحدد والبديل الآمن`)**:
  Open `Recommendations -> Auto-apply` in Google Ads and **uncheck all automatic network/expansion recommendations** so Display Expansion can never be turned back on automatically.
