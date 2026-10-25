# FW-043: Arabic HTML Email `dir='rtl'` & Unicode `<bdi>` Isolation Rendering Checklist (Gmail, Outlook & Apple Mail)
## قائمة فحص وقالب برمجة رسائل البريد العربية (`dir='rtl'` وعزل `<bdi>`) لمنع تشوه المحاذاة وانعكاس الأرقام في Gmail وOutlook

- **Consolidated Contextual Child IDs (`MERGE_INTO_EXISTING`)**: `AMP-241`, `AMP-251`, `AMP-261`, `AMP-271`
- **Selected Artifact Type**: `CHECKLIST`
- **Intended Audience**: CRM Manager, Email Marketing Specialist, Lifecycle Marketer, Data Privacy Officer
- **Target Markets & Languages**: Egypt & GCC (`Saudi Arabia, UAE, Kuwait, Qatar, Bahrain, Oman`) — Bilingual Arabic (`Egyptian Ammiya`, `Saudi/Gulf Khaleeji`, `White MSA`) + English
- **Version**: `1.2` | **Last Reviewed**: `2026-10-25` | **Status**: `READY_FOR_REVIEW`

## 1. Plain-Language Promise & Why This Artifact Form Fits the Job

- **What You Can Make or Decide (EN)**: Prevent AI-generated Klaviyo, HubSpot, Mailchimp, and Braze HTML emails from rendering Arabic right-to-left text flushed left or scrambling mixed prices (`299 SAR`), promo codes (`RAMADAN20`), and phone numbers.
- **ما الذي يمكنك إنجازه أو حسمه بهذه الأداة (AR)**: منع رسائل البريد الإلكتروني المولدة بالذكاء الاصطناعي في Klaviyo وHubSpot وMailchimp من عرض النص العربي بمحاذاة يسارية معطوبة أو قلب ترتيب الأسعار (`299 SAR`) وأكواد الخصم والأرقام في Gmail وOutlook.
- **Why `CHECKLIST` Fits This User Job (EN)**: MailTester's September 2026 RTL rendering audit confirms that Gmail and Outlook desktop strip `<style>`-level direction properties when `dir="rtl"` is missing from HTML wrapper tables/cells, and Unicode's BiDi algorithm scrambles inline Latin promo codes, prices, and `+966/+20` phone numbers without `<bdi>` or `&rlm;`; a technical CHECKLIST + master HTML boilerplate solves this permanently.
- **لماذا يناسب شكل `CHECKLIST` هذه المهمة (AR)**: يثبت فحص MailTester (سبتمبر 2026) أن Gmail وOutlook يتجاهلان محاذاة اليمين لليسار إذا غابت سمة `dir="rtl"` عن جداول وخلايا HTML، كما تنعكس الأسعار وأكواد الخصم الإنجليزية وسط السطر العربي بدون عزل `<bdi>`؛ لذا توفر قائمة الفحص والقالب البرمجي حلاً جذرياً.

## 2. "Use It When" Trigger, Boundaries & Exact Inputs to Prepare

- **Use It When (EN)**: Use before sending any Arabic or bilingual HTML email campaign or automated flow (welcome, cart recovery, order receipt) across Gmail, Outlook, iOS Mail, and Yahoo/Maktoob.
- **متى تستخدم هذه الأداة (AR)**: تُستخدم قبل إرسال أي حملة بريد إلكتروني عربية أو ثنائية اللغة أو رسائل التدفق الآلي عبر Gmail وOutlook وApple Mail.
- **When NOT to Use It (EN)**: Do not rely solely on CSS `direction: rtl;` inside a `<head><style>` block—Outlook Word-rendering engines and Gmail clipping frequently ignore `<head>` CSS unless HTML attributes (`dir="rtl" align="right"`) are set inline on `<table>` and `<td>`.
- **متى لا تستخدم هذه الأداة (AR)**: لا تعتمد فقط على كتابة `direction: rtl` داخل وسم `<style>` في الترويسة؛ لأن محرك Outlook وتطبيقات الجوال تتطلب وجود `dir="rtl" align="right"` مباشرة داخل وسوم `<table>` و`<td>`.

### Exact Inputs to Prepare Before Starting (`المدخلات المطلوب تجهيزها`)
1. ESP HTML Template (`Klaviyo`, `HubSpot`, `Braze`, `Mailchimp`, `Customer.io`)
2. List of dynamic merge variables containing Latin/numeric strings (`{{promo_code}}`, `{{price_sar}}`, `{{order_id}}`, `{{phone_e164}}`)
3. Arabic-safe fallback font stack (`AMP-238`)

### Privacy-Safe Data Handling (`ضوابط الخصوصية وحماية البيانات الشخصية PDPL`)
- **Strict PII Redaction Before Prompting**: Under Saudi PDPL (Art. 25), UAE Federal Decree-Law No. 45 of 2021, Qatar Law No. 13 of 2016, and Egypt Law No. 151 of 2020, **never paste raw customer names, unhashed mobile numbers (`+9665...` / `+201...`), email addresses, national IDs, or private WhatsApp transcripts into public/consumer LLM interfaces**. Use anonymized placeholders (`{first_name}`, `ORD_10045`) during prompt testing and restrict live customer data to zero-data-retention enterprise API endpoints or local deterministic scripts.

## 3. The Directly Usable Artifact (`الأداة التطبيقية الجاهزة للنسخ والتنفيذ`)

### 1. Copy-Ready RTL & BiDi-Safe Master Email HTML Wrapper

```html
<!DOCTYPE html>
<html lang="ar" dir="rtl" xmlns="http://www.w3.org/1999/xhtml" xmlns:v="urn:schemas-microsoft-com:vml" xmlns:o="urn:schemas-microsoft-com:office:office">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>{{EMAIL_SUBJECT}}</title>
</head>
<body dir="rtl" style="margin:0; padding:0; direction:rtl; text-align:right; background-color:#F7F8FA; font-family:'Tajawal', 'Cairo', 'Segoe UI', Tahoma, Arial, sans-serif;">
  <!-- Outer Wrapper Table with explicit dir="rtl" for Outlook & Gmail -->
  <table role="presentation" dir="rtl" width="100%" cellpadding="0" cellspacing="0" border="0" style="direction:rtl; text-align:right; background-color:#F7F8FA;">
    <tr>
      <td align="center" dir="rtl" style="padding:24px 12px; direction:rtl;">
        <!-- 600px Container Table -->
        <table role="presentation" dir="rtl" width="600" cellpadding="0" cellspacing="0" border="0" style="max-width:600px; width:100%; direction:rtl; text-align:right; background-color:#FFFFFF; border-radius:8px;">
          <tr>
            <!-- Every content <td> MUST include dir="rtl" align="right" and inline direction:rtl; text-align:right; -->
            <td dir="rtl" align="right" style="padding:32px 28px; direction:rtl; text-align:right; font-family:'Tajawal', 'Cairo', 'Segoe UI', Tahoma, Arial, sans-serif; font-size:16px; line-height:1.75; color:#1A1A1A;">
              <h1 style="margin:0 0 16px 0; font-size:22px; line-height:1.4; direction:rtl; text-align:right;">
                أهلاً <bdi>{{ first_name }}</bdi>، طلبك رقم <bdi style="direction:ltr; unicode-bidi:isolate;">#{{ order_id }}</bdi> جاهز للشحن!
              </h1>
              <p style="margin:0 0 16px 0; direction:rtl; text-align:right;">
                إجمالي الطلب: <bdi style="direction:ltr; unicode-bidi:isolate; font-weight:700;">{{ order_total }} SAR</bdi> (شامل ضريبة القيمة المضافة 15%)، ويمكنك استخدام كود الخصم <bdi style="direction:ltr; unicode-bidi:isolate; background:#F0F4F8; padding:2px 6px; border-radius:4px; font-family:monospace;">{{ promo_code }}</bdi> في طلبك القادم.
              </p>
              <p style="margin:0; direction:rtl; text-align:right;">
                للتواصل مع خدمة العملاء: <bdi style="direction:ltr; unicode-bidi:isolate;">+966 55 123 4567</bdi>&rlm;
              </p>
            </td>
          </tr>
        </table>
      </td>
    </tr>
  </table>
</body>
</html>
```

### 2. Pre-Send 5-Point RTL Rendering Checklist
- [ ] **Check 1 — Triple `dir="rtl"` Declaration**: Confirm `dir="rtl"` is present on `<html>`, `<body>`, every structural `<table role="presentation">`, and every text `<td dir="rtl" align="right">`.
- [ ] **Check 2 — Wrap Every Inline Latin/Numeric Variable in `<bdi style="direction:ltr; unicode-bidi:isolate;">`**: Wrap `{{ first_name }}` (in case a user entered an English name), `{{ order_id }}`, `{{ promo_code }}`, `{{ price }}`, URLs, and phone numbers (`+966 ...` / `+20 ...`) so punctuation and `+`/`#`/`%` signs never jump to the wrong side of the number!
- [ ] **Check 3 — Bullet Lists (`<ul>`/`<ol>`) in Outlook**: Standard `<ul>` bullets often render on the far left of an RTL paragraph in Windows Outlook; either set `<ul dir="rtl" style="direction:rtl; text-align:right; padding-right:20px; margin-right:0;">` or use a 2-column RTL `<table>` (`Column 1: •` | `Column 2: Text`).

## 4. Model & Platform Capability Branches (`فروع قدرات النماذج والمنصات والبدائل الاحتياطية`)

| System / Platform | Capability Status | Official Documentation & Access Date | Operational Constraint in Egypt & GCC | Fallback When Feature/Modality Is Unavailable |
| :--- | :--- | :--- | :--- | :--- |
| **Gmail, Microsoft Outlook (Word Engine) & Apple Mail RTL / BiDi Rendering** | `supported` | [Official Reference](https://mailtester.com/blog/right-to-left-email-rendering-problems-gmail-outlook/) (`2026-10-25`) | MailTester's Sep 2026 RTL audit confirms that inline HTML `dir='rtl' align='right'` on `<table>`/`<td>` plus `<bdi>`/`&rlm;` around mixed LTR tokens is required for consistent cross-client rendering. | For plain-text / minimal HTML B2B emails where `<bdi>` is stripped, append `&rlm;` (`‏`) immediately after every inline English word or number. |

## 5. Consolidated Regional & Vertical Adaptation Matrix (`دمج الأنماط السياقية الفرعية بدون حشو`)

Per Agent 2 v1.2's anti-padding rule, the following **4 cross-verified contextual synthesis patterns** and **0 screened duplicate variants** share this core mechanism and are consolidated directly into this source-of-truth framework:

| Child Pattern ID | Disposition | Regional / Sector Operating Context | Specific Adaptation & Guardrail Integrated in This Asset | Evidence Tier |
| :--- | :--- | :--- | :--- | :--- |
| **`AMP-241`** | `MERGE_INTO_EXISTING` | Egyptian E-Commerce & Social Commerce (Shopify / WooCommerce / Cairo & Alexandria) | Validated RTL MJML/HTML email boilerplate with explicit dir='rtl', text-align:right, and <bdi> wrappers for prices/codes.; Specifically impacts Egyptian brands operating in EGP where merchant-specific payment mix from recent order records, Mobile Wallets (Vodafone Cash), InstaPay, and Fawry dominate. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-251`** | `MERGE_INTO_EXISTING` | UAE & Multi-Market GCC Enterprise / Retail (Dubai, Abu Dhabi, Doha, Kuwait) | Validated RTL MJML/HTML email boilerplate with explicit dir='rtl', text-align:right, and <bdi> wrappers for prices/codes.; Specifically impacts bilingual Arabic/English campaigns in high-CPM, expat-dense Gulf markets under UAE PDPL / TDRA and Qatari regulations. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-261`** | `MERGE_INTO_EXISTING` | High-Trust & Regulated Verticals (Healthcare/SFDA/EDA, Fintech/SAMA/FRA, Real Estate) | Validated RTL MJML/HTML email boilerplate with explicit dir='rtl', text-align:right, and <bdi> wrappers for prices/codes.; Specifically impacts regulated claims requiring SFDA, EDA, MOH, SAMA, FRA, or RERA compliance pre-clearance and strict hallucination guardrails. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-271`** | `MERGE_INTO_EXISTING` | Seasonal Peak Operations (Ramadan, Eid, White/Yellow Friday, Saudi Founding/National Day) | Validated RTL MJML/HTML email boilerplate with explicit dir='rtl', text-align:right, and <bdi> wrappers for prices/codes.; Specifically impacts high-velocity seasonal surges where CPMs jump 40-70%, prices change rapidly, and Hijri calendar cultural sensitivity is paramount. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |

### Context-Specific Execution Knobs Across the 5 MENA Operating Environments
1. **Saudi D2C E-Commerce (`Salla / Zid / Riyadh & Jeddah Retail`)**: Enforce `SAR` tax-inclusive pricing (`15% ZATCA VAT`), native `Mada / Apple Pay / Tabby / Tamara` visibility (`AMP-387`), `GAMR Mawthooq` creator verification (`AMP-281`), and White Saudi Khaleeji orthography (`AMP-002`, `AMP-177`).
2. **Egyptian E-Commerce & Social Commerce (`Shopify / WooCommerce / Cairo & Alexandria`)**: Use each merchant’s own order and payment data to assess Cash on Delivery (`COD`), mobile wallets, InstaPay, Fawry, `valU`, address fields, and pre-dispatch WhatsApp confirmation. Verify current provider terms and local requirements before implementation.
3. **UAE & Multi-Market GCC Enterprise / Retail (`Dubai, Abu Dhabi, Doha, Kuwait`)**: Separate high-CPM UAE/Qatar budgets from lower-CPM markets (`AMP-061`), enforce UAE `TDRA` `9 PM – 7 AM` SMS curfew + `AD-` prefix (`AMP-442`), UAE Media Council permits (`AMP-282`), and bilingual Arabic/English canonical & currency parity (`current applicable UAE VAT`, `current applicable Qatar/Kuwait tax rules`, 3-decimal `KWD` `AMP-239`).
4. **High-Trust & Regulated Verticals (`Healthcare SFDA/MOH/EDA, FinTech SAMA/FRA, Real Estate REGA/RERA`)**: Strip all therapeutic/cure verbs (`AMP-176`, `AMP-286`), display mandatory `MOH/SFDA/DHA/EDA/Fal/Trakheesi` permit numbers (`AMP-070`), and route budgets to high-credibility channels (`AMP-290`, `AMP-339`).
5. **Seasonal Peak Operations (`Ramadan, Eid, White/Yellow Friday, Saudi Founding/National Day`)**: Lock Hijri-Gregorian overlaps (`Feb 2027 Ramadan x Saudi Founding Day x Kuwait National Day` `AMP-125`), pre-schedule GMC `sale_price_effective_date` 48h ahead (`AMP-063`), verify 30-day baseline discount permits (`AMP-064`), and disable Meta Advantage+ auto-music (`AMP-065`).

## 6. Worked Example Summary & Failure Recovery (`ملخص المثال التطبيقي وخطة الإنقاذ`)

*(Full step-by-step worked example with annotated human edits is also provided in `EXAMPLE.md`)*

- **Sample Input Brief**: - **ESP**: Klaviyo Abandoned Cart Flow for a Saudi & UAE Perfume Store.
- **Broken AI HTML Output**: Used a standard LTR Klaviyo drag-and-drop block without `dir="rtl"` or `<bdi>`. In Gmail and Outlook, the line `"استخدم كود خصم VIP25 للحصول على خصم 25% والاتصال على +966 50 000 0000"` rendered flushed left as `"0000 000 50 966+ %25 VIP25..."` with the `+` sign and `%` sign detached and reversed.
- **Human Review & Key Edits Applied**: 1. **Outlook Desktop VML Button Check**: Added `direction:rtl;` inside the CTA button table cell so the left-pointing arrow (`← أكملي طلبك الآن`) points in the natural RTL reading direction (`AMP-389`).
2. **Tested Across 4 Clients**: Verified rendering on Gmail iOS, Gmail Web, Apple Mail, and Outlook 365 Desktop (Windows).
- **Final Usable Output**: - Production Klaviyo HTML template passing 100% RTL alignment and BiDi number/code isolation across Gmail, Outlook, and Apple Mail.
- **What Can Go Wrong**: A customer registers their first name in English (`"Sarah"`) on an Arabic store; in the welcome email `'مرحباً Sarah، شكراً لتسجيلك!'`, the Arabic comma `،` jumps to the right of `Sarah` because an unisolated Latin token at the start of an RTL line flips adjacent neutral punctuation.
- **Correction & Fallback**: Always wrap `{{ first_name }}` in `<bdi>{{ first_name }}</bdi>&rlm;` (followed by the Right-to-Left Mark entity `&rlm;`) whenever a merge tag can contain either Arabic or Latin script.

## 7. Measurement Plan & Hypothesis Framing (`خطة القياس والضوابط الإحصائية`)

- **Primary Metric to Track**: 100% pass rate on Litmus/Email-on-Acid/MailTester RTL visual checks across Outlook & Gmail, plus Promo Code Redemption Rate and Email CTR.
- **Baseline Definition**: Pre-fix visual audit of active automated email templates.
- **Observation Window**: 14 days post-template update. *(Must span full 7/14-day weekly cycles and account for 25th–30th monthly salary windows per `AMP-391`)*.
- **What Cannot Be Concluded (Boundary)**: Fixing RTL rendering eliminates broken layout friction and unreadable promo codes, while subject line and offer value drive open and purchase rates.
