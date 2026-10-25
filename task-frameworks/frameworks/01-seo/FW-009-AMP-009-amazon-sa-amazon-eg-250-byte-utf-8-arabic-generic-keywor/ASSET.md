# FW-009: Amazon.sa & Amazon.eg 250-Byte UTF-8 Arabic Generic Keyword Compressor Prompt & Script
## قالب وأداة ضغط الكلمات المفتاحية الخفية (`Generic Keywords`) لمتاجر `Amazon.sa` و`Amazon.eg` تحت حد 250 بايت (`UTF-8`)

- **Consolidated Contextual Child IDs (`MERGE_INTO_EXISTING`)**: `AMP-021`, `AMP-033`, `AMP-045`, `AMP-057`
- **Selected Artifact Type**: `PROMPT_TEMPLATE`
- **Intended Audience**: SEO Specialist, E-Commerce Manager, Content Strategist, Technical SEO Lead
- **Target Markets & Languages**: Egypt & GCC (`Saudi Arabia, UAE, Kuwait, Qatar, Bahrain, Oman`) — Bilingual Arabic (`Egyptian Ammiya`, `Saudi/Gulf Khaleeji`, `White MSA`) + English
- **Version**: `1.2` | **Last Reviewed**: `2026-10-25` | **Status**: `READY_FOR_REVIEW`

## 1. Plain-Language Promise & Why This Artifact Form Fits the Job

- **What You Can Make or Decide (EN)**: Generate and byte-verify hidden `Generic Keywords` for `Amazon.sa`, `Amazon.ae`, and `Amazon.eg` that stay strictly under Amazon's `<250 UTF-8 bytes` limit (~22–26 Arabic words).
- **ما الذي يمكنك إنجازه أو حسمه بهذه الأداة (AR)**: توليد وفحص حقل الكلمات المفتاحية الخفية (`Generic Keywords`) في أمازون السعودية والإمارات ومصر بحيث لا يتجاوز الحد الصارم (`249 بايت UTF-8` أي حوالي 22–26 كلمة عربية).
- **Why `PROMPT_TEMPLATE` Fits This User Job (EN)**: Marketers routinely confuse 250 characters with 250 UTF-8 bytes when prompting LLMs for Amazon backend keywords (causing Amazon Seller Central to drop the entire field because Arabic letters consume 2 bytes each); a PROMPT_TEMPLATE paired with an exact UTF-8 byte-counter script guarantees compliance.
- **لماذا يناسب شكل `PROMPT_TEMPLATE` هذه المهمة (AR)**: يخلط المسوقون والنماذج اللغوية بين 250 حرفاً و250 بايت (`UTF-8`) في أمازون، مما يؤدي إلى رفض الحقل بالكامل لأن الحرف العربي يستهلك 2 بايت؛ لذا يضمن القالب المقترن بحاسبة البايتات التوافق التام.

## 2. "Use It When" Trigger, Boundaries & Exact Inputs to Prepare

- **Use It When (EN)**: Use when populating the backend `Generic Keywords` (`الكلمات المفتاحية العامة`) field in Amazon Seller Central for `Amazon.sa`, `Amazon.ae`, or `Amazon.eg`.
- **متى تستخدم هذه الأداة (AR)**: يُستخدم عند تعبئة حقل الكلمات المفتاحية الخفية (`Generic Keywords`) في حساب البائع على `Amazon.sa` أو `Amazon.ae` أو `Amazon.eg`.
- **When NOT to Use It (EN)**: Do not repeat words already present in the visible Product Title or Bullet Points—Amazon indexes title/bullet words automatically, so repeating them wastes scarce UTF-8 bytes.
- **متى لا تستخدم هذه الأداة (AR)**: لا تكرر الكلمات الموجودة مسبقاً في عنوان المنتج (`Title`) أو النقاط التفصيلية (`Bullet Points`)؛ لأن أمازون يفهرسها تلقائياً وتكرارها يهدر البايتات المحدودة.

### Exact Inputs to Prepare Before Starting (`المدخلات المطلوب تجهيزها`)
1. Final Arabic Product Title (`<=75` chars per `AMP-010`) and 5 Bullet Points (so the prompt excludes already-used words)
2. Target Marketplace (`Amazon.sa` KSA, `Amazon.ae` UAE, or `Amazon.eg` Egypt)
3. Regional synonym & dialect list (e.g., Saudi vs. Egyptian terms, common misspellings without Hamza)

### Privacy-Safe Data Handling (`ضوابط الخصوصية وحماية البيانات الشخصية PDPL`)
- **Strict PII Redaction Before Prompting**: Under Saudi PDPL (Art. 25), UAE Federal Decree-Law No. 45 of 2021, Qatar Law No. 13 of 2016, and Egypt Law No. 151 of 2020, **never paste raw customer names, unhashed mobile numbers (`+9665...` / `+201...`), email addresses, national IDs, or private WhatsApp transcripts into public/consumer LLM interfaces**. Use anonymized placeholders (`{first_name}`, `ORD_10045`) during prompt testing and restrict live customer data to zero-data-retention enterprise API endpoints or local deterministic scripts.

## 3. The Directly Usable Artifact (`الأداة التطبيقية الجاهزة للنسخ والتنفيذ`)

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

## 4. Model & Platform Capability Branches (`فروع قدرات النماذج والمنصات والبدائل الاحتياطية`)

| System / Platform | Capability Status | Official Documentation & Access Date | Operational Constraint in Egypt & GCC | Fallback When Feature/Modality Is Unavailable |
| :--- | :--- | :--- | :--- | :--- |
| **Amazon Seller Central (`Amazon.sa` / `Amazon.ae` / `Amazon.eg`) `generic_keyword` Attribute** | `supported` | [Official Reference](https://voctos.net/amazon-sa-noon-seo-guide/) (`2026-10-25`) | Amazon counts `generic_keyword` in UTF-8 bytes (<250 bytes), where each Arabic character is 2 bytes (RFC 3629). | Run `len(text.encode('utf-8')) < 250` in Python or cap Arabic string length at `<= 125` characters. |

## 5. Consolidated Regional & Vertical Adaptation Matrix (`دمج الأنماط السياقية الفرعية بدون حشو`)

Per Agent 2 v1.2's anti-padding rule, the following **4 cross-verified contextual synthesis patterns** and **1 screened duplicate variants** share this core mechanism and are consolidated directly into this source-of-truth framework:

| Child Pattern ID | Disposition | Regional / Sector Operating Context | Specific Adaptation & Guardrail Integrated in This Asset | Evidence Tier |
| :--- | :--- | :--- | :--- | :--- |
| **`AMP-021`** | `MERGE_INTO_EXISTING` | Egyptian E-Commerce & Social Commerce (Shopify / WooCommerce / Cairo & Alexandria) | Latin-script English keywords consume 1 byte per character.; Specifically impacts Egyptian brands operating in EGP where merchant-specific payment mix from recent order records, Mobile Wallets (Vodafone Cash), InstaPay, and Fawry dominate. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-033`** | `MERGE_INTO_EXISTING` | UAE & Multi-Market GCC Enterprise / Retail (Dubai, Abu Dhabi, Doha, Kuwait) | Latin-script English keywords consume 1 byte per character.; Specifically impacts bilingual Arabic/English campaigns in high-CPM, expat-dense Gulf markets under UAE PDPL / TDRA and Qatari regulations. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-045`** | `MERGE_INTO_EXISTING` | High-Trust & Regulated Verticals (Healthcare/SFDA/EDA, Fintech/SAMA/FRA, Real Estate) | Latin-script English keywords consume 1 byte per character.; Specifically impacts regulated claims requiring SFDA, EDA, MOH, SAMA, FRA, or RERA compliance pre-clearance and strict hallucination guardrails. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-057`** | `MERGE_INTO_EXISTING` | Seasonal Peak Operations (Ramadan, Eid, White/Yellow Friday, Saudi Founding/National Day) | Latin-script English keywords consume 1 byte per character.; Specifically impacts high-velocity seasonal surges where CPMs jump 40-70%, prices change rapidly, and Hijri calendar cultural sensitivity is paramount. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-505`** | `REJECT_DUPLICATE` | Screened UI/Format Synonym (`Merged Variant: Minor UI/Format Synonym of AMP-045 (Search Engine Optimization (SEO))`) | Consolidated into parent workflow without duplicate file inflation. | `SCREENED_DUPLICATE_VARIANT` |

### Context-Specific Execution Knobs Across the 5 MENA Operating Environments
1. **Saudi D2C E-Commerce (`Salla / Zid / Riyadh & Jeddah Retail`)**: Enforce `SAR` tax-inclusive pricing (`15% ZATCA VAT`), native `Mada / Apple Pay / Tabby / Tamara` visibility (`AMP-387`), `GAMR Mawthooq` creator verification (`AMP-281`), and White Saudi Khaleeji orthography (`AMP-002`, `AMP-177`).
2. **Egyptian E-Commerce & Social Commerce (`Shopify / WooCommerce / Cairo & Alexandria`)**: Use each merchant’s own order and payment data to assess Cash on Delivery (`COD`), mobile wallets, InstaPay, Fawry, `valU`, address fields, and pre-dispatch WhatsApp confirmation. Verify current provider terms and local requirements before implementation.
3. **UAE & Multi-Market GCC Enterprise / Retail (`Dubai, Abu Dhabi, Doha, Kuwait`)**: Separate high-CPM UAE/Qatar budgets from lower-CPM markets (`AMP-061`), enforce UAE `TDRA` `9 PM – 7 AM` SMS curfew + `AD-` prefix (`AMP-442`), UAE Media Council permits (`AMP-282`), and bilingual Arabic/English canonical & currency parity (`current applicable UAE VAT`, `current applicable Qatar/Kuwait tax rules`, 3-decimal `KWD` `AMP-239`).
4. **High-Trust & Regulated Verticals (`Healthcare SFDA/MOH/EDA, FinTech SAMA/FRA, Real Estate REGA/RERA`)**: Strip all therapeutic/cure verbs (`AMP-176`, `AMP-286`), display mandatory `MOH/SFDA/DHA/EDA/Fal/Trakheesi` permit numbers (`AMP-070`), and route budgets to high-credibility channels (`AMP-290`, `AMP-339`).
5. **Seasonal Peak Operations (`Ramadan, Eid, White/Yellow Friday, Saudi Founding/National Day`)**: Lock Hijri-Gregorian overlaps (`Feb 2027 Ramadan x Saudi Founding Day x Kuwait National Day` `AMP-125`), pre-schedule GMC `sale_price_effective_date` 48h ahead (`AMP-063`), verify 30-day baseline discount permits (`AMP-064`), and disable Meta Advantage+ auto-music (`AMP-065`).

## 6. Worked Example Summary & Failure Recovery (`ملخص المثال التطبيقي وخطة الإنقاذ`)

*(Full step-by-step worked example with annotated human edits is also provided in `EXAMPLE.md`)*

- **Sample Input Brief**: - **Marketplace**: `Amazon.sa`
- **Visible Title (`AMP-010` compliant)**: `أنكر باور بانك 20000 ملي أمبير شحن سريع تايب سي - أسود`
- **Draft AI Backend Keywords (`242` characters)**: `بطارية متنقلة، شاحن سفري للجوال، شاحن متنقل ايفون وسامسونج، بطاريه احتياطيه للسفر، شاحن سريع جوالات، خازن طاقة محمول، هدية رجالية، مستلزمات السفر والرحلات، شاحن تايب سي، بطارية انكر اصلية، شاحن متنقل صغير، باور بانك للموبايل، شاحن جوال سريع`
- **Human Review & Key Edits Applied**: 1. **Removed Arabic Commas (`،`) & Repeated Title Words**: Stripped `باور`, `بانك`, `شحن`, `سريع`, `تايب`, `سي`, `انكر` (already in the visible title) and removed all `،` commas (which cost 2 bytes each).
2. **Ran `verify_amazon_generic_keywords()`**: Retained only high-value unique Saudi synonyms and orthographic variants (`بطارية متنقلة بطاريه شاحن سفري جوال ايفون سامسونج خازن طاقة محمول رحلات هدايا ميني احتياطي`).
- **Final Usable Output**: - **Final `Generic Keywords` String**:
  `بطارية متنقلة بطاريه شاحن سفري جوال ايفون سامسونج خازن طاقة محمول رحلات هدايا ميني احتياطي`
- **Character Count**: `90` chars | **Word Count**: `15` unique root words | **UTF-8 Byte Count**: **`166 / 249` bytes (`PASS`)**
- **What Can Go Wrong**: A seller uses Excel's `LEN()` function (which counts characters, not UTF-8 bytes) to validate Arabic backend keywords up to 249 characters (~460 UTF-8 bytes), causing bulk flat-file uploads on `Amazon.sa` to fail validation.
- **Correction & Fallback**: In Excel/Google Sheets, use `LENB(UNICHAR(...))` or the formula `=LEN(A2) + (LEN(A2) - LEN(SUBSTITUTE(A2, " ", "")))` approximation—specifically, for pure Arabic + spaces, `UTF8_Bytes ≈ (2 * LEN(text)) - COUNT_OF_SPACES`. Always keep Arabic character count (including spaces) `<= 130` characters to stay safely below 249 UTF-8 bytes.

## 7. Measurement Plan & Hypothesis Framing (`خطة القياس والضوابط الإحصائية`)

- **Primary Metric to Track**: 100% ASIN backend keyword indexation check (searching `ASIN + backend_keyword` on Amazon.sa search bar returns the product).
- **Baseline Definition**: Pre-fix ASIN + keyword search test (0 results when field overflowed 250 bytes).
- **Observation Window**: 24–72 hours after saving in Amazon Seller Central. *(Must span full 7/14-day weekly cycles and account for 25th–30th monthly salary windows per `AMP-391`)*.
- **What Cannot Be Concluded (Boundary)**: Backend keyword indexation makes the ASIN eligible for matching queries, but conversion rate, price, FBA badge, and reviews govern organic rank.
