# Arabic HTML Email `dir='rtl'` & Unicode `<bdi>` Isolation Rendering Checklist (Gmail, Outlook & Apple Mail)
## <span dir="rtl">قائمة فحص وقالب برمجة رسائل البريد العربية (`dir='rtl'` وعزل `<bdi>`) لمنع تشوه المحاذاة وانعكاس الأرقام في Gmail وOutlook</span>

> **Asset ID**: `FW-043` (`AMP-231`) | **Artifact Type**: `CHECKLIST` | **Channel**: Email Marketing | **Markets**: Egypt & GCC (`KSA, UAE, Kuwait, Qatar, Bahrain, Oman`) | **Version**: `1.2` (`Reviewed 2026-10-25`)

**What You Can Do With This (`ماذا يمكنك أن تنجز بهذه الأداة؟`)**:
- **EN**: Prevent AI-generated Klaviyo, HubSpot, Mailchimp, and Braze HTML emails from rendering Arabic right-to-left text flushed left or scrambling mixed prices (`299 SAR`), promo codes (`RAMADAN20`), and phone numbers.
- **AR**: <span dir="rtl">منع رسائل البريد الإلكتروني المولدة بالذكاء الاصطناعي في Klaviyo وHubSpot وMailchimp من عرض النص العربي بمحاذاة يسارية معطوبة أو قلب ترتيب الأسعار (`299 SAR`) وأكواد الخصم والأرقام في Gmail وOutlook.</span>

## 1. Use It When & Required Inputs (`متى تستخدمها وما المدخلات المطلوبة؟`)

- **Use It When (EN)**: Use before sending any Arabic or bilingual HTML email campaign or automated flow (welcome, cart recovery, order receipt) across Gmail, Outlook, iOS Mail, and Yahoo/Maktoob.
- **متى تستخدمها (AR)**: <span dir="rtl">تُستخدم قبل إرسال أي حملة بريد إلكتروني عربية أو ثنائية اللغة أو رسائل التدفق الآلي عبر Gmail وOutlook وApple Mail.</span>
- **When NOT to Use It (EN)**: Do not rely solely on CSS `direction: rtl;` inside a `<head><style>` block—Outlook Word-rendering engines and Gmail clipping frequently ignore `<head>` CSS unless HTML attributes (`dir="rtl" align="right"`) are set inline on `<table>` and `<td>`.
- **متى لا تستخدمها (AR)**: <span dir="rtl">لا تعتمد فقط على كتابة `direction: rtl` داخل وسم `<style>` في الترويسة؛ لأن محرك Outlook وتطبيقات الجوال تتطلب وجود `dir="rtl" align="right"` مباشرة داخل وسوم `<table>` و`<td>`.</span>

### Exact Inputs to Prepare (`المدخلات المطلوب تجهيزها قبل البدء`)
- ESP HTML Template (`Klaviyo`, `HubSpot`, `Braze`, `Mailchimp`, `Customer.io`)
- List of dynamic merge variables containing Latin/numeric strings (`{{promo_code}}`, `{{price_sar}}`, `{{order_id}}`, `{{phone_e164}}`)
- Arabic-safe fallback font stack (`AMP-238`)

## 2. The Working `CHECKLIST` (`الأداة الكاملة الجاهزة للنسخ والتطبيق الفوري`)

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

## 3. Complete End-to-End Worked Example (`مثال تطبيقي متكامل من المدخلات حتى المراجعة البشرية والنتيجة النهائية`)

*(Illustrative scenario — original example for training, never represented as a verified client outcome)*

### Step A: Sample Brief / Input (`موجز المدخلات`)
- **ESP**: Klaviyo Abandoned Cart Flow for a Saudi & UAE Perfume Store.
- **Broken AI HTML Output**: Used a standard LTR Klaviyo drag-and-drop block without `dir="rtl"` or `<bdi>`. In Gmail and Outlook, the line `"استخدم كود خصم VIP25 للحصول على خصم 25% والاتصال على +966 50 000 0000"` rendered flushed left as `"0000 000 50 966+ %25 VIP25..."` with the `+` sign and `%` sign detached and reversed.

### Step B: Initial Output (`المخرج الأولي`)
- **Applied Master RTL Wrapper + `<bdi>` Isolation**:
  - Wrapped `VIP25`, `25%`, `299.00 SAR`, and `+966 50 000 0000` in `<bdi style="direction:ltr; unicode-bidi:isolate;">` inside `<td dir="rtl" align="right">`.

### Step C: Human Review & Edits (`التدقيق البشري والتعديلات`)
1. **Outlook Desktop VML Button Check**: Added `direction:rtl;` inside the CTA button table cell so the left-pointing arrow (`← أكملي طلبك الآن`) points in the natural RTL reading direction (`AMP-389`).
2. **Tested Across 4 Clients**: Verified rendering on Gmail iOS, Gmail Web, Apple Mail, and Outlook 365 Desktop (Windows).

### Step D: Final Reviewed Example Outcome (`النتيجة النهائية المعتمدة`)
- Production Klaviyo HTML template passing 100% RTL alignment and BiDi number/code isolation across Gmail, Outlook, and Apple Mail.

## 4. What Can Go Wrong & How to Fix It (`الأخطاء الشائعة وخطة الإنقاذ`)

- **Failure Case (`المشكلة المحتملة`)**: A customer registers their first name in English (`"Sarah"`) on an Arabic store; in the welcome email `'مرحباً Sarah، شكراً لتسجيلك!'`, the Arabic comma `،` jumps to the right of `Sarah` because an unisolated Latin token at the start of an RTL line flips adjacent neutral punctuation.
- **Correction & Fallback (`الحل الإجرائي والبديل الآمن`)**: Always wrap `{{ first_name }}` in `<bdi>{{ first_name }}</bdi>&rlm;` (followed by the Right-to-Left Mark entity `&rlm;`) whenever a merge tag can contain either Arabic or Latin script.

## 5. Model & Platform Capability Matrix (`مصفوفة قدرات النماذج والمنصات — 2026-10-25`)

| Platform / Model | Status | Official Documentation | MENA Operational Constraint | Fallback |
| :--- | :--- | :--- | :--- | :--- |
| **Gmail, Microsoft Outlook (Word Engine) & Apple Mail RTL / BiDi Rendering** | `supported` | [Official Docs](https://mailtester.com/blog/right-to-left-email-rendering-problems-gmail-outlook/) (`2026-10-25`) | MailTester's Sep 2026 RTL audit confirms that inline HTML `dir='rtl' align='right'` on `<table>`/`<td>` plus `<bdi>`/`&rlm;` around mixed LTR tokens is required for consistent cross-client rendering. | For plain-text / minimal HTML B2B emails where `<bdi>` is stripped, append `&rlm;` (`‏`) immediately after every inline English word or number. |

## 6. How to Measure Success (`خطة القياس والضوابط`)

- **Primary Metric**: 100% pass rate on Litmus/Email-on-Acid/MailTester RTL visual checks across Outlook & Gmail, plus Promo Code Redemption Rate and Email CTR.
- **Baseline**: Pre-fix visual audit of active automated email templates.
- **Observation Window**: 14 days post-template update.
- **Interpretation Boundary**: Fixing RTL rendering eliminates broken layout friction and unreadable promo codes, while subject line and offer value drive open and purchase rates.

## 7. Primary Sources & Evidence Boundaries (`المصادر الموثقة وحدود الأدلة`)

- [Top Arabic Content Writing Mistakes Hurting Your SEO Rankings](https://www.aiqalam.com/en/blog/top-arabic-content-writing-mistakes-hurting-your-seo-rankings) — *AI Qalam* (Published `2026-10-24`, Accessed `2026-10-25`): Documents poor RTL text alignment, unnatural AI phrasing, and morphological keyword stuffing in Arabic content.
- [Solving Right-to-Left Email Rendering Problems in Gmail and Outlook](https://mailtester.com/blog/right-to-left-email-rendering-problems-gmail-outlook/) — *MailTester* (Published `2026-09-24`, Accessed `2026-10-25`): Documents how missing dir='rtl' attributes, inline CSS overrides, and mixed bidirectional strings cause broken Arabic email rendering in Outlook and Gmail across Klaviyo, HubSpot, and Mailchimp.
