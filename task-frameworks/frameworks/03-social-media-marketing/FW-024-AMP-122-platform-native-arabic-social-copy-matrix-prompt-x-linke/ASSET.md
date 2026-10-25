# FW-024: Platform-Native Arabic Social Copy Matrix Prompt (X, LinkedIn, Instagram, TikTok & Snapchat)
## قالب هندسة المحتوى العربي المخصص لكل منصة تواصل اجتماعي (إكس، لينكدإن، إنستغرام، تيك توك، وسناب شات)

- **Consolidated Contextual Child IDs (`MERGE_INTO_EXISTING`)**: `AMP-132`, `AMP-142`, `AMP-152`, `AMP-162`, `AMP-172`
- **Selected Artifact Type**: `PROMPT_TEMPLATE`
- **Intended Audience**: Social Media Manager, Community Manager, Brand Strategist, Account Director
- **Target Markets & Languages**: Egypt & GCC (`Saudi Arabia, UAE, Kuwait, Qatar, Bahrain, Oman`) — Bilingual Arabic (`Egyptian Ammiya`, `Saudi/Gulf Khaleeji`, `White MSA`) + English
- **Version**: `1.2` | **Last Reviewed**: `2026-10-25` | **Status**: `READY_FOR_REVIEW`

## 1. Plain-Language Promise & Why This Artifact Form Fits the Job

- **What You Can Make or Decide (EN)**: Transform a single campaign announcement into 5 platform-native Arabic/bilingual assets—respecting KSA X brevity, GCC/Egypt LinkedIn executive tone, Instagram Carousel saves, and TikTok/Snapchat spoken hooks—instead of cross-posting one stiff MSA paragraph.
- **ما الذي يمكنك إنجازه أو حسمه بهذه الأداة (AR)**: تحويل فكرة أو إعلان واحد إلى 5 مخرجات عربية وثنائية اللغة مصممة خصيصاً لطبيعة كل منصة (إكس، لينكدإن، إنستغرام، تيك توك، سناب شات) بدلاً من نسخ فقرة فصحى جافة واحدة وتعميمها.
- **Why `PROMPT_TEMPLATE` Fits This User Job (EN)**: Marketers frequently paste one AI-generated formal MSA caption across X, LinkedIn, Instagram, TikTok, and Snapchat, killing engagement because each platform rewards different mechanics; a multi-slot PROMPT_TEMPLATE enforces native formatting and register per channel.
- **لماذا يناسب شكل `PROMPT_TEMPLATE` هذه المهمة (AR)**: يؤدي نشر نص فصيح واحد مولد بالذكاء الاصطناعي عبر كافة المنصات إلى ضعف التفاعل لاختلاف خوارزمية ولغة كل منصة؛ لذا ينتج هذا القالب نسخاً مفصلة لكل قناة.

## 2. "Use It When" Trigger, Boundaries & Exact Inputs to Prepare

- **Use It When (EN)**: Use when drafting multi-platform social campaigns for product launches, seasonal offers, or thought leadership in KSA, UAE, or Egypt.
- **متى تستخدم هذه الأداة (AR)**: يُستخدم عند كتابة حملات التواصل الاجتماعي متعددة المنصات لإطلاق المنتجات أو العروض الموسمية أو محتوى القيادة الفكرية في السعودية والإمارات ومصر.
- **When NOT to Use It (EN)**: Do not use identical hashtag blocks (`#تسويق #نجاح #الرياض...`) across X, LinkedIn, and Snapchat—Snapchat Spotlights/Stories and X threads are penalized by hashtag stuffing.
- **متى لا تستخدم هذه الأداة (AR)**: لا تقم بنسخ كتلة وسوم (`Hashtags`) واحدة ولصقها في إكس ولينكدإن وسناب شات؛ فحشو الوسوم يضر بالوصول في إكس ولا يناسب قصص سناب شات.

### Exact Inputs to Prepare Before Starting (`المدخلات المطلوب تجهيزها`)
1. Core Offer / Insight Summary (Product, Price in SAR/AED/EGP, Key Proof Point, Landing Page URL)
2. Target Market & Dialect Track (`Saudi Khaleeji`, `UAE Bilingual`, or `Egyptian Ammiya`)
3. Visual Asset Availability (`5-slide Carousel`, `6s Snap video`, `30s TikTok/Reel`, `Text Thread`)

### Privacy-Safe Data Handling (`ضوابط الخصوصية وحماية البيانات الشخصية PDPL`)
- **Strict PII Redaction Before Prompting**: Under Saudi PDPL (Art. 25), UAE Federal Decree-Law No. 45 of 2021, Qatar Law No. 13 of 2016, and Egypt Law No. 151 of 2020, **never paste raw customer names, unhashed mobile numbers (`+9665...` / `+201...`), email addresses, national IDs, or private WhatsApp transcripts into public/consumer LLM interfaces**. Use anonymized placeholders (`{first_name}`, `ORD_10045`) during prompt testing and restrict live customer data to zero-data-retention enterprise API endpoints or local deterministic scripts.

## 3. The Directly Usable Artifact (`الأداة التطبيقية الجاهزة للنسخ والتنفيذ`)

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

## 4. Model & Platform Capability Branches (`فروع قدرات النماذج والمنصات والبدائل الاحتياطية`)

| System / Platform | Capability Status | Official Documentation & Access Date | Operational Constraint in Egypt & GCC | Fallback When Feature/Modality Is Unavailable |
| :--- | :--- | :--- | :--- | :--- |
| **Anthropic Claude 3.7/4 Sonnet & OpenAI GPT-4o Multi-Slot Prompting** | `supported` | [Official Reference](https://platform.claude.com/docs/en/build-with-claude/prompt-engineering/claude-prompting-best-practices) (`2026-10-25`) | XML-tagged role and constraint blocks reliably produce distinct register and length outputs per social platform in a single generation pass. | If a smaller model blends registers across slots, generate each platform in a separate prompt call. |

## 5. Consolidated Regional & Vertical Adaptation Matrix (`دمج الأنماط السياقية الفرعية بدون حشو`)

Per Agent 2 v1.2's anti-padding rule, the following **5 cross-verified contextual synthesis patterns** and **1 screened duplicate variants** share this core mechanism and are consolidated directly into this source-of-truth framework:

| Child Pattern ID | Disposition | Regional / Sector Operating Context | Specific Adaptation & Guardrail Integrated in This Asset | Evidence Tier |
| :--- | :--- | :--- | :--- | :--- |
| **`AMP-132`** | `MERGE_INTO_EXISTING` | Egyptian E-Commerce & Social Commerce (Shopify / WooCommerce / Cairo & Alexandria) | Channel-specific prompt templates with native format constraints and dialect registers.; Specifically impacts Egyptian brands operating in EGP where merchant-specific payment mix from recent order records, Mobile Wallets (Vodafone Cash), InstaPay, and Fawry dominate. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-142`** | `MERGE_INTO_EXISTING` | UAE & Multi-Market GCC Enterprise / Retail (Dubai, Abu Dhabi, Doha, Kuwait) | Channel-specific prompt templates with native format constraints and dialect registers.; Specifically impacts bilingual Arabic/English campaigns in high-CPM, expat-dense Gulf markets under UAE PDPL / TDRA and Qatari regulations. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-152`** | `MERGE_INTO_EXISTING` | High-Trust & Regulated Verticals (Healthcare/SFDA/EDA, Fintech/SAMA/FRA, Real Estate) | Channel-specific prompt templates with native format constraints and dialect registers.; Specifically impacts regulated claims requiring SFDA, EDA, MOH, SAMA, FRA, or RERA compliance pre-clearance and strict hallucination guardrails. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-162`** | `MERGE_INTO_EXISTING` | Seasonal Peak Operations (Ramadan, Eid, White/Yellow Friday, Saudi Founding/National Day) | Channel-specific prompt templates with native format constraints and dialect registers.; Specifically impacts high-velocity seasonal surges where CPMs jump 40-70%, prices change rapidly, and Hijri calendar cultural sensitivity is paramount. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-172`** | `MERGE_INTO_EXISTING` | Multi-Client Agency & MarTech API Automation Pipelines (LLM APIs, Webhooks, GA4, CAPI) | Channel-specific prompt templates with native format constraints and dialect registers.; Specifically impacts automated multi-SKU or multi-client LLM/API pipelines where schema validation, token cost, and attribution governance are required. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-512`** | `REJECT_DUPLICATE` | Screened UI/Format Synonym (`Merged Variant: Minor UI/Format Synonym of AMP-122 (Social Media Marketing)`) | Consolidated into parent workflow without duplicate file inflation. | `SCREENED_DUPLICATE_VARIANT` |

### Context-Specific Execution Knobs Across the 5 MENA Operating Environments
1. **Saudi D2C E-Commerce (`Salla / Zid / Riyadh & Jeddah Retail`)**: Enforce `SAR` tax-inclusive pricing (`15% ZATCA VAT`), native `Mada / Apple Pay / Tabby / Tamara` visibility (`AMP-387`), `GAMR Mawthooq` creator verification (`AMP-281`), and White Saudi Khaleeji orthography (`AMP-002`, `AMP-177`).
2. **Egyptian E-Commerce & Social Commerce (`Shopify / WooCommerce / Cairo & Alexandria`)**: Use each merchant’s own order and payment data to assess Cash on Delivery (`COD`), mobile wallets, InstaPay, Fawry, `valU`, address fields, and pre-dispatch WhatsApp confirmation. Verify current provider terms and local requirements before implementation.
3. **UAE & Multi-Market GCC Enterprise / Retail (`Dubai, Abu Dhabi, Doha, Kuwait`)**: Separate high-CPM UAE/Qatar budgets from lower-CPM markets (`AMP-061`), enforce UAE `TDRA` `9 PM – 7 AM` SMS curfew + `AD-` prefix (`AMP-442`), UAE Media Council permits (`AMP-282`), and bilingual Arabic/English canonical & currency parity (`current applicable UAE VAT`, `current applicable Qatar/Kuwait tax rules`, 3-decimal `KWD` `AMP-239`).
4. **High-Trust & Regulated Verticals (`Healthcare SFDA/MOH/EDA, FinTech SAMA/FRA, Real Estate REGA/RERA`)**: Strip all therapeutic/cure verbs (`AMP-176`, `AMP-286`), display mandatory `MOH/SFDA/DHA/EDA/Fal/Trakheesi` permit numbers (`AMP-070`), and route budgets to high-credibility channels (`AMP-290`, `AMP-339`).
5. **Seasonal Peak Operations (`Ramadan, Eid, White/Yellow Friday, Saudi Founding/National Day`)**: Lock Hijri-Gregorian overlaps (`Feb 2027 Ramadan x Saudi Founding Day x Kuwait National Day` `AMP-125`), pre-schedule GMC `sale_price_effective_date` 48h ahead (`AMP-063`), verify 30-day baseline discount permits (`AMP-064`), and disable Meta Advantage+ auto-music (`AMP-065`).

## 6. Worked Example Summary & Failure Recovery (`ملخص المثال التطبيقي وخطة الإنقاذ`)

*(Full step-by-step worked example with annotated human edits is also provided in `EXAMPLE.md`)*

- **Sample Input Brief**: - **Brand**: Saudi Home Coffee Equipment Brand launching a Portable Espresso Maker (`349 SAR` incl. VAT, 4 payments on Tabby).
- **Market**: Saudi Arabia (`White Saudi Khaleeji`).
- **Human Review & Key Edits Applied**: 1. **Removed Hashtag Clutter on X**: Stripped generic hashtags (`#قهوة #الرياض #تسوق`) from the X post so it reads like an authentic creator post.
2. **Added Safe-Zone Note on Snap/TikTok**: Marked all on-screen text coordinates inside the central `1080x1350` safe zone (`AMP-338`).
- **Final Usable Output**: - 5 channel-native assets approved and scheduled across X, LinkedIn, Instagram, TikTok, and Snapchat without a single duplicated paragraph.
- **What Can Go Wrong**: A social manager takes a 250-word formal LinkedIn post and pastes it verbatim as a TikTok video description and X post; X truncates it awkwardly and TikTok viewers scroll past in 0.8 seconds.
- **Correction & Fallback**: Enforce the Platform Mechanics Contract: never schedule a cross-network post unless the format (character count, hook second, dialect register, and CTA mechanic) matches the destination platform.

## 7. Measurement Plan & Hypothesis Framing (`خطة القياس والضوابط الإحصائية`)

- **Primary Metric to Track**: Platform-native engagement metrics: Saves/Shares Rate on Instagram, 2-Second View Rate (`Hook Rate`) on TikTok/Snap, and Link CTR on X/LinkedIn.
- **Baseline Definition**: Prior 30-day cross-posted MSA caption benchmarks.
- **Observation Window**: 14–28 days. *(Must span full 7/14-day weekly cycles and account for 25th–30th monthly salary windows per `AMP-391`)*.
- **What Cannot Be Concluded (Boundary)**: Platform-native formatting removes structural friction, while visual quality and offer attractiveness drive conversions.
