# End-to-End Worked Example & Failure Recovery — `FW-035` (`AMP-178`)

- **Framework**: English-to-Arabic Idiom, Metaphor & Polysemy Transcreation Checklist
- **العنوان بالعربية**: قائمة فحص التعريب الإبداعي (`Transcreation`) ومنع الترجمة الحرفية للتعبيرات الاصطلاحية والمشتركات اللفظية
- **Selected Artifact Type**: `CHECKLIST`
- **Disclaimer**: *All scenarios, brand names, SKU codes, and metrics below are original, realistic illustrative examples for MENA practitioner training and are never represented as verified client outcomes.*

## 1. Realistic Sample Brief / Input (`المدخلات وموجز الحالة العملية`)

- **Source English Hero Copy (Global SaaS + D2C Launch)**:
  `"Upgrade your workflow without breaking the bank. Our new platform is a game-changer that tackles your biggest pain points with no strings attached. Free trial—book a demo today!"`

## 2. Initial Generated / Completed Output (`المخرج الأولي عند تطبيق الأداة`)

- **Literal AI Draft (`REJECTED`)**:
  `"قم بترقية سير عملك بدون كسر البنك. منصتنا الجديدة هي مغير اللعبة الذي يعالج أكبر نقاط الألم لديك بدون خيوط مرفقة. تجربة حرة — كتاب عرض اليوم!"`

## 3. Human Review & Localization/Technical Edits (`المراجعة البشرية والتعديلات الرقابية والتقنية`)

1. **Replaced All 5 Calques & Polysemy Errors**: Converted `"بدون كسر البنك"`, `"مغير اللعبة"`, `"نقاط الألم"`, `"بدون خيوط مرفقة"`, and `"كتاب عرض"` into natural executive Arabic.
2. **Created Both GCC White MSA and Egyptian Business Versions**.

## 4. Final Reviewed Example Outcome (`النتيجة النهائية الجاهزة للتنفيذ`)

- **Approved Pan-Arab / GCC Executive Copy**:
  `"طوّر كفاءة أعمالك بتكلفة تناسب ميزانيتك. منصتنا الجديدة تمنح فريقك نقلة نوعية لحل أصعب التحديات التشغيلية دون أي التزامات مسبقة. جرّبها مجاناً واحجز عرضك التوضيحي اليوم!"`

## 5. What Can Go Wrong & Specific Correction / Fallback (`حالة الفشل المحتملة وخطة الإنقاذ والبديل`)

- **Common Failure Mode (`ما الذي قد يسير بشكل خاطئ؟`)**:
  An app localization pipeline sends a JSON file of raw button labels (`{"cta_1": "Book", "tag_2": "Light", "status_3": "Clear"}`) to an LLM without screen context; the Arabic app ships with `'كتاب'` on the hotel booking button and `'ضوء'` on the low-calorie menu filter.
- **Specific Correction & Non-AI / Platform Fallback (`الإصلاح المحدد والبديل الآمن`)**:
  Always pass `{key, english_text, screen_location, part_of_speech_and_meaning}` in UI localization payloads.
