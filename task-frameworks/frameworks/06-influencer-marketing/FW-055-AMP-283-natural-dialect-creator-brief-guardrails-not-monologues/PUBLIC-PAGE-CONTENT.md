# Natural Dialect Creator Brief & 'Guardrails-Not-Monologues' Prompt Template (Anti-Corporate Press Release)
## <span dir="rtl">قالب موجز المؤثرين (`Creator Brief`) بنظام «النقاط الموجهة لا النص الفصيح المحفوظ» للحفاظ على عفوية الـ UGC</span>

> **Asset ID**: `FW-055` (`AMP-283`) | **Artifact Type**: `PROMPT_TEMPLATE` | **Channel**: Influencer Marketing | **Markets**: Egypt & GCC (`KSA, UAE, Kuwait, Qatar, Bahrain, Oman`) | **Version**: `1.2` (`Reviewed 2026-10-25`)

**What You Can Do With This (`ماذا يمكنك أن تنجز بهذه الأداة؟`)**:
- **EN**: Generate creator briefs that lock mandatory product facts, price, and statutory disclosures while letting Saudi, Emirati, and Egyptian creators speak in their own natural camera cadence instead of reading a stiff AI press release.
- **AR**: <span dir="rtl">توليد موجز إبداعي (`Creator Brief`) يثبّت الحقائق الإلزامية للمنتج والسعر والضوابط النظامية مع ترك مساحة للمؤثر السعودي أو الإماراتي أو المصري للتحدث بطريقته العفوية بدلاً من قراءة بيان صحفي فصيح يقتل التفاعل.</span>

## 1. Use It When & Required Inputs (`متى تستخدمها وما المدخلات المطلوبة؟`)

- **Use It When (EN)**: Use whenever briefing influencers or UGC creators for Snapchat Stories, TikTok videos, or Instagram Reels in KSA, UAE, or Egypt.
- **متى تستخدمها (AR)**: <span dir="rtl">تُستخدم عند إعداد موجز العمل (`Brief`) للمؤثرين وصناع محتوى `UGC` على سناب شات وتيك توك وإنستغرام في السعودية والإمارات ومصر.</span>
- **When NOT to Use It (EN)**: Never force a native dialect creator to read a word-for-word Modern Standard Arabic (MSA) paragraph on Snapchat or TikTok.
- **متى لا تستخدمها (AR)**: <span dir="rtl">لا تلزم صانع محتوى يتحدث باللهجة المحلية بقراءة نص مكتوب بالفصحى حرفياً أمام الكاميرا في سناب شات أو تيك توك.</span>

### Exact Inputs to Prepare (`المدخلات المطلوب تجهيزها قبل البدء`)
- Creator Profile & Native Dialect (`Saudi Najdi/Hijazi`, `Emirati`, `Egyptian Cairene`)
- 1 Hero Product Demonstration Action (what the creator must *show* visually in Seconds 0–3)
- Non-Negotiable Commercial Facts (Price in SAR/AED/EGP, Tabby/Tamara/InstaPay availability, Promo Code, `#إعلان` badge)
- Prohibited Claims List (`AMP-176` SFDA/EDA medical claims, `AMP-064` fake discounts)

## 2. The Working `PROMPT_TEMPLATE` (`الأداة الكاملة الجاهزة للنسخ والتطبيق الفوري`)

### Copy-Ready "Guardrails, Not Monologues" Creator Brief Prompt

```xml
<system_role>
You are a MENA Creator Partnerships Director specializing in high-converting Snapchat, TikTok, and Instagram Reels UGC in Saudi Arabia, UAE, and Egypt.
STRICT RULE: Do NOT write a stiff word-for-word Modern Standard Arabic monologue for the creator to memorize. Creators convert when they speak in their own natural cadence ("من قلبهم وبطريقتهم").
Instead, generate a structured **"Creator Freedom + Guardrail Brief"** containing:
1. Visual Action in Second 1 (Show, Don't Tell — no static logo intro!).
2. 3 Natural Spoken Hook Options in the creator's dialect (Creator picks 1 and adapts in their own words).
3. 3 Bullet Talking Points (Facts to weave in naturally—NOT a script to read off a teleprompter).
4. Mandatory Statutory & Brand Red Lines (What they MUST display and what they MUST NEVER say).
</system_role>

<campaign_inputs>
- Product & Core Demo Action: {{PRODUCT_AND_VISUAL_DEMO}}
- Creator Dialect & Platform: {{DIALECT_AND_PLATFORM: e.g., Saudi Khaleeji on Snapchat | Egyptian Ammiya on TikTok/IG}}
- Offer, Price & Payment Hook: {{PRICE_AND_PAYMENT: e.g., 249 SAR incl. VAT + Tabby/Tamara + Code SARA15}}
- Regulatory Red Lines: {{REGULATORY_RULES: #إعلان badge, Mawthooq #, zero medical/therapeutic claims}}
</campaign_inputs>
```

## 3. Complete End-to-End Worked Example (`مثال تطبيقي متكامل من المدخلات حتى المراجعة البشرية والنتيجة النهائية`)

*(Illustrative scenario — original example for training, never represented as a verified client outcome)*

### Step A: Sample Brief / Input (`موجز المدخلات`)
- **Product**: Cordless Steam Garment Iron (`مكواة بخار محمولة للسفر والعبايات`, `199 SAR` incl. VAT, Tabby available).
- **Platform**: Saudi Lifestyle Creator on Snapchat Stories (`3` consecutive snaps, `15–25s` total).
- **Bad Corporate AI Script (Rejected by Creator)**: `"مرحباً بكم متابعيني الأعزاء، في عالمنا المتسارع نحتاج جميعاً إلى مظهر أنيق. لذلك أقدم لكم اليوم مكواة البخار الفريدة التي تتميز بتقنية التسخين الفائق..."`

### Step B: Initial Output (`المخرج الأولي`)
### 📋 موجز صانع المحتوى (Creator Brief — بلهجتك وعفويتك المعتادة)

1. **المشهد البصري في أول ثانيتين (بدون مقدمات ترحيبية طويلة!)**:
   - ابدأي السنابة الأولى وأنتِ تفردين طرف عباية أو شماغ مجعد بضغطة بخار واحدة مباشرة قدام الكاميرا عشان المتابع يشوف الفرق بعينه في أول ثانية (`AMP-333`).
2. **اختاري واحدة من هذي الدخلات (أو قوليها بطريقتك الخاصة)**:
   - *خيار 1*: `"أكثر شي كان يغثني بالسفر والدوام لما تطلع العباية معفطة من الشنطة.. شوفوا هذي وش سوت بـ 20 ثانية بس!"`
   - *خيار 2*: `"لو تدورون كواية بخار حجمها كبر الكف وتفك أزمة بالعزايم والسفر، شوفوا التجربة قدامكم:"`
3. **3 معلومات أساسية اذكريها بأسلوبك العفوي (بدون قراءة نص حرفي)**:
   - تسخن في `20 ثانية` وما تترك بقع موية على الحرير أو العبايات السوداء.
   - سعرها **`199 ريال` شامل الضريبة** ومقسمة على 4 دفعات مع **تابي وتمارا** (`أقل من 50 ريال بالشهر`).
   - كود الخصم الإضافي للمتابعين: **`[SARA10]`** مع ضمان سنتين.
4. **الضوابط الإلزامية (خطوط حمراء نظامية)**:
   - ✅ وضع وسم **`#إعلان`** واضحاً في أعلى جميع السنابات (`AMP-287`) مع سريان ترخيص موثوق (`AMP-281`).
   - 🚫 عدم تصوير أي علامة مائية لتطبيق آخر (`AMP-284`) أو وضع نص الكود في أسفل الشاشة فوق زر «ارفع الشاشة» (`AMP-338`).

### Step C: Human Review & Edits (`التدقيق البشري والتعديلات`)
1. **Added Pronunciation & Brand Name Note**: Added a 1-line phonetic note so the creator pronounces the English brand name naturally without stumbling.
2. **Approved 1-Take Raw Recording**: Instructed the creator to shoot on their iPhone native camera in natural room lighting rather than studio lighting so it blends seamlessly into organic Snapchat Stories.

### Step D: Final Reviewed Example Outcome (`النتيجة النهائية المعتمدة`)
- Creator delivered a natural 3-snap Saudi story sequence that passed compliance on first review and achieved a `2.4x` higher swipe-up rate than prior teleprompter-read scripts.

## 4. What Can Go Wrong & How to Fix It (`الأخطاء الشائعة وخطة الإنقاذ`)

- **Failure Case (`المشكلة المحتملة`)**: A brand manager rejects a creator's natural video because the creator said `'تجنن وتفك أزمة'` instead of the exact corporate phrase `'توفر حلاً مبتكراً وعصرياً'`, forcing a stiff reshoot that flops on Snapchat.
- **Correction & Fallback (`الحل الإجرائي والبديل الآمن`)**: Evaluate creator drafts strictly on **4 criteria**: (1) Did they show the product working in Sec 1–2? (2) Are the price/specs accurate? (3) Are `#إعلان` and regulatory rules respected? (4) Does it sound 100% like their organic posts? Never edit a creator's natural dialect into corporate MSA.

## 5. Model & Platform Capability Matrix (`مصفوفة قدرات النماذج والمنصات — 2026-10-25`)

| Platform / Model | Status | Official Documentation | MENA Operational Constraint | Fallback |
| :--- | :--- | :--- | :--- | :--- |
| **Snapchat & TikTok Gulf/Egypt Creator Best Practices** | `supported` | [Official Docs](https://esafqa.com/en/blog/snapchat-ads-guide-saudi-gulf/) (`2026-10-25`) | Snapchat and Esafqa Gulf guides confirm that native camera feel, spoken local dialect, and immediate visual product proof outperform polished corporate scripts. | Always send 3 bullet talking points + visual demo instructions instead of a verbatim paragraph. |

## 6. How to Measure Success (`خطة القياس والضوابط`)

- **Primary Metric**: First-Snap Hold Rate (`2-Second View Rate`), Story Completion Rate, and Tracked Swipe-Up / Landing Page Conversion Rate (`AMP-288`).
- **Baseline**: Prior verbatim-scripted creator campaign benchmarks.
- **Observation Window**: 7 days post-story publication.
- **Interpretation Boundary**: Natural creator delivery boosts hold rate and trust, while inventory availability and landing page speed (`AMP-393`) govern checkout completion.

## 7. Primary Sources & Evidence Boundaries (`المصادر الموثقة وحدود الأدلة`)

- [Why Direct Translation Fails in MENA SEO](https://23hublab.com/why-direct-translation-fails-in-mena-seo/) — *23HubLab* (Published `2026-04-01`, Accessed `2026-10-25`): AI/machine translations of English keyword lists fail in MENA because native searchers use distinct Arabic lexical roots and phrasing, leading to high bounce rates and poor dwell time.
- [Snapchat Ads Guide for Online Stores in Saudi Arabia and the Gulf](https://esafqa.com/en/blog/snapchat-ads-guide-saudi-gulf/) — *Esafqa* (Published `2026-10-09`, Accessed `2026-10-25`): Details Snapchat's official creative rules for Gulf stores: 9:16 native shoot, hero message in second 1, brand before second 2 (no static logo opening), 5-6s duration with offer in seconds 2-3, natural Saudi/Gulf dialect + captions, and zero recycled TikTok/Reels watermarks.
- [AI Translation Errors in Arabic, With Real Examples](https://locstars.com/ai-translation-errors-arabic/) — *Locstars* (Published `2026-10-22`, Accessed `2026-10-25`): Documents concrete English-to-Egyptian and Gulf Arabic LLM translation failures including register mixing, gender agreement errors, and literal idioms.
