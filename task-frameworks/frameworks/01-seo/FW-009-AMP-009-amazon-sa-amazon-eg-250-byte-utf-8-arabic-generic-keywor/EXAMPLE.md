# End-to-End Worked Example & Failure Recovery — `FW-009` (`AMP-009`)

- **Framework**: Amazon.sa & Amazon.eg 250-Byte UTF-8 Arabic Generic Keyword Compressor Prompt & Script
- **العنوان بالعربية**: قالب وأداة ضغط الكلمات المفتاحية الخفية (`Generic Keywords`) لمتاجر `Amazon.sa` و`Amazon.eg` تحت حد 250 بايت (`UTF-8`)
- **Selected Artifact Type**: `PROMPT_TEMPLATE`
- **Disclaimer**: *All scenarios, brand names, SKU codes, and metrics below are original, realistic illustrative examples for MENA practitioner training and are never represented as verified client outcomes.*

## 1. Realistic Sample Brief / Input (`المدخلات وموجز الحالة العملية`)

- **Marketplace**: `Amazon.sa`
- **Visible Title (`AMP-010` compliant)**: `أنكر باور بانك 20000 ملي أمبير شحن سريع تايب سي - أسود`
- **Draft AI Backend Keywords (`242` characters)**: `بطارية متنقلة، شاحن سفري للجوال، شاحن متنقل ايفون وسامسونج، بطاريه احتياطيه للسفر، شاحن سريع جوالات، خازن طاقة محمول، هدية رجالية، مستلزمات السفر والرحلات، شاحن تايب سي، بطارية انكر اصلية، شاحن متنقل صغير، باور بانك للموبايل، شاحن جوال سريع`

## 2. Initial Generated / Completed Output (`المخرج الأولي عند تطبيق الأداة`)

- Draft AI Backend Keywords Check:
  - Character Count: `242` characters (looks safe if counting characters!)
  - **Actual UTF-8 Byte Count**: **`451` UTF-8 bytes** (`FAIL` — exceeds Amazon.sa's 250-byte cap by 201 bytes! Amazon Seller Central silently drops or rejects the entire field).

## 3. Human Review & Localization/Technical Edits (`المراجعة البشرية والتعديلات الرقابية والتقنية`)

1. **Removed Arabic Commas (`،`) & Repeated Title Words**: Stripped `باور`, `بانك`, `شحن`, `سريع`, `تايب`, `سي`, `انكر` (already in the visible title) and removed all `،` commas (which cost 2 bytes each).
2. **Ran `verify_amazon_generic_keywords()`**: Retained only high-value unique Saudi synonyms and orthographic variants (`بطارية متنقلة بطاريه شاحن سفري جوال ايفون سامسونج خازن طاقة محمول رحلات هدايا ميني احتياطي`).

## 4. Final Reviewed Example Outcome (`النتيجة النهائية الجاهزة للتنفيذ`)

- **Final `Generic Keywords` String**:
  `بطارية متنقلة بطاريه شاحن سفري جوال ايفون سامسونج خازن طاقة محمول رحلات هدايا ميني احتياطي`
- **Character Count**: `90` chars | **Word Count**: `15` unique root words | **UTF-8 Byte Count**: **`166 / 249` bytes (`PASS`)**

## 5. What Can Go Wrong & Specific Correction / Fallback (`حالة الفشل المحتملة وخطة الإنقاذ والبديل`)

- **Common Failure Mode (`ما الذي قد يسير بشكل خاطئ؟`)**:
  A seller uses Excel's `LEN()` function (which counts characters, not UTF-8 bytes) to validate Arabic backend keywords up to 249 characters (~460 UTF-8 bytes), causing bulk flat-file uploads on `Amazon.sa` to fail validation.
- **Specific Correction & Non-AI / Platform Fallback (`الإصلاح المحدد والبديل الآمن`)**:
  In Excel/Google Sheets, use `LENB(UNICHAR(...))` or the formula `=LEN(A2) + (LEN(A2) - LEN(SUBSTITUTE(A2, " ", "")))` approximation—specifically, for pure Arabic + spaces, `UTF8_Bytes ≈ (2 * LEN(text)) - COUNT_OF_SPACES`. Always keep Arabic character count (including spaces) `<= 130` characters to stay safely below 249 UTF-8 bytes.
