# Arabic Orthographic Normalization Checklist (Hamza, Taa Marbuta, Alef Maqsura & Indic Digits)
## <span dir="rtl">قائمة فحص تطبيع الحروف والأرقام العربية في البحث الداخلي والـ SEO (الهمزات، التاء المربوطة، الألف المقصورة، والأرقام الهندية)</span>

> **Asset ID**: `FW-002` (`AMP-002`) | **Artifact Type**: `CHECKLIST` | **Channel**: Search Engine Optimization (SEO) | **Markets**: Egypt & GCC (`KSA, UAE, Kuwait, Qatar, Bahrain, Oman`) | **Version**: `1.2` (`Reviewed 2026-10-25`)

**What You Can Do With This (`ماذا يمكنك أن تنجز بهذه الأداة؟`)**:
- **EN**: Eliminate false '0 results found' pages and missed organic matches caused by unnormalized Arabic letter variants (`أ/إ/آ/ا`, `ة/ه`, `ى/ي`) and Arabic-Indic numerals (`٠-٩`).
- **AR**: <span dir="rtl">القضاء على صفحات «لا توجد نتائج» وفقدان الزيارات الناتجة عن اختلاف كتابة الهمزات (`أ/إ/آ/ا`) والتاء المربوطة (`ة/ه`) والألف المقصورة (`ى/ي`) والأرقام الهندية (`٠-٩`).</span>

## 1. Use It When & Required Inputs (`متى تستخدمها وما المدخلات المطلوبة؟`)

- **Use It When (EN)**: Use when configuring internal storefront search (Salla, Zid, Shopify, WooCommerce, custom Algolia/Elasticsearch) or auditing AI-generated Arabic product descriptions and tags.
- **متى تستخدمها (AR)**: <span dir="rtl">تُستخدم عند إعداد محرك البحث الداخلي للمتجر (سلة، زد، شوبيفاي، ووكومرس، أو Algolia/Elasticsearch) أو تدقيق أوصاف ووسوم المنتجات المولدة بالذكاء الاصطناعي.</span>
- **When NOT to Use It (EN)**: Do not strip Hamzas or Taa Marbuta from visible H1 headings or formal brand copy—normalization happens in the search index, backend tags, and query parser, while visible prose stays grammatically correct.
- **متى لا تستخدمها (AR)**: <span dir="rtl">لا تحذف الهمزات أو التاء المربوطة من العناوين المرئية (`H1`) أو النصوص الرسمية للعلامة؛ التطبيع يتم في فهرس البحث والوسوم الخلفية، بينما يبقى النص المرئي صحيحاً إملائياً.</span>

### Exact Inputs to Prepare (`المدخلات المطلوب تجهيزها قبل البدء`)
- Top 100 'Zero-Result' internal site search queries from GA4 (`view_search_results`) or platform analytics
- Storefront search engine configuration or theme JS / backend search pipeline access
- Product tag / synonym dictionary export (CSV/JSON)

## 2. The Working `CHECKLIST` (`الأداة الكاملة الجاهزة للنسخ والتطبيق الفوري`)

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

## 3. Complete End-to-End Worked Example (`مثال تطبيقي متكامل من المدخلات حتى المراجعة البشرية والنتيجة النهائية`)

*(Illustrative scenario — original example for training, never represented as a verified client outcome)*

### Step A: Sample Brief / Input (`موجز المدخلات`)
- **Store Context**: Saudi Perfume & Abaya Store on Salla + Custom Shopify Headless Storefront in Egypt.
- **Problem Observed**: AI generated 400 product titles using strict MSA (`"أطقم عطور نسائية فاخرة"`). Mobile shoppers typing `"اطقم عطور نسائيه"` on iOS Arabic keyboards hit a "لا توجد منتجات مطابقة" (No matching products) screen on the headless storefront.

### Step B: Initial Output (`المخرج الأولي`)
- Test 1 (`"أطقم عطور نسائية"`): 28 products returned.
- Test 2 (`"اطقم عطور نسائيه"`): 0 products returned (FAIL — Alef with Hamza `أ` and Taa Marbuta `ة` mismatch).
- Test 3 (`"عطر ١٠٠ مل"`): 0 products returned (FAIL — Arabic-Indic digits `١٠٠` not mapped to `100`).

### Step C: Human Review & Edits (`التدقيق البشري والتعديلات`)
1. **Search Pipeline Fix**: Deployed `normalizeArabicSearch()` on both the Algolia/Shopify search query hook and the indexed `searchable_title_normalized` attribute, while preserving the grammatically correct visible `title` (`"أطقم عطور نسائية فاخرة - 100 مل"`).
2. **Salla Storefront Tag Enrichment**: For the Salla store (where backend Elasticsearch analyzers are platform-managed), added a pre-upload CSV script that appends the normalized no-Hamza/Haa variant into the Product Tags (`الوسوم`) column.

### Step D: Final Reviewed Example Outcome (`النتيجة النهائية المعتمدة`)
- Query `"اطقم عطور نسائيه ١٠٠ مل"` → Normalized internally to `"اطقم عطور نساءيه 100 مل"` → Matches all 28 products with 0ms additional latency.
- Visible storefront typography remains 100% grammatically sound (`أطقم عطور نسائية فاخرة`).

## 4. What Can Go Wrong & How to Fix It (`الأخطاء الشائعة وخطة الإنقاذ`)

- **Failure Case (`المشكلة المحتملة`)**: A developer applies `normalizeArabicSearch()` directly to the visible database `product.title` column instead of a shadow `search_index_text` column, corrupting visible storefront headings with spelling errors (`نسائيه` instead of `نسائية`).
- **Correction & Fallback (`الحل الإجرائي والبديل الآمن`)**: Enforce Dual-Field Separation: never mutate display fields (`title`, `description_html`). Store normalized text exclusively in `searchable_text_normalized` or hidden synonym tags.

## 5. Model & Platform Capability Matrix (`مصفوفة قدرات النماذج والمنصات — 2026-10-25`)

| Platform / Model | Status | Official Documentation | MENA Operational Constraint | Fallback |
| :--- | :--- | :--- | :--- | :--- |
| **Elasticsearch / OpenSearch / Algolia `arabic` Analyzer** | `supported` | [Official Docs](https://voctos.net/arabic-site-search-normalization/) (`2026-10-25`) | Native `arabic_normalization` token filter handles Alef, Taa Marbuta, Alef Maqsura, Tatweel, and Indic digits out-of-the-box when enabled on the index. | On hosted SaaS platforms (Salla/Zid) where index settings are locked, inject normalized orthographic variants into Product Tags (`الوسوم`) and Meta Keywords. |

## 6. How to Measure Success (`خطة القياس والضوابط`)

- **Primary Metric**: Internal Site Search 'Zero-Results Rate' (`zero_result_searches / total_internal_searches`) and Search-to-Cart Conversion Rate.
- **Baseline**: 14-day pre-deployment Zero-Results Rate from GA4 `view_search_results` event.
- **Observation Window**: 14 days post-deployment.
- **Interpretation Boundary**: Reducing zero-result searches fixes discoverability friction but does not compensate for out-of-stock SKUs or uncompetitive pricing.

## 7. Primary Sources & Evidence Boundaries (`المصادر الموثقة وحدود الأدلة`)

- [Arabic Site Search Normalization: 20 Arab Online Stores Tested](https://voctos.net/arabic-site-search-normalization/) — *VOCTOS* (Published `2026-10-08`, Accessed `2026-10-25`): Internal site search on Salla and Zid stores fails when shoppers use variant Arabic spellings (Hamza أ/ا, Taa Marbuta ة/ه, Alef Maqsura ى/ي) or Arabic-Indic digits (٠-٩ vs 0-9) that differ from catalog product titles.
- [Arabic Keyword Research for Online Stores: A Practical Guide](https://esafqa.com/en/blog/arabic-keyword-research-guide/) — *Esafqa* (Published `2026-10-08`, Accessed `2026-10-25`): Demonstrates how a single product concept splits across MSA vs dialect, spelling variants, and lexical differences between Saudi Arabia, UAE, and Egypt.
- [The State of Arabic SEO in 2026: What Most Tools Miss](https://crawlix.app/blog/arabic-seo-2026/) — *Crawlix* (Published `2026-04-15`, Accessed `2026-10-25`): Explains why standard western SEO tools undercount Arabic search demand by failing to group morphological prefixes/suffixes and dialect-MSA code-switching ('أفضل سيارة' vs 'أحسن سيارة').
