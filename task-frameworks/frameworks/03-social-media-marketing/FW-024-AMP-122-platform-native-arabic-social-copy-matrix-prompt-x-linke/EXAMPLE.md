# End-to-End Worked Example & Failure Recovery — `FW-024` (`AMP-122`)

- **Framework**: Platform-Native Arabic Social Copy Matrix Prompt (X, LinkedIn, Instagram, TikTok & Snapchat)
- **العنوان بالعربية**: قالب هندسة المحتوى العربي المخصص لكل منصة تواصل اجتماعي (إكس، لينكدإن، إنستغرام، تيك توك، وسناب شات)
- **Selected Artifact Type**: `PROMPT_TEMPLATE`
- **Disclaimer**: *All scenarios, brand names, SKU codes, and metrics below are original, realistic illustrative examples for MENA practitioner training and are never represented as verified client outcomes.*

## 1. Realistic Sample Brief / Input (`المدخلات وموجز الحالة العملية`)

- **Brand**: Saudi Home Coffee Equipment Brand launching a Portable Espresso Maker (`349 SAR` incl. VAT, 4 payments on Tabby).
- **Market**: Saudi Arabia (`White Saudi Khaleeji`).

## 2. Initial Generated / Completed Output (`المخرج الأولي عند تطبيق الأداة`)

1. **X (Twitter KSA — 148 chars)**:
   `قهوتك المختصة صارت معك بالبر، بالمكتب، وحتى بالطيارة ☕️بدون كهرباء وبضغط 18 بار حقيقي. جربناها بالكشتة وهذي النتيجة 👇 (متوفرة بـ 349 ر.س مع تابي)`
2. **LinkedIn (KSA/GCC Retail Insight)**:
   `ليش 68% من محبي القهوة المختصة في السعودية يشتكون من قهوة السفر؟ ... [5-bullet product engineering breakdown]`
3. **Instagram 5-Slide Carousel**:
   - Slide 1: `إسبريسو بكريما ثقيلة.. بدون فيش كهرباء؟`
   - Slide 2: `المشكلة في مكائن السفر التقليدية (ضغط ضعيف وحرارة باردة)`
   - Slide 3: `الحل: ضغط 18 بار + تسخين ذاتي في 3 دقائق`
   - Slide 4: `تشتغل بالكبسولات أو البن المطحون`
   - Slide 5: `اطلبها الحين بـ 349 ر.س وقسمها على 4 دفعات مع تابي وتمارا`
4. **Snapchat 6-Second Script**:
   - `[0:00-0:01]` (Close-up rich espresso crema pouring in desert camp): `"إسبريسو مختص بنص البر بدون كهرباء!"`
   - `[0:01-0:03]` (Show portable machine + price badge): `"ضغط 18 بار بـ 349 ريال بس ومقسمة على 4 دفعات تابي."`
   - `[0:04-0:06]` (Tap CTA): `"اضغط تحت واطلبها قبل تخلص الدفعة."`

## 3. Human Review & Localization/Technical Edits (`المراجعة البشرية والتعديلات الرقابية والتقنية`)

1. **Removed Hashtag Clutter on X**: Stripped generic hashtags (`#قهوة #الرياض #تسوق`) from the X post so it reads like an authentic creator post.
2. **Added Safe-Zone Note on Snap/TikTok**: Marked all on-screen text coordinates inside the central `1080x1350` safe zone (`AMP-338`).

## 4. Final Reviewed Example Outcome (`النتيجة النهائية الجاهزة للتنفيذ`)

- 5 channel-native assets approved and scheduled across X, LinkedIn, Instagram, TikTok, and Snapchat without a single duplicated paragraph.

## 5. What Can Go Wrong & Specific Correction / Fallback (`حالة الفشل المحتملة وخطة الإنقاذ والبديل`)

- **Common Failure Mode (`ما الذي قد يسير بشكل خاطئ؟`)**:
  A social manager takes a 250-word formal LinkedIn post and pastes it verbatim as a TikTok video description and X post; X truncates it awkwardly and TikTok viewers scroll past in 0.8 seconds.
- **Specific Correction & Non-AI / Platform Fallback (`الإصلاح المحدد والبديل الآمن`)**:
  Enforce the Platform Mechanics Contract: never schedule a cross-network post unless the format (character count, hook second, dialect register, and CTA mechanic) matches the destination platform.
