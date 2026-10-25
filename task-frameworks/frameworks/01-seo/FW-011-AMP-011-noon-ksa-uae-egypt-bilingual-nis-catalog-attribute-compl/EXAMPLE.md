# End-to-End Worked Example & Failure Recovery — `FW-011` (`AMP-011`)

- **Framework**: Noon KSA, UAE & Egypt Bilingual NIS Catalog & Attribute Completeness Playbook
- **العنوان بالعربية**: دليل التشغيل الثنائي اللغة لكتالوجات نون (`Noon KSA / UAE / Egypt`) لضمان الظهور في الواجهة العربية
- **Selected Artifact Type**: `PLAYBOOK`
- **Disclaimer**: *All scenarios, brand names, SKU codes, and metrics below are original, realistic illustrative examples for MENA practitioner training and are never represented as verified client outcomes.*

## 1. Realistic Sample Brief / Input (`المدخلات وموجز الحالة العملية`)

- **SKU**: Digital Air Fryer 6.5L 1800W Black (Uploaded to Noon KSA with English fields only).
- **Problem**: Zero impressions from Arabic-browsing Noon shoppers in Riyadh and Dammam because `product_title_ar` and `description_ar` were left blank.

## 2. Initial Generated / Completed Output (`المخرج الأولي عند تطبيق الأداة`)

```json
{
  "partner_sku": "AF-65L-BLK",
  "product_title_en": "NutriCook Digital Air Fryer XL 6.5L 1800W with 10 Presets - Black",
  "product_title_ar": "نيوتري كوك قلاية هوائية ديجيتال بحجم عائلي 6.5 لتر 1800 واط بـ 10 برامج - أسود",
  "feature_bullet_1_ar": "سعة عائلية كبيرة 6.5 لتر تكفي لتحضير دجاجة كاملة أو 1.5 كجم من البطاطس دفعة واحدة.",
  "feature_bullet_2_ar": "قدرة 1800 واط مع تقنية تدوير الهواء الساخن 360 درجة لقرمشة مثالية بأقل نسبة دهون.",
  "feature_bullet_3_ar": "شاشة لمس رقمية ذكية تضم 10 برامج طهي مسبقة الإعداد (بطاطس، دجاج، لحم، سمك، مخبوزات).",
  "feature_bullet_4_ar": "سلة طهي غير لاصقة خالية من PFOA قابلة للفك والغسل في غسالة الأطباق بسهولة.",
  "feature_bullet_5_ar": "ضمان رسمي لمدة سنتين في المملكة العربية السعودية، يعمل على كهرباء 220-240 فولت 50/60 هرتز."
}
```

## 3. Human Review & Localization/Technical Edits (`المراجعة البشرية والتعديلات الرقابية والتقنية`)

1. **Saudi Electrical Standard Check**: Verified that Bullet 5 explicitly states `220-240 فولت 50/60 هرتز` and SASO/official 2-year KSA warranty, which is a top conversion driver on Noon KSA.
2. **Synonym Coverage**: Added `(اير فراير / Air Fryer)` inside `description_ar` so shoppers typing `اير فراير` in Arabic script match the listing.

## 4. Final Reviewed Example Outcome (`النتيجة النهائية الجاهزة للتنفيذ`)

- Listing published on both `noon.com/saudi-en/` and `noon.com/saudi-ar/` with 100% attribute completeness and active Arabic category filter indexing.

## 5. What Can Go Wrong & Specific Correction / Fallback (`حالة الفشل المحتملة وخطة الإنقاذ والبديل`)

- **Common Failure Mode (`ما الذي قد يسير بشكل خاطئ؟`)**:
  A catalog manager uploads machine-translated Arabic values into Noon's controlled picklist columns (e.g., typing `'أسود مطفي'` instead of selecting Noon's exact picklist value `'أسود'`), causing the NIS batch upload to fail validation.
- **Specific Correction & Non-AI / Platform Fallback (`الإصلاح المحدد والبديل الآمن`)**:
  Map controlled attribute columns (`colour_name_ar`, `brand_ar`, `department`) strictly against the `Valid Values` tab of the Noon NIS Excel template, using AI generation only for free-text fields (`title`, `bullets`, `description`).
