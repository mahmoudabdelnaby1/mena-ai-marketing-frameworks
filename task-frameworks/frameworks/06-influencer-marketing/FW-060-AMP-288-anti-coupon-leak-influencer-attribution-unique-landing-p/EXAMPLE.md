# End-to-End Worked Example & Failure Recovery — `FW-060` (`AMP-288`)

- **Framework**: Anti-Coupon-Leak Influencer Attribution & Unique Landing-Page / Cart-Link Workflow
- **العنوان بالعربية**: مسار عمل قياس عائد المؤثرين ومنع تسرب أكواد الخصم الثابتة (`Promo Code Cannibalization`) لزيارات الدفع العضوية
- **Selected Artifact Type**: `OPERATING_FRAMEWORK`
- **Disclaimer**: *All scenarios, brand names, SKU codes, and metrics below are original, realistic illustrative examples for MENA practitioner training and are never represented as verified client outcomes.*

## 1. Realistic Sample Brief / Input (`المدخلات وموجز الحالة العملية`)

- **Store**: Saudi Footwear & Sportswear Store on Salla/Shopify.
- **Problem**: Paid Creator X a `15%` commission on `410` orders that used code `FAHAD15` over 30 days. Forensic GA4 + backend audit revealed only `95` orders (`23%`) occurred during the 72-hour story burst or carried `utm_medium=influencer`; the other `315` orders (`77%`) happened weeks later from shoppers who were already on the checkout page, opened Google to search `"كود خصم متجر ..."`, found `FAHAD15` on a coupon site, and pasted it!

## 2. Initial Generated / Completed Output (`المخرج الأولي عند تطبيق الأداة`)

- **Attribution Reconciliation**:
  - `TIER_A_VERIFIED_CREATOR_DRIVEN`: `68` orders (`100%` credit)
  - `TIER_B_VIEW_THROUGH_PROBABLE` (within 72h burst): `27` orders (`50%` credit)
  - `TIER_C_COUPON_SCRAPER_CANNIBALIZATION` (after 72h / coupon site referrer): `315` orders (`0%` creator credit; code rotated/expired after 72h!).

## 3. Human Review & Localization/Technical Edits (`المراجعة البشرية والتعديلات الرقابية والتقنية`)

1. **Updated Creator Contract Commission Clause**: Defined commission-eligible orders strictly as orders placed via the tracked link or using the burst code **within 72 hours of story publication**.
2. **Launched `/ar/offers` Branded Coupon Page**: Captured `"كود خصم [اسم المتجر]"` searchers with a `5%` first-order code instead of leaking `15%` creator codes.

## 4. Final Reviewed Example Outcome (`النتيجة النهائية الجاهزة للتنفيذ`)

- Stopped `77%` coupon-scraper commission overpayment and locked all creator codes to 72-hour burst windows with auto-applied UTM deep links.

## 5. What Can Go Wrong & Specific Correction / Fallback (`حالة الفشل المحتملة وخطة الإنقاذ والبديل`)

- **Common Failure Mode (`ما الذي قد يسير بشكل خاطئ؟`)**:
  A creator refuses to use a link sticker and only says the promo code verbally on Snapchat; because Snapchat viewers open Safari/Chrome manually and type the store name on Google, 100% of their legitimate orders arrive as `google / organic` in GA4.
- **Specific Correction & Non-AI / Platform Fallback (`الإصلاح المحدد والبديل الآمن`)**:
  That is exactly why `classify_influencer_order()` includes **`TIER_B_VIEW_THROUGH_PROBABLE`**: for verbal-only Snapchat/TikTok posts, measure the **72-hour incremental lift in branded organic + direct orders using the burst code** compared to the prior 7-day baseline, and immediately expire the code at Hour 72 so coupon sites cannot harvest it later.
