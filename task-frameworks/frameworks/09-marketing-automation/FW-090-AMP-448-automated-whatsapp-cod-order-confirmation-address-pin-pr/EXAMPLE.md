# End-to-End Worked Example & Failure Recovery — `FW-090` (`AMP-448`)

- **Framework**: Automated WhatsApp COD Order Confirmation, Address-Pin & Prepaid-Switch Workflow (Egypt & KSA)
- **العنوان بالعربية**: مسار عمل التأكيد الآلي لطلبات الدفع عند الاستلام (`COD`) والتحقق من موقع التوصيل عبر واتساب قبل تسليم الشحنة للمندوب (مصر والسعودية)
- **Selected Artifact Type**: `OPERATING_FRAMEWORK`
- **Disclaimer**: *All scenarios, brand names, SKU codes, and metrics below are original, realistic illustrative examples for MENA practitioner training and are never represented as verified client outcomes.*

## 1. Realistic Sample Brief / Input (`المدخلات وموجز الحالة العملية`)

- **Store**: Cairo & Alexandria D2C Apparel & Cosmetics Store (`320` COD orders/day via Bosta).
- **Problem**: Store printed AWBs and shipped 100% of COD orders blindly. `29%` (`93` parcels/day) were returned to sender (`RTO` — fake phone numbers, buyers saying `'طلبت بالغلط'`, or missing building numbers), costing **`246,000 EGP / month`** in dead courier fees.

## 2. Initial Generated / Completed Output (`المخرج الأولي عند تطبيق الأداة`)

- **30-Day Results of the 4-Step WhatsApp COD Gate (`320` daily COD orders)**:
  - `74%` (`237` orders/day) tapped **`[ 1️⃣ تأكيد الطلب ]`** within 15 minutes → Auto-dispatched to Bosta immediately.
  - `11%` (`35` orders/day) tapped **`[ 2️⃣ تعديل العنوان / اللوكيشن ]`** → Added missing apartment/landmark or GPS pin, then auto-dispatched.
  - `9%` (`29` orders/day) tapped **`[ 3️⃣ إلغاء الطلب ]`** (`"طلبت بالخطأ / غيرت رأيي"`) → Cancelled **BEFORE** leaving the warehouse (`0 EGP` courier fee lost!).
  - `6%` (`19` orders/day) had disconnected/fake phone numbers → Caught and cancelled before shipping!

## 3. Human Review & Localization/Technical Edits (`المراجعة البشرية والتعديلات الرقابية والتقنية`)

1. **Fast-Track VIP Bypass (`AMP-240`)**: Added an automatic bypass rule: if the buyer is a **`TIER_1_VERIFIED_DELIVERED_VIP`** (`>= 2` past delivered orders and `<10%` RTO), mark the order ready to ship immediately while sending a courtesy confirmation notice.
2. **Courier GPS Note Injection**: Mapped the WhatsApp `location` message (`lat, long`) into Bosta/SMSA's driver notes field so the courier can open Google Maps in 1 tap.

## 4. Final Reviewed Example Outcome (`النتيجة النهائية الجاهزة للتنفيذ`)

- Courier RTO rate on shipped COD parcels dropped from `29%` to **`11.8%`**, saving over **`145,000 EGP / month`** in wasted round-trip shipping fees.

## 5. What Can Go Wrong & Specific Correction / Fallback (`حالة الفشل المحتملة وخطة الإنقاذ والبديل`)

- **Common Failure Mode (`ما الذي قد يسير بشكل خاطئ؟`)**:
  A store holds an Apple Pay / Mada / InstaPay prepaid order in the `Awaiting_COD_Confirmation` queue by mistake because the webhook didn't check `financial_status != 'paid'`; the paying customer gets angry asking why their paid order hasn't shipped.
- **Specific Correction & Non-AI / Platform Fallback (`الإصلاح المحدد والبديل الآمن`)**:
  Enforce the **Strict Entry Filter**: `IF order.financial_status == 'paid' THEN SHIP_IMMEDIATELY`. Only route orders where `payment_method == 'cod' AND financial_status == 'pending'` into the COD Confirmation Gate.
