# End-to-End Worked Example & Failure Recovery — `FW-041` (`AMP-184`)

- **Framework**: Arabic AI Rhetorical Cliché Scrubber & Native Hook Replacement Checklist
- **العنوان بالعربية**: قائمة فحص وتطهير المحتوى العربي من الكليشيهات المترجمة للذكاء الاصطناعي (`في عالم يتسارع فيه...` / `هل تبحث عن...`)
- **Selected Artifact Type**: `CHECKLIST`
- **Disclaimer**: *All scenarios, brand names, SKU codes, and metrics below are original, realistic illustrative examples for MENA practitioner training and are never represented as verified client outcomes.*

## 1. Realistic Sample Brief / Input (`المدخلات وموجز الحالة العملية`)

- **Draft AI Blog Intro (Saudi E-Commerce SEO Guide)**:
  `"في عالمنا الرقمي المتسارع اليوم، تلعب التجارة الإلكترونية دوراً محورياً في المملكة العربية السعودية. هل تبحث عن طريقة لزيادة مبيعات متجرك على سلة؟ إذا كنت تبحث عن ذلك، فقد وصلت إلى المكان الصحيح! مما لا شك فيه أن تحسين محركات البحث يُعد بمثابة حجر الزاوية لنجاحك."` *(68 words of pure zero-information AI filler!)*

## 2. Initial Generated / Completed Output (`المخرج الأولي عند تطبيق الأداة`)

- **`lint_arabic_ai_cliches()` Output**:
  - `clean`: `False` (`6` banned clichés detected in 4 sentences: `في عالمنا الرقمي`, `هل تبحث عن`, `وصلت إلى المكان الصحيح`, `مما لا شك فيه`, `يُعد بمثابة`, `حجر الزاوية`).

## 3. Human Review & Localization/Technical Edits (`المراجعة البشرية والتعديلات الرقابية والتقنية`)

1. **Deleted All 68 Words of Throat-Clearing**: Replaced the entire first paragraph with the concrete empirical finding from the VOCTOS Oct 2026 Salla/Zid audit.
2. **Applied Active Verbs**: Replaced `"يلعب دوراً محورياً"` and `"يُعد بمثابة"` with direct technical causes and fixes.

## 4. Final Reviewed Example Outcome (`النتيجة النهائية الجاهزة للتنفيذ`)

- **Rewritten High-Retention Intro (`34` words — 100% substance)**:
  `"أثبت فحص ميداني لـ 10 متاجر على منصة «سلة» في أكتوبر 2026 أن 60% من روابط المنتجات المدرجة في ملف sitemap.xml كانت معطوبة أو محوّلة، ولا يضم أي متجر منها حقل العلامة التجارية (brand) في بياناته المهيكلة. إليك طريقة إصلاح الخللين في 15 دقيقة:"`

## 5. What Can Go Wrong & Specific Correction / Fallback (`حالة الفشل المحتملة وخطة الإنقاذ والبديل`)

- **Common Failure Mode (`ما الذي قد يسير بشكل خاطئ؟`)**:
  An editor removes `'في عالم يتسارع فيه'` from Paragraph 1, but leaves `'تُعدّ بمثابة'` and `'ليس مجرد منتج بل هو أسلوب حياة'` repeated 9 times across the body headings.
- **Specific Correction & Non-AI / Platform Fallback (`الإصلاح المحدد والبديل الآمن`)**:
  Run `lint_arabic_ai_cliches()` across the **entire document body**, and enforce the rule: **Sentence 1 of the article must contain either a specific number, a named tool/platform, or a concrete user action**.
