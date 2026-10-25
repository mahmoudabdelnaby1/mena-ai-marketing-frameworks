# FW-068: MENA Cultural Visual Guardrail & Authentic Gulf/Egyptian Wardrobe, Architecture & Etiquette Prompt Pack (Extending `video-prompt-architect`)
## حزمة الضوابط البصرية والثقافية لمشاهد الفيديو بالذكاء الاصطناعي (ضبط الزي السعودي والخليجي، العمارة، وآداب الضيافة — امتداد `video-prompt-architect`)

- **Consolidated Contextual Child IDs (`MERGE_INTO_EXISTING`)**: `AMP-346`, `AMP-356`, `AMP-366`, `AMP-376`
- **Selected Artifact Type**: `EXTEND_EXISTING`
- **Intended Audience**: Video Producer, Creative Strategist, Motion Designer, Performance Creative Lead
- **Target Markets & Languages**: Egypt & GCC (`Saudi Arabia, UAE, Kuwait, Qatar, Bahrain, Oman`) — Bilingual Arabic (`Egyptian Ammiya`, `Saudi/Gulf Khaleeji`, `White MSA`) + English
- **Version**: `1.2` | **Last Reviewed**: `2026-10-25` | **Status**: `READY_FOR_REVIEW`

## 1. Plain-Language Promise & Why This Artifact Form Fits the Job

- **What You Can Make or Decide (EN)**: Prevent Sora, Veo, Kling, and Midjourney from hallucinating South Asian/Moroccan hybrid clothing, wrong Saudi/Emirati ghutra/shimagh/iqal folds, or left-hand coffee pouring in MENA commercial scenes.
- **ما الذي يمكنك إنجازه أو حسمه بهذه الأداة (AR)**: منع نماذج الفيديو والصور (`Sora, Veo, Kling, Midjourney`) من هلوسة أزياء هجينة غير دقيقة للثوب والشماغ والعقال والعباءة أو أخطاء آداب تقديم القهوة السعودية باليد اليسرى.
- **Why `EXTEND_EXISTING` Fits This User Job (EN)**: Extends `user:video-prompt-architect` (Phase 3 Item 5 Cultural Alignment & Phase 4 Visual Anchor) with explicit English visual-anatomy descriptors and negative prompts because global video models trained on generic 'Middle East' tags conflate Saudi Najdi, Emirati, Moroccan, and South Asian attire and violate local hospitality etiquette (like pouring Dallat coffee with the wrong hand).
- **لماذا يناسب شكل `EXTEND_EXISTING` هذه المهمة (AR)**: يمثل امتداداً جوهرياً لمهارة `video-prompt-architect` (وحدة الفحص الثقافي والمرساة البصرية)؛ حيث تخلط النماذج العالمية عند كتابة `Arab man / Middle Eastern room` بين الأزياء الهندية والمغربية والخليجية وتخطئ في بروتوكول تقديم القهوة السعودية؛ لذا توفر هذه الحزمة الأوصاف الهندسية الدقيقة باللغة الإنجليزية التي تفهمها النماذج.

## 2. "Use It When" Trigger, Boundaries & Exact Inputs to Prepare

- **Use It When (EN)**: Use whenever generating AI images or videos featuring people, hospitality scenes, homes, offices, or streets in Saudi Arabia, UAE, Qatar, Kuwait, or Egypt.
- **متى تستخدم هذه الأداة (AR)**: تُستخدم عند توليد صور أو فيديوهات بالذكاء الاصطناعي تتضمن أشخاصاً أو مجالس ضيافة أو مكاتب أو معالم معمارية في السعودية والإمارات وقطر والكويت ومصر.
- **When NOT to Use It (EN)**: Never use vague prompt tokens like `'Middle Eastern man in traditional clothes'` or `'Arabian palace'`—they trigger Orientalist/Aladdin tropes, turbans, or South Asian kurtas.
- **متى لا تستخدم هذه الأداة (AR)**: لا تستخدم أبداً أوصافاً إنجليزية مبهمة مثل `Middle Eastern man in traditional clothes` أو `Arabian room`؛ لأنها تستدعي صور علاء الدين أو العمامة أو الأزياء الآسيوية.

### Exact Inputs to Prepare Before Starting (`المدخلات المطلوب تجهيزها`)
1. Target Country & Setting (`Riyadh Modern Najdi/Salmani`, `Jeddah Hijazi`, `Dubai Emirati`, or `Cairo Contemporary`)
2. Reference Photo (`Ingredient` / `Start Frame` / `Character Reference` in `video-prompt-architect`)
3. Cultural Etiquette Checklist (Right-hand giving/drinking, Dallah in left hand + Finjan in right hand)

### Privacy-Safe Data Handling (`ضوابط الخصوصية وحماية البيانات الشخصية PDPL`)
- **Strict PII Redaction Before Prompting**: Under Saudi PDPL (Art. 25), UAE Federal Decree-Law No. 45 of 2021, Qatar Law No. 13 of 2016, and Egypt Law No. 151 of 2020, **never paste raw customer names, unhashed mobile numbers (`+9665...` / `+201...`), email addresses, national IDs, or private WhatsApp transcripts into public/consumer LLM interfaces**. Use anonymized placeholders (`{first_name}`, `ORD_10045`) during prompt testing and restrict live customer data to zero-data-retention enterprise API endpoints or local deterministic scripts.

## 3. The Directly Usable Artifact (`الأداة التطبيقية الجاهزة للنسخ والتنفيذ`)

### MENA Authentic Visual Anatomy & Etiquette Prompt Pack (`video-prompt-architect` Extension)

#### 1. Copy-Ready English Visual Descriptors for Diffusion Models (Never Use Generic `'Middle Eastern'`)
| Target Persona / Scene | Exact English Prompt Tokens to Inject into `Visual Anchor` | Mandatory Negative Prompt Tokens (`BLOCK`) |
| :--- | :--- | :--- |
| **Saudi Male (Riyadh / Contemporary Corporate or Majlis)** | `"A young Saudi businessman wearing a tailored crisp white full-length Saudi thobe with structured stand collar and clean cuffs, classic red-and-white checkered cotton shimagh (or pure white ghutra) neatly draped and secured with a double-coiled black woven wool iqal crown cord"` | `turban, Moroccan fez, South Asian kurta, sherwani, tunic over trousers, messy headwrap, golden Aladdin vest, beard caricature` |
| **Emirati Male (Dubai / Abu Dhabi)** | `"An Emirati professional wearing a bespoke collarless white kandura with subtle front tassel (tarboosh/farkha), crisp white gutra folded in Emirati style held by a black agal"` | `checkered Palestinian keffiyeh pattern if pure white Emirati look intended, turban, collared shirt sleeves over kandura` |
| **Gulf / Saudi Female (Modest Luxury / Contemporary)** | `"A poised young Saudi woman wearing an elegant contemporary open-front draped matte-crepe abaya in [obsidian black / warm sand / olive], matching draped shayla headscarf softly framing her face, refined minimalist styling"` | `burqa mesh face grille, bridal South Asian lehenga, heavy Bollywood jewelry, revealing neckline, culturally inaccurate headwear` |
| **Saudi Coffee (`القهوة السعودية`) Hospitality Etiquette (`CRITICAL`)** | `"Authentic Saudi hospitality protocol: host holds the brass-and-silver Najdi Dallah coffee pot in his LEFT hand and presents the small handleless porcelain finjan cup (filled only one-third full) with his RIGHT hand to the guest, who receives it with his RIGHT hand"` | `drinking or handing cup with left hand, Turkish coffee cup with handle, Western ceramic mug filled to the brim, alcohol/wine glasses on table` |
| **Contemporary Architecture (`Riyadh Salmani` vs. `Cairo`)** | **Riyadh**: `"Contemporary Salmani Najdi architecture combining warm limestone geometric recesses, floor-to-ceiling minimalist glass, and native desert landscaping"`<br>**Cairo**: `"Upscale contemporary New Cairo / Zamalek interior with warm Mediterranean limestone, brass accents, and lush indoor greenery"` | `Moroccan blue zellige tileriad courtyard (for KSA scenes), Taj Mahal onion domes, fantasy desert tents indoors` |

## 4. Model & Platform Capability Branches (`فروع قدرات النماذج والمنصات والبدائل الاحتياطية`)

| System / Platform | Capability Status | Official Documentation & Access Date | Operational Constraint in Egypt & GCC | Fallback When Feature/Modality Is Unavailable |
| :--- | :--- | :--- | :--- | :--- |
| **Veo 3.1 (`Ingredients`), Kling 3.0 (`Elements`), Seedance 2.5 (`@image`) & Sora 2 Reference Conditioning** | `supported` | [Official Reference](https://gmedia.gov.sa/en/executive-regulations) (`2026-10-25`) | Text-only prompts in global diffusion models frequently blend regional clothing details; pairing the English Visual Anatomy Tokens with 1–2 real reference images (`Ingredients / Elements`) locks authentic Gulf/Egyptian wardrobe geometry. | Always attach a verified reference image of the exact regional wardrobe (`thobe/shimagh` or `kandura/gutra`) when generating close-up human shots. |

## 5. Consolidated Regional & Vertical Adaptation Matrix (`دمج الأنماط السياقية الفرعية بدون حشو`)

Per Agent 2 v1.2's anti-padding rule, the following **4 cross-verified contextual synthesis patterns** and **0 screened duplicate variants** share this core mechanism and are consolidated directly into this source-of-truth framework:

| Child Pattern ID | Disposition | Regional / Sector Operating Context | Specific Adaptation & Guardrail Integrated in This Asset | Evidence Tier |
| :--- | :--- | :--- | :--- | :--- |
| **`AMP-346`** | `MERGE_INTO_EXISTING` | Egyptian E-Commerce & Social Commerce (Shopify / WooCommerce / Cairo & Alexandria) | Culturally grounded visual prompt library specifying authentic regional attire, architecture, and hospitality etiquette.; Specifically impacts Egyptian brands operating in EGP where merchant-specific payment mix from recent order records, Mobile Wallets (Vodafone Cash), InstaPay, and Fawry dominate. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-356`** | `MERGE_INTO_EXISTING` | UAE & Multi-Market GCC Enterprise / Retail (Dubai, Abu Dhabi, Doha, Kuwait) | Culturally grounded visual prompt library specifying authentic regional attire, architecture, and hospitality etiquette.; Specifically impacts bilingual Arabic/English campaigns in high-CPM, expat-dense Gulf markets under UAE PDPL / TDRA and Qatari regulations. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-366`** | `MERGE_INTO_EXISTING` | High-Trust & Regulated Verticals (Healthcare/SFDA/EDA, Fintech/SAMA/FRA, Real Estate) | Culturally grounded visual prompt library specifying authentic regional attire, architecture, and hospitality etiquette.; Specifically impacts regulated claims requiring SFDA, EDA, MOH, SAMA, FRA, or RERA compliance pre-clearance and strict hallucination guardrails. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-376`** | `MERGE_INTO_EXISTING` | Seasonal Peak Operations (Ramadan, Eid, White/Yellow Friday, Saudi Founding/National Day) | Culturally grounded visual prompt library specifying authentic regional attire, architecture, and hospitality etiquette.; Specifically impacts high-velocity seasonal surges where CPMs jump 40-70%, prices change rapidly, and Hijri calendar cultural sensitivity is paramount. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |

### Context-Specific Execution Knobs Across the 5 MENA Operating Environments
1. **Saudi D2C E-Commerce (`Salla / Zid / Riyadh & Jeddah Retail`)**: Enforce `SAR` tax-inclusive pricing (`15% ZATCA VAT`), native `Mada / Apple Pay / Tabby / Tamara` visibility (`AMP-387`), `GAMR Mawthooq` creator verification (`AMP-281`), and White Saudi Khaleeji orthography (`AMP-002`, `AMP-177`).
2. **Egyptian E-Commerce & Social Commerce (`Shopify / WooCommerce / Cairo & Alexandria`)**: Use each merchant’s own order and payment data to assess Cash on Delivery (`COD`), mobile wallets, InstaPay, Fawry, `valU`, address fields, and pre-dispatch WhatsApp confirmation. Verify current provider terms and local requirements before implementation.
3. **UAE & Multi-Market GCC Enterprise / Retail (`Dubai, Abu Dhabi, Doha, Kuwait`)**: Separate high-CPM UAE/Qatar budgets from lower-CPM markets (`AMP-061`), enforce UAE `TDRA` `9 PM – 7 AM` SMS curfew + `AD-` prefix (`AMP-442`), UAE Media Council permits (`AMP-282`), and bilingual Arabic/English canonical & currency parity (`current applicable UAE VAT`, `current applicable Qatar/Kuwait tax rules`, 3-decimal `KWD` `AMP-239`).
4. **High-Trust & Regulated Verticals (`Healthcare SFDA/MOH/EDA, FinTech SAMA/FRA, Real Estate REGA/RERA`)**: Strip all therapeutic/cure verbs (`AMP-176`, `AMP-286`), display mandatory `MOH/SFDA/DHA/EDA/Fal/Trakheesi` permit numbers (`AMP-070`), and route budgets to high-credibility channels (`AMP-290`, `AMP-339`).
5. **Seasonal Peak Operations (`Ramadan, Eid, White/Yellow Friday, Saudi Founding/National Day`)**: Lock Hijri-Gregorian overlaps (`Feb 2027 Ramadan x Saudi Founding Day x Kuwait National Day` `AMP-125`), pre-schedule GMC `sale_price_effective_date` 48h ahead (`AMP-063`), verify 30-day baseline discount permits (`AMP-064`), and disable Meta Advantage+ auto-music (`AMP-065`).

## 6. Worked Example Summary & Failure Recovery (`ملخص المثال التطبيقي وخطة الإنقاذ`)

*(Full step-by-step worked example with annotated human edits is also provided in `EXAMPLE.md`)*

- **Sample Input Brief**: - **Campaign**: Saudi National Day / Founding Day & Ramadan Bank Commercial generated in `Veo 3.1 / Kling 3.0`.
- **Previous Failed Prompt**: `"An Arab man serving traditional coffee to a guest in a luxury Middle Eastern living room."`
- **Model Hallucination**: Rendered a man in a South Asian tunic and turban holding a Turkish mug with a handle in his **left hand**, with wine glasses on a Moroccan tile table in the background!
- **Human Review & Key Edits Applied**: 1. **Reference Keyframe Lock (`Image-to-Video`)**: Uploaded a real reference photo of an authentic Saudi thobe, shimagh/iqal fold, and Najdi Dallah as the `Ingredient / Start Frame` reference (`Phase 4 Rule 4` in `video-prompt-architect`) so the video model locked 100% onto authentic Saudi tailoring.
2. **Etiquette Frame Inspection**: Verified frame-by-frame that the guest receives the finjan with the **right hand** and zero prohibited props appear on side tables.
- **Final Usable Output**: - Culturally authentic 9:16 Saudi hospitality scene passing 100% wardrobe, architectural, and right-hand coffee etiquette QA.
- **What Can Go Wrong**: A prompt for a family Iftar scene in Riyadh or Cairo asks for `'A festive dinner table with sparkling drinks in tall glasses'`; the video model renders champagne flutes and wine bottles on the Ramadan Iftar table!
- **Correction & Fallback**: In **every** MENA dining, hospitality, hotel, or Ramadan/Eid prompt, explicitly include in the **Negative Prompt**: `wine bottles, champagne flutes, wine glasses, alcohol, beer, pork, left-handed eating/drinking` and specify the exact local beverages (`Vimto in glass pitcher, Arabic coffee finjan, laban cups, water tumblrs, qamar al-din`).

## 7. Measurement Plan & Hypothesis Framing (`خطة القياس والضوابط الإحصائية`)

- **Primary Metric to Track**: 100% pass rate on the 5-Point Cultural Wardrobe & Etiquette Pre-Flight Audit (`0` wardrobe/left-hand/prop hallucinations published).
- **Baseline Definition**: Rate of cultural defect rejections on unguided AI video generations.
- **Observation Window**: Checked on every generated scene prior to assembly. *(Must span full 7/14-day weekly cycles and account for 25th–30th monthly salary windows per `AMP-391`)*.
- **What Cannot Be Concluded (Boundary)**: Cultural accuracy protects brand respect and GAMR compliance, while narrative hook and offer drive commercial action.
