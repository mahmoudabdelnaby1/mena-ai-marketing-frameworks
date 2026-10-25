# End-to-End Worked Example & Failure Recovery — `FW-053` (`AMP-281`)

- **Framework**: Saudi GAMR 'Mawthooq' (موثوق) Influencer License Verification & Contracting Checklist
- **العنوان بالعربية**: قائمة فحص التحقق الإلزامي من رخصة «موثوق» (`Mawthooq` - الهيئة العامة لتنظيم الإعلام `GAMR`) قبل التعاقد مع المؤثرين في السعودية
- **Selected Artifact Type**: `CHECKLIST`
- **Disclaimer**: *All scenarios, brand names, SKU codes, and metrics below are original, realistic illustrative examples for MENA practitioner training and are never represented as verified client outcomes.*

## 1. Realistic Sample Brief / Input (`المدخلات وموجز الحالة العملية`)

- **Campaign**: Riyadh Coffee & Roastery Chain launching a new winter menu with 12 Saudi lifestyle & food creators shortlisted by an AI influencer tool (`SAR 180,000` total creator budget).
- **Pre-Flight Audit Result**:
  - `8` creators supplied active verified `Mawthooq` license numbers.
  - `2` micro-influencers had **no `Mawthooq` license** (`"نعلن بدون ترخيص لأن حسابنا صغير"` — illegal under GAMR rules, which apply to any paid/barter ad regardless of follower size).
  - `1` creator supplied a `Mawthooq` license that had **expired 4 months ago**.
  - `1` creator was a tourist on a visit visa filming in Riyadh with no Saudi agency/commercial permit.

## 2. Initial Generated / Completed Output (`المخرج الأولي عند تطبيق الأداة`)

- **Compliance Triage**:
  - **Approved Immediately (`8` Creators)**: Contracted with `Mawthooq` number logged in campaign ledger.
  - **On Hold (`1` Expired Creator)**: Paused PO until creator renewed via `gmedia.gov.sa` (renewed in 48 hours -> moved to Approved).
  - **Replaced (`3` Unlicensed Creators)**: Replaced with 3 pre-vetted `Mawthooq`-licensed micro-creators in Riyadh.

## 3. Human Review & Localization/Technical Edits (`المراجعة البشرية والتعديلات الرقابية والتقنية`)

1. **Added License Column to Master Campaign Tracker**: Made `mawthooq_license_number` and `mawthooq_expiry_date` mandatory blocking fields in the agency's procurement sheet before finance can issue any 50% advance payment.
2. **Paired with `#إعلان` Disclosure (`AMP-287`)**: Added mandatory `#إعلان` overlay check on all story frames.

## 4. Final Reviewed Example Outcome (`النتيجة النهائية الجاهزة للتنفيذ`)

- `12 / 12` contracted Saudi creators verified with active `GAMR Mawthooq` licenses and documented compliance clauses prior to campaign launch.

## 5. What Can Go Wrong & Specific Correction / Fallback (`حالة الفشل المحتملة وخطة الإنقاذ والبديل`)

- **Common Failure Mode (`ما الذي قد يسير بشكل خاطئ؟`)**:
  A brand sends 30 'free PR gift boxes' with a written WhatsApp message saying `'الهدية مقابل تصوير 3 سنابات مع رابط المتجر وكود الخصم'`; GAMR treats barter/gifted posts with a posting or promo-code obligation as commercial advertising requiring `Mawthooq` and `#إعلان` disclosure.
- **Specific Correction & Non-AI / Platform Fallback (`الإصلاح المحدد والبديل الآمن`)**:
  Apply the exact same `Mawthooq` verification checklist to **barter, affiliate-code, and PR-gifting campaigns** whenever there is an agreement or expectation to post.
