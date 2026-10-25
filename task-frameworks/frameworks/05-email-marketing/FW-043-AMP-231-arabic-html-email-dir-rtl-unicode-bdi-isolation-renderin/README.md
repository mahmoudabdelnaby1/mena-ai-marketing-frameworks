# `FW-043` — Arabic HTML Email `dir='rtl'` & Unicode `<bdi>` Isolation Rendering Checklist (Gmail, Outlook & Apple Mail)
## قائمة فحص وقالب برمجة رسائل البريد العربية (`dir='rtl'` وعزل `<bdi>`) لمنع تشوه المحاذاة وانعكاس الأرقام في Gmail وOutlook

- **One-Sentence Promise (EN)**: Prevent AI-generated Klaviyo, HubSpot, Mailchimp, and Braze HTML emails from rendering Arabic right-to-left text flushed left or scrambling mixed prices (`299 SAR`), promo codes (`RAMADAN20`), and phone numbers.
- **الوعد التطبيقي في جملة واحدة (AR)**: منع رسائل البريد الإلكتروني المولدة بالذكاء الاصطناعي في Klaviyo وHubSpot وMailchimp من عرض النص العربي بمحاذاة يسارية معطوبة أو قلب ترتيب الأسعار (`299 SAR`) وأكواد الخصم والأرقام في Gmail وOutlook.
- **Selected Artifact Type**: `CHECKLIST` *(Chosen because: MailTester's September 2026 RTL rendering audit confirms that Gmail and Outlook desktop strip `<style>`-level direction properties when `dir="rtl"` is missing from HTML wrapper tables/cells, and Unicode's BiDi algorithm scrambles inline Latin promo codes, prices, and `+966/+20` phone numbers without `<bdi>` or `&rlm;`; a technical CHECKLIST + master HTML boilerplate solves this permanently.)*
- **Consolidated Child Pattern IDs (`MERGE_INTO_EXISTING`)**: `AMP-241`, `AMP-251`, `AMP-261`, `AMP-271`
- **Screened Duplicate IDs (`REJECT_DUPLICATE`)**: None
- **Intended Audience**: CRM Manager, Email Marketing Specialist, Lifecycle Marketer, Data Privacy Officer
- **Markets & Languages**: Egypt & GCC (`KSA, UAE, Kuwait, Qatar, Bahrain, Oman`) | Arabic (`Egyptian Ammiya, Saudi/Gulf Khaleeji, White MSA`) & English

## When to Use This Asset (`متى تستخدم هذه الأداة؟`)

- **Trigger (EN)**: Use before sending any Arabic or bilingual HTML email campaign or automated flow (welcome, cart recovery, order receipt) across Gmail, Outlook, iOS Mail, and Yahoo/Maktoob.
- **داعي الاستخدام (AR)**: تُستخدم قبل إرسال أي حملة بريد إلكتروني عربية أو ثنائية اللغة أو رسائل التدفق الآلي عبر Gmail وOutlook وApple Mail.
- **Do NOT Use When**: Do not rely solely on CSS `direction: rtl;` inside a `<head><style>` block—Outlook Word-rendering engines and Gmail clipping frequently ignore `<head>` CSS unless HTML attributes (`dir="rtl" align="right"`) are set inline on `<table>` and `<td>`.

## Quick Start (3 Steps for a Non-Expert Marketer)

1. **Prepare Your Inputs (`جهّز المدخلات`)**:
   - ESP HTML Template (`Klaviyo`, `HubSpot`, `Braze`, `Mailchimp`, `Customer.io`)
   - List of dynamic merge variables containing Latin/numeric strings (`{{promo_code}}`, `{{price_sar}}`, `{{order_id}}`, `{{phone_e164}}`)
   - Arabic-safe fallback font stack (`AMP-238`)
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
