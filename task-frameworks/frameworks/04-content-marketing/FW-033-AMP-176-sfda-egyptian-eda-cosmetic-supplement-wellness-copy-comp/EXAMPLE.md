# End-to-End Worked Example & Failure Recovery — `FW-033` (`AMP-176`)

- **Framework**: Beauty, Supplement & Wellness Claims Review Checklist
- **العنوان بالعربية**: قائمة مراجعة ادعاءات منتجات الجمال والمكملات والعافية
- **Selected Artifact Type**: `CHECKLIST`
- **Disclaimer**: *All scenarios, brand names, SKU codes, and metrics below are original, realistic illustrative examples for MENA practitioner training and are never represented as verified client outcomes.*

## 1. Realistic Sample Brief / Input (`المدخلات وموجز الحالة العملية`)

- **Product**: Rosemary & Caffeine Hair Serum (`Cosmetic Notification in SFDA eCosma & Egypt EDA`).
- **Draft AI Copy**: `"سيروم الروزماري الطبي المعجزة! يعالج الصلع الوراثي وينبت الشعر من جديد خلال 14 يوماً، ويقضي نهائياً على التهابات وثعلبة فروة الرأس. معتمد طبياً من هيئة الغذاء والدواء!"`

## 2. Initial Generated / Completed Output (`المخرج الأولي عند تطبيق الأداة`)

- **`scan_sfda_eda_claims()` Result**:
  - `compliant`: `False` (`BLOCK`)
  - `flagged_therapeutic_terms`: `['يعالج', 'الصلع', 'ينبت الشعر', 'يقضي نهائياً', 'معتمد طبياً']`

## 3. Human Review & Localization/Technical Edits (`المراجعة البشرية والتعديلات الرقابية والتقنية`)

1. **Replaced All 5 Therapeutic Claims**: Rewrote using surface cosmetic conditioning and appearance verbs permitted for notified cosmetics.
2. **Corrected SFDA Terminology**: Removed `"معتمد طبياً"` and kept accurate notification reference in the product specification table.

## 4. Final Reviewed Example Outcome (`النتيجة النهائية الجاهزة للتنفيذ`)

- **Compliant SFDA / EDA Product Copy**:
  `"سيروم العناية بالشعر بخلاصة إكليل الجبل (الروزماري) والكافيين. تركيبة خفيفة تغذي فروة الرأس وترطب خصلات الشعر الجافة لتمنحكِ مظهراً أكثر كثافة ولمعاناً وحيوية مع الاستخدام المنتظم."`

## 5. What Can Go Wrong & Specific Correction / Fallback (`حالة الفشل المحتملة وخطة الإنقاذ والبديل`)

- **Common Failure Mode (`ما الذي قد يسير بشكل خاطئ؟`)**:
  An e-commerce store uses an AI review-summary widget that highlights a customer review saying `'هذا الكريم عالج الأكزيما عندي نهائياً'` inside a paid Meta/Snapchat ad headline; SFDA treats promotional use of third-party therapeutic claims in ads as an advertiser violation.
- **Specific Correction & Non-AI / Platform Fallback (`الإصلاح المحدد والبديل الآمن`)**:
  Apply the `FORBIDDEN_THERAPEUTIC_RE` filter to both brand-authored copy AND any user-generated review or creator script (`AMP-286`) used in marketing.
