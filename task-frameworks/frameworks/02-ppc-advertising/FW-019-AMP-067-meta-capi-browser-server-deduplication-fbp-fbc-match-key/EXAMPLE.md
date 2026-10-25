# End-to-End Worked Example & Failure Recovery — `FW-019` (`AMP-067`)

- **Framework**: Meta CAPI Browser/Server Deduplication & `fbp`/`fbc` Match-Key Checklist for MENA Checkouts
- **العنوان بالعربية**: قائمة فحص منع ازدواجية التحويلات (`Deduplication`) وتمرير مفاتيح `fbp`/`fbc` في `Meta CAPI` لمتاجر المنطقة
- **Selected Artifact Type**: `CHECKLIST`
- **Disclaimer**: *All scenarios, brand names, SKU codes, and metrics below are original, realistic illustrative examples for MENA practitioner training and are never represented as verified client outcomes.*

## 1. Realistic Sample Brief / Input (`المدخلات وموجز الحالة العملية`)

- **Store**: KSA & Egypt Dual-Storefront using Salla (KSA with Tamara/Tabby/Mada) and WooCommerce (Egypt with Paymob/Fawry).
- **Diagnostics**:
  1. WooCommerce reported `240` Meta Purchases while actual orders were `125` (Browser Pixel used `order_id: 8812` while Server CAPI plugin generated `event_id: c9a1-44f2...`).
  2. Event Match Quality (EMQ) for `Purchase` was `4.1 / 10` because Egyptian phone numbers (`010...`) were hashed without prepending country code `20` and `_fbc` was lost during Paymob 3DS redirect.

## 2. Initial Generated / Completed Output (`المخرج الأولي عند تطبيق الأداة`)

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

## 3. Human Review & Localization/Technical Edits (`المراجعة البشرية والتعديلات الرقابية والتقنية`)

1. **Unified `event_id`**: Locked both GTM Browser Pixel and Server CAPI webhook to `event_id = "PUR_" + str(order.id)`.
2. **Checkout Session Persistence**: Stored `_fbp` and `_fbc` in the WooCommerce/Salla order meta before redirecting to Tabby/Paymob, and deployed `normalize_and_hash_mena_phone()` before hashing `ph`.

## 4. Final Reviewed Example Outcome (`النتيجة النهائية الجاهزة للتنفيذ`)

- Duplicate Purchase inflation (`92%` over-reporting) eliminated (`1:1` parity with backend orders).
- Meta `Purchase` Event Match Quality (EMQ) rose from `4.1/10` to **`8.6/10`**.

## 5. What Can Go Wrong & Specific Correction / Fallback (`حالة الفشل المحتملة وخطة الإنقاذ والبديل`)

- **Common Failure Mode (`ما الذي قد يسير بشكل خاطئ؟`)**:
  A merchant enables both Salla/Shopify's native Meta CAPI integration AND a second third-party GTM Server-Side CAPI container firing on the same pixel with different `event_id` prefixes (`shopify_123` vs `gtm_123`), doubling every reported conversion.
- **Specific Correction & Non-AI / Platform Fallback (`الإصلاح المحدد والبديل الآمن`)**:
  Maintain strictly ONE active CAPI pipeline per Pixel ID, or ensure all pipelines use the exact same deterministic `event_id` formula (`order_id`).
