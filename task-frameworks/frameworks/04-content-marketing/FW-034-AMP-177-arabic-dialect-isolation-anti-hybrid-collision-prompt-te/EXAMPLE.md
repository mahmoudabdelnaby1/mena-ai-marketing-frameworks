# End-to-End Worked Example & Failure Recovery — `FW-034` (`AMP-177`)

- **Framework**: Arabic Dialect Isolation & Anti-Hybrid-Collision Prompt Template (Egyptian Ammiya vs. Saudi/Gulf Khaleeji vs. White MSA)
- **العنوان بالعربية**: قالب عزل اللهجات العربية ومنع الخلط اللهجي الهجين (العامية المصرية مقابل الخليجية السعودية مقابل الفصحى البيضاء)
- **Selected Artifact Type**: `PROMPT_TEMPLATE`
- **Disclaimer**: *All scenarios, brand names, SKU codes, and metrics below are original, realistic illustrative examples for MENA practitioner training and are never represented as verified client outcomes.*

## 1. Realistic Sample Brief / Input (`المدخلات وموجز الحالة العملية`)

- **Track**: `SAUDI_WHITE_KHALEEJI` (`Riyadh & Jeddah Coffee Subscription App`).
- **Broken Hybrid AI Draft (Before Prompt)**: `"لو عايز تشرب قهوة مختصة كل يوم الصبح، تطبيقنا بيوفرلك باقات كتير منيحة توصلك لحد باب البيت الحين وبسعر خيالي!"` *(Collides Egyptian `لو عايز / بيوفرلك / لحد`, Levantine `كتير منيحة`, and Gulf `الحين` in 20 words!)*

## 2. Initial Generated / Completed Output (`المخرج الأولي عند تطبيق الأداة`)

- **Dialect Collision Audit of Broken Draft**:
  - Detected Egyptian tokens: `عايز`, `بيوفرلك`, `لحد`
  - Detected Levantine tokens: `كتير`, `منيحة`
- **Rewritten `SAUDI_WHITE_KHALEEJI` Output**:
  `"ودك بقهوة مختصة تضبط يومك كل صباح؟ تطبيقنا يوصلك باقاتك المفضلة لباب بيتك أو مكتبك بالرياض الحين، وبسعر يفرق معك!"`
- **Bonus `EGYPTIAN_CAIRENE_AMMIYA` Output (For Cairo Launch)**:
  `"لو عايز تبدأ يومك بقهوة مختصة مظبوطة كل صبح، تطبيقنا هيوصلك باقتك لحد باب البيت أو المكتب في دقائق وبسعر يوفر معاك بجد!"`

## 3. Human Review & Localization/Technical Edits (`المراجعة البشرية والتعديلات الرقابية والتقنية`)

1. **Orthography Check (`ذا` vs `ده`)**: Confirmed Saudi copy uses `"كذا"` / `"هذا"` (with Thal `ذ`) while Egyptian copy uses `"كده"` / `"ده"` (with Dal `د`).
2. **Ran Automated Regex Linter**: Confirmed `0` banned cross-dialect tokens in either version.

## 4. Final Reviewed Example Outcome (`النتيجة النهائية الجاهزة للتنفيذ`)

- Two 100% dialect-pure scripts delivered (`SAUDI_WHITE_KHALEEJI` for Riyadh/Jeddah and `EGYPTIAN_CAIRENE_AMMIYA` for Cairo) with zero hybrid collisions.

## 5. What Can Go Wrong & Specific Correction / Fallback (`حالة الفشل المحتملة وخطة الإنقاذ والبديل`)

- **Common Failure Mode (`ما الذي قد يسير بشكل خاطئ؟`)**:
  A prompt specifies `'Write in Gulf Arabic'`, and the LLM mixes Kuwaiti `'شدعوة / صج'`, Emirati `'وايد / عسب'`, and Hijazi `'دحين'` in a single paragraph aimed at a Riyadh audience.
- **Specific Correction & Non-AI / Platform Fallback (`الإصلاح المحدد والبديل الآمن`)**:
  Specify the exact **Country & Sub-Register** (`Saudi White Khaleeji` vs. `Emirati Khaleeji` vs. `Kuwaiti Khaleeji`) rather than the umbrella term `'Gulf Arabic'`.
