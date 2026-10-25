# Diffusion Clean-Plate Generation & Post-Production RTL Arabic Typography Workflow (Extending `video-prompt-architect`)
## <span dir="rtl">مسار عمل توليد المشاهد النظيفة (`Clean-Plate`) وإضافة النصوص العربية المتجهية في المونتاج (امتداد لمهارة `video-prompt-architect`)</span>

> **Asset ID**: `FW-063` (`AMP-331`) | **Artifact Type**: `EXTEND_EXISTING` | **Channel**: Video Advertising | **Markets**: Egypt & GCC (`KSA, UAE, Kuwait, Qatar, Bahrain, Oman`) | **Version**: `1.2` (`Reviewed 2026-10-25`)

**What You Can Do With This (`ماذا يمكنك أن تنجز بهذه الأداة؟`)**:
- **EN**: Eliminate reversed, disconnected Left-to-Right Arabic gibberish inside Sora, Veo, Kling, Midjourney, and DALL·E outputs by enforcing a `text-free clean plate` prompt + post-production RTL vector overlay pipeline.
- **AR**: <span dir="rtl">القضاء نهائياً على الحروف العربية المقطعة والمعكوسة من اليسار لليمين داخل نماذج توليد الفيديو والصور (`Sora, Veo, Kling, Midjourney, DALL·E`) عبر فصل توليد المشهد البصري النظيف عن طبقة الخط العربي المتجهي في المونتاج.</span>

## 1. Use It When & Required Inputs (`متى تستخدمها وما المدخلات المطلوبة؟`)

- **Use It When (EN)**: Use whenever generating AI video ads, product hero visuals, or social thumbnails that require Arabic headlines, prices (`SAR/AED/EGP`), or brand packaging text.
- **متى تستخدمها (AR)**: <span dir="rtl">تُستخدم عند إنتاج إعلانات الفيديو أو الصور بالذكاء الاصطناعي التي تتطلب ظهور عناوين عربية أو أسعار أو شعارات على الشاشة.</span>
- **When NOT to Use It (EN)**: Never ask DALL·E, Midjourney, Sora, Veo, or Kling to 'write the Arabic sentence `خصم 50% بمناسبة اليوم الوطني` on a neon sign or storefront board' inside the diffusion prompt.
- **متى لا تستخدمها (AR)**: <span dir="rtl">لا تطلب أبداً من نماذج التوليد البصري كتابة جملة عربية داخل البرومبت (`Write the Arabic text "..." on the sign`).</span>

### Exact Inputs to Prepare (`المدخلات المطلوب تجهيزها قبل البدء`)
- Scene Visual Concept (from `video-prompt-architect` Master Prompt)
- Negative Prompt Token Pack (`no text, no Arabic calligraphy, no signage, no watermarks, clean blank packaging surface`)
- Vector Brand Logo (`.svg` / transparent `.png`) + Arabic Typography file (`Tajawal` / `Cairo` / `IBM Plex Sans Arabic`) for CapCut/Premiere/After Effects overlay

## 2. The Working `EXTEND_EXISTING` (`الأداة الكاملة الجاهزة للنسخ والتطبيق الفوري`)

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

## 3. Complete End-to-End Worked Example (`مثال تطبيقي متكامل من المدخلات حتى المراجعة البشرية والنتيجة النهائية`)

*(Illustrative scenario — original example for training, never represented as a verified client outcome)*

### Step A: Sample Brief / Input (`موجز المدخلات`)
- **Scenario**: Riyadh Luxury Perfume Launch (`15s` vertical ad on Kling 3.0 / Veo 3.1).
- **Previous Failure**: Prompt asked the video model for `'A golden neon sign in a Riyadh desert camp reading عطر الفخامة الملكي'`. The model rendered disconnected, reversed LTR letters (`ي ك ل م ل ا ة م ا خ ف ل ا`).

### Step B: Initial Output (`المخرج الأولي`)
- **Stage 1 Clean-Plate Prompt**:
  `Cinematic 9:16 vertical commercial shot in a luxury Riyadh desert camp at twilight. A minimalist matte-black glass perfume flacon rests on a warm sandstone plinth in the lower-center frame, leaving clean, moody amber-lit negative space in the upper-middle third of the frame. Volumetric desert breeze, warm tungsten lanterns (2800K) in soft bokeh background. Zero text, zero signage, blank glass surface ready for post-production composite. --ar 9:16`
- **Stage 2 Vector Overlay Spec**: Exported clean `.srt` / CapCut text layer with `"عطر الفخامة الملكي — إصدار الرياض الخاص"` in `IBM Plex Sans Arabic Bold` positioned at `Y: 360px`.

### Step C: Human Review & Edits (`التدقيق البشري والتعديلات`)
1. **Verified Adobe Premiere / CapCut RTL Setting**: Added reminder to enable **`World-Ready Layout / Middle Eastern & South Asian Text Engine (تفعيل محرك النصوص العربية من اليمين لليسار)`** in Premiere/After Effects before pasting the overlay table.
2. **Product Label Composite**: Composited the real vector `.png` bottle label onto the Start Frame keyframe before running Image-to-Video so the bottle label stayed 100% sharp.

### Step D: Final Reviewed Example Outcome (`النتيجة النهائية المعتمدة`)
- Delivered cinema-grade 9:16 video ad with zero hallucinated Arabic glyphs and razor-sharp vector Arabic headlines and bottle branding.

## 4. What Can Go Wrong & How to Fix It (`الأخطاء الشائعة وخطة الإنقاذ`)

- **Failure Case (`المشكلة المحتملة`)**: An editor pastes the clean Arabic text from Stage 2 into Adobe Premiere/After Effects on a machine where 'Default Composer' is set to Latin instead of 'Middle Eastern Composer'—causing Premiere itself to render the Arabic letters disconnected from left to right!
- **Correction & Fallback (`الحل الإجرائي والبديل الآمن`)**: In Adobe Premiere Pro / After Effects: open `Preferences -> Type (أو Graphics)` -> Switch Text Engine to **`Middle Eastern and South Asian`** and set paragraph direction to `Right-to-Left` before creating the text layer.

## 5. Model & Platform Capability Matrix (`مصفوفة قدرات النماذج والمنصات — 2026-10-25`)

| Platform / Model | Status | Official Documentation | MENA Operational Constraint | Fallback |
| :--- | :--- | :--- | :--- | :--- |
| **OpenAI DALL·E / Sora 2, Google Imagen / Veo 3.1 & Kling 3.0 Text Rendering in Arabic** | `unsupported` | [Official Docs](https://developers.openai.com/api/docs/guides/images-vision) (`2026-10-25`) | OpenAI and Google Gemini developer/support documentation and community bug trackers confirm diffusion image/video models frequently disconnect or reverse right-to-left Arabic ligatures. | Always generate text-free clean plates with negative space and overlay Arabic typography as vector text in post-production. |

## 6. How to Measure Success (`خطة القياس والضوابط`)

- **Primary Metric**: 100% Arabic typographic legibility and spelling accuracy in published video ads (`0` reversed/broken AI glyphs) and improved 2-second thumbstop rate.
- **Baseline**: Pre-launch creative QA rejection rate.
- **Observation Window**: Checked on 100% of AI video assets prior to media launch.
- **Interpretation Boundary**: Clean vector Arabic overlays protect brand credibility and readability, while spoken hook and offer drive CTR.

## 7. Primary Sources & Evidence Boundaries (`المصادر الموثقة وحدود الأدلة`)

- [Images and vision | OpenAI API](https://developers.openai.com/api/docs/guides/images-vision) — *OpenAI* (Published `2026-07-01`, Accessed `2026-10-25`): Distinguishes multimodal vision input understanding from raster image generation endpoints.
- [Improving Arabic Text Rendering in AI Image Generation](https://community.openai.com/t/improving-arabic-text-rendering-in-ai-image-generation/1376545) — *OpenAI Developer Community* (Published `2026-03-13`, Accessed `2026-10-25`): Documents persistent spelling errors, disconnected Arabic letters, and reversed LTR glyph rendering inside AI-generated images.
- [Arabic text rendering in Image Generation: characters appear disconnected](https://support.google.com/gemini/thread/406579327/urgent-arabic-text-rendering-in-image-generation-is-broken-characters-appear-disconnected-and-no?hl=en) — *Google Gemini Support Community* (Published `2026-02-01`, Accessed `2026-10-25`): Confirms that prompting image generation models directly for embedded Arabic copy produces disconnected, unshaped RTL characters.
