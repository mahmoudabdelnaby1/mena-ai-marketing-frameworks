# FW-005: Bilingual Storefront `/en/` Title & Meta Tag Localization Workflow (Salla & Zid)
## مسار عمل تعريب وترجمة وسوم العناوين (`<title>`) والميتا للصفحات الإنجليزية في متاجر سلة وزد

- **Consolidated Contextual Child IDs (`MERGE_INTO_EXISTING`)**: `AMP-017`, `AMP-029`, `AMP-041`, `AMP-053`
- **Selected Artifact Type**: `OPERATING_FRAMEWORK`
- **Intended Audience**: SEO Specialist, E-Commerce Manager, Content Strategist, Technical SEO Lead
- **Target Markets & Languages**: Egypt & GCC (`Saudi Arabia, UAE, Kuwait, Qatar, Bahrain, Oman`) — Bilingual Arabic (`Egyptian Ammiya`, `Saudi/Gulf Khaleeji`, `White MSA`) + English
- **Version**: `1.2` | **Last Reviewed**: `2026-10-25` | **Status**: `READY_FOR_REVIEW`

## 1. Plain-Language Promise & Why This Artifact Form Fits the Job

- **What You Can Make or Decide (EN)**: Eliminate untranslated Arabic-script `<title>` tags on `/en/` storefront pages through a structured bilingual catalog export-translate-validate workflow.
- **ما الذي يمكنك إنجازه أو حسمه بهذه الأداة (AR)**: القضاء على بقاء وسوم `<title>` باللغة العربية داخل الصفحات الإنجليزية (`/en/`) عبر مسار عمل منظم لتصدير وترجمة وتدقيق حقول الـ SEO لكل لغة.
- **Why `OPERATING_FRAMEWORK` Fits This User Job (EN)**: Because 4 of 6 Salla stores and 4 of 5 Zid stores with English enabled served Arabic-script `<title>` tags on `/en/` URLs in the Oct 2026 audit, teams need an end-to-end OPERATING_FRAMEWORK connecting catalog export, structured LLM JSON localization, and post-import HTML verification.
- **لماذا يناسب شكل `OPERATING_FRAMEWORK` هذه المهمة (AR)**: نظراً لأن 4 من 6 متاجر سلة و4 من 5 متاجر زد مفعلة للإنجليزية تركت وسم `<title>` بالعربية على صفحات `/en/` (فحص أكتوبر 2026)، يحتاج الفريق إلى إطار تشغيلي متكامل يربط تصدير الكتالوج بالترجمة المهيكلة والفحص النهائي.

## 2. "Use It When" Trigger, Boundaries & Exact Inputs to Prepare

- **Use It When (EN)**: Use when managing bilingual (`/ar/` + `/en/`) product catalogs on Salla, Zid, Shopify, or WooCommerce in KSA, UAE, Qatar, Kuwait, or Egypt.
- **متى تستخدم هذه الأداة (AR)**: يُستخدم عند إدارة كتالوجات منتجات ثنائية اللغة (`/ar/` و`/en/`) على سلة أو زد أو شوبيفاي أو ووكومرس في الخليج ومصر.
- **When NOT to Use It (EN)**: Do not run automated title updates without locking brand names, model numbers, and weight/volume units (`ml`, `g`, `SAR`, `AED`, `EGP`).
- **متى لا تستخدم هذه الأداة (AR)**: لا تقم بتحديث العناوين آلياً دون تثبيت أسماء العلامات التجارية وأرقام الموديلات ووحدات القياس والوزن (`مل`، `جرام`، `ر.س`).

### Exact Inputs to Prepare Before Starting (`المدخلات المطلوب تجهيزها`)
1. Catalog SEO CSV/Excel export containing both `title_ar`, `seo_title_ar` and `title_en`, `seo_title_en` columns
2. Brand Glossary (official English spelling of Arabic brand names, e.g., `عبدالصمد القرشي` -> `Abdul Samad Al Qurashi`)
3. Target character caps (`50–60` characters for Google SERP `<title>`, `<=75` chars if syncing to Amazon.sa/ae)

### Privacy-Safe Data Handling (`ضوابط الخصوصية وحماية البيانات الشخصية PDPL`)
- **Strict PII Redaction Before Prompting**: Under Saudi PDPL (Art. 25), UAE Federal Decree-Law No. 45 of 2021, Qatar Law No. 13 of 2016, and Egypt Law No. 151 of 2020, **never paste raw customer names, unhashed mobile numbers (`+9665...` / `+201...`), email addresses, national IDs, or private WhatsApp transcripts into public/consumer LLM interfaces**. Use anonymized placeholders (`{first_name}`, `ORD_10045`) during prompt testing and restrict live customer data to zero-data-retention enterprise API endpoints or local deterministic scripts.

## 3. The Directly Usable Artifact (`الأداة التطبيقية الجاهزة للنسخ والتنفيذ`)

### 4-Stage Bilingual `<title>` & Meta Localization Workflow

#### Stage 1: Detect Arabic Script Leaking into `/en/` `<title>` Tags
Run this regex check against your `/en/` sitemap URLs or catalog CSV column `seo_title_en`:
```python
import re
ARABIC_SCRIPT_RE = re.compile(r"[؀-ۿ]")

def has_arabic_leak(en_title: str) -> bool:
    return bool(ARABIC_SCRIPT_RE.search(en_title or ""))
```
- **Gate 1 Rule**: Any `/en/` URL where `seo_title_en` is empty (causing the platform to fall back to `seo_title_ar`) or matches `[؀-ۿ]` is flagged for batch localization.

#### Stage 2: Structured LLM Localization Prompt (JSON Schema Enforced)
```xml
<system_role>
You are a Bilingual MENA E-Commerce SEO Specialist. Convert Arabic product SEO metadata into natural, commercial English for GCC & Egypt expat shoppers.
</system_role>
<rules>
1. Output `seo_title_en` strictly in Latin script (`0` Arabic characters matching `[؀-ۿ]`).
2. Keep `seo_title_en` between 45 and 60 characters including brand suffix.
3. Preserve exact SKU capacities (`100ml`, `250g`, `500W`) and official brand transliterations from the Brand Glossary.
4. Include commercial intent modifiers relevant to English-speaking GCC/Egypt buyers (e.g., "Fast Delivery in Riyadh & Dubai", "Authentic", "Shop Online").
</rules>
```

#### Stage 3: Platform Field Mapping Verification (Salla & Zid Specific)
- [ ] **In Salla**: Open Product -> `تحسين محركات البحث (SEO)` -> Switch the language toggle at the top of the modal from `العربية` to `EN (الإنجليزية)` -> Populate `عنوان الصفحة (Page Title)` and `وصف الصفحة (Page Description)` explicitly for `EN`. Leaving `EN` SEO fields blank causes Salla to serve the Arabic `<title>` on `/en/`!
- [ ] **In Zid**: Open Product -> `خيارات تحسين محركات البحث` -> Populate the English localization fields via the Multilingual App / CSV import template before publishing.

#### Stage 4: Post-Import Live HTML Verification
- [ ] Fetch 10 sampled `/en/` product URLs and verify `has_arabic_leak(title_tag) == False`.

## 4. Model & Platform Capability Branches (`فروع قدرات النماذج والمنصات والبدائل الاحتياطية`)

| System / Platform | Capability Status | Official Documentation & Access Date | Operational Constraint in Egypt & GCC | Fallback When Feature/Modality Is Unavailable |
| :--- | :--- | :--- | :--- | :--- |
| **Salla & Zid Multilingual SEO Title Fields** | `supported` | [Official Reference](https://voctos.net/salla-zid-store-seo-audit/) (`2026-10-25`) | Both platforms support separate English SEO titles, but 4/6 Salla stores and 4/5 Zid stores in the Oct 2026 audit left the English SEO title unmapped, defaulting to Arabic. | Enforce regex check `[؀-ۿ]` on all `/en/` `<title>` tags after every catalog update. |

## 5. Consolidated Regional & Vertical Adaptation Matrix (`دمج الأنماط السياقية الفرعية بدون حشو`)

Per Agent 2 v1.2's anti-padding rule, the following **4 cross-verified contextual synthesis patterns** and **0 screened duplicate variants** share this core mechanism and are consolidated directly into this source-of-truth framework:

| Child Pattern ID | Disposition | Regional / Sector Operating Context | Specific Adaptation & Guardrail Integrated in This Asset | Evidence Tier |
| :--- | :--- | :--- | :--- | :--- |
| **`AMP-017`** | `MERGE_INTO_EXISTING` | Egyptian E-Commerce & Social Commerce (Shopify / WooCommerce / Cairo & Alexandria) | Stores operating solely in Arabic without an /en/ subfolder.; Specifically impacts Egyptian brands operating in EGP where merchant-specific payment mix from recent order records, Mobile Wallets (Vodafone Cash), InstaPay, and Fawry dominate. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-029`** | `MERGE_INTO_EXISTING` | UAE & Multi-Market GCC Enterprise / Retail (Dubai, Abu Dhabi, Doha, Kuwait) | Stores operating solely in Arabic without an /en/ subfolder.; Specifically impacts bilingual Arabic/English campaigns in high-CPM, expat-dense Gulf markets under UAE PDPL / TDRA and Qatari regulations. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-041`** | `MERGE_INTO_EXISTING` | High-Trust & Regulated Verticals (Healthcare/SFDA/EDA, Fintech/SAMA/FRA, Real Estate) | Stores operating solely in Arabic without an /en/ subfolder.; Specifically impacts regulated claims requiring SFDA, EDA, MOH, SAMA, FRA, or RERA compliance pre-clearance and strict hallucination guardrails. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-053`** | `MERGE_INTO_EXISTING` | Seasonal Peak Operations (Ramadan, Eid, White/Yellow Friday, Saudi Founding/National Day) | Stores operating solely in Arabic without an /en/ subfolder.; Specifically impacts high-velocity seasonal surges where CPMs jump 40-70%, prices change rapidly, and Hijri calendar cultural sensitivity is paramount. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |

### Context-Specific Execution Knobs Across the 5 MENA Operating Environments
1. **Saudi D2C E-Commerce (`Salla / Zid / Riyadh & Jeddah Retail`)**: Enforce `SAR` tax-inclusive pricing (`15% ZATCA VAT`), native `Mada / Apple Pay / Tabby / Tamara` visibility (`AMP-387`), `GAMR Mawthooq` creator verification (`AMP-281`), and White Saudi Khaleeji orthography (`AMP-002`, `AMP-177`).
2. **Egyptian E-Commerce & Social Commerce (`Shopify / WooCommerce / Cairo & Alexandria`)**: Use each merchant’s own order and payment data to assess Cash on Delivery (`COD`), mobile wallets, InstaPay, Fawry, `valU`, address fields, and pre-dispatch WhatsApp confirmation. Verify current provider terms and local requirements before implementation.
3. **UAE & Multi-Market GCC Enterprise / Retail (`Dubai, Abu Dhabi, Doha, Kuwait`)**: Separate high-CPM UAE/Qatar budgets from lower-CPM markets (`AMP-061`), enforce UAE `TDRA` `9 PM – 7 AM` SMS curfew + `AD-` prefix (`AMP-442`), UAE Media Council permits (`AMP-282`), and bilingual Arabic/English canonical & currency parity (`current applicable UAE VAT`, `current applicable Qatar/Kuwait tax rules`, 3-decimal `KWD` `AMP-239`).
4. **High-Trust & Regulated Verticals (`Healthcare SFDA/MOH/EDA, FinTech SAMA/FRA, Real Estate REGA/RERA`)**: Strip all therapeutic/cure verbs (`AMP-176`, `AMP-286`), display mandatory `MOH/SFDA/DHA/EDA/Fal/Trakheesi` permit numbers (`AMP-070`), and route budgets to high-credibility channels (`AMP-290`, `AMP-339`).
5. **Seasonal Peak Operations (`Ramadan, Eid, White/Yellow Friday, Saudi Founding/National Day`)**: Lock Hijri-Gregorian overlaps (`Feb 2027 Ramadan x Saudi Founding Day x Kuwait National Day` `AMP-125`), pre-schedule GMC `sale_price_effective_date` 48h ahead (`AMP-063`), verify 30-day baseline discount permits (`AMP-064`), and disable Meta Advantage+ auto-music (`AMP-065`).

## 6. Worked Example Summary & Failure Recovery (`ملخص المثال التطبيقي وخطة الإنقاذ`)

*(Full step-by-step worked example with annotated human edits is also provided in `EXAMPLE.md`)*

- **Sample Input Brief**: - **Store**: Saudi Oud & Bakhoor Store on Zid (`https://bakhoor-example.sa/en/products/royal-cambodi-oud`).
- **Current Broken `/en/` `<title>`**: `<title>عود كمبودي ملكي فاخر 50 جرام - متجر طيب</title>` (100% Arabic script on `/en/` URL).
- **Human Review & Key Edits Applied**: 1. **Glossary Check**: Confirmed the brand's preferred English spelling is `"Bakhoor"` rather than `"Bukhoor"` to match their Google Merchant Center English feed.
2. **Zid Field Check**: Imported into Zid's English SEO Title field and verified live HTML `<title>` on `/en/products/royal-cambodi-oud`.
- **Final Usable Output**: - **Live `/en/` `<title>` (60 chars)**: `Royal Cambodi Oud Wood Chips 50g | Authentic Bakhoor - Tayeb`
- **Live `/ar/` `<title>` (52 chars)**: `عود كمبودي ملكي فاخر 50 جرام | توصيل سريع - متجر طيب`
- **What Can Go Wrong**: A marketer translates the main product name (`Product Title`) in the English tab of Salla/Zid, but forgets to switch the language tab inside the separate bottom `SEO Settings` box—so the page `<h1>` is in English while `<title>` remains in Arabic.
- **Correction & Fallback**: Always audit the rendered `<title>` element in raw HTML (`curl -s URL | grep '<title>'`), never just the product name column in the dashboard.

## 7. Measurement Plan & Hypothesis Framing (`خطة القياس والضوابط الإحصائية`)

- **Primary Metric to Track**: Percentage of `/en/` URLs with zero Arabic characters in `<title>`, plus English-query CTR in Google Search Console.
- **Baseline Definition**: Pre-fix count of `/en/` pages serving Arabic `<title>` tags.
- **Observation Window**: 14–28 days post-crawl. *(Must span full 7/14-day weekly cycles and account for 25th–30th monthly salary windows per `AMP-391`)*.
- **What Cannot Be Concluded (Boundary)**: Fixing `/en/` `<title>` tags must be paired with `AMP-004` (self-referencing `/en/` canonicals) on Salla to take effect in Google Search.
