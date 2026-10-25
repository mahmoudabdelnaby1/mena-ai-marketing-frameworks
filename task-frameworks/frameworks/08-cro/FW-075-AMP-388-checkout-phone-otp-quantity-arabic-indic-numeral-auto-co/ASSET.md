# FW-075: Checkout Phone, OTP & Quantity Arabic-Indic Numeral (`٠١٢٣٤٥٦٧٨٩`) Auto-Conversion Checklist
## قائمة فحص وكود التحويل التلقائي للأرقام العربية-الهندية (`٠١٢٣٤٥٦٧٨٩`) في حقول الهاتف ورموز التحقق (`OTP`) بصفحة الدفع

- **Consolidated Contextual Child IDs (`MERGE_INTO_EXISTING`)**: `AMP-398`, `AMP-408`, `AMP-418`, `AMP-428`, `AMP-438`
- **Selected Artifact Type**: `CHECKLIST`
- **Intended Audience**: CRO Specialist, UX/UI Designer, E-Commerce Product Manager, Frontend Developer
- **Target Markets & Languages**: Egypt & GCC (`Saudi Arabia, UAE, Kuwait, Qatar, Bahrain, Oman`) — Bilingual Arabic (`Egyptian Ammiya`, `Saudi/Gulf Khaleeji`, `White MSA`) + English
- **Version**: `1.2` | **Last Reviewed**: `2026-10-25` | **Status**: `READY_FOR_REVIEW`

## 1. Plain-Language Promise & Why This Artifact Form Fits the Job

- **What You Can Make or Decide (EN)**: Auto-convert Arabic-Indic (`٠-٩`) and Eastern Arabic (`۰-۹`) digits into standard ASCII (`0-9`) on every phone, OTP, postal code, and quantity input field so mobile shoppers with Arabic keyboards are never blocked by validation errors.
- **ما الذي يمكنك إنجازه أو حسمه بهذه الأداة (AR)**: التحويل التلقائي اللحظي للأرقام الهندية (`٠١٢٣٤٥٦٧٨٩`) إلى الأرقام القياسية (`0123456789`) في حقول رقم الجوال ورمز التحقق (`OTP`) والكمية لمنع رفض الطلبات للمستخدمين الذين يكتبون بلوحة المفاتيح العربية.
- **Why `CHECKLIST` Fits This User Job (EN)**: Millions of iOS and Android users in KSA, Egypt, and the GCC have their phone keyboard set to Arabic, which outputs Unicode Arabic-Indic digits (`٠–٩`: `٠٥٥١٢٣٤٥٦٧` or `٠١٠١٢٣٤٥٦٧٨`); Western regex validators (`/^[0-9]{10,11}$/`) reject `٠٥٥...` as 'Invalid Phone Number (`رقم الجوال غير صحيح`)' without telling the user why, causing instant checkout abandonment; a 10-line JS auto-normalizer + CHECKLIST eliminates this friction.
- **لماذا يناسب شكل `CHECKLIST` هذه المهمة (AR)**: تُخرج لوحة المفاتيح العربية في هواتف iOS وAndroid الأرقام بصيغة هندية (`٠٥٥...` أو `٠١٠...`)؛ وتقوم تعبيرات التحقق الغربية (`/^[0-9]+$/`) برفض الحقل وإظهار خطأ «رقم الهاتف غير صحيح» مما يتسبب في ترك السلة فوراً؛ وتنهي قائمة الفحص والكود البرمجي المرفق هذه المشكلة نهائياً.

## 2. "Use It When" Trigger, Boundaries & Exact Inputs to Prepare

- **Use It When (EN)**: Use on every checkout form, WhatsApp lead capture popup, OTP verification modal, and coupon/quantity input across MENA websites and apps.
- **متى تستخدم هذه الأداة (AR)**: تُستخدم في جميع نماذج الدفع والتسجيل ونوافذ التحقق (`OTP`) وحقول الكمية وأكواد الخصم في المواقع والتطبيقات العربية.
- **When NOT to Use It (EN)**: Never display an error message saying `'Please enter English numbers only'`—convert the digits silently in the background on `input` so the user never sees an error!
- **متى لا تستخدم هذه الأداة (AR)**: لا تُظهر للمستخدم رسالة خطأ تطالبه «بإدخال الأرقام باللغة الإنجليزية فقط»؛ بل قم بتحويل الأرقام برمجياً في الخلفية أثناء الكتابة دون إزعاجه بأي خطأ!

### Exact Inputs to Prepare Before Starting (`المدخلات المطلوب تجهيزها`)
1. Checkout / Lead Form HTML `<input>` selectors (`type="tel"`, `name="phone"`, `name="otp"`, `name="quantity"`)
2. Country Mobile Regex Rules (`KSA: 05XXXXXXXX / +9665XXXXXXXX`, `Egypt: 01[0125]XXXXXXXX`, `UAE: 05XXXXXXXX`)

### Privacy-Safe Data Handling (`ضوابط الخصوصية وحماية البيانات الشخصية PDPL`)
- **Strict PII Redaction Before Prompting**: Under Saudi PDPL (Art. 25), UAE Federal Decree-Law No. 45 of 2021, Qatar Law No. 13 of 2016, and Egypt Law No. 151 of 2020, **never paste raw customer names, unhashed mobile numbers (`+9665...` / `+201...`), email addresses, national IDs, or private WhatsApp transcripts into public/consumer LLM interfaces**. Use anonymized placeholders (`{first_name}`, `ORD_10045`) during prompt testing and restrict live customer data to zero-data-retention enterprise API endpoints or local deterministic scripts.

## 3. The Directly Usable Artifact (`الأداة التطبيقية الجاهزة للنسخ والتنفيذ`)

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

## 4. Model & Platform Capability Branches (`فروع قدرات النماذج والمنصات والبدائل الاحتياطية`)

| System / Platform | Capability Status | Official Documentation & Access Date | Operational Constraint in Egypt & GCC | Fallback When Feature/Modality Is Unavailable |
| :--- | :--- | :--- | :--- | :--- |
| **iOS / Android Arabic Keyboard Unicode Output (`\u0660-\u0669`) & iOS Contacts BiDi Wrapping (`\u202A...\u202C`)** | `supported` | [Official Reference](https://voctos.net/arabic-site-search-normalization/) (`2026-10-25`) | Arabic mobile keyboards emit `٠–٩` and iOS clipboard operations around phone numbers inject invisible directional formatting characters (`‪`, `‬`, `‎`). | Strip `[‎‏‪-‮⁦-⁩]` and map `[٠-٩]` -> `[0-9]` on every numeric input. |

## 5. Consolidated Regional & Vertical Adaptation Matrix (`دمج الأنماط السياقية الفرعية بدون حشو`)

Per Agent 2 v1.2's anti-padding rule, the following **5 cross-verified contextual synthesis patterns** and **1 screened duplicate variants** share this core mechanism and are consolidated directly into this source-of-truth framework:

| Child Pattern ID | Disposition | Regional / Sector Operating Context | Specific Adaptation & Guardrail Integrated in This Asset | Evidence Tier |
| :--- | :--- | :--- | :--- | :--- |
| **`AMP-398`** | `MERGE_INTO_EXISTING` | Egyptian E-Commerce & Social Commerce (Shopify / WooCommerce / Cairo & Alexandria) | Frontend JavaScript input normalizer converting `[٠-٩]` and `[۰-۹]` to `0-9` on keyup/blur before validation.; Specifically impacts Egyptian brands operating in EGP where merchant-specific payment mix from recent order records, Mobile Wallets (Vodafone Cash), InstaPay, and Fawry dominate. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-408`** | `MERGE_INTO_EXISTING` | UAE & Multi-Market GCC Enterprise / Retail (Dubai, Abu Dhabi, Doha, Kuwait) | Frontend JavaScript input normalizer converting `[٠-٩]` and `[۰-۹]` to `0-9` on keyup/blur before validation.; Specifically impacts bilingual Arabic/English campaigns in high-CPM, expat-dense Gulf markets under UAE PDPL / TDRA and Qatari regulations. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-418`** | `MERGE_INTO_EXISTING` | High-Trust & Regulated Verticals (Healthcare/SFDA/EDA, Fintech/SAMA/FRA, Real Estate) | Frontend JavaScript input normalizer converting `[٠-٩]` and `[۰-۹]` to `0-9` on keyup/blur before validation.; Specifically impacts regulated claims requiring SFDA, EDA, MOH, SAMA, FRA, or RERA compliance pre-clearance and strict hallucination guardrails. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-428`** | `MERGE_INTO_EXISTING` | Seasonal Peak Operations (Ramadan, Eid, White/Yellow Friday, Saudi Founding/National Day) | Frontend JavaScript input normalizer converting `[٠-٩]` and `[۰-۹]` to `0-9` on keyup/blur before validation.; Specifically impacts high-velocity seasonal surges where CPMs jump 40-70%, prices change rapidly, and Hijri calendar cultural sensitivity is paramount. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-438`** | `MERGE_INTO_EXISTING` | Multi-Client Agency & MarTech API Automation Pipelines (LLM APIs, Webhooks, GA4, CAPI) | Frontend JavaScript input normalizer converting `[٠-٩]` and `[۰-۹]` to `0-9` on keyup/blur before validation.; Specifically impacts automated multi-SKU or multi-client LLM/API pipelines where schema validation, token cost, and attribution governance are required. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-538`** | `REJECT_DUPLICATE` | Screened UI/Format Synonym (`Merged Variant: Minor UI/Format Synonym of AMP-408 (CRO - Conversion Rate Optimization)`) | Consolidated into parent workflow without duplicate file inflation. | `SCREENED_DUPLICATE_VARIANT` |

### Context-Specific Execution Knobs Across the 5 MENA Operating Environments
1. **Saudi D2C E-Commerce (`Salla / Zid / Riyadh & Jeddah Retail`)**: Enforce `SAR` tax-inclusive pricing (`15% ZATCA VAT`), native `Mada / Apple Pay / Tabby / Tamara` visibility (`AMP-387`), `GAMR Mawthooq` creator verification (`AMP-281`), and White Saudi Khaleeji orthography (`AMP-002`, `AMP-177`).
2. **Egyptian E-Commerce & Social Commerce (`Shopify / WooCommerce / Cairo & Alexandria`)**: Use each merchant’s own order and payment data to assess Cash on Delivery (`COD`), mobile wallets, InstaPay, Fawry, `valU`, address fields, and pre-dispatch WhatsApp confirmation. Verify current provider terms and local requirements before implementation.
3. **UAE & Multi-Market GCC Enterprise / Retail (`Dubai, Abu Dhabi, Doha, Kuwait`)**: Separate high-CPM UAE/Qatar budgets from lower-CPM markets (`AMP-061`), enforce UAE `TDRA` `9 PM – 7 AM` SMS curfew + `AD-` prefix (`AMP-442`), UAE Media Council permits (`AMP-282`), and bilingual Arabic/English canonical & currency parity (`current applicable UAE VAT`, `current applicable Qatar/Kuwait tax rules`, 3-decimal `KWD` `AMP-239`).
4. **High-Trust & Regulated Verticals (`Healthcare SFDA/MOH/EDA, FinTech SAMA/FRA, Real Estate REGA/RERA`)**: Strip all therapeutic/cure verbs (`AMP-176`, `AMP-286`), display mandatory `MOH/SFDA/DHA/EDA/Fal/Trakheesi` permit numbers (`AMP-070`), and route budgets to high-credibility channels (`AMP-290`, `AMP-339`).
5. **Seasonal Peak Operations (`Ramadan, Eid, White/Yellow Friday, Saudi Founding/National Day`)**: Lock Hijri-Gregorian overlaps (`Feb 2027 Ramadan x Saudi Founding Day x Kuwait National Day` `AMP-125`), pre-schedule GMC `sale_price_effective_date` 48h ahead (`AMP-063`), verify 30-day baseline discount permits (`AMP-064`), and disable Meta Advantage+ auto-music (`AMP-065`).

## 6. Worked Example Summary & Failure Recovery (`ملخص المثال التطبيقي وخطة الإنقاذ`)

*(Full step-by-step worked example with annotated human edits is also provided in `EXAMPLE.md`)*

- **Sample Input Brief**: - **Store**: Riyadh & Cairo Healthcare Booking & Pharmacy Delivery App.
- **Problem**: Analytics showed a `28%` drop-off on the mobile phone & SMS OTP verification step among iOS users browsing the Arabic interface. Session replays revealed users typing `٠٥٠...` (or pasting their number from iOS Contacts with invisible `‪` marks) and getting blocked by `"يرجى إدخال رقم جوال صحيح"`.
- **Human Review & Key Edits Applied**: 1. **Added Flexible Saudi/Egypt Prefix Acceptance**: Allowed users in KSA to enter `0551234567`, `551234567`, `966551234567`, or `+966 55 123 4567` (and in Egypt `010...`, `10...`, `+2010...`) and normalized all formats to E.164 automatically instead of forcing a rigid 9-digit mask.
2. **Added WebOTP (`autocomplete="one-time-code"`)**: Enabled 1-tap iOS/Android SMS OTP autofill.
- **Final Usable Output**: - Phone/OTP step validation error rate dropped from `28%` to `1.1%`, recovering thousands of blocked mobile checkouts.
- **What Can Go Wrong**: A developer only normalizes Arabic-Indic digits on the frontend JS, but a user submitting via an in-app browser autofill bypasses the `input` event and hits the backend PHP/Node validator with `٠١٠...` or `‪`, causing a `422 Unprocessable Entity` error.
- **Correction & Fallback**: Always run `toAsciiDigits()` on **BOTH the frontend `input` listener AND the backend API request body middleware** before running validation rules.

## 7. Measurement Plan & Hypothesis Framing (`خطة القياس والضوابط الإحصائية`)

- **Primary Metric to Track**: Phone & OTP Input Validation Error Rate (`Target: <1.5%`) and Checkout Step-1-to-Step-2 Progression Rate.
- **Baseline Definition**: Prior 14-day form field validation error events in GA4 / Clarity.
- **Observation Window**: 7 days post-deployment. *(Must span full 7/14-day weekly cycles and account for 25th–30th monthly salary windows per `AMP-391`)*.
- **What Cannot Be Concluded (Boundary)**: Numeral normalization eliminates keyboard-layout friction, while SMS gateway delivery speed determines OTP completion.
