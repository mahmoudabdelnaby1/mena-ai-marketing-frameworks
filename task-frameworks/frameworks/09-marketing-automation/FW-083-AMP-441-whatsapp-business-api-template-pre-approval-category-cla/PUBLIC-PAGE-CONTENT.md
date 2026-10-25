# WhatsApp Business API Template Pre-Approval & Category Classification Checklist (`MARKETING` vs. `UTILITY`)
## <span dir="rtl">قائمة فحص اعتماد قوالب `WhatsApp Business API` ومنع الرفض الآلي (تصنيف `Marketing` مقابل `Utility` وأمثلة المتغيرات `{{1}}`)</span>

> **Asset ID**: `FW-083` (`AMP-441`) | **Artifact Type**: `CHECKLIST` | **Channel**: Marketing Automation | **Markets**: Egypt & GCC (`KSA, UAE, Kuwait, Qatar, Bahrain, Oman`) | **Version**: `1.2` (`Reviewed 2026-10-25`)

**What You Can Do With This (`ماذا يمكنك أن تنجز بهذه الأداة؟`)**:
- **EN**: Prevent Meta from rejecting ~1 in 3 WhatsApp Business API templates by choosing the right category (`MARKETING` vs. `UTILITY`), embedding mandatory realistic Arabic sample values for every `{{1}}` variable, and never starting or ending a template with a bare variable.
- **AR**: <span dir="rtl">منع الرفض التلقائي لثلث قوالب `WhatsApp Business API` عبر مطابقة التصنيف الصحيح (`Marketing` مقابل `Utility`)، وإرفاق أمثلة حقيقية لكل متغير `{{1}}`، وعدم بدء أو إنهاء القالب بمتغير مجرد.</span>

## 1. Use It When & Required Inputs (`متى تستخدمها وما المدخلات المطلوبة؟`)

- **Use It When (EN)**: Use before submitting any Arabic or English message template in Meta WhatsApp Manager, Wati, Respond.io, Infobip, Unifonic, or Twilio.
- **متى تستخدمها (AR)**: <span dir="rtl">تُستخدم قبل إرسال أي قالب رسالة (`Message Template`) للمراجعة في مدير أعمال واتساب (`Meta WhatsApp Manager`) أو منصات الربط.</span>
- **When NOT to Use It (EN)**: Never submit a template containing a discount code, cross-sell offer, cart recovery nudge, or win-back message under the `UTILITY` category—Meta's classifier will reject it or force-reclassify it to `MARKETING`.
- **متى لا تستخدمها (AR)**: <span dir="rtl">لا تقم أبداً بتصنيف رسالة تحتوي على كود خصم أو استرداد سلة متروكة أو عرض ترويجي تحت فئة `UTILITY`؛ لأن نظام ميتا سيرفضها فوراً أو يحولها قسرياً إلى `MARKETING`.</span>

### Exact Inputs to Prepare (`المدخلات المطلوب تجهيزها قبل البدء`)
- Draft Arabic/English WhatsApp Template Body, Header, Footer, and Buttons
- Intended Template Category (`MARKETING`, `UTILITY`, or `AUTHENTICATION`)
- Sample Realistic Values for every numbered placeholder (`{{1}}`, `{{2}}`, `{{3}}`)

## 2. The Working `CHECKLIST` (`الأداة الكاملة الجاهزة للنسخ والتطبيق الفوري`)

### WhatsApp Business API Template Pre-Submission Checklist & Linter

#### 1. Category Classification Rules (`Meta WhatsApp Policy — Verified 2026-10-25`)
| Category | Allowed Use Cases (`100% Pure`) | Prohibited Content (`Causes Instant Rejection or Reclassification`) | Mandatory Structural Elements |
| :--- | :--- | :--- | :--- |
| **`UTILITY` (`خدمي / تشغيلي`)** | Order confirmation (`AMP-448`), shipping update, ZATCA/ETA invoice delivery, appointment reminder, payment receipt. | **Zero upsells (`AMP-237`), zero discount codes, zero 'Check out our new collection' links**, zero abandoned-cart nudges! Must reference a specific active transaction/order `{{1}}`. | Include Order ID `{{1}}` and specific transactional status. |
| **`MARKETING` (`تسويقي`)** | Abandoned cart recovery (`AMP-235`), seasonal sales, back-in-stock alerts, review requests with coupon incentives (`AMP-392`), win-back offers. | Unconsented cold lists (`AMP-232`), deceptive medical/financial claims (`AMP-176`), URL shorteners (`bit.ly` / `tinyurl` — **strictly rejected by Meta!**). | Include a **`Quick-Reply Unsubscribe Button ('إلغاء الاشتراك')`** in the footer/buttons (`AMP-233`, `AMP-447`)! |
| **`AUTHENTICATION` (`تحقق OTP`)** | One-time login or checkout passcodes (`OTP`). | Any custom promotional or conversational text; must use Meta's fixed preset authentication template structure. | Copy-Code button + expiry minutes. |

#### 2. Copy-Ready Python WhatsApp Template Syntax Linter (Run Before API/UI Submission)
```python
import re

def lint_whatsapp_template(body_text: str, category: str, variable_samples: dict):
    issues = []
    text = (body_text or "").strip()
    # Rule 1: Never start or end the template with a variable {{n}}
    if re.match(r"^\{\{\d+\}\}", text) or re.search(r"\{\{\d+\}\}[.،!؟?]*$", text):
        issues.append("FAIL: Template cannot start or end directly with a {{variable}}. Wrap with fixed Arabic words.")
    # Rule 2: Never place two variables directly adjacent ({{1}} {{2}})
    if re.search(r"\{\{\d+\}\}\s*\{\{\d+\}\}", text):
        issues.append("FAIL: Adjacent variables ({{1}} {{2}}) without separating words are rejected by Meta.")
    # Rule 3: Sequential numbering starting at {{1}} with non-empty examples
    vars_found = sorted(set(int(m) for m in re.findall(r"\{\{(\d+)\}\}", text)))
    if vars_found and vars_found != list(range(1, len(vars_found) + 1)):
        issues.append(f"FAIL: Variables must be sequential starting at {{{{1}}}}; found {vars_found}.")
    for v in vars_found:
        if not variable_samples.get(str(v)):
            issues.append(f"FAIL: Missing mandatory sample value for {{{{{v}}}}}.")
    # Rule 4: No public URL shorteners in body
    if re.search(r"(bit\.ly|tinyurl\.com|t\.co|rb\.gy|shorturl\.at)", text, re.IGNORECASE):
        issues.append("FAIL: Third-party URL shorteners (bit.ly, etc.) are rejected; use your full verified brand domain.")
    # Rule 5: Check Utility purity
    if category.upper() == "UTILITY" and re.search(r"(خصم|كود|عرض|تخفيضات|تسوق الآن|سلتك)", text):
        issues.append("FAIL: Promotional tokens detected inside a UTILITY template; switch category to MARKETING or strip promo text.")
    return {"valid": len(issues) == 0, "issues": issues}
```

## 3. Complete End-to-End Worked Example (`مثال تطبيقي متكامل من المدخلات حتى المراجعة البشرية والنتيجة النهائية`)

*(Illustrative scenario — original example for training, never represented as a verified client outcome)*

### Step A: Sample Brief / Input (`موجز المدخلات`)
- **Submission**: Saudi E-Commerce Store submitting an Order Confirmation template under `UTILITY`.
- **Rejected Draft**:
  `"{{1}}، تم تأكيد طلبك {{2}} {{3}}! استخدم كود VIP10 لخصم 10% على طلبك القادم من هنا: https://bit.ly/3xyz — {{4}}"` (Submitted with empty variable sample fields).

### Step B: Initial Output (`المخرج الأولي`)
- **`lint_whatsapp_template()` Output (`4 Fatal Rejection Reasons Found`)**:
  1. `FAIL`: Starts with `{{1}}` and ends with `{{4}}` (bare variables at start and end).
  2. `FAIL`: Adjacent variables `{{2}} {{3}}` with no separating words.
  3. `FAIL`: Promotional text (`"استخدم كود VIP10 لخصم 10%"`) and `bit.ly` shortener inside a `UTILITY` template.
  4. `FAIL`: Missing sample values for `{{1}}..{{4}}`.

### Step C: Human Review & Edits (`التدقيق البشري والتعديلات`)
1. **Rewrote into Pure `UTILITY` Template with Fixed Wrapping Words**:
   `"أهلاً بك يا {{1}}، تم تأكيد طلبك رقم {{2}} بقيمة {{3}} ريال سعودي بنجاح. يمكنك متابعة حالة الشحنة عبر الرابط الرسمي للمتجر بالأسفل. شكراً لثقتك بنا."`
2. **Attached Realistic Arabic Sample Values**: `{{1}}: "أحمد"`, `{{2}}: "#ORD-99412"`, `{{3}}: "349.00"`, and replaced `bit.ly` with a dynamic button pointing to `https://store.sa/orders/{{1}}`.

### Step D: Final Reviewed Example Outcome (`النتيجة النهائية المعتمدة`)
- Template approved by Meta WhatsApp Manager in `< 2 minutes` under `UTILITY` pricing with `0` rejections.

## 4. What Can Go Wrong & How to Fix It (`الأخطاء الشائعة وخطة الإنقاذ`)

- **Failure Case (`المشكلة المحتملة`)**: A marketer submits a template with `{{1}}` and `{{3}}` (skipping `{{2}}` after editing a sentence); Meta's API rejects the payload with `Invalid parameter: variable parameters must be sequential`.
- **Correction & Fallback (`الحل الإجرائي والبديل الآمن`)**: Always run `lint_whatsapp_template()` before clicking Submit in WhatsApp Manager or Wati/Respond.io.

## 5. Model & Platform Capability Matrix (`مصفوفة قدرات النماذج والمنصات — 2026-10-25`)

| Platform / Model | Status | Official Documentation | MENA Operational Constraint | Fallback |
| :--- | :--- | :--- | :--- | :--- |
| **Meta WhatsApp Business Platform Template Guidelines & Category Pricing** | `supported` | [Official Docs](https://developers.facebook.com/documentation/business-messaging/whatsapp/messages/template-messages) (`2026-10-25`) | Meta enforces automated template review checking category alignment (Marketing vs Utility vs Authentication), sequential variable syntax, mandatory sample values, and domain transparency. | Never mix promotional copy into `UTILITY` templates; create two separate templates instead. |

## 6. How to Measure Success (`خطة القياس والضوابط`)

- **Primary Metric**: First-Pass WhatsApp Template Approval Rate (`Target: >= 98%`) and Zero unexpected `UTILITY -> MARKETING` category reclassifications.
- **Baseline**: Prior template rejection rate in WhatsApp Manager (`~33%` industry benchmark).
- **Observation Window**: Enforced on 100% of template submissions.
- **Interpretation Boundary**: Template approval unlocks sending capability, while pacing and opt-out buttons (`AMP-447`) protect phone number quality rating.

## 7. Primary Sources & Evidence Boundaries (`المصادر الموثقة وحدود الأدلة`)

- [Template messages - Meta for Developers](https://developers.facebook.com/documentation/business-messaging/whatsapp/messages/template-messages) — *Meta for Developers* (Published `2026-04-23`, Accessed `2026-10-25`): Business-initiated WhatsApp messages outside the 24-hour customer service window require pre-approved templates with strict variable syntax and category matching.
- [Pricing on the WhatsApp Business Platform | Meta for Developers](https://developers.facebook.com/documentation/business-messaging/whatsapp/pricing) — *Meta for Developers* (Published `2026-09-30`, Accessed `2026-10-25`): Differentiates rates across Marketing, Utility, Authentication, and Service messages by recipient country code (including Egypt and Saudi Arabia).
- [Marketing templates | Meta for Developers](https://developers.facebook.com/documentation/business-messaging/whatsapp/templates/marketing-templates) — *Meta for Developers* (Published `2026-06-17`, Accessed `2026-10-25`): Defines required components, headers, body variables, and CTA button constraints for promotional WhatsApp templates.
- [WhatsApp templates rejected: 7 errors Meta sees](https://asisteclick.com/en/blog/plantillas-whatsapp-rechazadas-meta-7-errores/) — *AsisteClick* (Published `2026-04-30`, Accessed `2026-10-25`): Reports that roughly 1 in 3 WhatsApp Business API templates fail review due to category mismatch, adjacent/trailing variables, URL shorteners, or vague promotional copy.
- [Why WhatsApp Rejects Your Message Templates — and How to Get Approved on the First Try](https://www.tenreply.com/blog/whatsapp-template-rejected-how-to-get-approved) — *Tenreply* (Published `2026-07-19`, Accessed `2026-10-25`): Details technical Meta review checks: mandatory realistic sample values for {{1}}, domain-verified URLs, single clear purpose, and post-approval quality monitoring.
