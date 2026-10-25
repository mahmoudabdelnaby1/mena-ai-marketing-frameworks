# FW-063: Diffusion Clean-Plate Generation & Post-Production RTL Arabic Typography Workflow (Extending `video-prompt-architect`)
## مسار عمل توليد المشاهد النظيفة (`Clean-Plate`) وإضافة النصوص العربية المتجهية في المونتاج (امتداد لمهارة `video-prompt-architect`)

- **Consolidated Contextual Child IDs (`MERGE_INTO_EXISTING`)**: `AMP-341`, `AMP-351`, `AMP-361`, `AMP-371`, `AMP-381`
- **Selected Artifact Type**: `EXTEND_EXISTING`
- **Intended Audience**: Video Producer, Creative Strategist, Motion Designer, Performance Creative Lead
- **Target Markets & Languages**: Egypt & GCC (`Saudi Arabia, UAE, Kuwait, Qatar, Bahrain, Oman`) — Bilingual Arabic (`Egyptian Ammiya`, `Saudi/Gulf Khaleeji`, `White MSA`) + English
- **Version**: `1.2` | **Last Reviewed**: `2026-10-25` | **Status**: `READY_FOR_REVIEW`

## 1. Plain-Language Promise & Why This Artifact Form Fits the Job

- **What You Can Make or Decide (EN)**: Eliminate reversed, disconnected Left-to-Right Arabic gibberish inside Sora, Veo, Kling, Midjourney, and DALL·E outputs by enforcing a `text-free clean plate` prompt + post-production RTL vector overlay pipeline.
- **ما الذي يمكنك إنجازه أو حسمه بهذه الأداة (AR)**: القضاء نهائياً على الحروف العربية المقطعة والمعكوسة من اليسار لليمين داخل نماذج توليد الفيديو والصور (`Sora, Veo, Kling, Midjourney, DALL·E`) عبر فصل توليد المشهد البصري النظيف عن طبقة الخط العربي المتجهي في المونتاج.
- **Why `EXTEND_EXISTING` Fits This User Job (EN)**: Extends `user:video-prompt-architect` (Phase 4 Item 5 On-screen Text) into a deterministic 2-Stage Clean-Plate + Vector Overlay workflow because image and video diffusion models do not natively shape connected right-to-left Arabic glyphs reliably.
- **لماذا يناسب شكل `EXTEND_EXISTING` هذه المهمة (AR)**: يمثل امتداداً مباشراً لمهارة `video-prompt-architect` (المرحلة 4 بند النصوص على الشاشة)؛ حيث يفصل هندسياً بين توليد المشهد السينمائي الخالي من النصوص وبين تركيب الخط العربي المتصل في برامج المونتاج.

## 2. "Use It When" Trigger, Boundaries & Exact Inputs to Prepare

- **Use It When (EN)**: Use whenever generating AI video ads, product hero visuals, or social thumbnails that require Arabic headlines, prices (`SAR/AED/EGP`), or brand packaging text.
- **متى تستخدم هذه الأداة (AR)**: تُستخدم عند إنتاج إعلانات الفيديو أو الصور بالذكاء الاصطناعي التي تتطلب ظهور عناوين عربية أو أسعار أو شعارات على الشاشة.
- **When NOT to Use It (EN)**: Never ask DALL·E, Midjourney, Sora, Veo, or Kling to 'write the Arabic sentence `خصم 50% بمناسبة اليوم الوطني` on a neon sign or storefront board' inside the diffusion prompt.
- **متى لا تستخدم هذه الأداة (AR)**: لا تطلب أبداً من نماذج التوليد البصري كتابة جملة عربية داخل البرومبت (`Write the Arabic text "..." on the sign`).

### Exact Inputs to Prepare Before Starting (`المدخلات المطلوب تجهيزها`)
1. Scene Visual Concept (from `video-prompt-architect` Master Prompt)
2. Negative Prompt Token Pack (`no text, no Arabic calligraphy, no signage, no watermarks, clean blank packaging surface`)
3. Vector Brand Logo (`.svg` / transparent `.png`) + Arabic Typography file (`Tajawal` / `Cairo` / `IBM Plex Sans Arabic`) for CapCut/Premiere/After Effects overlay

### Privacy-Safe Data Handling (`ضوابط الخصوصية وحماية البيانات الشخصية PDPL`)
- **Strict PII Redaction Before Prompting**: Under Saudi PDPL (Art. 25), UAE Federal Decree-Law No. 45 of 2021, Qatar Law No. 13 of 2016, and Egypt Law No. 151 of 2020, **never paste raw customer names, unhashed mobile numbers (`+9665...` / `+201...`), email addresses, national IDs, or private WhatsApp transcripts into public/consumer LLM interfaces**. Use anonymized placeholders (`{first_name}`, `ORD_10045`) during prompt testing and restrict live customer data to zero-data-retention enterprise API endpoints or local deterministic scripts.

## 3. The Directly Usable Artifact (`الأداة التطبيقية الجاهزة للنسخ والتنفيذ`)

### 2-Stage Clean-Plate + Vector Arabic Overlay Pipeline (`video-prompt-architect` Extension)

#### Stage 1: Prompt Modification Rule (Strip All On-Screen Text Commands from Diffusion Prompts)
Whenever the user selects Options `ب / ج / د / هـ` (On-screen Text) in `video-prompt-architect` Intake Question 5:
1. **In the Visual Diffusion Prompt (`Veo 3.1 / Sora 2 / Kling 3.0 / Midjourney`)**:
   - **REMOVE** any instruction asking the model to render Arabic letters on signs, screens, or floating titles.
   - **ADD Explicit Negative-Space Composition**: `"Compose the subject in the lower two-thirds of the 9:16 frame, leaving clean uncluttered negative space with soft bokeh in the upper-middle safe zone (Y: 250px to 650px) for post-production typography overlay. Blank unbranded matte packaging surface, zero text, zero signage, zero letters."`
   - **ADD to Negative Prompt**: `text, letters, Arabic script, pseudo-Arabic calligraphy, signage, billboards, watermarks, subtitles, captions, gibberish glyphs, numbers, logos`.
   - **For Branded Product Bottles/Boxes**: Use **Image-to-Video Reference (`Ingredients` in Veo / `@image1` in Seedance / `Start Frame` coated in Photoshop with real vector label)** rather than asking the model to spell the Arabic label from scratch!

#### Stage 2: Post-Production RTL Timecode & Safe-Zone Overlay Sheet (Output Automatically by Agent)
Generate this companion table alongside every video prompt pack so the editor (or CapCut/Premiere script) drops in crisp vector Arabic text in 60 seconds:
| Timecode | Arabic Vector Text (Copy-Paste into CapCut/Premiere with RTL Shaping ON) | Font & Style | Safe-Zone Coordinates (`1080x1920`) |
| :--- | :--- | :--- | :--- |
| `00:00 – 00:02` | `قهوة مختصة بضغط 18 بار.. بدون كهرباء!` | `Cairo ExtraBold 64pt`, White `#FFFFFF` on dark pill `#111827CC` | Center-Top (`X: 540, Y: 380` — below top UI bar) |
| `00:02 – 00:04` | `349 ر.س شامل الضريبة | قسّمها على 4 دفعات تابي` | `Tajawal Bold 52pt`, Gold `#F59E0B` accent | Center-Mid (`X: 540, Y: 1180` — safely above bottom 420px UI zone!) |
| `00:04 – 00:06` | `اطلبها الحين من الرابط تحت 👇` | `Cairo Bold 56pt` | Center (`X: 540, Y: 1280`) |

## 4. Model & Platform Capability Branches (`فروع قدرات النماذج والمنصات والبدائل الاحتياطية`)

| System / Platform | Capability Status | Official Documentation & Access Date | Operational Constraint in Egypt & GCC | Fallback When Feature/Modality Is Unavailable |
| :--- | :--- | :--- | :--- | :--- |
| **OpenAI DALL·E / Sora 2, Google Imagen / Veo 3.1 & Kling 3.0 Text Rendering in Arabic** | `unsupported` | [Official Reference](https://developers.openai.com/api/docs/guides/images-vision) (`2026-10-25`) | OpenAI and Google Gemini developer/support documentation and community bug trackers confirm diffusion image/video models frequently disconnect or reverse right-to-left Arabic ligatures. | Always generate text-free clean plates with negative space and overlay Arabic typography as vector text in post-production. |

## 5. Consolidated Regional & Vertical Adaptation Matrix (`دمج الأنماط السياقية الفرعية بدون حشو`)

Per Agent 2 v1.2's anti-padding rule, the following **5 cross-verified contextual synthesis patterns** and **1 screened duplicate variants** share this core mechanism and are consolidated directly into this source-of-truth framework:

| Child Pattern ID | Disposition | Regional / Sector Operating Context | Specific Adaptation & Guardrail Integrated in This Asset | Evidence Tier |
| :--- | :--- | :--- | :--- | :--- |
| **`AMP-341`** | `MERGE_INTO_EXISTING` | Egyptian E-Commerce & Social Commerce (Shopify / WooCommerce / Cairo & Alexandria) | Generating clean, text-free visual plates (`clean composition, text-free, no labels`) and compositing editable RTL vector typography in After Effects, Premiere, Canva, or Figma.; Specifically impacts Egyptian brands operating in EGP where merchant-specific payment mix from recent order records, Mobile Wallets (Vodafone Cash), InstaPay, and Fawry dominate. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-351`** | `MERGE_INTO_EXISTING` | UAE & Multi-Market GCC Enterprise / Retail (Dubai, Abu Dhabi, Doha, Kuwait) | Generating clean, text-free visual plates (`clean composition, text-free, no labels`) and compositing editable RTL vector typography in After Effects, Premiere, Canva, or Figma.; Specifically impacts bilingual Arabic/English campaigns in high-CPM, expat-dense Gulf markets under UAE PDPL / TDRA and Qatari regulations. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-361`** | `MERGE_INTO_EXISTING` | High-Trust & Regulated Verticals (Healthcare/SFDA/EDA, Fintech/SAMA/FRA, Real Estate) | Generating clean, text-free visual plates (`clean composition, text-free, no labels`) and compositing editable RTL vector typography in After Effects, Premiere, Canva, or Figma.; Specifically impacts regulated claims requiring SFDA, EDA, MOH, SAMA, FRA, or RERA compliance pre-clearance and strict hallucination guardrails. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-371`** | `MERGE_INTO_EXISTING` | Seasonal Peak Operations (Ramadan, Eid, White/Yellow Friday, Saudi Founding/National Day) | Generating clean, text-free visual plates (`clean composition, text-free, no labels`) and compositing editable RTL vector typography in After Effects, Premiere, Canva, or Figma.; Specifically impacts high-velocity seasonal surges where CPMs jump 40-70%, prices change rapidly, and Hijri calendar cultural sensitivity is paramount. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-381`** | `MERGE_INTO_EXISTING` | Multi-Client Agency & MarTech API Automation Pipelines (LLM APIs, Webhooks, GA4, CAPI) | Generating clean, text-free visual plates (`clean composition, text-free, no labels`) and compositing editable RTL vector typography in After Effects, Premiere, Canva, or Figma.; Specifically impacts automated multi-SKU or multi-client LLM/API pipelines where schema validation, token cost, and attribution governance are required. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-531`** | `REJECT_DUPLICATE` | Screened UI/Format Synonym (`Merged Variant: Minor UI/Format Synonym of AMP-331 (Video Advertising)`) | Consolidated into parent workflow without duplicate file inflation. | `SCREENED_DUPLICATE_VARIANT` |

### Context-Specific Execution Knobs Across the 5 MENA Operating Environments
1. **Saudi D2C E-Commerce (`Salla / Zid / Riyadh & Jeddah Retail`)**: Enforce `SAR` tax-inclusive pricing (`15% ZATCA VAT`), native `Mada / Apple Pay / Tabby / Tamara` visibility (`AMP-387`), `GAMR Mawthooq` creator verification (`AMP-281`), and White Saudi Khaleeji orthography (`AMP-002`, `AMP-177`).
2. **Egyptian E-Commerce & Social Commerce (`Shopify / WooCommerce / Cairo & Alexandria`)**: Use each merchant’s own order and payment data to assess Cash on Delivery (`COD`), mobile wallets, InstaPay, Fawry, `valU`, address fields, and pre-dispatch WhatsApp confirmation. Verify current provider terms and local requirements before implementation.
3. **UAE & Multi-Market GCC Enterprise / Retail (`Dubai, Abu Dhabi, Doha, Kuwait`)**: Separate high-CPM UAE/Qatar budgets from lower-CPM markets (`AMP-061`), enforce UAE `TDRA` `9 PM – 7 AM` SMS curfew + `AD-` prefix (`AMP-442`), UAE Media Council permits (`AMP-282`), and bilingual Arabic/English canonical & currency parity (`current applicable UAE VAT`, `current applicable Qatar/Kuwait tax rules`, 3-decimal `KWD` `AMP-239`).
4. **High-Trust & Regulated Verticals (`Healthcare SFDA/MOH/EDA, FinTech SAMA/FRA, Real Estate REGA/RERA`)**: Strip all therapeutic/cure verbs (`AMP-176`, `AMP-286`), display mandatory `MOH/SFDA/DHA/EDA/Fal/Trakheesi` permit numbers (`AMP-070`), and route budgets to high-credibility channels (`AMP-290`, `AMP-339`).
5. **Seasonal Peak Operations (`Ramadan, Eid, White/Yellow Friday, Saudi Founding/National Day`)**: Lock Hijri-Gregorian overlaps (`Feb 2027 Ramadan x Saudi Founding Day x Kuwait National Day` `AMP-125`), pre-schedule GMC `sale_price_effective_date` 48h ahead (`AMP-063`), verify 30-day baseline discount permits (`AMP-064`), and disable Meta Advantage+ auto-music (`AMP-065`).

## 6. Worked Example Summary & Failure Recovery (`ملخص المثال التطبيقي وخطة الإنقاذ`)

*(Full step-by-step worked example with annotated human edits is also provided in `EXAMPLE.md`)*

- **Sample Input Brief**: - **Scenario**: Riyadh Luxury Perfume Launch (`15s` vertical ad on Kling 3.0 / Veo 3.1).
- **Previous Failure**: Prompt asked the video model for `'A golden neon sign in a Riyadh desert camp reading عطر الفخامة الملكي'`. The model rendered disconnected, reversed LTR letters (`ي ك ل م ل ا ة م ا خ ف ل ا`).
- **Human Review & Key Edits Applied**: 1. **Verified Adobe Premiere / CapCut RTL Setting**: Added reminder to enable **`World-Ready Layout / Middle Eastern & South Asian Text Engine (تفعيل محرك النصوص العربية من اليمين لليسار)`** in Premiere/After Effects before pasting the overlay table.
2. **Product Label Composite**: Composited the real vector `.png` bottle label onto the Start Frame keyframe before running Image-to-Video so the bottle label stayed 100% sharp.
- **Final Usable Output**: - Delivered cinema-grade 9:16 video ad with zero hallucinated Arabic glyphs and razor-sharp vector Arabic headlines and bottle branding.
- **What Can Go Wrong**: An editor pastes the clean Arabic text from Stage 2 into Adobe Premiere/After Effects on a machine where 'Default Composer' is set to Latin instead of 'Middle Eastern Composer'—causing Premiere itself to render the Arabic letters disconnected from left to right!
- **Correction & Fallback**: In Adobe Premiere Pro / After Effects: open `Preferences -> Type (أو Graphics)` -> Switch Text Engine to **`Middle Eastern and South Asian`** and set paragraph direction to `Right-to-Left` before creating the text layer.

## 7. Measurement Plan & Hypothesis Framing (`خطة القياس والضوابط الإحصائية`)

- **Primary Metric to Track**: 100% Arabic typographic legibility and spelling accuracy in published video ads (`0` reversed/broken AI glyphs) and improved 2-second thumbstop rate.
- **Baseline Definition**: Pre-launch creative QA rejection rate.
- **Observation Window**: Checked on 100% of AI video assets prior to media launch. *(Must span full 7/14-day weekly cycles and account for 25th–30th monthly salary windows per `AMP-391`)*.
- **What Cannot Be Concluded (Boundary)**: Clean vector Arabic overlays protect brand credibility and readability, while spoken hook and offer drive CTR.
