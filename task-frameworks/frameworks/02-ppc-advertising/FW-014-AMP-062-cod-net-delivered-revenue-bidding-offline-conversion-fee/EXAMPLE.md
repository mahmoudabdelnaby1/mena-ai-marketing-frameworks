# End-to-End Worked Example & Failure Recovery — `FW-014` (`AMP-062`)

- **Framework**: COD Net-Delivered Revenue Bidding & Offline Conversion Feedback Workflow (Egypt & KSA)
- **العنوان بالعربية**: مسار عمل تدريب خوارزميات الإعلانات على «طلبات الدفع عند الاستلام المسلّمة فعلياً» بدلاً من الطلبات الوهمية (مصر والسعودية)
- **Selected Artifact Type**: `OPERATING_FRAMEWORK`
- **Disclaimer**: *All scenarios, brand names, SKU codes, and metrics below are original, realistic illustrative examples for MENA practitioner training and are never represented as verified client outcomes.*

## 1. Realistic Sample Brief / Input (`المدخلات وموجز الحالة العملية`)

- **Store**: Cairo Footwear & Apparel Brand (`1,200 EGP` average order value).
- **Historical Data**: Prepaid (Card/InstaPay/valU) delivery rate = `95%`; Cairo/Giza COD delivery rate = `74%`; Upper Egypt/Delta unconfirmed COD delivery rate = `58%`.
- **Problem**: Platform-reported Meta ROAS looked like `4.8x`, but after `34%` blended COD refusals and double-way courier fees (`95 EGP` per returned parcel), actual bank-collected ROAS was `2.6x`.

## 2. Initial Generated / Completed Output (`المخرج الأولي عند تطبيق الأداة`)

- **Applied Layer 1 Value Multipliers**:
  - Order #101 (`1,200 EGP` via InstaPay): Sends `value: 1140.00 EGP` to Meta Pixel + CAPI.
  - Order #102 (`1,200 EGP` via COD in Nasr City, Cairo): Sends `value: 888.00 EGP`.
  - Order #103 (`1,200 EGP` via COD in High-Return Zone without landmark): Sends `value: 696.00 EGP`.
- **Applied Layer 2 Audience Hygiene**: Excluded `210` cancelled/refused COD orders from the 1% Purchaser Lookalike seed.

## 3. Human Review & Localization/Technical Edits (`المراجعة البشرية والتعديلات الرقابية والتقنية`)

1. **Accounting vs. Bidding Separation**: Kept raw `order_total` (`1,200 EGP`) in a custom parameter `gross_order_value` for finance reporting while passing the expected-delivered value in the standard `value` field used by Meta's tROAS bidder.
2. **Prepaid Incentive Pairing**: Added a `50 EGP` instant discount / free shipping badge for InstaPay & Card on the checkout page (`AMP-386`) to reinforce the bidding shift.

## 4. Final Reviewed Example Outcome (`النتيجة النهائية الجاهزة للتنفيذ`)

- Meta and Google Value-Bidding (`tROAS`) now optimize on risk-adjusted net delivered revenue (`value`) with daily Bosta/Aramex webhook sync updating Delivered Customer Lists.

## 5. What Can Go Wrong & Specific Correction / Fallback (`حالة الفشل المحتملة وخطة الإنقاذ والبديل`)

- **Common Failure Mode (`ما الذي قد يسير بشكل خاطئ؟`)**:
  A media buyer switches the primary campaign conversion event to 'Courier Delivered' (which happens 5–8 days after the click in remote governorates); because Meta's optimal learning signal relies heavily on conversions within 24–72 hours of click, ad sets get stuck in 'Learning Limited'.
- **Specific Correction & Non-AI / Platform Fallback (`الإصلاح المحدد والبديل الآمن`)**:
  Always keep the immediate checkout `Purchase` event (with risk-discounted `value`) or same-hour `WhatsApp_Confirmed_Order` as the primary optimization event, and use 5-day Courier Delivered webhooks for Value Adjustments and Seed Audience building.
