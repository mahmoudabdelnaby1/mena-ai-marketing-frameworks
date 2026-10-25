# `FW-084` — UAE TDRA Marketing SMS Curfew (`9:00 PM – 7:00 AM` Block), `AD-` Sender Prefix & Opt-Out Compliance Checklist
## قائمة فحص الامتثال للوائح هيئة تنظيم الاتصالات الإماراتية (`TDRA` — حظر الرسائل الترويجية من `9 مساءً حتى 7 صباحاً` وبادئة `AD-`)

- **One-Sentence Promise (EN)**: Configure UAE SMS and automated marketing pipelines to strictly enforce TDRA's `9:00 PM to 7:00 AM` Gulf Standard Time (`UTC+4`) promotional curfew, mandatory `AD-` Sender ID prefix, and free opt-out mechanism.
- **الوعد التطبيقي في جملة واحدة (AR)**: ضبط أنظمة أتمتة الرسائل النصية (`SMS`) الموجهة للإمارات للالتزام الصارم بحظر الإرسال الليلي من `9:00 مساءً حتى 7:00 صباحاً` بتوقيت الإمارات (`UTC+4`)، وإضافة بادئة `AD-` لاسم المرسل، وتفعيل آلية الإلغاء المجانية.
- **Selected Artifact Type**: `CHECKLIST` *(Chosen because: Kaelo Global's Oct 2026 legal analysis of the UAE Telecommunications and Digital Government Regulatory Authority (`TDRA`) Unsolicited Electronic Communications Regulatory Policy v1.1 (s. 8.3, 8.8, 9.2.4, 9.2.5) confirms that marketing texts in the UAE are strictly barred between `9:00 PM and 7:00 AM` local time, must carry the `AD-` sender prefix, require prior opt-in consent, and must cease immediately upon opt-out; global AI automation flows triggered at `10:30 PM` (e.g., an evening '1-hour abandoned cart SMS') violate TDRA curfew automatically unless gated!)*
- **Consolidated Child Pattern IDs (`MERGE_INTO_EXISTING`)**: `AMP-452`, `AMP-462`, `AMP-472`, `AMP-482`, `AMP-492`
- **Screened Duplicate IDs (`REJECT_DUPLICATE`)**: `AMP-542`
- **Intended Audience**: Marketing Operations Manager, CRM & Automation Architect, Data Analyst, Growth Engineer
- **Markets & Languages**: Egypt & GCC (`KSA, UAE, Kuwait, Qatar, Bahrain, Oman`) | Arabic (`Egyptian Ammiya, Saudi/Gulf Khaleeji, White MSA`) & English

## When to Use This Asset (`متى تستخدم هذه الأداة؟`)

- **Trigger (EN)**: Use whenever configuring SMS marketing broadcasts or automated behavioral triggers (abandoned cart, win-back, flash sale) targeting UAE mobile numbers (`+971 5...`).
- **داعي الاستخدام (AR)**: تُستخدم عند إعداد أي حملة رسائل نصية (`SMS`) أو رسائل آلية (مثل تذكير السلة المتروكة) تستهدف أرقام الهواتف الإماراتية (`+971`).
- **Do NOT Use When**: Never allow an automated `'Wait 1 Hour -> Send Abandoned Cart SMS'` workflow to fire at `10:15 PM` Dubai time when a shopper abandons their cart at `9:15 PM`—queue it until `7:15 AM` (or `9:00 AM`) the next morning!

## Quick Start (3 Steps for a Non-Expert Marketer)

1. **Prepare Your Inputs (`جهّز المدخلات`)**:
   - SMS Gateway Configuration (`Etisalat by e& / du` registered `AD-BrandName` Sender ID via Unifonic, Twilio, Infobip, or CEQUENS)
   - Automation Workflow Quiet-Hours / Send-Window settings locked to `Asia/Dubai (UTC+4)`
   - Verified Opt-In Consent & Master DND Suppression List (`AMP-232`, `AMP-233`)
2. **Copy or Run the Artifact (`انسخ القالب أو طبّق قائمة الفحص`)**:
   - Open [`ASSET.md`](./ASSET.md) and copy the ready-to-use `CHECKLIST` block (or run the included validation snippet).
3. **Compare Against the Worked Example & Verify (`قارن بالمثال العملي وتجنب الأخطاء`)**:
   - Review [`EXAMPLE.md`](./EXAMPLE.md) to see the realistic input brief → raw output → human review edits → final usable result, plus the common failure mode and recovery step.
   - Check [`SOURCES.md`](./SOURCES.md) for primary official documentation, access dates (`2026-10-25`), and regulatory/technical boundaries.

## Files in This Folder

- [`README.md`](./README.md): Plain-language overview, selected artifact type, use trigger, and 3-step quick start.
- [`ASSET.md`](./ASSET.md): The complete, copy-ready `CHECKLIST` (bilingual Arabic + English), model capability branches, regional adaptation matrix, and measurement plan.
- [`EXAMPLE.md`](./EXAMPLE.md): End-to-end worked example with human review pass and failure/recovery scenario.
- [`SOURCES.md`](./SOURCES.md): Direct primary references (`2026-10-25`), separating problem evidence from official capability/regulatory evidence.
- [`PUBLIC-PAGE-CONTENT.md`](./PUBLIC-PAGE-CONTENT.md): Complete user-facing web publication page containing both the full working artifact and the complete worked example.
