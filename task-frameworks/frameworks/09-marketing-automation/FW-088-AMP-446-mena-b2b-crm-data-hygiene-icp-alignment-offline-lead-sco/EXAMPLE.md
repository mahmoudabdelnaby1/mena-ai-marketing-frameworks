# End-to-End Worked Example & Failure Recovery — `FW-088` (`AMP-446`)

- **Framework**: MENA B2B CRM Data Hygiene, ICP Alignment & Offline Lead-Scoring Feedback Framework
- **العنوان بالعربية**: الإطار التشغيلي لتنظيف بيانات `CRM` ومواءمة معايير العميل المثالي (`ICP`) بين التسويق والمبيعات في قطاع الأعمال (`B2B`)
- **Selected Artifact Type**: `OPERATING_FRAMEWORK`
- **Disclaimer**: *All scenarios, brand names, SKU codes, and metrics below are original, realistic illustrative examples for MENA practitioner training and are never represented as verified client outcomes.*

## 1. Realistic Sample Brief / Input (`المدخلات وموجز الحالة العملية`)

- **Company**: Riyadh, Dubai & Cairo B2B Logistics & Warehouse Management SaaS (`Average Annual Contract: $14,000`).
- **Problem**: Marketing celebrated generating `1,200` 'AI-scored leads' in Q3, but Sales closed only `6` deals (`0.5%` close rate) and complained that `78%` of leads were truck drivers looking for jobs (`"وظائف سائق"`), university students, or duplicate entries of existing clients.

## 2. Initial Generated / Completed Output (`المخرج الأولي عند تطبيق الأداة`)

- **Executed 4-Stage Overhaul**:
  1. De-duplicated `14,800` CRM contacts via E.164 phone normalization (`AMP-388`) and bilingual company matching (merged `2,310` duplicate Arabic/English records).
  2. Added the `Inquiry Purpose` (`شراء النظام لشركتي` vs. `التقديم على وظيفة`) routing gate + Arabic morphological negative keywords (`AMP-066`).
  3. Connected HubSpot `Lifecycle Stage == SQL` webhook to Google Ads and Meta CAPI.

## 3. Human Review & Localization/Technical Edits (`المراجعة البشرية والتعديلات الرقابية والتقنية`)

1. **Pragmatic MENA SME Email Rule**: Note that in Egypt and KSA, many legitimate traditional wholesale/retail business owners (`أصحاب مؤسسات تجارية حقيقية`) still use a personal `@gmail.com` or `@hotmail.com` address while conducting business on WhatsApp—so instead of hard-blocking `@gmail.com`, required **`اسم المؤسسة/المتجر + عدد الفروع + رقم جوال موثق`** to qualify them!
2. **Enforced 10-Minute Speed-to-Lead SLA on `Score >= 60` SQLs**: Routed verified `SQL` leads directly to the regional AE's WhatsApp/Phone queue within 60 seconds.

## 4. Final Reviewed Example Outcome (`النتيجة النهائية الجاهزة للتنفيذ`)

- Raw junk lead volume dropped by `64%`, Sales rep time wasted on job seekers fell to `0%`, and MQL-to-SQL conversion rate rose from `9%` to **`38%`**.

## 5. What Can Go Wrong & Specific Correction / Fallback (`حالة الفشل المحتملة وخطة الإنقاذ والبديل`)

- **Common Failure Mode (`ما الذي قد يسير بشكل خاطئ؟`)**:
  A Western B2B lead-scoring template automatically disqualifies (`-100 pts`) any lead submitting a `@gmail.com` or `@yahoo.com` email address; in Egypt and Saudi Arabia, this blocks 40%+ of profitable traditional family trading companies, clinics, and retail store owners who do not use corporate email daily.
- **Specific Correction & Non-AI / Platform Fallback (`الإصلاح المحدد والبديل الآمن`)**:
  In MENA B2B scoring, **do not auto-reject `@gmail.com` if the user provides a valid local mobile number (`+9665...` / `+201...`), a real store/establishment name (`اسم المنشأة أو المتجر`), and qualifying branch/employee count**!
