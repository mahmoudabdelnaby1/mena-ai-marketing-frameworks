# End-to-End Worked Example & Failure Recovery — `FW-084` (`AMP-442`)

- **Framework**: UAE TDRA Marketing SMS Curfew (`9:00 PM – 7:00 AM` Block), `AD-` Sender Prefix & Opt-Out Compliance Checklist
- **العنوان بالعربية**: قائمة فحص الامتثال للوائح هيئة تنظيم الاتصالات الإماراتية (`TDRA` — حظر الرسائل الترويجية من `9 مساءً حتى 7 صباحاً` وبادئة `AD-`)
- **Selected Artifact Type**: `CHECKLIST`
- **Disclaimer**: *All scenarios, brand names, SKU codes, and metrics below are original, realistic illustrative examples for MENA practitioner training and are never represented as verified client outcomes.*

## 1. Realistic Sample Brief / Input (`المدخلات وموجز الحالة العملية`)

- **Brand**: Dubai & Riyadh D2C Fashion Brand running Klaviyo / Braze SMS automations.
- **Violations Detected**:
  1. The `'1-Hour Abandoned Cart SMS'` fired at `11:40 PM` Dubai time whenever late-night shoppers abandoned carts at `10:40 PM`.
  2. Marketing team sent a flash-sale blast over the transactional `BrandOTP` sender ID (missing the `AD-` prefix) to avoid promotional filtering.

## 2. Initial Generated / Completed Output (`المخرج الأولي عند تطبيق الأداة`)

- **Compliance Remediation**:
  1. Enabled `get_tdra_safe_send_timestamp()` / Smart Quiet Hours (`20:30 to 08:30 Asia/Dubai`) on all automated flows targeting `+971` numbers so late-night triggers hold safely until `08:30 AM` GST.
  2. Locked all promotional flows strictly to the registered `AD-BrandName` Sender ID and reserved `BrandOTP` exclusively for `AUTHENTICATION` / transactional delivery notices (`AMP-237`).

## 3. Human Review & Localization/Technical Edits (`المراجعة البشرية والتعديلات الرقابية والتقنية`)

1. **Added 30-Minute Carrier Buffer (`20:30` Cutoff Instead of `20:59`)**: Because bulk SMS batches of 50,000 messages can take 15–25 minutes to drain through telecom SMPP queues, stopped initiating UAE promotional batches after **`8:30 PM` Dubai time** so no trailing message ever lands on a phone at `9:02 PM`!
2. **Extended Similar Respectful Quiet Hours to KSA (`CST`) & Egypt (`NTRA`)**: Applied evening quiet hours (`9:30 PM – 8:30 AM` local time) across KSA and Egypt promotional SMS as well.

## 4. Final Reviewed Example Outcome (`النتيجة النهائية الجاهزة للتنفيذ`)

- `100%` of UAE promotional SMS traffic locked to `AD-` Sender ID within the `08:30 AM – 08:30 PM` (`Asia/Dubai`) safe window, with zero night-curfew violations.

## 5. What Can Go Wrong & Specific Correction / Fallback (`حالة الفشل المحتملة وخطة الإنقاذ والبديل`)

- **Common Failure Mode (`ما الذي قد يسير بشكل خاطئ؟`)**:
  An international marketing team in London (`UTC+0`) schedules a UAE SMS broadcast for `'6:00 PM London Time'`, forgetting that Dubai (`UTC+4`) is 4 hours ahead—delivering the promotional SMS to 40,000 Emirati phones at **`10:00 PM` Dubai time** (1 hour into the TDRA illegal curfew window!).
- **Specific Correction & Non-AI / Platform Fallback (`الإصلاح المحدد والبديل الآمن`)**:
  Always configure SMS campaign schedulers to use **`Recipient Local Timezone (Asia/Dubai UTC+4)`**, NEVER the marketer's browser/headquarters timezone!
