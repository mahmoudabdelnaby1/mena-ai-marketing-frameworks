# Amazon.sa & Amazon.eg 250-Byte UTF-8 Arabic Generic Keyword Compressor Prompt & Script
## <span dir="rtl">قالب وأداة ضغط الكلمات المفتاحية الخفية (`Generic Keywords`) لمتاجر `Amazon.sa` و`Amazon.eg` تحت حد 250 بايت (`UTF-8`)</span>

> **Asset ID**: `FW-009` (`AMP-009`) | **Artifact Type**: `PROMPT_TEMPLATE` | **Channel**: Search Engine Optimization (SEO) | **Markets**: Egypt & GCC (`KSA, UAE, Kuwait, Qatar, Bahrain, Oman`) | **Version**: `1.2` (`Reviewed 2026-10-25`)

**What You Can Do With This (`ماذا يمكنك أن تنجز بهذه الأداة؟`)**:
- **EN**: Generate and byte-verify hidden `Generic Keywords` for `Amazon.sa`, `Amazon.ae`, and `Amazon.eg` that stay strictly under Amazon's `<250 UTF-8 bytes` limit (~22–26 Arabic words).
- **AR**: <span dir="rtl">توليد وفحص حقل الكلمات المفتاحية الخفية (`Generic Keywords`) في أمازون السعودية والإمارات ومصر بحيث لا يتجاوز الحد الصارم (`249 بايت UTF-8` أي حوالي 22–26 كلمة عربية).</span>

## 1. Use It When & Required Inputs (`متى تستخدمها وما المدخلات المطلوبة؟`)

- **Use It When (EN)**: Use when populating the backend `Generic Keywords` (`الكلمات المفتاحية العامة`) field in Amazon Seller Central for `Amazon.sa`, `Amazon.ae`, or `Amazon.eg`.
- **متى تستخدمها (AR)**: <span dir="rtl">يُستخدم عند تعبئة حقل الكلمات المفتاحية الخفية (`Generic Keywords`) في حساب البائع على `Amazon.sa` أو `Amazon.ae` أو `Amazon.eg`.</span>
- **When NOT to Use It (EN)**: Do not repeat words already present in the visible Product Title or Bullet Points—Amazon indexes title/bullet words automatically, so repeating them wastes scarce UTF-8 bytes.
- **متى لا تستخدمها (AR)**: <span dir="rtl">لا تكرر الكلمات الموجودة مسبقاً في عنوان المنتج (`Title`) أو النقاط التفصيلية (`Bullet Points`)؛ لأن أمازون يفهرسها تلقائياً وتكرارها يهدر البايتات المحدودة.</span>

### Exact Inputs to Prepare (`المدخلات المطلوب تجهيزها قبل البدء`)
- Final Arabic Product Title (`<=75` chars per `AMP-010`) and 5 Bullet Points (so the prompt excludes already-used words)
- Target Marketplace (`Amazon.sa` KSA, `Amazon.ae` UAE, or `Amazon.eg` Egypt)
- Regional synonym & dialect list (e.g., Saudi vs. Egyptian terms, common misspellings without Hamza)

## 2. The Working `PROMPT_TEMPLATE` (`الأداة الكاملة الجاهزة للنسخ والتطبيق الفوري`)

### 1. Copy-Ready Prompt Template (`Amazon.sa` / `Amazon.eg` `<250 UTF-8 Bytes` Optimizer)

```xml
<system_role>
You are an Amazon MENA Catalog SEO Specialist for Amazon.sa, Amazon.ae, and Amazon.eg.
CRITICAL BYTE CONSTRAINT: Amazon enforces a hard limit of LESS THAN 250 UTF-8 BYTES (max 249 bytes) on the Generic Keywords field.
In UTF-8 (RFC 3629), every Arabic letter takes 2 bytes and each space takes 1 byte. Therefore, 249 UTF-8 bytes holds ONLY ~110–120 Arabic letters + spaces (roughly 20 to 25 Arabic words total!).
</system_role>

<inputs>
- Marketplace: {{MARKETPLACE: Amazon.sa | Amazon.ae | Amazon.eg}}
- Words Already in Visible Title & Bullets (DO NOT REPEAT THESE): {{EXISTING_TITLE_AND_BULLET_WORDS}}
- Product Category & Core Use Case: {{PRODUCT_SUMMARY}}
</inputs>

<compression_rules>
1. Output a single space-separated line of unique backend search terms (NO commas, NO semicolons, NO punctuation—commas waste 1 byte each; Arabic comma `،` wastes 2 bytes!).
2. Exclude all words already present in {{EXISTING_TITLE_AND_BULLET_WORDS}}.
3. Exclude stop words (`في`, `من`, `على`, `مع`, `لـ`, `الي`, `افضل`, `ارخص`, `جديد`, `اصلي`).
4. Include high-intent regional synonyms and unnormalized spelling variants not in the title (e.g., for KSA: `جوال شاحن تايب سي متنقل`; for Egypt: `باور بانك موبايل شحن سريع`).
5. TARGET LENGTH: Strictly between 180 and 235 UTF-8 bytes (max 100 Arabic characters + 20 spaces) to guarantee a safe margin under 249 bytes.
</compression_rules>
```

### 2. Mandatory Python UTF-8 Byte Gate (Verify Before Pasting into Seller Central)
```python
def verify_amazon_generic_keywords(raw_keywords: str, title_and_bullets: str = ""):
    # Strip commas/punctuation that waste UTF-8 bytes
    cleaned = " ".join(
        w for w in raw_keywords.replace("،", " ").replace(",", " ").replace(";", " ").split()
    )
    # Remove duplicate tokens while preserving order
    seen = set(title_and_bullets.split())
    deduped_tokens = []
    for token in cleaned.split():
        if token not in seen:
            seen.add(token)
            deduped_tokens.append(token)
    final_str = " ".join(deduped_tokens)
    utf8_bytes = len(final_str.encode("utf-8"))
    # If over 245 bytes, trim trailing words until <= 245 UTF-8 bytes
    while utf8_bytes > 245 and deduped_tokens:
        deduped_tokens.pop()
        final_str = " ".join(deduped_tokens)
        utf8_bytes = len(final_str.encode("utf-8"))
    return {
        "final_generic_keywords": final_str,
        "char_count": len(final_str),
        "word_count": len(deduped_tokens),
        "utf8_byte_count": utf8_bytes,
        "status": "PASS (<250 UTF-8 bytes)" if utf8_bytes < 250 else "FAIL"
    }
```

## 3. Complete End-to-End Worked Example (`مثال تطبيقي متكامل من المدخلات حتى المراجعة البشرية والنتيجة النهائية`)

*(Illustrative scenario — original example for training, never represented as a verified client outcome)*

### Step A: Sample Brief / Input (`موجز المدخلات`)
- **Marketplace**: `Amazon.sa`
- **Visible Title (`AMP-010` compliant)**: `أنكر باور بانك 20000 ملي أمبير شحن سريع تايب سي - أسود`
- **Draft AI Backend Keywords (`242` characters)**: `بطارية متنقلة، شاحن سفري للجوال، شاحن متنقل ايفون وسامسونج، بطاريه احتياطيه للسفر، شاحن سريع جوالات، خازن طاقة محمول، هدية رجالية، مستلزمات السفر والرحلات، شاحن تايب سي، بطارية انكر اصلية، شاحن متنقل صغير، باور بانك للموبايل، شاحن جوال سريع`

### Step B: Initial Output (`المخرج الأولي`)
- Draft AI Backend Keywords Check:
  - Character Count: `242` characters (looks safe if counting characters!)
  - **Actual UTF-8 Byte Count**: **`451` UTF-8 bytes** (`FAIL` — exceeds Amazon.sa's 250-byte cap by 201 bytes! Amazon Seller Central silently drops or rejects the entire field).

### Step C: Human Review & Edits (`التدقيق البشري والتعديلات`)
1. **Removed Arabic Commas (`،`) & Repeated Title Words**: Stripped `باور`, `بانك`, `شحن`, `سريع`, `تايب`, `سي`, `انكر` (already in the visible title) and removed all `،` commas (which cost 2 bytes each).
2. **Ran `verify_amazon_generic_keywords()`**: Retained only high-value unique Saudi synonyms and orthographic variants (`بطارية متنقلة بطاريه شاحن سفري جوال ايفون سامسونج خازن طاقة محمول رحلات هدايا ميني احتياطي`).

### Step D: Final Reviewed Example Outcome (`النتيجة النهائية المعتمدة`)
- **Final `Generic Keywords` String**:
  `بطارية متنقلة بطاريه شاحن سفري جوال ايفون سامسونج خازن طاقة محمول رحلات هدايا ميني احتياطي`
- **Character Count**: `90` chars | **Word Count**: `15` unique root words | **UTF-8 Byte Count**: **`166 / 249` bytes (`PASS`)**

## 4. What Can Go Wrong & How to Fix It (`الأخطاء الشائعة وخطة الإنقاذ`)

- **Failure Case (`المشكلة المحتملة`)**: A seller uses Excel's `LEN()` function (which counts characters, not UTF-8 bytes) to validate Arabic backend keywords up to 249 characters (~460 UTF-8 bytes), causing bulk flat-file uploads on `Amazon.sa` to fail validation.
- **Correction & Fallback (`الحل الإجرائي والبديل الآمن`)**: In Excel/Google Sheets, use `LENB(UNICHAR(...))` or the formula `=LEN(A2) + (LEN(A2) - LEN(SUBSTITUTE(A2, " ", "")))` approximation—specifically, for pure Arabic + spaces, `UTF8_Bytes ≈ (2 * LEN(text)) - COUNT_OF_SPACES`. Always keep Arabic character count (including spaces) `<= 130` characters to stay safely below 249 UTF-8 bytes.

## 5. Model & Platform Capability Matrix (`مصفوفة قدرات النماذج والمنصات — 2026-10-25`)

| Platform / Model | Status | Official Documentation | MENA Operational Constraint | Fallback |
| :--- | :--- | :--- | :--- | :--- |
| **Amazon Seller Central (`Amazon.sa` / `Amazon.ae` / `Amazon.eg`) `generic_keyword` Attribute** | `supported` | [Official Docs](https://voctos.net/amazon-sa-noon-seo-guide/) (`2026-10-25`) | Amazon counts `generic_keyword` in UTF-8 bytes (<250 bytes), where each Arabic character is 2 bytes (RFC 3629). | Run `len(text.encode('utf-8')) < 250` in Python or cap Arabic string length at `<= 125` characters. |

## 6. How to Measure Success (`خطة القياس والضوابط`)

- **Primary Metric**: 100% ASIN backend keyword indexation check (searching `ASIN + backend_keyword` on Amazon.sa search bar returns the product).
- **Baseline**: Pre-fix ASIN + keyword search test (0 results when field overflowed 250 bytes).
- **Observation Window**: 24–72 hours after saving in Amazon Seller Central.
- **Interpretation Boundary**: Backend keyword indexation makes the ASIN eligible for matching queries, but conversion rate, price, FBA badge, and reviews govern organic rank.

## 7. Primary Sources & Evidence Boundaries (`المصادر الموثقة وحدود الأدلة`)

- [Amazon.sa and noon SEO in 2026: How Product Search Works on Saudi and UAE Marketplaces](https://voctos.net/amazon-sa-noon-seo-guide/) — *VOCTOS* (Published `2026-10-08`, Accessed `2026-10-25`): Amazon.sa enforces a 75-character title rule (June/July 2026) and a <250-byte hidden keyword limit where UTF-8 Arabic letters consume 2 bytes each (~26 Arabic words max vs ~54 Latin); Noon requires English in KSA/UAE but hides English-only listings on its Arabic site; GA4 misclassifies amazon.sa and noon.com into Referral.
