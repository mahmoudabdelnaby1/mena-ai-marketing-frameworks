# End-to-End Worked Example & Failure Recovery — `FW-047` (`AMP-235`)

- **Framework**: MENA Payment-Rail Specific Abandoned Checkout Recovery Workflow (COD vs. Tabby/Tamara BNPL vs. Fawry/InstaPay)
- **العنوان بالعربية**: مسار عمل استرداد السلات المتروكة المخصص حسب وسيلة الدفع في مصر والخليج (`COD` مقابل `Tabby/Tamara` مقابل كود `فوري/إنستاباي`)
- **Selected Artifact Type**: `OPERATING_FRAMEWORK`
- **Disclaimer**: *All scenarios, brand names, SKU codes, and metrics below are original, realistic illustrative examples for MENA practitioner training and are never represented as verified client outcomes.*

## 1. Realistic Sample Brief / Input (`المدخلات وموجز الحالة العملية`)

- **Store**: Cairo Electronics & Home Appliances Store on WooCommerce + Paymob/Fawry (`Average Cart: 3,200 EGP`).
- **Problem**: `38%` of shoppers selecting `Fawry Reference Code` at checkout let the 48-hour code expire because Klaviyo sent them a generic English-translated `'You forgot your cart!'` email that did NOT contain their 10-digit Fawry reference number (`{{fawry_ref}}`) or the Fawry service code (`788`).

## 2. Initial Generated / Completed Output (`المخرج الأولي عند تطبيق الأداة`)

- **Deployed Branch A (`Fawry Pending Payment Flow`)**:
  - **T+5m Email + SMS/WhatsApp**: Displays `<bdi style="font-size:22px; font-weight:bold;">{{fawry_ref_number}}</bdi>`, exact amount (`3,200 EGP`), Fawry Service Code (`788`), and 48-hour expiry timestamp.
  - **T+18h Evening Reminder (`6:00 PM` when shoppers are out commuting)**: `"كود فوري الخاص بطلبك ({{fawry_ref_number}}) ما زال مفعلاً — يمكنك سداده من أي ماكينة فوري أو تطبيق MyFawry في دقيقة واحدة."`

## 3. Human Review & Localization/Technical Edits (`المراجعة البشرية والتعديلات الرقابية والتقنية`)

1. **Added MyFawry App & InstaPay Switch Option**: Included a secondary button inside the T+18h email: `"تفضل الدفع من موبايلك الآن بدون الذهاب لمنفذ فوري؟ ادفع بضغطة واحدة عبر تطبيق MyFawry أو إنستاباي من هنا"`.
2. **Suppressed Generic Abandoned Cart Flow**: Added filter `payment_method != 'fawry_pay_at_outlet'` to the generic abandoned cart flow so Fawry buyers never receive conflicting messages.

## 4. Final Reviewed Example Outcome (`النتيجة النهائية الجاهزة للتنفيذ`)

- 4-Branch payment-specific recovery flows active across Egypt and KSA with dynamic `<bdi>` reference code injection and zero margin-cannibalizing discounts on pending OTC orders.

## 5. What Can Go Wrong & Specific Correction / Fallback (`حالة الفشل المحتملة وخطة الإنقاذ والبديل`)

- **Common Failure Mode (`ما الذي قد يسير بشكل خاطئ؟`)**:
  A customer generates a Fawry reference code (`1,000 EGP`), then receives an automated 'Abandoned Cart 15% Off (`850 EGP`)' email 2 hours later; the customer abandons the first Fawry code, creates a second discounted order, and inventory stays double-locked for 48 hours.
- **Specific Correction & Non-AI / Platform Fallback (`الإصلاح المحدد والبديل الآمن`)**:
  Treat `Pending Fawry OTC` and `Pending Bank/InstaPay Transfer` as **`Awaiting_Offline_Settlement`** (a post-order state), strictly excluded from pre-order `Abandoned_Cart` discount flows.
