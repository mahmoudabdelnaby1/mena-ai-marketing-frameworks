# MENA Cultural Visual Guardrail & Authentic Gulf/Egyptian Wardrobe, Architecture & Etiquette Prompt Pack (Extending `video-prompt-architect`)
## <span dir="rtl">حزمة الضوابط البصرية والثقافية لمشاهد الفيديو بالذكاء الاصطناعي (ضبط الزي السعودي والخليجي، العمارة، وآداب الضيافة — امتداد `video-prompt-architect`)</span>

> **Asset ID**: `FW-068` (`AMP-336`) | **Artifact Type**: `EXTEND_EXISTING` | **Channel**: Video Advertising | **Markets**: Egypt & GCC (`KSA, UAE, Kuwait, Qatar, Bahrain, Oman`) | **Version**: `1.2` (`Reviewed 2026-10-25`)

**What You Can Do With This (`ماذا يمكنك أن تنجز بهذه الأداة؟`)**:
- **EN**: Prevent Sora, Veo, Kling, and Midjourney from hallucinating South Asian/Moroccan hybrid clothing, wrong Saudi/Emirati ghutra/shimagh/iqal folds, or left-hand coffee pouring in MENA commercial scenes.
- **AR**: <span dir="rtl">منع نماذج الفيديو والصور (`Sora, Veo, Kling, Midjourney`) من هلوسة أزياء هجينة غير دقيقة للثوب والشماغ والعقال والعباءة أو أخطاء آداب تقديم القهوة السعودية باليد اليسرى.</span>

## 1. Use It When & Required Inputs (`متى تستخدمها وما المدخلات المطلوبة؟`)

- **Use It When (EN)**: Use whenever generating AI images or videos featuring people, hospitality scenes, homes, offices, or streets in Saudi Arabia, UAE, Qatar, Kuwait, or Egypt.
- **متى تستخدمها (AR)**: <span dir="rtl">تُستخدم عند توليد صور أو فيديوهات بالذكاء الاصطناعي تتضمن أشخاصاً أو مجالس ضيافة أو مكاتب أو معالم معمارية في السعودية والإمارات وقطر والكويت ومصر.</span>
- **When NOT to Use It (EN)**: Never use vague prompt tokens like `'Middle Eastern man in traditional clothes'` or `'Arabian palace'`—they trigger Orientalist/Aladdin tropes, turbans, or South Asian kurtas.
- **متى لا تستخدمها (AR)**: <span dir="rtl">لا تستخدم أبداً أوصافاً إنجليزية مبهمة مثل `Middle Eastern man in traditional clothes` أو `Arabian room`؛ لأنها تستدعي صور علاء الدين أو العمامة أو الأزياء الآسيوية.</span>

### Exact Inputs to Prepare (`المدخلات المطلوب تجهيزها قبل البدء`)
- Target Country & Setting (`Riyadh Modern Najdi/Salmani`, `Jeddah Hijazi`, `Dubai Emirati`, or `Cairo Contemporary`)
- Reference Photo (`Ingredient` / `Start Frame` / `Character Reference` in `video-prompt-architect`)
- Cultural Etiquette Checklist (Right-hand giving/drinking, Dallah in left hand + Finjan in right hand)

## 2. The Working `EXTEND_EXISTING` (`الأداة الكاملة الجاهزة للنسخ والتطبيق الفوري`)

### MENA Authentic Visual Anatomy & Etiquette Prompt Pack (`video-prompt-architect` Extension)

#### 1. Copy-Ready English Visual Descriptors for Diffusion Models (Never Use Generic `'Middle Eastern'`)
| Target Persona / Scene | Exact English Prompt Tokens to Inject into `Visual Anchor` | Mandatory Negative Prompt Tokens (`BLOCK`) |
| :--- | :--- | :--- |
| **Saudi Male (Riyadh / Contemporary Corporate or Majlis)** | `"A young Saudi businessman wearing a tailored crisp white full-length Saudi thobe with structured stand collar and clean cuffs, classic red-and-white checkered cotton shimagh (or pure white ghutra) neatly draped and secured with a double-coiled black woven wool iqal crown cord"` | `turban, Moroccan fez, South Asian kurta, sherwani, tunic over trousers, messy headwrap, golden Aladdin vest, beard caricature` |
| **Emirati Male (Dubai / Abu Dhabi)** | `"An Emirati professional wearing a bespoke collarless white kandura with subtle front tassel (tarboosh/farkha), crisp white gutra folded in Emirati style held by a black agal"` | `checkered Palestinian keffiyeh pattern if pure white Emirati look intended, turban, collared shirt sleeves over kandura` |
| **Gulf / Saudi Female (Modest Luxury / Contemporary)** | `"A poised young Saudi woman wearing an elegant contemporary open-front draped matte-crepe abaya in [obsidian black / warm sand / olive], matching draped shayla headscarf softly framing her face, refined minimalist styling"` | `burqa mesh face grille, bridal South Asian lehenga, heavy Bollywood jewelry, revealing neckline, culturally inaccurate headwear` |
| **Saudi Coffee (`القهوة السعودية`) Hospitality Etiquette (`CRITICAL`)** | `"Authentic Saudi hospitality protocol: host holds the brass-and-silver Najdi Dallah coffee pot in his LEFT hand and presents the small handleless porcelain finjan cup (filled only one-third full) with his RIGHT hand to the guest, who receives it with his RIGHT hand"` | `drinking or handing cup with left hand, Turkish coffee cup with handle, Western ceramic mug filled to the brim, alcohol/wine glasses on table` |
| **Contemporary Architecture (`Riyadh Salmani` vs. `Cairo`)** | **Riyadh**: `"Contemporary Salmani Najdi architecture combining warm limestone geometric recesses, floor-to-ceiling minimalist glass, and native desert landscaping"`<br>**Cairo**: `"Upscale contemporary New Cairo / Zamalek interior with warm Mediterranean limestone, brass accents, and lush indoor greenery"` | `Moroccan blue zellige tileriad courtyard (for KSA scenes), Taj Mahal onion domes, fantasy desert tents indoors` |

## 3. Complete End-to-End Worked Example (`مثال تطبيقي متكامل من المدخلات حتى المراجعة البشرية والنتيجة النهائية`)

*(Illustrative scenario — original example for training, never represented as a verified client outcome)*

### Step A: Sample Brief / Input (`موجز المدخلات`)
- **Campaign**: Saudi National Day / Founding Day & Ramadan Bank Commercial generated in `Veo 3.1 / Kling 3.0`.
- **Previous Failed Prompt**: `"An Arab man serving traditional coffee to a guest in a luxury Middle Eastern living room."`
- **Model Hallucination**: Rendered a man in a South Asian tunic and turban holding a Turkish mug with a handle in his **left hand**, with wine glasses on a Moroccan tile table in the background!

### Step B: Initial Output (`المخرج الأولي`)
- **Corrected `video-prompt-architect` Master Prompt with Cultural Guardrail Pack**:
  `Medium cinematic 9:16 shot inside a contemporary Riyadh Salmani-style majlis with warm limestone walls and soft daylight. A welcoming Saudi host in a crisp tailored white collared thobe, neatly draped red-and-white shimagh, and black double-coiled iqal holds a traditional brass Najdi Dallah in his left hand and offers a small handleless porcelain finjan cup with his RIGHT hand to an honoured guest who receives it with his RIGHT hand. Fresh Khalas dates in a minimalist wooden bowl on the low table. Warm 3500K lighting, 50mm lens, f/2.0. Negative prompt: left-handed serving, cup with handle, wine glasses, alcohol, turban, South Asian kurta, Moroccan tiles, text, watermarks. --ar 9:16`

### Step C: Human Review & Edits (`التدقيق البشري والتعديلات`)
1. **Reference Keyframe Lock (`Image-to-Video`)**: Uploaded a real reference photo of an authentic Saudi thobe, shimagh/iqal fold, and Najdi Dallah as the `Ingredient / Start Frame` reference (`Phase 4 Rule 4` in `video-prompt-architect`) so the video model locked 100% onto authentic Saudi tailoring.
2. **Etiquette Frame Inspection**: Verified frame-by-frame that the guest receives the finjan with the **right hand** and zero prohibited props appear on side tables.

### Step D: Final Reviewed Example Outcome (`النتيجة النهائية المعتمدة`)
- Culturally authentic 9:16 Saudi hospitality scene passing 100% wardrobe, architectural, and right-hand coffee etiquette QA.

## 4. What Can Go Wrong & How to Fix It (`الأخطاء الشائعة وخطة الإنقاذ`)

- **Failure Case (`المشكلة المحتملة`)**: A prompt for a family Iftar scene in Riyadh or Cairo asks for `'A festive dinner table with sparkling drinks in tall glasses'`; the video model renders champagne flutes and wine bottles on the Ramadan Iftar table!
- **Correction & Fallback (`الحل الإجرائي والبديل الآمن`)**: In **every** MENA dining, hospitality, hotel, or Ramadan/Eid prompt, explicitly include in the **Negative Prompt**: `wine bottles, champagne flutes, wine glasses, alcohol, beer, pork, left-handed eating/drinking` and specify the exact local beverages (`Vimto in glass pitcher, Arabic coffee finjan, laban cups, water tumblrs, qamar al-din`).

## 5. Model & Platform Capability Matrix (`مصفوفة قدرات النماذج والمنصات — 2026-10-25`)

| Platform / Model | Status | Official Documentation | MENA Operational Constraint | Fallback |
| :--- | :--- | :--- | :--- | :--- |
| **Veo 3.1 (`Ingredients`), Kling 3.0 (`Elements`), Seedance 2.5 (`@image`) & Sora 2 Reference Conditioning** | `supported` | [Official Docs](https://gmedia.gov.sa/en/executive-regulations) (`2026-10-25`) | Text-only prompts in global diffusion models frequently blend regional clothing details; pairing the English Visual Anatomy Tokens with 1–2 real reference images (`Ingredients / Elements`) locks authentic Gulf/Egyptian wardrobe geometry. | Always attach a verified reference image of the exact regional wardrobe (`thobe/shimagh` or `kandura/gutra`) when generating close-up human shots. |

## 6. How to Measure Success (`خطة القياس والضوابط`)

- **Primary Metric**: 100% pass rate on the 5-Point Cultural Wardrobe & Etiquette Pre-Flight Audit (`0` wardrobe/left-hand/prop hallucinations published).
- **Baseline**: Rate of cultural defect rejections on unguided AI video generations.
- **Observation Window**: Checked on every generated scene prior to assembly.
- **Interpretation Boundary**: Cultural accuracy protects brand respect and GAMR compliance, while narrative hook and offer drive commercial action.

## 7. Primary Sources & Evidence Boundaries (`المصادر الموثقة وحدود الأدلة`)

- [Snap Advertising Policies - Snap Inc.](https://www.snap.com/ad-policies) — *Snap Inc.* (Published `2026-06-01`, Accessed `2026-10-25`): Enforces country-specific creative, cultural sensitivity, financial, and health/cosmetic claim rules across Saudi Arabia, UAE, and Egypt.
- [Laws and Executive Regulations - General Authority for Media Regulation](https://gmedia.gov.sa/en/executive-regulations) — *Saudi General Authority of Media Regulation (GAMR)* (Published `2026-09-14`, Accessed `2026-10-25`): Sets media content controls, cultural/religious compliance, and advertising disclosure requirements in Saudi Arabia.
- [GCC Marketing Playbook: UAE, Saudi Arabia and Qatar](https://thegrower.ai/gcc-marketing) — *Grower AI* (Published `2026-10-12`, Accessed `2026-10-25`): Cites DataReportal Digital 2026 reach: Snapchat reaches 72.9% in KSA vs 44.9% in UAE and 39.5% in Qatar; LinkedIn reaches 87.6% in UAE vs 34.6% in KSA; X reaches 43.1% in KSA vs 25.0% in UAE; also discusses Saudi localization policy (Saudi localization requirements vary by activity and workforce inputs; check the current official HRSD calculator).
