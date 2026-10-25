# End-to-End Worked Example & Failure Recovery — `FW-079` (`AMP-392`)

- **Framework**: Authentic Verified-Buyer Review & Social Proof Governance Checklist (Eliminating Fake AI Review Widgets)
- **العنوان بالعربية**: قائمة فحص حوكمة التقييمات وإثباتات الثقة الاجتماعية (`Social Proof` — منع ودجات التقييمات الوهمية المولدة بالذكاء الاصطناعي)
- **Selected Artifact Type**: `CHECKLIST`
- **Disclaimer**: *All scenarios, brand names, SKU codes, and metrics below are original, realistic illustrative examples for MENA practitioner training and are never represented as verified client outcomes.*

## 1. Realistic Sample Brief / Input (`المدخلات وموجز الحالة العملية`)

- **Store**: Jeddah & Cairo D2C Home Appliance Store.
- **Problem**: Agency had installed an AI review generator that posted 120 reviews in formal translated Arabic (`"هذا الخلاط يغير قواعد اللعبة في مطبخي - جون سميث / الرياض"`) and a popup firing every 8 seconds. Bounce rate was `76%` and comments on Instagram ads called the site a scam.

## 2. Initial Generated / Completed Output (`المخرج الأولي عند تطبيق الأداة`)

- **Executed Authenticity Overhaul**:
  1. Deleted all 120 unverified/translated reviews and uninstalled the fake toast popup app.
  2. Added the store's official **Saudi Business Center Verification Badge (`موثق في المركز السعودي للأعمال`)** and clear 2-year warranty card below the Add-to-Cart button.
  3. Launched the `T+3 Days Post-Delivery` WhatsApp review request flow for real delivered orders.

## 3. Human Review & Localization/Technical Edits (`المراجعة البشرية والتعديلات الرقابية والتقنية`)

1. **Kept Genuine 4-Star Constructive Reviews Live**: Instructed moderation staff NOT to hide honest 4-star reviews (e.g., `"المنتج ممتاز وصوته هادي بس الكرتون وصل متأخر يوم"`), because a `4.7 / 5.0` rating with real Saudi/Egyptian dialect phrasing converts significantly higher than a suspicious `5.00 / 5.00` wall of AI praise!
2. **Validated `aggregateRating` Schema (`AMP-007`)**: Connected the verified review count (`142 real reviews, 4.8 average`) to the `Product` JSON-LD schema.

## 4. Final Reviewed Example Outcome (`النتيجة النهائية الجاهزة للتنفيذ`)

- `142` genuine, order-verified customer reviews (with real mobile photos in Saudi & Egyptian homes) collected in 21 days; PDP conversion rate increased by `+29%`.

## 5. What Can Go Wrong & Specific Correction / Fallback (`حالة الفشل المحتملة وخطة الإنقاذ والبديل`)

- **Common Failure Mode (`ما الذي قد يسير بشكل خاطئ؟`)**:
  An automated review email fires `5 days after Order Placed`; because a shipment to Upper Egypt or Northern KSA took 6 days to arrive, the customer receives `'كيف كان المنتج؟ قيمه الآن!'` before receiving the parcel, prompting an angry 1-star review saying `'الطلب لم يصلني أصلاً!'`.
- **Specific Correction & Non-AI / Platform Fallback (`الإصلاح المحدد والبديل الآمن`)**:
  Trigger review requests **strictly off the Courier `DELIVERED` event (`+48 to 72 hours`)**, never off `Order Placed + X days`!
