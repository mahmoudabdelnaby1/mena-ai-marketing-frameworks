# End-to-End Worked Example & Failure Recovery — `FW-017` (`AMP-065`)

- **Framework**: Meta Advantage+ Creative Auto-Enhancement Guardrail Checklist for Arab & Ramadan Campaigns
- **العنوان بالعربية**: قائمة فحص وضبط التحسينات التلقائية (`Meta Advantage+ Creative`) لحماية الهوية البصرية والنصوص العربية وحملات رمضان
- **Selected Artifact Type**: `CHECKLIST`
- **Disclaimer**: *All scenarios, brand names, SKU codes, and metrics below are original, realistic illustrative examples for MENA practitioner training and are never represented as verified client outcomes.*

## 1. Realistic Sample Brief / Input (`المدخلات وموجز الحالة العملية`)

- **Campaign**: Saudi Ramadan Oud & Gift Box Campaign on Instagram Reels & Facebook Feed (`SAR 150,000` budget).
- **Incident Prevented**: Media buyer uploaded a serene 1:1 static graphic with Arabic calligraphy (`"رمضان يجمعنا على الطيب"`). Meta Advantage+ Creative defaulted `Add Music` (`ON`) with an upbeat Western dance track and `Image Expansion` (`ON`) which stretched the top of the Oud bottle into a crooked shape.

## 2. Initial Generated / Completed Output (`المخرج الأولي عند تطبيق الأداة`)

- Ad-Level Audit prior to launch:
  - `Add Music`: `ON` (`FAIL` — Western dance beat attached to Ramadan Oud graphic)
  - `Expand Image`: `ON` (`FAIL` — distorted bottle cap in 9:16 preview)
  - `Visual Touch-ups`: `ON` (`FAIL` — oversaturated dark mahogany wood box into bright orange)

## 3. Human Review & Localization/Technical Edits (`المراجعة البشرية والتعديلات الرقابية والتقنية`)

1. **Disabled All 3 Destructive Toggles**: Turned OFF `Add Music`, `Expand Image`, and `Visual Touch-ups`.
2. **Uploaded Native Placement Assets**: Supplied a dedicated `1080x1920` (9:16) graphic and a `1080x1080` (1:1) graphic created by the design team so no AI outpainting was needed.

## 4. Final Reviewed Example Outcome (`النتيجة النهائية الجاهزة للتنفيذ`)

- Campaign launched across KSA with 100% brand-faithful colors, native 9:16/1:1 geometry, and zero unapproved audio tracks.

## 5. What Can Go Wrong & Specific Correction / Fallback (`حالة الفشل المحتملة وخطة الإنقاذ والبديل`)

- **Common Failure Mode (`ما الذي قد يسير بشكل خاطئ؟`)**:
  An agency turns off Advantage+ Creative toggles on Ad #1, then uses 'Duplicate Ad' and changes the media file—Meta Ads Manager silently re-enables `Expand Image` and `Visual Touch-ups` when new media is selected.
- **Specific Correction & Non-AI / Platform Fallback (`الإصلاح المحدد والبديل الآمن`)**:
  Always make the Advantage+ Creative toggle check the **very last step after uploading final media**, immediately before clicking the green `Publish` button.
