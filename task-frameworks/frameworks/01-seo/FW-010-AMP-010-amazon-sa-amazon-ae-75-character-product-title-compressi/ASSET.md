# FW-010: Amazon.sa & Amazon.ae 75-Character Product Title Compression Prompt & Policy Template
## قالب صياغة وضغط عناوين منتجات `Amazon.sa` و`Amazon.ae` ضمن السقف الرسمي (75 حرفاً) لمنع إعادة الكتابة الآلية

- **Consolidated Contextual Child IDs (`MERGE_INTO_EXISTING`)**: `AMP-022`, `AMP-034`, `AMP-046`, `AMP-058`
- **Selected Artifact Type**: `CONTENT_TEMPLATE`
- **Intended Audience**: SEO Specialist, E-Commerce Manager, Content Strategist, Technical SEO Lead
- **Target Markets & Languages**: Egypt & GCC (`Saudi Arabia, UAE, Kuwait, Qatar, Bahrain, Oman`) — Bilingual Arabic (`Egyptian Ammiya`, `Saudi/Gulf Khaleeji`, `White MSA`) + English
- **Version**: `1.2` | **Last Reviewed**: `2026-10-25` | **Status**: `READY_FOR_REVIEW`

## 1. Plain-Language Promise & Why This Artifact Form Fits the Job

- **What You Can Make or Decide (EN)**: Craft high-converting Arabic and English Amazon product titles strictly within the 75-character policy cap so Amazon does not truncate or auto-rewrite your title after 14 days.
- **ما الذي يمكنك إنجازه أو حسمه بهذه الأداة (AR)**: صياغة عناوين منتجات أمازون السعودية والإمارات ضمن السقف الرسمي (75 حرفاً) لمنع بتر العنوان أو تغييره تلقائياً بواسطة ذكاء أمازون الاصطناعي بعد 14 يوماً.
- **Why `CONTENT_TEMPLATE` Fits This User Job (EN)**: Amazon's June/July 2026 title policy update enforces a 75-character cap on Saudi and UAE Seller Central policy pages and replaces non-compliant titles automatically after 14 days; a strict CONTENT_TEMPLATE with slot budgets lets catalog managers write compliant titles every time.
- **لماذا يناسب شكل `CONTENT_TEMPLATE` هذه المهمة (AR)**: يفرض تحديث أمازون (يونيو/يوليو 2026) في السعودية والإمارات حداً أقصى يبلغ 75 حرفاً لعنوان المنتج مع استبدال العناوين المخالفة آلياً بعد 14 يوماً؛ لذا يوفر قالب المحتوى صيغة قياسية منضبطة.

## 2. "Use It When" Trigger, Boundaries & Exact Inputs to Prepare

- **Use It When (EN)**: Use when creating or updating ASIN titles on `Amazon.sa`, `Amazon.ae`, or `Amazon.eg` via Seller Central or Vendor Central.
- **متى تستخدم هذه الأداة (AR)**: يُستخدم عند إنشاء أو تحديث عناوين المنتجات (`Product Title`) على `Amazon.sa` أو `Amazon.ae` أو `Amazon.eg`.
- **When NOT to Use It (EN)**: Do not stuff promotional phrases (`شحن مجاني`, `أفضل مبيعاً`, `خصم 50%`), symbols (`!`, `*`, `؟`), or repeat the same root word more than twice in an Amazon title—both violate Amazon policy regardless of character length.
- **متى لا تستخدم هذه الأداة (AR)**: لا تقم بحشو عبارات ترويجية (`شحن مجاني`، `الأكثر مبيعاً`، `خصم`) أو رموز (`!`، `*`) أو تكرار نفس الكلمة أكثر من مرتين داخل عنوان أمازون.

### Exact Inputs to Prepare Before Starting (`المدخلات المطلوب تجهيزها`)
1. Brand Name (Arabic & English)
2. Core Product Noun (highest search-volume native term from `AMP-001`)
3. 1–2 Defining Specs (Capacity/Size/Power/Material + Color/Count)
4. Bullet Point #1 & Backend Generic Keywords (`AMP-009`) to hold overflow attributes

### Privacy-Safe Data Handling (`ضوابط الخصوصية وحماية البيانات الشخصية PDPL`)
- **Strict PII Redaction Before Prompting**: Under Saudi PDPL (Art. 25), UAE Federal Decree-Law No. 45 of 2021, Qatar Law No. 13 of 2016, and Egypt Law No. 151 of 2020, **never paste raw customer names, unhashed mobile numbers (`+9665...` / `+201...`), email addresses, national IDs, or private WhatsApp transcripts into public/consumer LLM interfaces**. Use anonymized placeholders (`{first_name}`, `ORD_10045`) during prompt testing and restrict live customer data to zero-data-retention enterprise API endpoints or local deterministic scripts.

## 3. The Directly Usable Artifact (`الأداة التطبيقية الجاهزة للنسخ والتنفيذ`)

### Amazon MENA `<= 75-Character` Product Title Formula & Prompt

#### 1. The 4-Slot Title Formula (`Max 70–75 Characters Including Spaces`)
```text
[Slot 1: Brand (6–12 chars)] + [Slot 2: Core Native Product Noun (15–22 chars)] + [Slot 3: Key Tech Spec / Size (12–18 chars)] + [Slot 4: Variant / Color / Pack (6–12 chars)]
```
- **Hard Guardrails (Amazon June/July 2026 KSA/UAE Policy)**:
  1. **Total Character Count**: `<= 75` characters (including spaces).
  2. **Word Repetition Limit**: Never repeat any word more than `2` times.
  3. **Forbidden Characters**: `! $ ? _ { } ^ ¬ ¦` and promotional claims (`Best Seller`, `Free Shipping`, `الأصلي 100%`).
  4. **Overflow Routing**: Move secondary benefits, compatibility lists, and secondary synonyms to **Bullet Point 1** and the **`<250-byte` Generic Keywords (`AMP-009`)**.

#### 2. Copy-Ready LLM Title Compression Prompt
```xml
<system_role>
You are an Amazon.sa / Amazon.ae Catalog Compliance Specialist.
Rewrite the raw product description into an Amazon-compliant Arabic title and English title.
</system_role>
<constraints>
1. HARD CAP: Every title MUST be <= 72 characters (including spaces) so it safely passes Amazon's 75-character KSA/UAE limit.
2. Follow the exact formula: [Brand] + [Core Native Noun] + [1-2 Defining Numeric Specs] + [Color/Pack].
3. Use ASCII numerals (`20000mAh`, `1.5L`, `50ml`) instead of spelled-out numbers to save characters and improve mobile scannability.
4. Zero promotional words, zero banned symbols, and no word repeated >2 times.
5. Output a JSON object with `title_ar`, `title_ar_len`, `title_en`, `title_en_len`, and `overflow_terms_for_bullets_and_backend`.
</constraints>
```

## 4. Model & Platform Capability Branches (`فروع قدرات النماذج والمنصات والبدائل الاحتياطية`)

| System / Platform | Capability Status | Official Documentation & Access Date | Operational Constraint in Egypt & GCC | Fallback When Feature/Modality Is Unavailable |
| :--- | :--- | :--- | :--- | :--- |
| **Amazon.sa & Amazon.ae Product Title Policy (75-Char Cap & 14-Day Auto-Rewrite)** | `supported` | [Official Reference](https://voctos.net/amazon-sa-noon-seo-guide/) (`2026-10-25`) | VOCTOS's Oct 2026 marketplace study confirmed the 75-character limit on KSA and UAE policy pages and the 14-day review window before Amazon-generated titles apply. | Enforce `len(title) <= 75` in catalog flat-files before upload. |

## 5. Consolidated Regional & Vertical Adaptation Matrix (`دمج الأنماط السياقية الفرعية بدون حشو`)

Per Agent 2 v1.2's anti-padding rule, the following **4 cross-verified contextual synthesis patterns** and **1 screened duplicate variants** share this core mechanism and are consolidated directly into this source-of-truth framework:

| Child Pattern ID | Disposition | Regional / Sector Operating Context | Specific Adaptation & Guardrail Integrated in This Asset | Evidence Tier |
| :--- | :--- | :--- | :--- | :--- |
| **`AMP-022`** | `MERGE_INTO_EXISTING` | Egyptian E-Commerce & Social Commerce (Shopify / WooCommerce / Cairo & Alexandria) | Media categories exempt from the 75-character cap.; Specifically impacts Egyptian brands operating in EGP where merchant-specific payment mix from recent order records, Mobile Wallets (Vodafone Cash), InstaPay, and Fawry dominate. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-034`** | `MERGE_INTO_EXISTING` | UAE & Multi-Market GCC Enterprise / Retail (Dubai, Abu Dhabi, Doha, Kuwait) | Media categories exempt from the 75-character cap.; Specifically impacts bilingual Arabic/English campaigns in high-CPM, expat-dense Gulf markets under UAE PDPL / TDRA and Qatari regulations. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-046`** | `MERGE_INTO_EXISTING` | High-Trust & Regulated Verticals (Healthcare/SFDA/EDA, Fintech/SAMA/FRA, Real Estate) | Media categories exempt from the 75-character cap.; Specifically impacts regulated claims requiring SFDA, EDA, MOH, SAMA, FRA, or RERA compliance pre-clearance and strict hallucination guardrails. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-058`** | `MERGE_INTO_EXISTING` | Seasonal Peak Operations (Ramadan, Eid, White/Yellow Friday, Saudi Founding/National Day) | Media categories exempt from the 75-character cap.; Specifically impacts high-velocity seasonal surges where CPMs jump 40-70%, prices change rapidly, and Hijri calendar cultural sensitivity is paramount. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-504`** | `REJECT_DUPLICATE` | Screened UI/Format Synonym (`Merged Variant: Minor UI/Format Synonym of AMP-034 (Search Engine Optimization (SEO))`) | Consolidated into parent workflow without duplicate file inflation. | `SCREENED_DUPLICATE_VARIANT` |

### Context-Specific Execution Knobs Across the 5 MENA Operating Environments
1. **Saudi D2C E-Commerce (`Salla / Zid / Riyadh & Jeddah Retail`)**: Enforce `SAR` tax-inclusive pricing (`15% ZATCA VAT`), native `Mada / Apple Pay / Tabby / Tamara` visibility (`AMP-387`), `GAMR Mawthooq` creator verification (`AMP-281`), and White Saudi Khaleeji orthography (`AMP-002`, `AMP-177`).
2. **Egyptian E-Commerce & Social Commerce (`Shopify / WooCommerce / Cairo & Alexandria`)**: Use each merchant’s own order and payment data to assess Cash on Delivery (`COD`), mobile wallets, InstaPay, Fawry, `valU`, address fields, and pre-dispatch WhatsApp confirmation. Verify current provider terms and local requirements before implementation.
3. **UAE & Multi-Market GCC Enterprise / Retail (`Dubai, Abu Dhabi, Doha, Kuwait`)**: Separate high-CPM UAE/Qatar budgets from lower-CPM markets (`AMP-061`), enforce UAE `TDRA` `9 PM – 7 AM` SMS curfew + `AD-` prefix (`AMP-442`), UAE Media Council permits (`AMP-282`), and bilingual Arabic/English canonical & currency parity (`current applicable UAE VAT`, `current applicable Qatar/Kuwait tax rules`, 3-decimal `KWD` `AMP-239`).
4. **High-Trust & Regulated Verticals (`Healthcare SFDA/MOH/EDA, FinTech SAMA/FRA, Real Estate REGA/RERA`)**: Strip all therapeutic/cure verbs (`AMP-176`, `AMP-286`), display mandatory `MOH/SFDA/DHA/EDA/Fal/Trakheesi` permit numbers (`AMP-070`), and route budgets to high-credibility channels (`AMP-290`, `AMP-339`).
5. **Seasonal Peak Operations (`Ramadan, Eid, White/Yellow Friday, Saudi Founding/National Day`)**: Lock Hijri-Gregorian overlaps (`Feb 2027 Ramadan x Saudi Founding Day x Kuwait National Day` `AMP-125`), pre-schedule GMC `sale_price_effective_date` 48h ahead (`AMP-063`), verify 30-day baseline discount permits (`AMP-064`), and disable Meta Advantage+ auto-music (`AMP-065`).

## 6. Worked Example Summary & Failure Recovery (`ملخص المثال التطبيقي وخطة الإنقاذ`)

*(Full step-by-step worked example with annotated human edits is also provided in `EXAMPLE.md`)*

- **Sample Input Brief**: - **Raw Verbose AI Title (`164` characters)**:
  `ماكينة قهوة إسبريسو وكابتشينو احترافية من ديلونجي ديديكا، مضخة ضغط عالي 15 بار مع عصا تبخير الحليب لتحضير اللاتيه والقهوة المختصة في المنزل والمكتب، لون فضي ستانلس ستيل`
- **Human Review & Key Edits Applied**: 1. **Character Count Verification**: Verified `len(title_ar) == 62` (`<= 75` pass) and `len(title_en) == 66` (`<= 75` pass).
2. **Model Number Placement**: Kept `EC685.M` in the Arabic title because Saudi buyers frequently search the exact De'Longhi model code, and moved `"كابتشينو ولاتيه"` into `Generic Keywords` (`AMP-009`).
- **Final Usable Output**: - **`Amazon.sa` Arabic Title (`62 / 75` chars)**:
  `ديلونجي ماكينة إسبريسو ديديكا 15 بار مع مبخر حليب، فضي EC685.M`
- **`Amazon.sa` English Title (`66 / 75` chars)**:
  `De'Longhi Dedica Espresso Machine 15 Bar with Milk Frother, Silver`
- **What Can Go Wrong**: A seller uploads a 150-character keyword-stuffed title generated by a generic ChatGPT prompt; after 14 days in Seller Central's 'Review listing updates', Amazon's AI overwrites the title with an awkward machine translation that omits the pack size.
- **Correction & Fallback**: Audit Seller Central -> `Inventory -> Review Listing Updates` weekly and proactively compress all titles to `<= 75` characters using the 4-Slot Formula.

## 7. Measurement Plan & Hypothesis Framing (`خطة القياس والضوابط الإحصائية`)

- **Primary Metric to Track**: Zero title suppression alerts or unapproved Amazon auto-rewrites in Seller Central (`Review Listing Updates`), plus mobile search result CTR.
- **Baseline Definition**: Count of ASINs flagged for title length violations in Seller Central Account Health / Listing Quality Dashboard.
- **Observation Window**: 14–21 days post-update. *(Must span full 7/14-day weekly cycles and account for 25th–30th monthly salary windows per `AMP-391`)*.
- **What Cannot Be Concluded (Boundary)**: Compliant titles prevent suppression and truncation, while Buy Box share and ad rank still depend on fulfillment (FBA) and pricing.
