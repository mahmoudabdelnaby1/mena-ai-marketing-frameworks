# End-to-End Worked Example & Failure Recovery — `FW-077` (`AMP-390`)

- **Framework**: Egypt & KSA Localized Checkout Address Form Workflow
- **العنوان بالعربية**: مسار تخصيص حقول العنوان في صفحة الدفع لمصر والسعودية
- **Selected Artifact Type**: `OPERATING_FRAMEWORK`
- **Disclaimer**: *All scenarios, brand names, SKU codes, and metrics below are original, realistic illustrative examples for MENA practitioner training and are never represented as verified client outcomes.*

## 1. Realistic Sample Brief / Input (`المدخلات وموجز الحالة العملية`)

- **Store**: Multi-country Home & Kitchen Store on WooCommerce / Shopify selling in Egypt, KSA, and UAE.
- **Problem**:
  1. Checkout had `Postal Code` set to `Required` with a 5-digit regex; in UAE (which has no postal code system at all!) and Egypt, `22%` of users failed validation on the address step.
  2. Egyptian buyers typed only `"القاهرة - شارع عباس العقاد"` with no building/apartment or landmark, causing Bosta couriers to mark `19%` of parcels as `'Incomplete Address - Delayed'`.

## 2. Initial Generated / Completed Output (`المخرج الأولي عند تطبيق الأداة`)

- **Checkout Address Reconfiguration**:
  1. Set `Postal Code` to **Hidden/Optional** (silently passing `"00000"` to 3DS card processors that require a non-null string).
  2. Added cascading `Governorate -> District` dropdown for Egypt synced with Bosta's zone IDs, plus explicit placeholder `"اسم الشارع، رقم العمارة، الدور، الشقة + أقرب علامة مميزة (مثال: بجوار...)"`.

## 3. Human Review & Localization/Technical Edits (`المراجعة البشرية والتعديلات الرقابية والتقنية`)

1. **Arabic-Indic Numeral Normalization on Building/Apartment Fields (`AMP-388`)**: Ensured building and floor numbers typed in Arabic-Indic digits (`عمارة ١٤ الدور ٣ شقة ٧`) pass validation smoothly.
2. **Paired with Post-Checkout WhatsApp Location Pin (`AMP-448`)**: For KSA and Egypt COD orders, offered a 1-tap WhatsApp location pin confirmation after checkout.

## 4. Final Reviewed Example Outcome (`النتيجة النهائية الجاهزة للتنفيذ`)

- Address-step abandonment dropped from `22%` to `3.4%`, and courier first-attempt delivery success rate increased by `14` percentage points.

## 5. What Can Go Wrong & Specific Correction / Fallback (`حالة الفشل المحتملة وخطة الإنقاذ والبديل`)

- **Common Failure Mode (`ما الذي قد يسير بشكل خاطئ؟`)**:
  A store removes the `Postal Code` field from the frontend HTML, but their credit-card gateway (e.g., Stripe/Checkout.com/Cybersource AVS check) rejects the backend API call because `billing_address.postal_code` was sent as `null`.
- **Specific Correction & Non-AI / Platform Fallback (`الإصلاح المحدد والبديل الآمن`)**:
  Hide the `Postal Code` input from the user on the frontend UI in Egypt and UAE, and **populate a hidden default value (`"00000"`) in the backend payload** so legacy payment-gateway schemas never throw a null-field error.
