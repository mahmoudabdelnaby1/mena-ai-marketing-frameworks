# End-to-End Worked Example & Failure Recovery — `FW-039` (`AMP-182`)

- **Framework**: Arabic Grammatical Gender-Targeting & Dual/Plural Morphology Prompt Template
- **العنوان بالعربية**: قالب ضبط المخاطب النحوي والتأنيث والتذكير في النصوص التسويقية العربية (تجاوز حيادية الضمير الإنجليزي `You`)
- **Selected Artifact Type**: `PROMPT_TEMPLATE`
- **Disclaimer**: *All scenarios, brand names, SKU codes, and metrics below are original, realistic illustrative examples for MENA practitioner training and are never represented as verified client outcomes.*

## 1. Realistic Sample Brief / Input (`المدخلات وموجز الحالة العملية`)

- **Brand**: Riyadh & Cairo Luxury Abaya & Modest Eveningwear Brand (`100% Female Customer Base`).
- **Broken Masculine AI Push Notification**: `"أهلاً بك! لا تفوت فرصة الحصول على عبايتك المفضلة بخصم 20%، اختر مقاسك الآن وادفع عبر تابي!"` *(Addresses a woman buying an abaya as a man: `لا تفوت / اختر مقاسك / ادفع`!)*

## 2. Initial Generated / Completed Output (`المخرج الأولي عند تطبيق الأداة`)

- **Corrected `FEMININE_SINGULAR_ANTI` Outputs**:
  - **Saudi Khaleeji Version**: `"حياكِ الله! لا تفوتين فرصة اقتناء عبايتك المفضلة بخصم 20% ✨ اختاري مقاسك الحين وقسّميها على 4 دفعات مع تابي."`
  - **Egyptian Ammiya Version**: `"أهلاً بيكي! متفوتيش فرصة اختيار عبايتك المفضلة بخصم 20% ✨ اختاري مقاسك دلوقتي وقسطيها براحتك."`
  - **White MSA Version**: `"أهلاً بكِ! لا تفوّتي فرصة التألق بعبايتكِ المفضلة بخصم 20% — اختاري مقاسكِ الآن بالتقسيط المريح."`

## 3. Human Review & Localization/Technical Edits (`المراجعة البشرية والتعديلات الرقابية والتقنية`)

1. **Verified Saudi Present-Tense `-ين` vs Imperative `-ي`**: Checked that negative present (`لا تفوتين` in Khaleeji vs `لا تفوّتي` in MSA and `متفوتيش` in Egyptian) matches native spoken morphology.
2. **Updated App UI Strings**: Audited checkout and push templates (`اشترِي الآن`, `أضيفي للسلة`) across the women's store theme.

## 4. Final Reviewed Example Outcome (`النتيجة النهائية الجاهزة للتنفيذ`)

- All push notifications, cart buttons, and email flows inflected in 100% natural feminine singular across KSA and Egypt.

## 5. What Can Go Wrong & Specific Correction / Fallback (`حالة الفشل المحتملة وخطة الإنقاذ والبديل`)

- **Common Failure Mode (`ما الذي قد يسير بشكل خاطئ؟`)**:
  A unisex fragrance store sends a single push notification with `'اخترِ/اختاري عطرك/عطركِ المفضل الآن يا عزيزي/عزيزتي'` full of slashes, making the notification look like a government tax form and clipping the preview text.
- **Specific Correction & Non-AI / Platform Fallback (`الإصلاح المحدد والبديل الآمن`)**:
  For unsegmented unisex lists, always use the **`GENDER_INCLUSIVE_NO_SLASHES`** rule (e.g., `'اكتشفوا مجموعتنا الجديدة من العطور الفاخرة — تسوقوا الآن'` or noun-led `'عطر يناسب كل الأوقات — للطلب الآن'`).
