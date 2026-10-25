# End-to-End Worked Example & Failure Recovery — `FW-002` (`AMP-002`)

- **Framework**: Arabic Orthographic Normalization Checklist (Hamza, Taa Marbuta, Alef Maqsura & Indic Digits)
- **العنوان بالعربية**: قائمة فحص تطبيع الحروف والأرقام العربية في البحث الداخلي والـ SEO (الهمزات، التاء المربوطة، الألف المقصورة، والأرقام الهندية)
- **Selected Artifact Type**: `CHECKLIST`
- **Disclaimer**: *All scenarios, brand names, SKU codes, and metrics below are original, realistic illustrative examples for MENA practitioner training and are never represented as verified client outcomes.*

## 1. Realistic Sample Brief / Input (`المدخلات وموجز الحالة العملية`)

- **Store Context**: Saudi Perfume & Abaya Store on Salla + Custom Shopify Headless Storefront in Egypt.
- **Problem Observed**: AI generated 400 product titles using strict MSA (`"أطقم عطور نسائية فاخرة"`). Mobile shoppers typing `"اطقم عطور نسائيه"` on iOS Arabic keyboards hit a "لا توجد منتجات مطابقة" (No matching products) screen on the headless storefront.

## 2. Initial Generated / Completed Output (`المخرج الأولي عند تطبيق الأداة`)

- Test 1 (`"أطقم عطور نسائية"`): 28 products returned.
- Test 2 (`"اطقم عطور نسائيه"`): 0 products returned (FAIL — Alef with Hamza `أ` and Taa Marbuta `ة` mismatch).
- Test 3 (`"عطر ١٠٠ مل"`): 0 products returned (FAIL — Arabic-Indic digits `١٠٠` not mapped to `100`).

## 3. Human Review & Localization/Technical Edits (`المراجعة البشرية والتعديلات الرقابية والتقنية`)

1. **Search Pipeline Fix**: Deployed `normalizeArabicSearch()` on both the Algolia/Shopify search query hook and the indexed `searchable_title_normalized` attribute, while preserving the grammatically correct visible `title` (`"أطقم عطور نسائية فاخرة - 100 مل"`).
2. **Salla Storefront Tag Enrichment**: For the Salla store (where backend Elasticsearch analyzers are platform-managed), added a pre-upload CSV script that appends the normalized no-Hamza/Haa variant into the Product Tags (`الوسوم`) column.

## 4. Final Reviewed Example Outcome (`النتيجة النهائية الجاهزة للتنفيذ`)

- Query `"اطقم عطور نسائيه ١٠٠ مل"` → Normalized internally to `"اطقم عطور نساءيه 100 مل"` → Matches all 28 products with 0ms additional latency.
- Visible storefront typography remains 100% grammatically sound (`أطقم عطور نسائية فاخرة`).

## 5. What Can Go Wrong & Specific Correction / Fallback (`حالة الفشل المحتملة وخطة الإنقاذ والبديل`)

- **Common Failure Mode (`ما الذي قد يسير بشكل خاطئ؟`)**:
  A developer applies `normalizeArabicSearch()` directly to the visible database `product.title` column instead of a shadow `search_index_text` column, corrupting visible storefront headings with spelling errors (`نسائيه` instead of `نسائية`).
- **Specific Correction & Non-AI / Platform Fallback (`الإصلاح المحدد والبديل الآمن`)**:
  Enforce Dual-Field Separation: never mutate display fields (`title`, `description_html`). Store normalized text exclusively in `searchable_text_normalized` or hidden synonym tags.
