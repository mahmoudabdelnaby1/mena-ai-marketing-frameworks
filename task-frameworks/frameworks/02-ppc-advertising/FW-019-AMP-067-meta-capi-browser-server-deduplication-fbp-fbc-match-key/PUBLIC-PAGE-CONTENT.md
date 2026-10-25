# Meta CAPI Browser/Server Deduplication & `fbp`/`fbc` Match-Key Checklist for MENA Checkouts
## <span dir="rtl">قائمة فحص منع ازدواجية التحويلات (`Deduplication`) وتمرير مفاتيح `fbp`/`fbc` في `Meta CAPI` لمتاجر المنطقة</span>

> **Asset ID**: `FW-019` (`AMP-067`) | **Artifact Type**: `CHECKLIST` | **Channel**: Pay-Per-Click (PPC) Advertising | **Markets**: Egypt & GCC (`KSA, UAE, Kuwait, Qatar, Bahrain, Oman`) | **Version**: `1.2` (`Reviewed 2026-10-25`)

**What You Can Do With This (`ماذا يمكنك أن تنجز بهذه الأداة؟`)**:
- **EN**: Fix Meta Pixel + Conversions API (CAPI) double-counting and missing `_fbp`/`_fbc` cookies across Salla, Zid, Shopify, and third-party payment redirects (Paymob, Moyasar, Tap, HyperPay, Tabby, Tamara).
- **AR**: <span dir="rtl">إصلاح مشكلة حساب التحويل مرتين (`Double-Counting`) وفقدان معرفات `_fbp` و`_fbc` عند الانتقال لبوابات الدفع (Paymob, Moyasar, Tap, HyperPay, Tabby, Tamara) في متاجر سلة وزد وشوبيفاي.</span>

## 1. Use It When & Required Inputs (`متى تستخدمها وما المدخلات المطلوبة؟`)

- **Use It When (EN)**: Use when configuring or auditing Meta Pixel + Conversions API (`CAPI`) on Salla, Zid, Shopify, WooCommerce, or custom checkouts in Egypt and the GCC.
- **متى تستخدمها (AR)**: <span dir="rtl">تُستخدم عند إعداد أو تدقيق ربط `Meta Pixel` مع `Conversions API (CAPI)` على سلة أو زد أو شوبيفاي أو ووكومرس في مصر والخليج.</span>
- **When NOT to Use It (EN)**: Do not send unhashed raw phone numbers or emails to third-party endpoints—normalize and SHA-256 hash customer identifiers per Meta CAPI specification and Saudi/UAE/Egypt PDPL rules.
- **متى لا تستخدمها (AR)**: <span dir="rtl">لا ترسل أرقام الهواتف أو البريد الإلكتروني كنص مكشوف غير مشفر؛ يجب تطبيع الأرقام وتشفيرها بـ `SHA-256` وفق معايير Meta CAPI وأنظمة حماية البيانات (`PDPL`).</span>

### Exact Inputs to Prepare (`المدخلات المطلوب تجهيزها قبل البدء`)
- Meta Events Manager access (`Overview -> Purchase -> View Details -> Event Deduplication & Event Match Quality`)
- List of active checkout redirect gateways (e.g., Tabby, Tamara, Moyasar, HyperPay, Tap, Paymob, Fawry, Kashier)
- Sample test order ID (`order_id`) to trace in Meta Events Manager `Test Events`

## 2. The Working `CHECKLIST` (`الأداة الكاملة الجاهزة للنسخ والتطبيق الفوري`)

### Meta CAPI Deduplication & MENA Payment-Redirect Checklist

#### 1. Event Deduplication Gate (`Browser Pixel` vs. `Server CAPI`)
- [ ] **Check 1 — Identical `event_name` AND `event_id`**:
  - Both the Browser Pixel `fbq('track', 'Purchase', {...}, {eventID: 'ORD_10045'})` AND the Server CAPI payload (`"event_name": "Purchase", "event_id": "ORD_10045"`) MUST pass the **exact same deterministic `event_id`** (use the canonical `order_id` or `transaction_id`, NEVER a random `UUID()` generated separately on client and server!).
- [ ] **Check 2 — Verify Deduplication Rate in Events Manager**:
  - Open `Meta Events Manager -> Purchase -> Event Deduplication`:
  - **Pass Target**: `% of Browser events deduplicated >= 80%`, and `Same event_id received` badge is green.

#### 2. Preserving `_fbp` and `_fbc` Across MENA Payment Redirects (Tabby / Tamara / Paymob / Mada 3DS)
When a shopper clicks "Pay with Tabby/Tamara" or completes a Mada/Meeza 3D-Secure redirect, the final webhook often fires asynchronously from the payment gateway to your backend **without browser cookies**:
- [ ] **Check 3 — Persist `_fbp`, `_fbc`, `client_ip_address`, and `client_user_agent` on Cart/Order Creation**:
  Before redirecting the user to Tabby/Tamara/Paymob, save `_fbp` and `_fbc` (or construct `fb.1.{timestamp}.{fbclid}` if URL has `fbclid`) into the backend `order_metadata` table so the server webhook includes them when firing CAPI `Purchase`!

#### 3. MENA Phone Number Normalization Before SHA-256 Hashing (`em` / `ph`)
- [ ] **Check 4 — Convert Arabic-Indic Digits & Local `05`/`01` Prefixes to E.164 Digits Only Before SHA-256**:
  - Saudi Arabia: `٠٥٥١٢٣٤٥٦٧` or `0551234567` → **`966551234567`** → `SHA-256(966551234567)`
  - UAE: `0501234567` → **`971501234567`** → `SHA-256(971501234567)`
  - Egypt: `٠١٠١٢٣٤٥٦٧٨` or `01012345678` → **`201012345678`** → `SHA-256(201012345678)`
  *(If you hash `"0551234567"` without the `966` country code or hash Arabic-Indic `"٠٥٥..."`, the SHA-256 digest will NOT match Meta's identity graph, tanking Event Match Quality!)*

## 3. Complete End-to-End Worked Example (`مثال تطبيقي متكامل من المدخلات حتى المراجعة البشرية والنتيجة النهائية`)

*(Illustrative scenario — original example for training, never represented as a verified client outcome)*

### Step A: Sample Brief / Input (`موجز المدخلات`)
- **Store**: KSA & Egypt Dual-Storefront using Salla (KSA with Tamara/Tabby/Mada) and WooCommerce (Egypt with Paymob/Fawry).
- **Diagnostics**:
  1. WooCommerce reported `240` Meta Purchases while actual orders were `125` (Browser Pixel used `order_id: 8812` while Server CAPI plugin generated `event_id: c9a1-44f2...`).
  2. Event Match Quality (EMQ) for `Purchase` was `4.1 / 10` because Egyptian phone numbers (`010...`) were hashed without prepending country code `20` and `_fbc` was lost during Paymob 3DS redirect.

### Step B: Initial Output (`المخرج الأولي`)
```python
import hashlib, re

def normalize_and_hash_mena_phone(raw_phone: str, default_cc: str = "966") -> str:
    # 1. Convert Arabic-Indic (٠-٩) to ASCII (0-9) and strip non-digits
    ascii_digits = re.sub(
        r"[٠-٩]",
        lambda m: str(ord(m.group(0)) - 0x0660),
        raw_phone or ""
    )
    digits = re.sub(r"\D+", "", ascii_digits)
    if digits.startswith("00"):
        digits = digits[2:]
    elif digits.startswith("05") and len(digits) == 10:  # KSA / UAE local mobile
        digits = default_cc + digits[1:]
    elif digits.startswith("01") and len(digits) == 11:  # Egypt local mobile (010/011/012/015)
        digits = "20" + digits[1:]
    return hashlib.sha256(digits.encode("utf-8")).hexdigest()
```

### Step C: Human Review & Edits (`التدقيق البشري والتعديلات`)
1. **Unified `event_id`**: Locked both GTM Browser Pixel and Server CAPI webhook to `event_id = "PUR_" + str(order.id)`.
2. **Checkout Session Persistence**: Stored `_fbp` and `_fbc` in the WooCommerce/Salla order meta before redirecting to Tabby/Paymob, and deployed `normalize_and_hash_mena_phone()` before hashing `ph`.

### Step D: Final Reviewed Example Outcome (`النتيجة النهائية المعتمدة`)
- Duplicate Purchase inflation (`92%` over-reporting) eliminated (`1:1` parity with backend orders).
- Meta `Purchase` Event Match Quality (EMQ) rose from `4.1/10` to **`8.6/10`**.

## 4. What Can Go Wrong & How to Fix It (`الأخطاء الشائعة وخطة الإنقاذ`)

- **Failure Case (`المشكلة المحتملة`)**: A merchant enables both Salla/Shopify's native Meta CAPI integration AND a second third-party GTM Server-Side CAPI container firing on the same pixel with different `event_id` prefixes (`shopify_123` vs `gtm_123`), doubling every reported conversion.
- **Correction & Fallback (`الحل الإجرائي والبديل الآمن`)**: Maintain strictly ONE active CAPI pipeline per Pixel ID, or ensure all pipelines use the exact same deterministic `event_id` formula (`order_id`).

## 5. Model & Platform Capability Matrix (`مصفوفة قدرات النماذج والمنصات — 2026-10-25`)

| Platform / Model | Status | Official Documentation | MENA Operational Constraint | Fallback |
| :--- | :--- | :--- | :--- | :--- |
| **Meta Conversions API (CAPI) Deduplication & Customer Information Parameters** | `supported` | [Official Docs](https://developers.facebook.com/documentation/ads-commerce/conversions-api) (`2026-10-25`) | Meta requires matching `event_name` and `event_id` within 48 hours for deduplication, and E.164 country-code digits (without leading `+` or `00`) before SHA-256 hashing. | Verify in Meta Events Manager `Test Events` tab using a real test order before scaling spend. |

## 6. How to Measure Success (`خطة القياس والضوابط`)

- **Primary Metric**: Meta Event Match Quality (`EMQ` target `>= 8.0/10`) and Discrepancy `%` between Meta Deduplicated Purchases and Backend ERP Orders.
- **Baseline**: Pre-fix EMQ score and Pixel-to-Backend order count variance.
- **Observation Window**: 7 days post-deployment.
- **Interpretation Boundary**: Accurate CAPI deduplication fixes attribution and bidding signal quality, which may initially lower artificially inflated ROAS numbers to reflect true business reality.

## 7. Primary Sources & Evidence Boundaries (`المصادر الموثقة وحدود الأدلة`)

- [Conversions API - Meta for Developers](https://developers.facebook.com/documentation/ads-commerce/conversions-api) — *Meta for Developers* (Published `2026-09-28`, Accessed `2026-10-25`): Server-side CAPI requires event_id deduplication alongside browser Pixel and customer information parameters (fbp, fbc, hashed email/phone) for Event Match Quality.
- [Troubleshoot the Conversions API - Meta for Developers](https://developers.facebook.com/documentation/ads-commerce/conversions-api/support) — *Meta for Developers* (Published `2023-11-30`, Accessed `2026-10-25`): Diagnosing payload mismatches, redundant server firing, and missing deduplication keys in Meta Events Manager.
- [Digital Advertising Landscape in Egypt (2026)](https://23hublab.com/digital-advertising-landscape-in-egypt/) — *23HubLab* (Published `2026-03-15`, Accessed `2026-10-25`): In Egypt, standard Meta Pixel captures only 60-75% of conversions (25-40% lost to in-app browsers, iOS ATT, and ad blockers), while platform-reported conversions overstate actual revenue by 20-40% due to COD cancellations and last-click inflation; provides 2026 EGP CPM/CPC/CPL benchmarks and notes Snapchat is niche in Egypt vs TikTok/Meta.
- [Shopify + Meta Conversions API issue : r/FacebookAds](https://www.reddit.com/r/FacebookAds/comments/1ixwjoy/shopify_meta_conversions_api_issue/) — *Reddit Practitioner Community* (Published `2025-02-25`, Accessed `2026-10-25`): Illustrates native CAPI integration failures where server events drop fbp/fbc parameters or fail to fire on manual/third-party COD checkouts.
