# Video Prompt Architect (`user:video-prompt-architect`) — MENA Production & Compliance Extension Pack (v1.2)
## حزمة الترقية الإقليمية لمهارة مهندس برومبت الفيديو الاحترافي (`مصر والخليج — v1.2`)

- **Target Existing Skill**: `user:video-prompt-architect` (v1.0)
- **Extended By**: Agent 2: AI Marketing Framework Designer (`v1.2`)
- **Last Reviewed**: `2026-10-25`
- **Covered Pattern IDs**:
  1. **`AMP-331` (`FW-063` — `EXTEND_EXISTING`)**: Diffusion Clean-Plate Generation & Post-Production RTL Arabic Typography Overlay (prevents reversed/broken Arabic glyphs in Sora 2, Veo 3.1, Kling 3.0, Midjourney, DALL·E).
  2. **`AMP-332` (`FW-064` — `EXTEND_EXISTING`)**: Arabic TTS Full Vocalization (`تشكيل صوتي كامل`) & Homograph Disambiguation for ElevenLabs, HeyGen, and Veo 3.1 Audio.
  3. **`AMP-333` (`FW-065` — `EXTEND_EXISTING`)**: Snapchat 5–6 Second Gulf Micro-Commercial Mode (Hero message in Sec 1, SAR/AED + Tabby/Tamara offer in Sec 2–3, zero static logo opener).
  4. **`AMP-336` (`FW-068` — `EXTEND_EXISTING`)**: Authentic Gulf & Egyptian Wardrobe, Salmani/Hijazi Architecture & Right-Hand Hospitality Etiquette Guardrail Pack.
  5. **`AMP-177` (`FW-034` — Companion Module)**: Dialect Isolation & Cross-Dialect Exclusion Matrix (prevents mixing Egyptian `كده/عايز`, Levantine `هلق/كتير`, and Saudi Khaleeji `الحين/ودك` in one script).

## FW-063 (`AMP-331`): Diffusion Clean-Plate Generation & Post-Production RTL Arabic Typography Workflow (Extending `video-prompt-architect`)
### مسار عمل توليد المشاهد النظيفة (`Clean-Plate`) وإضافة النصوص العربية المتجهية في المونتاج (امتداد لمهارة `video-prompt-architect`)

- **Disposition**: `EXTEND_EXISTING` (`EXTEND_EXISTING`)
- **Promise**: Eliminate reversed, disconnected Left-to-Right Arabic gibberish inside Sora, Veo, Kling, Midjourney, and DALL·E outputs by enforcing a `text-free clean plate` prompt + post-production RTL vector overlay pipeline. / القضاء نهائياً على الحروف العربية المقطعة والمعكوسة من اليسار لليمين داخل نماذج توليد الفيديو والصور (`Sora, Veo, Kling, Midjourney, DALL·E`) عبر فصل توليد المشهد البصري النظيف عن طبقة الخط العربي المتجهي في المونتاج.

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

### Worked Integration Example
- **Input**: - **Scenario**: Riyadh Luxury Perfume Launch (`15s` vertical ad on Kling 3.0 / Veo 3.1).
- **Previous Failure**: Prompt asked the video model for `'A golden neon sign in a Riyadh desert camp reading عطر الفخامة الملكي'`. The model rendered disconnected, reversed LTR letters (`ي ك ل م ل ا ة م ا خ ف ل ا`).
- **Human Review Pass**: 1. **Verified Adobe Premiere / CapCut RTL Setting**: Added reminder to enable **`World-Ready Layout / Middle Eastern & South Asian Text Engine (تفعيل محرك النصوص العربية من اليمين لليسار)`** in Premiere/After Effects before pasting the overlay table.
2. **Product Label Composite**: Composited the real vector `.png` bottle label onto the Start Frame keyframe before running Image-to-Video so the bottle label stayed 100% sharp.
- **Final Output**: - Delivered cinema-grade 9:16 video ad with zero hallucinated Arabic glyphs and razor-sharp vector Arabic headlines and bottle branding.

## FW-064 (`AMP-332`): Arabic TTS Full Vocalization (Tashkeel) & Homograph Disambiguation Prompt (ElevenLabs / HeyGen / Veo Audio — Extending `video-prompt-architect`)
### قالب التشكيل الصوتي الكامل وفك التباس المتشابهات الخطية لتوليد التعليق الصوتي العربي (`ElevenLabs / HeyGen / Veo` — امتداد `video-prompt-architect`)

- **Disposition**: `EXTEND_EXISTING` (`EXTEND_EXISTING`)
- **Promise**: Add phonetic diacritics (`تشكيل كامل على أواخر وبواطن الكلمات`), Sukun markers (`ْ`) for spoken dialects, and Arabic phonetic respellings of foreign brand names so AI voiceovers never mispronounce Arabic homographs. / إضافة التشكيل الصوتي الدقيق وعلامات السكون اللهجية والكتابة الصوتية لأسماء العلامات الأجنبية لمنع أخطاء النطق الشائعة للمتشابهات الخطية في منصات `ElevenLabs` و`HeyGen` و`Veo 3.1`.

### Copy-Ready Arabic TTS Vocalization & Phonetic Script Prep Prompt

```xml
<system_role>
You are an Arabic Computational Phonetician & AI Voiceover Director for ElevenLabs, HeyGen, and Veo 3.1.
PROBLEM TO SOLVE: Unvocalized Arabic scripts cause TTS models to mispronounce homographs (e.g., reading `جَرَّبْ` as `جُرِبَ`, `عِطْر` as `عَطَر`, `قَدَّمَ` as `قَدَم`, or `سِعْر` as `سَعَر`) and stumble when switching mid-sentence between RTL Arabic and LTR English brand names or numbers.
</system_role>

<script_input>
- Raw Arabic Script: {{RAW_ARABIC_SCRIPT}}
- Target Spoken Register: {{REGISTER: DIALECT_SAUDI_KHALEEJI | DIALECT_EGYPTIAN_AMMIYA | FORMAL_MSA_BROADCAST}}
- Target TTS Engine: {{ENGINE: ElevenLabs Multilingual v2/v3 | HeyGen | Veo 3.1 Native Dialogue}}
</script_input>

<phonetic_transformation_rules>
1. **Homograph Disambiguation (Internal Diacritics Mandatory)**:
   - Place explicit Fatḥah (`َ`), Kasrah (`ِ`), Ḍammah (`ُ`), and Shaddah (`ّ`) on every root consonant where ambiguity exists (`سِعْرْ` not `سعر`, `تُوَفِّرْ` not `توفر`, `مُخْتَصَّة` not `مختصة`, `جَرِّبْهَا` not `جربها`).
2. **Dialectal Pausal Sukun (`تسكين أواخر الكلمات في اللهجات والفصحى الإعلانية`)**:
   - If {{REGISTER}} is `DIALECT_SAUDI_KHALEEJI` or `DIALECT_EGYPTIAN_AMMIYA`: NEVER put tanween (`ٌ / ً / ٍ`) or formal grammatical case endings at the end of words! Instead, place a **Sukun (`ْ`)** on word endings before pauses so the TTS engine speaks naturally like a native Saudi/Egyptian speaker.
   -Even in `FORMAL_MSA_BROADCAST`, place Sukun (`ْ`) at every comma (`،`), dash (`—`), and period (`.`) (`الوقف بالسكون`).
3. **Transliterate All Numbers, Currencies & Foreign Brand Names into Vocalized Arabic Script**:
   - Never leave `349 SAR` or `iPhone 16 Pro` in digits/Latin inside an Arabic TTS paragraph (TTS engines pause, switch accent, or read `SAR` as the word `"سار"`!).
   - Rewrite numbers and brands phonetically in vocalized Arabic as spoken in the target dialect:
     - `349 SAR` (KSA) → `ثَلاثْ مِيَّة وتِسْعَة وأَرْبَعِينْ رِيَالْ`
     - `15%` → `خَمْسْطَعْشَرْ بِالمِيَّة` (KSA) / `خَمَصْتَاشَرْ فِي المِيَّة` (Egypt) / `خَمْسَةَ عَشَرَ بِالمِائَة` (MSA)
     - `Tabby & Tamara` → `تَابِي وتَمَارَا` | `InstaPay` → `إِنْسْتَا بَايْ`
4. **Breath & Pacing Markers**:
   - Keep sentences `<= 10 words` per breath and use `...` or `—` for natural 0.3s micro-pauses.
</phonetic_transformation_rules>
```

### Worked Integration Example
- **Input**: - **Raw Unvocalized Saudi Script**:
  `"جرب عطرنا الجديد اليوم بـ 299 SAR فقط مع تقسيط Tabby بدون فوائد، الكمية محدودة!"`
- **TTS Engine Failures on Raw Script**: ElevenLabs read `"جرب"` as `"جَرَبْ"` (scabies/skin disease instead of `"جَرِّبْ"` try!), read `"عطرنا"` as `"عَطَرْنَا"`, and read `"299 SAR"` in a robotic English voice as `"Two hundred ninety-nine S-A-R"`.
- **Human Review Pass**: 1. **Paired with ElevenLabs Parameter Settings (`AMP-337`)**: Set `Stability = 0.65`, `Similarity = 0.80`, and **`Style Exaggeration = 0.00`** so the vocalized script is read cleanly without breath artifacts.
2. **Kept Display Captions Separate from TTS Input**: Reminded the video editor to feed the **Vocalized Phonetic Script** (`مِيتِينْ وتِسْعَة وتِسْعِينْ رِيَالْ`) to ElevenLabs for audio generation, while displaying the clean **Visual Caption** (`299 ر.س`) on screen (`AMP-335`)!
- **Final Output**: - Zero homograph mispronunciations and seamless Arabic number/brand pronunciation on the first ElevenLabs generation pass.

## FW-065 (`AMP-333`): Snapchat 5–6 Second Gulf Commercial Prompt & Storyboard Template (Sec 1 Hero Message, Sec 2–3 Offer — Extending `video-prompt-architect`)
### قالب هندسة إعلانات سناب شات الخليجية ذات الـ 5–6 ثوانٍ (الرسالة في الثانية 1، العرض في الثانية 2–3، ومنع افتتاحية الشعار الثابت)

- **Disposition**: `EXTEND_EXISTING` (`EXTEND_EXISTING`)
- **Promise**: Structure Gulf Snapchat video ads and AI video prompts to hit Snapchat's proven 5–6 second vertical cadence—delivering the core message in Second 1 and the concrete SAR/AED offer in Seconds 2–3 with zero static logo openings. / هيكلة إعلانات سناب شات الموجهة للخليج وبرومبتات توليد الفيديو وفق الإيقاع القياسي لسناب شات (5–6 ثوانٍ: الرسالة الأساسية في الثانية 1، والعرض والسعر في الثانية 2–3، مع حظر البدء بشعار ثابت).

### Gulf Snapchat 5–6 Second Micro-Commercial Blueprint (`video-prompt-architect` Extension)

#### 1. Second-by-Second Timeline Contract (`Total: 5.5 to 6.0 Seconds — Max 14 Spoken Arabic Words`)
| Second Window | Visual Camera & Subject Action | Audio / Spoken Khaleeji VO (`AMP-332` Vocalized) | On-Screen Safe-Zone Overlay (`AMP-338`) |
| :--- | :--- | :--- | :--- |
| **`0.0s – 1.2s` (`Second 1: Immediate Hero Message — NO LOGO CARD`)** | **Start mid-action (`In Media Res`)**: Hands unboxing, pouring, spraying, or demonstrating the product result in close-up `9:16`. | **4–5 words max**:<br>`"قهوتك المختصة صارت معك بالبر!"` | High-contrast hook pill at `Y: 360px` + small corner `#إعلان` badge (`AMP-287`). |
| **`1.2s – 3.5s` (`Seconds 2–3: Establish Offer, Price & BNPL`)** | Smooth camera whip/pull-back showing full product in hand + clear physical scale. | **5–6 words max**:<br>`"بـ ثلاث مية وتسعة وأربعين ريال ومقسمة على تابي."` | Large Price & Offer Badge at `Y: 1150px`: **`349 ر.س (شامل الضريبة) | 4 دفعات تابي`**. |
| **`3.5s – 5.8s` (`Seconds 4–6: Direct Swipe/Tap CTA`)** | Satisfying final product hero lock + hand pointing or directional visual cue toward the bottom CTA button. | **3–4 words max**:<br>`"ارفع الشاشة واطلبها الحين!"` | Directional arrow pointing to Snapchat's native bottom CTA bar (`اطلب الآن`). |

#### 2. Copy-Ready `video-prompt-architect` Prompt Block for 6s Single-Shot Snapchat Ad (`Veo 3.1 / Kling 3.0 / Sora 2`)
```text
Vertical 9:16 high-energy Gulf commercial single-take shot (6 seconds, 24fps).
[0.0s-1.5s]: Starts immediately in mid-action—no fade-in, no static logo card. Extreme close-up of a sleek matte-black portable espresso maker held in a young Saudi man's right hand (wearing crisp white thobe cuff) pouring rich golden crema espresso into a glass cup inside a sunlit Riyadh desert camp.
[1.5s-4.0s]: Rapid smooth handheld camera pull-back revealing the compact device size and warm desert morning atmosphere, upper-middle frame kept clean with soft bokeh for post-production Arabic offer overlay.
[4.0s-6.0s]: Subject lifts the cup toward camera with a confident warm smile. Natural morning sunlight (4500K), crisp commercial contrast, zero embedded text, zero watermarks. --ar 9:16 --duration 6s
```

### Worked Integration Example
- **Input**: - **Brand**: Saudi Home Fragrance & Diffuser Store on Salla (`Smart Waterless Car & Majlis Diffuser`, `179 SAR` incl. VAT).
- **Previous 25-Second Ad**: Opened with 3 seconds of a spinning gold logo, followed by 10 seconds of slow B-roll before mentioning the product at Second 14. Result: `89%` of Snapchat viewers swiped away before Second 3 (`Average Watch Time: 1.4s`).
- **Human Review Pass**: 1. **Word Count Trim**: Confirmed spoken script is exactly `16` short Arabic words (`5.2 seconds` spoken at energetic Gulf cadence).
2. **Right-Hand Etiquette Check (`AMP-336`)**: Confirmed the hand holding/tapping the diffuser in the prompt is explicitly the **right hand**.
- **Final Output**: - 5.5-second Snapchat Gulf Commercial & Story Ad pack delivered with Sec 1 action hook, Sec 2–3 SAR/Tabby offer, and 3x improvement in Offer-View Rate.

## FW-068 (`AMP-336`): MENA Cultural Visual Guardrail & Authentic Gulf/Egyptian Wardrobe, Architecture & Etiquette Prompt Pack (Extending `video-prompt-architect`)
### حزمة الضوابط البصرية والثقافية لمشاهد الفيديو بالذكاء الاصطناعي (ضبط الزي السعودي والخليجي، العمارة، وآداب الضيافة — امتداد `video-prompt-architect`)

- **Disposition**: `EXTEND_EXISTING` (`EXTEND_EXISTING`)
- **Promise**: Prevent Sora, Veo, Kling, and Midjourney from hallucinating South Asian/Moroccan hybrid clothing, wrong Saudi/Emirati ghutra/shimagh/iqal folds, or left-hand coffee pouring in MENA commercial scenes. / منع نماذج الفيديو والصور (`Sora, Veo, Kling, Midjourney`) من هلوسة أزياء هجينة غير دقيقة للثوب والشماغ والعقال والعباءة أو أخطاء آداب تقديم القهوة السعودية باليد اليسرى.

### MENA Authentic Visual Anatomy & Etiquette Prompt Pack (`video-prompt-architect` Extension)

#### 1. Copy-Ready English Visual Descriptors for Diffusion Models (Never Use Generic `'Middle Eastern'`)
| Target Persona / Scene | Exact English Prompt Tokens to Inject into `Visual Anchor` | Mandatory Negative Prompt Tokens (`BLOCK`) |
| :--- | :--- | :--- |
| **Saudi Male (Riyadh / Contemporary Corporate or Majlis)** | `"A young Saudi businessman wearing a tailored crisp white full-length Saudi thobe with structured stand collar and clean cuffs, classic red-and-white checkered cotton shimagh (or pure white ghutra) neatly draped and secured with a double-coiled black woven wool iqal crown cord"` | `turban, Moroccan fez, South Asian kurta, sherwani, tunic over trousers, messy headwrap, golden Aladdin vest, beard caricature` |
| **Emirati Male (Dubai / Abu Dhabi)** | `"An Emirati professional wearing a bespoke collarless white kandura with subtle front tassel (tarboosh/farkha), crisp white gutra folded in Emirati style held by a black agal"` | `checkered Palestinian keffiyeh pattern if pure white Emirati look intended, turban, collared shirt sleeves over kandura` |
| **Gulf / Saudi Female (Modest Luxury / Contemporary)** | `"A poised young Saudi woman wearing an elegant contemporary open-front draped matte-crepe abaya in [obsidian black / warm sand / olive], matching draped shayla headscarf softly framing her face, refined minimalist styling"` | `burqa mesh face grille, bridal South Asian lehenga, heavy Bollywood jewelry, revealing neckline, culturally inaccurate headwear` |
| **Saudi Coffee (`القهوة السعودية`) Hospitality Etiquette (`CRITICAL`)** | `"Authentic Saudi hospitality protocol: host holds the brass-and-silver Najdi Dallah coffee pot in his LEFT hand and presents the small handleless porcelain finjan cup (filled only one-third full) with his RIGHT hand to the guest, who receives it with his RIGHT hand"` | `drinking or handing cup with left hand, Turkish coffee cup with handle, Western ceramic mug filled to the brim, alcohol/wine glasses on table` |
| **Contemporary Architecture (`Riyadh Salmani` vs. `Cairo`)** | **Riyadh**: `"Contemporary Salmani Najdi architecture combining warm limestone geometric recesses, floor-to-ceiling minimalist glass, and native desert landscaping"`<br>**Cairo**: `"Upscale contemporary New Cairo / Zamalek interior with warm Mediterranean limestone, brass accents, and lush indoor greenery"` | `Moroccan blue zellige tileriad courtyard (for KSA scenes), Taj Mahal onion domes, fantasy desert tents indoors` |

### Worked Integration Example
- **Input**: - **Campaign**: Saudi National Day / Founding Day & Ramadan Bank Commercial generated in `Veo 3.1 / Kling 3.0`.
- **Previous Failed Prompt**: `"An Arab man serving traditional coffee to a guest in a luxury Middle Eastern living room."`
- **Model Hallucination**: Rendered a man in a South Asian tunic and turban holding a Turkish mug with a handle in his **left hand**, with wine glasses on a Moroccan tile table in the background!
- **Human Review Pass**: 1. **Reference Keyframe Lock (`Image-to-Video`)**: Uploaded a real reference photo of an authentic Saudi thobe, shimagh/iqal fold, and Najdi Dallah as the `Ingredient / Start Frame` reference (`Phase 4 Rule 4` in `video-prompt-architect`) so the video model locked 100% onto authentic Saudi tailoring.
2. **Etiquette Frame Inspection**: Verified frame-by-frame that the guest receives the finjan with the **right hand** and zero prohibited props appear on side tables.
- **Final Output**: - Culturally authentic 9:16 Saudi hospitality scene passing 100% wardrobe, architectural, and right-hand coffee etiquette QA.

## FW-034 (`AMP-177`): Arabic Dialect Isolation & Anti-Hybrid-Collision Prompt Template (Egyptian Ammiya vs. Saudi/Gulf Khaleeji vs. White MSA)
### قالب عزل اللهجات العربية ومنع الخلط اللهجي الهجين (العامية المصرية مقابل الخليجية السعودية مقابل الفصحى البيضاء)

- **Disposition**: `CREATE_FRAMEWORK` (`PROMPT_TEMPLATE`)
- **Promise**: Lock LLM copy generation to one pure Arabic dialect register—preventing jarring mid-sentence collisions of Egyptian (`كده/عايز`), Levantine (`هلق/كتير`), and Saudi Khaleeji (`الحين/ودك`) in the same script. / تقييد النموذج اللغوي بسجل لهجي واحد نقي ومنع الخلط الهجين المحرج بين العامية المصرية (`كده/عايز`) والشامية (`هلق/كتير`) والخليجية (`الحين/ودك`) داخل النص الواحد.

### Copy-Ready Dialect-Lock Prompt Template (With Cross-Dialect Exclusion Matrix)

```xml
<system_role>
You are a Native Arabic Copywriter & Socio-Linguistic Editor.
CRITICAL FAILURE TO AVOID: Never mix Arabic dialects in the same text. If the selected track is SAUDI_KHALEEJI, a single Egyptian token ("كده", "عايز", "برضو", "دلوقتي", "إزاي") or Levantine token ("هلق", "كتير", "كرمال", "منيح", "شو") is an automatic FAIL. Conversely, if the track is EGYPTIAN_AMMIYA, a single Gulf token ("الحين", "وش", "ودك", "واجد", "زين") or Levantine token is an automatic FAIL.
</system_role>

<selected_track>{{TRACK: SAUDI_WHITE_KHALEEJI | EMIRATI_KHALEEJI | EGYPTIAN_CAIRENE_AMMIYA | MODERN_WHITE_MSA}}</selected_track>
<grammatical_gender>{{GENDER: MASCULINE_SINGULAR | FEMININE_SINGULAR | PLURAL_INCLUSIVE}}</grammatical_gender>

<dialect_isolation_rules>
1. IF SAUDI_WHITE_KHALEEJI:
   - Allowed Natural Markers: الحين، وش، ودك، مره، عشان، كذا، توه، يمديك، أبشر، حياك، لا يفوتك.
   - BANNED (Zero Tolerance): كده، عايز، دلوقتي، إزاي، بتاع، خالص (Egyptian); هلق، كتير، كرمال، منيح، هيك، شو (Levantine).
2. IF EMIRATI_KHALEEJI:
   - Allowed Natural Markers: الحين، وايد، شقايل، عسب، جيه، يبالك، فالك طيب، مرحبا الساع.
   - BANNED (Zero Tolerance): كده، دلوقتي، عايز (Egyptian); هلق، كتير، هيك (Levantine).
3. IF EGYPTIAN_CAIRENE_AMMIYA:
   - Allowed Natural Markers: دلوقتي، كده، عايز/عايزة، إزاي، علشان، أوي، بجد، متفوتش، يلا.
   - BANNED (Zero Tolerance): الحين، وش، ودك، كذا، وايد، يمديك (Gulf); هلق، كرمال، منيح، هيك (Levantine).
4. IF MODERN_WHITE_MSA:
   - Crisp, contemporary pan-Arab standard Arabic free of archaic dictionary words and free of regional slang.
</dialect_isolation_rules>

<self_verification_step>
After generating the draft, scan every word against the BANNED list for {{TRACK}}. Output a JSON block `{"dialect_purity_check": "PASS", "banned_tokens_found": []}` alongside the final copy.
</self_verification_step>
```

### Worked Integration Example
- **Input**: - **Track**: `SAUDI_WHITE_KHALEEJI` (`Riyadh & Jeddah Coffee Subscription App`).
- **Broken Hybrid AI Draft (Before Prompt)**: `"لو عايز تشرب قهوة مختصة كل يوم الصبح، تطبيقنا بيوفرلك باقات كتير منيحة توصلك لحد باب البيت الحين وبسعر خيالي!"` *(Collides Egyptian `لو عايز / بيوفرلك / لحد`, Levantine `كتير منيحة`, and Gulf `الحين` in 20 words!)*
- **Human Review Pass**: 1. **Orthography Check (`ذا` vs `ده`)**: Confirmed Saudi copy uses `"كذا"` / `"هذا"` (with Thal `ذ`) while Egyptian copy uses `"كده"` / `"ده"` (with Dal `د`).
2. **Ran Automated Regex Linter**: Confirmed `0` banned cross-dialect tokens in either version.
- **Final Output**: - Two 100% dialect-pure scripts delivered (`SAUDI_WHITE_KHALEEJI` for Riyadh/Jeddah and `EGYPTIAN_CAIRENE_AMMIYA` for Cairo) with zero hybrid collisions.
