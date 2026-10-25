# Platform-Native Arabic Social Copy Matrix Prompt (X, LinkedIn, Instagram, TikTok & Snapchat)
## <span dir="rtl">قالب هندسة المحتوى العربي المخصص لكل منصة تواصل اجتماعي (إكس، لينكدإن، إنستغرام، تيك توك، وسناب شات)</span>

> **Asset ID**: `FW-024` (`AMP-122`) | **Artifact Type**: `PROMPT_TEMPLATE` | **Channel**: Social Media Marketing | **Markets**: Egypt & GCC (`KSA, UAE, Kuwait, Qatar, Bahrain, Oman`) | **Version**: `1.2` (`Reviewed 2026-10-25`)

**What You Can Do With This (`ماذا يمكنك أن تنجز بهذه الأداة؟`)**:
- **EN**: Transform a single campaign announcement into 5 platform-native Arabic/bilingual assets—respecting KSA X brevity, GCC/Egypt LinkedIn executive tone, Instagram Carousel saves, and TikTok/Snapchat spoken hooks—instead of cross-posting one stiff MSA paragraph.
- **AR**: <span dir="rtl">تحويل فكرة أو إعلان واحد إلى 5 مخرجات عربية وثنائية اللغة مصممة خصيصاً لطبيعة كل منصة (إكس، لينكدإن، إنستغرام، تيك توك، سناب شات) بدلاً من نسخ فقرة فصحى جافة واحدة وتعميمها.</span>

## 1. Use It When & Required Inputs (`متى تستخدمها وما المدخلات المطلوبة؟`)

- **Use It When (EN)**: Use when drafting multi-platform social campaigns for product launches, seasonal offers, or thought leadership in KSA, UAE, or Egypt.
- **متى تستخدمها (AR)**: <span dir="rtl">يُستخدم عند كتابة حملات التواصل الاجتماعي متعددة المنصات لإطلاق المنتجات أو العروض الموسمية أو محتوى القيادة الفكرية في السعودية والإمارات ومصر.</span>
- **When NOT to Use It (EN)**: Do not use identical hashtag blocks (`#تسويق #نجاح #الرياض...`) across X, LinkedIn, and Snapchat—Snapchat Spotlights/Stories and X threads are penalized by hashtag stuffing.
- **متى لا تستخدمها (AR)**: <span dir="rtl">لا تقم بنسخ كتلة وسوم (`Hashtags`) واحدة ولصقها في إكس ولينكدإن وسناب شات؛ فحشو الوسوم يضر بالوصول في إكس ولا يناسب قصص سناب شات.</span>

### Exact Inputs to Prepare (`المدخلات المطلوب تجهيزها قبل البدء`)
- Core Offer / Insight Summary (Product, Price in SAR/AED/EGP, Key Proof Point, Landing Page URL)
- Target Market & Dialect Track (`Saudi Khaleeji`, `UAE Bilingual`, or `Egyptian Ammiya`)
- Visual Asset Availability (`5-slide Carousel`, `6s Snap video`, `30s TikTok/Reel`, `Text Thread`)

## 2. The Working `PROMPT_TEMPLATE` (`الأداة الكاملة الجاهزة للنسخ والتطبيق الفوري`)

### Copy-Ready Multi-Platform Native Arabic Social Prompt

```xml
<system_role>
You are a Head of Social Creative for MENA (Riyadh, Dubai, Cairo).
STRICT RULE: Never output one generic Modern Standard Arabic (MSA) caption for all platforms, and NEVER use banned AI clichés ("في عالم يتسارع فيه...", "هل تبحث عن...", "لا شك أن...").
</system_role>

<campaign_brief>
- Core Offer / Topic: {{OFFER_OR_TOPIC}}
- Target Country & Dialect: {{COUNTRY_DIALECT: KSA (White Saudi Khaleeji) | UAE (Gulf Arabic + Executive English) | Egypt (Natural Cairene Ammiya)}}
- Key Proof / Price / CTA: {{PROOF_AND_CTA}}
</campaign_brief>

<platform_mechanics_contract>
Generate 5 distinct, platform-native versions:
1. **X (Twitter — KSA/GCC Pulse)**:
   - Max 220 characters for the hook post (punchy conversational Khaleeji or crisp white Arabic, max 1–2 relevant hashtags or 0 hashtags, direct question or sharp data point).
2. **LinkedIn (UAE / KSA / Egypt Executive B2B & Brand)**:
   - Opening 2-line pattern interrupt (before "See more / عرض المزيد"), concrete operational numbers, clean bullet structure, bilingual executive summary if targeting UAE/GCC, max 3 hashtags at the very bottom.
3. **Instagram (Carousel Slide Plan + Caption)**:
   - Slide-by-slide headline copy (5 slides designed to trigger `Save / حفظ` and `Share`), plus a concise caption where the first 90 characters carry the hook and CTA (`الرابط في البايو` or automated DM keyword trigger).
4. **TikTok / IG Reels Spoken Script (`15–25s`)**:
   - Spoken local dialect (`<= 10 words per breath`), visual action in Second 0–2, on-screen burned-in Arabic caption (`<= 6 words per card`), and casual spoken CTA.
5. **Snapchat Story / Commercial (`5–6s` Gulf Format — `AMP-333`)**:
   - Second 1: Immediate spoken & visual hook (NO static logo opener).
   - Second 2–3: Product in hand + exact offer (`SAR/AED` price + Tabby/Tamara).
   - Second 4–6: Direct "ارفع الشاشة / اضغط للطلب الآن" swipe/tap CTA.
</platform_mechanics_contract>
```

## 3. Complete End-to-End Worked Example (`مثال تطبيقي متكامل من المدخلات حتى المراجعة البشرية والنتيجة النهائية`)

*(Illustrative scenario — original example for training, never represented as a verified client outcome)*

### Step A: Sample Brief / Input (`موجز المدخلات`)
- **Brand**: Saudi Home Coffee Equipment Brand launching a Portable Espresso Maker (`349 SAR` incl. VAT, 4 payments on Tabby).
- **Market**: Saudi Arabia (`White Saudi Khaleeji`).

### Step B: Initial Output (`المخرج الأولي`)
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

### Step C: Human Review & Edits (`التدقيق البشري والتعديلات`)
1. **Removed Hashtag Clutter on X**: Stripped generic hashtags (`#قهوة #الرياض #تسوق`) from the X post so it reads like an authentic creator post.
2. **Added Safe-Zone Note on Snap/TikTok**: Marked all on-screen text coordinates inside the central `1080x1350` safe zone (`AMP-338`).

### Step D: Final Reviewed Example Outcome (`النتيجة النهائية المعتمدة`)
- 5 channel-native assets approved and scheduled across X, LinkedIn, Instagram, TikTok, and Snapchat without a single duplicated paragraph.

## 4. What Can Go Wrong & How to Fix It (`الأخطاء الشائعة وخطة الإنقاذ`)

- **Failure Case (`المشكلة المحتملة`)**: A social manager takes a 250-word formal LinkedIn post and pastes it verbatim as a TikTok video description and X post; X truncates it awkwardly and TikTok viewers scroll past in 0.8 seconds.
- **Correction & Fallback (`الحل الإجرائي والبديل الآمن`)**: Enforce the Platform Mechanics Contract: never schedule a cross-network post unless the format (character count, hook second, dialect register, and CTA mechanic) matches the destination platform.

## 5. Model & Platform Capability Matrix (`مصفوفة قدرات النماذج والمنصات — 2026-10-25`)

| Platform / Model | Status | Official Documentation | MENA Operational Constraint | Fallback |
| :--- | :--- | :--- | :--- | :--- |
| **Anthropic Claude 3.7/4 Sonnet & OpenAI GPT-4o Multi-Slot Prompting** | `supported` | [Official Docs](https://platform.claude.com/docs/en/build-with-claude/prompt-engineering/claude-prompting-best-practices) (`2026-10-25`) | XML-tagged role and constraint blocks reliably produce distinct register and length outputs per social platform in a single generation pass. | If a smaller model blends registers across slots, generate each platform in a separate prompt call. |

## 6. How to Measure Success (`خطة القياس والضوابط`)

- **Primary Metric**: Platform-native engagement metrics: Saves/Shares Rate on Instagram, 2-Second View Rate (`Hook Rate`) on TikTok/Snap, and Link CTR on X/LinkedIn.
- **Baseline**: Prior 30-day cross-posted MSA caption benchmarks.
- **Observation Window**: 14–28 days.
- **Interpretation Boundary**: Platform-native formatting removes structural friction, while visual quality and offer attractiveness drive conversions.

## 7. Primary Sources & Evidence Boundaries (`المصادر الموثقة وحدود الأدلة`)

- [Prompting best practices - Claude Platform Docs](https://platform.claude.com/docs/en/build-with-claude/prompt-engineering/claude-prompting-best-practices) — *Anthropic* (Published `2026-08-15`, Accessed `2026-10-25`): Recommends XML tag structuring, explicit role/audience context, few-shot examples, and verification criteria to avoid generic outputs.
- [Snapchat Ads Guide for Online Stores in Saudi Arabia and the Gulf](https://esafqa.com/en/blog/snapchat-ads-guide-saudi-gulf/) — *Esafqa* (Published `2026-10-09`, Accessed `2026-10-25`): Details Snapchat's official creative rules for Gulf stores: 9:16 native shoot, hero message in second 1, brand before second 2 (no static logo opening), 5-6s duration with offer in seconds 2-3, natural Saudi/Gulf dialect + captions, and zero recycled TikTok/Reels watermarks.
