# Checkout Phone, OTP & Quantity Arabic-Indic Numeral (`٠١٢٣٤٥٦٧٨٩`) Auto-Conversion Checklist
## <span dir="rtl">قائمة فحص وكود التحويل التلقائي للأرقام العربية-الهندية (`٠١٢٣٤٥٦٧٨٩`) في حقول الهاتف ورموز التحقق (`OTP`) بصفحة الدفع</span>

> **Asset ID**: `FW-075` (`AMP-388`) | **Artifact Type**: `CHECKLIST` | **Channel**: CRO - Conversion Rate Optimization | **Markets**: Egypt & GCC (`KSA, UAE, Kuwait, Qatar, Bahrain, Oman`) | **Version**: `1.2` (`Reviewed 2026-10-25`)

**What You Can Do With This (`ماذا يمكنك أن تنجز بهذه الأداة؟`)**:
- **EN**: Auto-convert Arabic-Indic (`٠-٩`) and Eastern Arabic (`۰-۹`) digits into standard ASCII (`0-9`) on every phone, OTP, postal code, and quantity input field so mobile shoppers with Arabic keyboards are never blocked by validation errors.
- **AR**: <span dir="rtl">التحويل التلقائي اللحظي للأرقام الهندية (`٠١٢٣٤٥٦٧٨٩`) إلى الأرقام القياسية (`0123456789`) في حقول رقم الجوال ورمز التحقق (`OTP`) والكمية لمنع رفض الطلبات للمستخدمين الذين يكتبون بلوحة المفاتيح العربية.</span>

## 1. Use It When & Required Inputs (`متى تستخدمها وما المدخلات المطلوبة؟`)

- **Use It When (EN)**: Use on every checkout form, WhatsApp lead capture popup, OTP verification modal, and coupon/quantity input across MENA websites and apps.
- **متى تستخدمها (AR)**: <span dir="rtl">تُستخدم في جميع نماذج الدفع والتسجيل ونوافذ التحقق (`OTP`) وحقول الكمية وأكواد الخصم في المواقع والتطبيقات العربية.</span>
- **When NOT to Use It (EN)**: Never display an error message saying `'Please enter English numbers only'`—convert the digits silently in the background on `input` so the user never sees an error!
- **متى لا تستخدمها (AR)**: <span dir="rtl">لا تُظهر للمستخدم رسالة خطأ تطالبه «بإدخال الأرقام باللغة الإنجليزية فقط»؛ بل قم بتحويل الأرقام برمجياً في الخلفية أثناء الكتابة دون إزعاجه بأي خطأ!</span>

### Exact Inputs to Prepare (`المدخلات المطلوب تجهيزها قبل البدء`)
- Checkout / Lead Form HTML `<input>` selectors (`type="tel"`, `name="phone"`, `name="otp"`, `name="quantity"`)
- Country Mobile Regex Rules (`KSA: 05XXXXXXXX / +9665XXXXXXXX`, `Egypt: 01[0125]XXXXXXXX`, `UAE: 05XXXXXXXX`)

## 2. The Working `CHECKLIST` (`الأداة الكاملة الجاهزة للنسخ والتطبيق الفوري`)

### 1. Copy-Ready Silent Numeral Auto-Converter (`Drop into Checkout / Global Footer JS`)

```javascript
/**
 * Silently converts Arabic-Indic (٠-٩) and Extended Arabic-Indic (۰-۹) numerals
 * to standard ASCII digits (0-9) in real time as the user types or pastes.
 * Also strips invisible BiDi control characters (‎, ‏, ‪-‮) pasted from iOS Contacts!
 */
(function attachMenaNumeralNormalizer() {
  function toAsciiDigits(str) {
    if (!str) return '';
    return str
      .replace(/[٠-٩]/g, function(d) { return String(d.charCodeAt(0) - 0x0660); })
      .replace(/[۰-۹]/g, function(d) { return String(d.charCodeAt(0) - 0x06F0); })
      .replace(/[‎‏‪-‮⁦-⁩]/g, ''); // Strip iOS copy-paste BiDi marks
  }

  document.addEventListener('input', function(e) {
    var el = e.target;
    if (!el || el.tagName !== 'INPUT') return;
    var isNumericField = (
      el.type === 'tel' ||
      el.inputMode === 'numeric' ||
      el.inputMode === 'tel' ||
      /(phone|mobile|tel|otp|code|pin|zip|postal|qty|quantity|national_address|building)/i.test(el.name + ' ' + el.id + ' ' + el.className)
    );
    if (isNumericField) {
      var cleaned = toAsciiDigits(el.value);
      if (cleaned !== el.value) {
        var pos = el.selectionStart;
        el.value = cleaned;
        try { el.setSelectionRange(pos, pos); } catch (_) {}
      }
    }
  }, true);
})();
```

### 2. Checkout Numeric Input QA Checklist
- [ ] **Check 1 — Switch iOS/Android Keyboard to Arabic & Type `٠٥٥١٢٣٤٥٦٧` / `٠١٠١٢٣٤٥٦٧٨`**:
  - Confirm the input field converts `٠٥٥١٢٣٤٥٦٧` to `0551234567` smoothly as you type with zero validation errors.
- [ ] **Check 2 — iOS Contacts Copy-Paste Test (`Invisible BiDi Marks`)**:
  - When a user copies a phone number from iOS Contacts or WhatsApp (`"‪+966 55 123 4567‬"`), iOS wraps the string in invisible Unicode Left-to-Right Embedding characters (`‪` and `‬`), which cause standard regex `/^\+?[0-9 ]+$/` to **FAIL** even though the number looks completely normal on screen! Confirm the script above strips `[‎‏‪-‮⁦-⁩]` automatically.
- [ ] **Check 3 — HTML Attributes (`dir="ltr" inputmode="tel" autocomplete="tel"`)**:
  - Set `dir="ltr" inputmode="tel" autocomplete="tel"` on all phone and OTP `<input>` elements so digits never reverse order while typing on an RTL page.

## 3. Complete End-to-End Worked Example (`مثال تطبيقي متكامل من المدخلات حتى المراجعة البشرية والنتيجة النهائية`)

*(Illustrative scenario — original example for training, never represented as a verified client outcome)*

### Step A: Sample Brief / Input (`موجز المدخلات`)
- **Store**: Riyadh & Cairo Healthcare Booking & Pharmacy Delivery App.
- **Problem**: Analytics showed a `28%` drop-off on the mobile phone & SMS OTP verification step among iOS users browsing the Arabic interface. Session replays revealed users typing `٠٥٠...` (or pasting their number from iOS Contacts with invisible `‪` marks) and getting blocked by `"يرجى إدخال رقم جوال صحيح"`.

### Step B: Initial Output (`المخرج الأولي`)
- **Deployed `attachMenaNumeralNormalizer()` + Server-Side Fallback**:
  - Client-side listener converts `٠-٩` to `0-9` and strips iOS BiDi invisible marks on `input`.
  - Backend API endpoint runs the exact same normalization before validating and hashing for CAPI (`AMP-067`).

### Step C: Human Review & Edits (`التدقيق البشري والتعديلات`)
1. **Added Flexible Saudi/Egypt Prefix Acceptance**: Allowed users in KSA to enter `0551234567`, `551234567`, `966551234567`, or `+966 55 123 4567` (and in Egypt `010...`, `10...`, `+2010...`) and normalized all formats to E.164 automatically instead of forcing a rigid 9-digit mask.
2. **Added WebOTP (`autocomplete="one-time-code"`)**: Enabled 1-tap iOS/Android SMS OTP autofill.

### Step D: Final Reviewed Example Outcome (`النتيجة النهائية المعتمدة`)
- Phone/OTP step validation error rate dropped from `28%` to `1.1%`, recovering thousands of blocked mobile checkouts.

## 4. What Can Go Wrong & How to Fix It (`الأخطاء الشائعة وخطة الإنقاذ`)

- **Failure Case (`المشكلة المحتملة`)**: A developer only normalizes Arabic-Indic digits on the frontend JS, but a user submitting via an in-app browser autofill bypasses the `input` event and hits the backend PHP/Node validator with `٠١٠...` or `‪`, causing a `422 Unprocessable Entity` error.
- **Correction & Fallback (`الحل الإجرائي والبديل الآمن`)**: Always run `toAsciiDigits()` on **BOTH the frontend `input` listener AND the backend API request body middleware** before running validation rules.

## 5. Model & Platform Capability Matrix (`مصفوفة قدرات النماذج والمنصات — 2026-10-25`)

| Platform / Model | Status | Official Documentation | MENA Operational Constraint | Fallback |
| :--- | :--- | :--- | :--- | :--- |
| **iOS / Android Arabic Keyboard Unicode Output (`\u0660-\u0669`) & iOS Contacts BiDi Wrapping (`\u202A...\u202C`)** | `supported` | [Official Docs](https://voctos.net/arabic-site-search-normalization/) (`2026-10-25`) | Arabic mobile keyboards emit `٠–٩` and iOS clipboard operations around phone numbers inject invisible directional formatting characters (`‪`, `‬`, `‎`). | Strip `[‎‏‪-‮⁦-⁩]` and map `[٠-٩]` -> `[0-9]` on every numeric input. |

## 6. How to Measure Success (`خطة القياس والضوابط`)

- **Primary Metric**: Phone & OTP Input Validation Error Rate (`Target: <1.5%`) and Checkout Step-1-to-Step-2 Progression Rate.
- **Baseline**: Prior 14-day form field validation error events in GA4 / Clarity.
- **Observation Window**: 7 days post-deployment.
- **Interpretation Boundary**: Numeral normalization eliminates keyboard-layout friction, while SMS gateway delivery speed determines OTP completion.

## 7. Primary Sources & Evidence Boundaries (`المصادر الموثقة وحدود الأدلة`)

- [Arabic Site Search Normalization: 20 Arab Online Stores Tested](https://voctos.net/arabic-site-search-normalization/) — *VOCTOS* (Published `2026-10-08`, Accessed `2026-10-25`): Internal site search on Salla and Zid stores fails when shoppers use variant Arabic spellings (Hamza أ/ا, Taa Marbuta ة/ه, Alef Maqsura ى/ي) or Arabic-Indic digits (٠-٩ vs 0-9) that differ from catalog product titles.
- [The Arabic SEO in Saudi Arabia Mistakes Costing Riyadh Brands Rankings](https://digistreetmedia.com/blog/the-arabic-seo-in-saudi-arabia-mistakes-costing-riyadh-brands-rankings/) — *DigiStreet Media* (Published `2026-09-29`, Accessed `2026-10-25`): Identifies 5 recurring KSA SEO failures: treating Arabic as translation, running one strategy across Arabic/English, broken hreflang/RTL mobile UX, ignoring Vision 2030 sector context, and chasing non-local backlinks while treating Riyadh, Jeddah, and Dammam as homogeneous.
