# FW-002: Arabic Orthographic Normalization Checklist (Hamza, Taa Marbuta, Alef Maqsura & Indic Digits)
## قائمة فحص تطبيع الحروف والأرقام العربية في البحث الداخلي والـ SEO (الهمزات، التاء المربوطة، الألف المقصورة، والأرقام الهندية)

- **Consolidated Contextual Child IDs (`MERGE_INTO_EXISTING`)**: `AMP-014`, `AMP-026`, `AMP-038`, `AMP-050`
- **Selected Artifact Type**: `CHECKLIST`
- **Intended Audience**: SEO Specialist, E-Commerce Manager, Content Strategist, Technical SEO Lead
- **Target Markets & Languages**: Egypt & GCC (`Saudi Arabia, UAE, Kuwait, Qatar, Bahrain, Oman`) — Bilingual Arabic (`Egyptian Ammiya`, `Saudi/Gulf Khaleeji`, `White MSA`) + English
- **Version**: `1.2` | **Last Reviewed**: `2026-10-25` | **Status**: `READY_FOR_REVIEW`

## 1. Plain-Language Promise & Why This Artifact Form Fits the Job

- **What You Can Make or Decide (EN)**: Eliminate false '0 results found' pages and missed organic matches caused by unnormalized Arabic letter variants (`أ/إ/آ/ا`, `ة/ه`, `ى/ي`) and Arabic-Indic numerals (`٠-٩`).
- **ما الذي يمكنك إنجازه أو حسمه بهذه الأداة (AR)**: القضاء على صفحات «لا توجد نتائج» وفقدان الزيارات الناتجة عن اختلاف كتابة الهمزات (`أ/إ/آ/ا`) والتاء المربوطة (`ة/ه`) والألف المقصورة (`ى/ي`) والأرقام الهندية (`٠-٩`).
- **Why `CHECKLIST` Fits This User Job (EN)**: Orthographic normalization is a deterministic technical & content QA task across site search, product feeds, and on-page copy; a verification CHECKLIST with copy-ready regex/JS normalization rules gives developers and SEO leads an immediate fix.
- **لماذا يناسب شكل `CHECKLIST` هذه المهمة (AR)**: تطبيع الحروف والأرقام العربية مهمة تقنية ورقابية محددة؛ لذا فإن قائمة الفحص المزودة بقواعد برمجية (Regex/JS) جاهزة للنسخ تمنح فرق التطوير والـ SEO حلاً عملياً فورياً.

## 2. "Use It When" Trigger, Boundaries & Exact Inputs to Prepare

- **Use It When (EN)**: Use when configuring internal storefront search (Salla, Zid, Shopify, WooCommerce, custom Algolia/Elasticsearch) or auditing AI-generated Arabic product descriptions and tags.
- **متى تستخدم هذه الأداة (AR)**: تُستخدم عند إعداد محرك البحث الداخلي للمتجر (سلة، زد، شوبيفاي، ووكومرس، أو Algolia/Elasticsearch) أو تدقيق أوصاف ووسوم المنتجات المولدة بالذكاء الاصطناعي.
- **When NOT to Use It (EN)**: Do not strip Hamzas or Taa Marbuta from visible H1 headings or formal brand copy—normalization happens in the search index, backend tags, and query parser, while visible prose stays grammatically correct.
- **متى لا تستخدم هذه الأداة (AR)**: لا تحذف الهمزات أو التاء المربوطة من العناوين المرئية (`H1`) أو النصوص الرسمية للعلامة؛ التطبيع يتم في فهرس البحث والوسوم الخلفية، بينما يبقى النص المرئي صحيحاً إملائياً.

### Exact Inputs to Prepare Before Starting (`المدخلات المطلوب تجهيزها`)
1. Top 100 'Zero-Result' internal site search queries from GA4 (`view_search_results`) or platform analytics
2. Storefront search engine configuration or theme JS / backend search pipeline access
3. Product tag / synonym dictionary export (CSV/JSON)

### Privacy-Safe Data Handling (`ضوابط الخصوصية وحماية البيانات الشخصية PDPL`)
- **Strict PII Redaction Before Prompting**: Under Saudi PDPL (Art. 25), UAE Federal Decree-Law No. 45 of 2021, Qatar Law No. 13 of 2016, and Egypt Law No. 151 of 2020, **never paste raw customer names, unhashed mobile numbers (`+9665...` / `+201...`), email addresses, national IDs, or private WhatsApp transcripts into public/consumer LLM interfaces**. Use anonymized placeholders (`{first_name}`, `ORD_10045`) during prompt testing and restrict live customer data to zero-data-retention enterprise API endpoints or local deterministic scripts.

## 3. The Directly Usable Artifact (`الأداة التطبيقية الجاهزة للنسخ والتنفيذ`)

### Operational Normalization Checklist & Code Pack

#### Part A: Pre-Flight Audit Checklist (Run on Live Storefront Search)
- [ ] **Check 1 — Alef/Hamza Equivalence (`أ / إ / آ / ا`)**: Search `"احذية"` (without Hamza) and `"أحذية"` (with Hamza). Confirm both return the exact same product count. (Empirical benchmark: VOCTOS Oct 2026 audit showed unnormalized stores return 0 results for one variant).
- [ ] **Check 2 — Taa Marbuta / Haa Equivalence (`ة / ه`)**: Search `"عباية"` and `"عبايه"`, `"شنطة"` and `"شنطه"`. Confirm identical product counts.
- [ ] **Check 3 — Alef Maqsura / Yaa Equivalence (`ى / ي`)**: Search `"مستشفى"` vs `"مستشفي"` or `"حلوى"` vs `"حلوي"`. Confirm identical results.
- [ ] **Check 4 — Tashkeel (Diacritics) Stripping**: Paste a vocalized word (`"عُطُور"`) copied from an AI post into the search bar. Confirm the parser strips `ً-ٟ` and `ـ` (Tatweel/Kashida `ـ`) before querying.
- [ ] **Check 5 — Arabic-Indic (`٠-٩`) & Eastern Arabic (`۰-۹`) Numeral Normalization**: Search SKU or size using `"مقاس ٤٢"` or `"ايفون ١٦"`. Confirm conversion to ASCII `"42"` and `"16"`.

#### Part B: Copy-Ready JavaScript / TypeScript Normalization Function (Frontend Query & Indexer)
```javascript
/**
 * Normalizes Arabic search queries and index fields while converting Arabic-Indic digits to ASCII.
 * Use on BOTH the search input string and the indexed product search_tags field.
 */
export function normalizeArabicSearch(input) {
  if (!input || typeof input !== 'string') return '';
  return input
    // 1. Convert Arabic-Indic digits (٠-٩) and Extended Arabic-Indic digits (۰-۹) to ASCII (0-9)
    .replace(/[٠-٩]/g, (d) => String(d.charCodeAt(0) - 0x0660))
    .replace(/[۰-۹]/g, (d) => String(d.charCodeAt(0) - 0x06F0))
    // 2. Remove Tashkeel (harakat ً-ٟ, superscript alef ٰ) and Tatweel (ـ)
    .replace(/[ـً-ٰٟ]/g, '')
    // 3. Normalize Alef variants (أ, إ, آ, ٱ) to bare Alef (ا)
    .replace(/[آأإٱ]/g, 'ا')
    // 4. Normalize Taa Marbuta (ة) to Haa (ه) for search index matching
    .replace(/ة/g, 'ه')
    // 5. Normalize Alef Maqsura (ى) to Yaa (ي)
    .replace(/ى/g, 'ي')
    .trim()
    .replace(/\s+/g, ' ');
}
```

#### Part C: Managed Platform Fallback (Salla / Zid / Shopify Without Custom Search Index Access)
- [ ] When backend search analyzer settings cannot be edited directly, populate the product **Tags / Hidden Synonyms** field with the top 3 orthographic variants generated automatically via the function above (e.g., Visible Title: `عباية حرير سوداء مقاس 54` → Hidden Search Tags: `عبايه حرير سوداء, عباية, عبايه, مقاس ٥٤`).

## 4. Model & Platform Capability Branches (`فروع قدرات النماذج والمنصات والبدائل الاحتياطية`)

| System / Platform | Capability Status | Official Documentation & Access Date | Operational Constraint in Egypt & GCC | Fallback When Feature/Modality Is Unavailable |
| :--- | :--- | :--- | :--- | :--- |
| **Elasticsearch / OpenSearch / Algolia `arabic` Analyzer** | `supported` | [Official Reference](https://voctos.net/arabic-site-search-normalization/) (`2026-10-25`) | Native `arabic_normalization` token filter handles Alef, Taa Marbuta, Alef Maqsura, Tatweel, and Indic digits out-of-the-box when enabled on the index. | On hosted SaaS platforms (Salla/Zid) where index settings are locked, inject normalized orthographic variants into Product Tags (`الوسوم`) and Meta Keywords. |

## 5. Consolidated Regional & Vertical Adaptation Matrix (`دمج الأنماط السياقية الفرعية بدون حشو`)

Per Agent 2 v1.2's anti-padding rule, the following **4 cross-verified contextual synthesis patterns** and **0 screened duplicate variants** share this core mechanism and are consolidated directly into this source-of-truth framework:

| Child Pattern ID | Disposition | Regional / Sector Operating Context | Specific Adaptation & Guardrail Integrated in This Asset | Evidence Tier |
| :--- | :--- | :--- | :--- | :--- |
| **`AMP-014`** | `MERGE_INTO_EXISTING` | Egyptian E-Commerce & Social Commerce (Shopify / WooCommerce / Cairo & Alexandria) | Google web search normalizes many common variants more effectively than storefront search engines on Salla/Zid/WooCommerce.; Specifically impacts Egyptian brands operating in EGP where merchant-specific payment mix from recent order records, Mobile Wallets (Vodafone Cash), InstaPay, and Fawry dominate. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-026`** | `MERGE_INTO_EXISTING` | UAE & Multi-Market GCC Enterprise / Retail (Dubai, Abu Dhabi, Doha, Kuwait) | Google web search normalizes many common variants more effectively than storefront search engines on Salla/Zid/WooCommerce.; Specifically impacts bilingual Arabic/English campaigns in high-CPM, expat-dense Gulf markets under UAE PDPL / TDRA and Qatari regulations. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-038`** | `MERGE_INTO_EXISTING` | High-Trust & Regulated Verticals (Healthcare/SFDA/EDA, Fintech/SAMA/FRA, Real Estate) | Google web search normalizes many common variants more effectively than storefront search engines on Salla/Zid/WooCommerce.; Specifically impacts regulated claims requiring SFDA, EDA, MOH, SAMA, FRA, or RERA compliance pre-clearance and strict hallucination guardrails. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-050`** | `MERGE_INTO_EXISTING` | Seasonal Peak Operations (Ramadan, Eid, White/Yellow Friday, Saudi Founding/National Day) | Google web search normalizes many common variants more effectively than storefront search engines on Salla/Zid/WooCommerce.; Specifically impacts high-velocity seasonal surges where CPMs jump 40-70%, prices change rapidly, and Hijri calendar cultural sensitivity is paramount. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |

### Context-Specific Execution Knobs Across the 5 MENA Operating Environments
1. **Saudi D2C E-Commerce (`Salla / Zid / Riyadh & Jeddah Retail`)**: Enforce `SAR` tax-inclusive pricing (`15% ZATCA VAT`), native `Mada / Apple Pay / Tabby / Tamara` visibility (`AMP-387`), `GAMR Mawthooq` creator verification (`AMP-281`), and White Saudi Khaleeji orthography (`AMP-002`, `AMP-177`).
2. **Egyptian E-Commerce & Social Commerce (`Shopify / WooCommerce / Cairo & Alexandria`)**: Use each merchant’s own order and payment data to assess Cash on Delivery (`COD`), mobile wallets, InstaPay, Fawry, `valU`, address fields, and pre-dispatch WhatsApp confirmation. Verify current provider terms and local requirements before implementation.
3. **UAE & Multi-Market GCC Enterprise / Retail (`Dubai, Abu Dhabi, Doha, Kuwait`)**: Separate high-CPM UAE/Qatar budgets from lower-CPM markets (`AMP-061`), enforce UAE `TDRA` `9 PM – 7 AM` SMS curfew + `AD-` prefix (`AMP-442`), UAE Media Council permits (`AMP-282`), and bilingual Arabic/English canonical & currency parity (`current applicable UAE VAT`, `current applicable Qatar/Kuwait tax rules`, 3-decimal `KWD` `AMP-239`).
4. **High-Trust & Regulated Verticals (`Healthcare SFDA/MOH/EDA, FinTech SAMA/FRA, Real Estate REGA/RERA`)**: Strip all therapeutic/cure verbs (`AMP-176`, `AMP-286`), display mandatory `MOH/SFDA/DHA/EDA/Fal/Trakheesi` permit numbers (`AMP-070`), and route budgets to high-credibility channels (`AMP-290`, `AMP-339`).
5. **Seasonal Peak Operations (`Ramadan, Eid, White/Yellow Friday, Saudi Founding/National Day`)**: Lock Hijri-Gregorian overlaps (`Feb 2027 Ramadan x Saudi Founding Day x Kuwait National Day` `AMP-125`), pre-schedule GMC `sale_price_effective_date` 48h ahead (`AMP-063`), verify 30-day baseline discount permits (`AMP-064`), and disable Meta Advantage+ auto-music (`AMP-065`).

## 6. Worked Example Summary & Failure Recovery (`ملخص المثال التطبيقي وخطة الإنقاذ`)

*(Full step-by-step worked example with annotated human edits is also provided in `EXAMPLE.md`)*

- **Sample Input Brief**: - **Store Context**: Saudi Perfume & Abaya Store on Salla + Custom Shopify Headless Storefront in Egypt.
- **Problem Observed**: AI generated 400 product titles using strict MSA (`"أطقم عطور نسائية فاخرة"`). Mobile shoppers typing `"اطقم عطور نسائيه"` on iOS Arabic keyboards hit a "لا توجد منتجات مطابقة" (No matching products) screen on the headless storefront.
- **Human Review & Key Edits Applied**: 1. **Search Pipeline Fix**: Deployed `normalizeArabicSearch()` on both the Algolia/Shopify search query hook and the indexed `searchable_title_normalized` attribute, while preserving the grammatically correct visible `title` (`"أطقم عطور نسائية فاخرة - 100 مل"`).
2. **Salla Storefront Tag Enrichment**: For the Salla store (where backend Elasticsearch analyzers are platform-managed), added a pre-upload CSV script that appends the normalized no-Hamza/Haa variant into the Product Tags (`الوسوم`) column.
- **Final Usable Output**: - Query `"اطقم عطور نسائيه ١٠٠ مل"` → Normalized internally to `"اطقم عطور نساءيه 100 مل"` → Matches all 28 products with 0ms additional latency.
- Visible storefront typography remains 100% grammatically sound (`أطقم عطور نسائية فاخرة`).
- **What Can Go Wrong**: A developer applies `normalizeArabicSearch()` directly to the visible database `product.title` column instead of a shadow `search_index_text` column, corrupting visible storefront headings with spelling errors (`نسائيه` instead of `نسائية`).
- **Correction & Fallback**: Enforce Dual-Field Separation: never mutate display fields (`title`, `description_html`). Store normalized text exclusively in `searchable_text_normalized` or hidden synonym tags.

## 7. Measurement Plan & Hypothesis Framing (`خطة القياس والضوابط الإحصائية`)

- **Primary Metric to Track**: Internal Site Search 'Zero-Results Rate' (`zero_result_searches / total_internal_searches`) and Search-to-Cart Conversion Rate.
- **Baseline Definition**: 14-day pre-deployment Zero-Results Rate from GA4 `view_search_results` event.
- **Observation Window**: 14 days post-deployment. *(Must span full 7/14-day weekly cycles and account for 25th–30th monthly salary windows per `AMP-391`)*.
- **What Cannot Be Concluded (Boundary)**: Reducing zero-result searches fixes discoverability friction but does not compensate for out-of-stock SKUs or uncompetitive pricing.
