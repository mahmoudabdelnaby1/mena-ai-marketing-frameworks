# End-to-End Worked Example & Failure Recovery — `FW-074` (`AMP-387`)

- **Framework**: KSA & UAE Above-the-Fold Tabby & Tamara BNPL Price-Split Widget Checklist
- **العنوان بالعربية**: قائمة فحص وضع شارات تقسيط «تابي» و«تمارا» (`Tabby & Tamara`) بجوار السعر مباشرة أعلى طية صفحة المنتج في السعودية والإمارات
- **Selected Artifact Type**: `CHECKLIST`
- **Disclaimer**: *All scenarios, brand names, SKU codes, and metrics below are original, realistic illustrative examples for MENA practitioner training and are never represented as verified client outcomes.*

## 1. Realistic Sample Brief / Input (`المدخلات وموجز الحالة العملية`)

- **Store**: Dubai & Riyadh Luxury Eyewear & Watches Store on Shopify (`AOV: 680 AED / 700 SAR`).
- **Problem**: Tabby and Tamara were active at the final checkout payment step, but on the Product Detail Page (PDP), the AI-designed landing page template only showed `700 SAR` at the top and buried small greyscale payment icons at the very bottom footer (`Y: 4200px`).

## 2. Initial Generated / Completed Output (`المخرج الأولي عند تطبيق الأداة`)

- **PDP & Cart Drawer Fix**:
  1. Placed the dynamic RTL Tabby & Tamara 4-payment box (`"أو قسّمها على 4 دفعات بقيمة 175.00 ر.س بدون فوائد"`) `8px` directly beneath the `700.00 ر.س` price tag above the fold.
  2. Added the interactive modal explaining `"ادفع 25% اليوم (175 ر.س) والباقي على 3 أشهر بدون أي رسوم"`.

## 3. Human Review & Localization/Technical Edits (`المراجعة البشرية والتعديلات الرقابية والتقنية`)

1. **Sharia-Compliance Reassurance**: Included the official Tabby/Tamara note (`"متوافق مع أحكام الشريعة الإسلامية — بدون فوائد"`) inside the info tooltip, which resolves the #1 hesitation among Saudi shoppers.
2. **Checked Salla Native Toggle**: For the brand's Salla KSA sub-store, verified that `إعدادات الدفع -> إظهار بنر تابي وتمارا في صفحة المنتج` was toggled ON and styled above the fold.

## 4. Final Reviewed Example Outcome (`النتيجة النهائية الجاهزة للتنفيذ`)

- Above-the-fold dynamic BNPL price-split widget live across 100% of PDPs and the slide-out cart drawer in KSA and UAE.

## 5. What Can Go Wrong & Specific Correction / Fallback (`حالة الفشل المحتملة وخطة الإنقاذ والبديل`)

- **Common Failure Mode (`ما الذي قد يسير بشكل خاطئ؟`)**:
  A developer hard-codes `/ 4` integer division in Liquid (`divided_by: 4` instead of `divided_by: 4.0`), causing rounding truncation on odd prices, or displays the Tabby widget on a `25 SAR` accessory that is below the merchant's minimum BNPL cart threshold (`e.g., 100 SAR`), leading to a declined option at checkout.
- **Specific Correction & Non-AI / Platform Fallback (`الإصلاح المحدد والبديل الآمن`)**:
  Wrap the BNPL widget in an eligibility threshold check (`{% if product.price >= 10000 %}` in cents/halalas) and for items under `100 SAR`, display `"أضف منتجات بقيمة [100 - price] ر.س لتفعيل التقسيط على 4 دفعات عبر تابي وتمارا"`!
