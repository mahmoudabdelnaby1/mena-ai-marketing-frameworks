# Bilingual Storefront `/en/` Title & Meta Tag Localization Workflow (Salla & Zid)
## <span dir="rtl">مسار عمل تعريب وترجمة وسوم العناوين (`<title>`) والميتا للصفحات الإنجليزية في متاجر سلة وزد</span>

> **Asset ID**: `FW-005` (`AMP-005`) | **Artifact Type**: `OPERATING_FRAMEWORK` | **Channel**: Search Engine Optimization (SEO) | **Markets**: Egypt & GCC (`KSA, UAE, Kuwait, Qatar, Bahrain, Oman`) | **Version**: `1.2` (`Reviewed 2026-10-25`)

**What You Can Do With This (`ماذا يمكنك أن تنجز بهذه الأداة؟`)**:
- **EN**: Eliminate untranslated Arabic-script `<title>` tags on `/en/` storefront pages through a structured bilingual catalog export-translate-validate workflow.
- **AR**: <span dir="rtl">القضاء على بقاء وسوم `<title>` باللغة العربية داخل الصفحات الإنجليزية (`/en/`) عبر مسار عمل منظم لتصدير وترجمة وتدقيق حقول الـ SEO لكل لغة.</span>

## 1. Use It When & Required Inputs (`متى تستخدمها وما المدخلات المطلوبة؟`)

- **Use It When (EN)**: Use when managing bilingual (`/ar/` + `/en/`) product catalogs on Salla, Zid, Shopify, or WooCommerce in KSA, UAE, Qatar, Kuwait, or Egypt.
- **متى تستخدمها (AR)**: <span dir="rtl">يُستخدم عند إدارة كتالوجات منتجات ثنائية اللغة (`/ar/` و`/en/`) على سلة أو زد أو شوبيفاي أو ووكومرس في الخليج ومصر.</span>
- **When NOT to Use It (EN)**: Do not run automated title updates without locking brand names, model numbers, and weight/volume units (`ml`, `g`, `SAR`, `AED`, `EGP`).
- **متى لا تستخدمها (AR)**: <span dir="rtl">لا تقم بتحديث العناوين آلياً دون تثبيت أسماء العلامات التجارية وأرقام الموديلات ووحدات القياس والوزن (`مل`، `جرام`، `ر.س`).</span>

### Exact Inputs to Prepare (`المدخلات المطلوب تجهيزها قبل البدء`)
- Catalog SEO CSV/Excel export containing both `title_ar`, `seo_title_ar` and `title_en`, `seo_title_en` columns
- Brand Glossary (official English spelling of Arabic brand names, e.g., `عبدالصمد القرشي` -> `Abdul Samad Al Qurashi`)
- Target character caps (`50–60` characters for Google SERP `<title>`, `<=75` chars if syncing to Amazon.sa/ae)

## 2. The Working `OPERATING_FRAMEWORK` (`الأداة الكاملة الجاهزة للنسخ والتطبيق الفوري`)

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

## 3. Complete End-to-End Worked Example (`مثال تطبيقي متكامل من المدخلات حتى المراجعة البشرية والنتيجة النهائية`)

*(Illustrative scenario — original example for training, never represented as a verified client outcome)*

### Step A: Sample Brief / Input (`موجز المدخلات`)
- **Store**: Saudi Oud & Bakhoor Store on Zid (`https://bakhoor-example.sa/en/products/royal-cambodi-oud`).
- **Current Broken `/en/` `<title>`**: `<title>عود كمبودي ملكي فاخر 50 جرام - متجر طيب</title>` (100% Arabic script on `/en/` URL).

### Step B: Initial Output (`المخرج الأولي`)
```json
{
  "sku": "OUD-CAM-50G",
  "seo_title_ar": "عود كمبودي ملكي فاخر 50 جرام | توصيل سريع - متجر طيب",
  "seo_title_en": "Royal Cambodi Oud Wood Chips 50g | Authentic Bukhoor - Tayeb",
  "seo_title_en_char_count": 60,
  "arabic_script_detected_in_en": false,
  "meta_description_en": "Shop 100% natural Royal Cambodi Oud chips (50g) in Saudi Arabia & UAE. Rich long-lasting aroma with fast delivery in Riyadh, Jeddah & Dubai. Tabby available."
}
```

### Step C: Human Review & Edits (`التدقيق البشري والتعديلات`)
1. **Glossary Check**: Confirmed the brand's preferred English spelling is `"Bakhoor"` rather than `"Bukhoor"` to match their Google Merchant Center English feed.
2. **Zid Field Check**: Imported into Zid's English SEO Title field and verified live HTML `<title>` on `/en/products/royal-cambodi-oud`.

### Step D: Final Reviewed Example Outcome (`النتيجة النهائية المعتمدة`)
- **Live `/en/` `<title>` (60 chars)**: `Royal Cambodi Oud Wood Chips 50g | Authentic Bakhoor - Tayeb`
- **Live `/ar/` `<title>` (52 chars)**: `عود كمبودي ملكي فاخر 50 جرام | توصيل سريع - متجر طيب`

## 4. What Can Go Wrong & How to Fix It (`الأخطاء الشائعة وخطة الإنقاذ`)

- **Failure Case (`المشكلة المحتملة`)**: A marketer translates the main product name (`Product Title`) in the English tab of Salla/Zid, but forgets to switch the language tab inside the separate bottom `SEO Settings` box—so the page `<h1>` is in English while `<title>` remains in Arabic.
- **Correction & Fallback (`الحل الإجرائي والبديل الآمن`)**: Always audit the rendered `<title>` element in raw HTML (`curl -s URL | grep '<title>'`), never just the product name column in the dashboard.

## 5. Model & Platform Capability Matrix (`مصفوفة قدرات النماذج والمنصات — 2026-10-25`)

| Platform / Model | Status | Official Documentation | MENA Operational Constraint | Fallback |
| :--- | :--- | :--- | :--- | :--- |
| **Salla & Zid Multilingual SEO Title Fields** | `supported` | [Official Docs](https://voctos.net/salla-zid-store-seo-audit/) (`2026-10-25`) | Both platforms support separate English SEO titles, but 4/6 Salla stores and 4/5 Zid stores in the Oct 2026 audit left the English SEO title unmapped, defaulting to Arabic. | Enforce regex check `[؀-ۿ]` on all `/en/` `<title>` tags after every catalog update. |

## 6. How to Measure Success (`خطة القياس والضوابط`)

- **Primary Metric**: Percentage of `/en/` URLs with zero Arabic characters in `<title>`, plus English-query CTR in Google Search Console.
- **Baseline**: Pre-fix count of `/en/` pages serving Arabic `<title>` tags.
- **Observation Window**: 14–28 days post-crawl.
- **Interpretation Boundary**: Fixing `/en/` `<title>` tags must be paired with `AMP-004` (self-referencing `/en/` canonicals) on Salla to take effect in Google Search.

## 7. Primary Sources & Evidence Boundaries (`المصادر الموثقة وحدود الأدلة`)

- [تحسين محركات البحث للمتاجر الإلكترونية | زد المدونة](https://zid.sa/ar/blog/%D8%AA%D8%AD%D8%B3%D9%8A%D9%86-%D9%85%D8%AD%D8%B1%D9%83%D8%A7%D8%AA_%D8%A7%D9%84%D8%A8%D8%AD%D8%AB/) — *Zid* (Published `2023-03-26`, Accessed `2026-10-25`): Outlines Zid's e-commerce SEO structure for product titles, meta descriptions, and category taxonomy.
- [We Audited 20 Salla and Zid Stores: The SEO Defaults Saudi Merchants Inherit (2026)](https://voctos.net/salla-zid-store-seo-audit/) — *VOCTOS* (Published `2026-10-08`, Accessed `2026-10-25`): Audit of 20 Saudi stores (10 Salla, 10 Zid): 60% of sampled Salla sitemap URLs (88/146) redirected or returned 410; 6/6 Salla English pages canonicalized to Arabic; 9/10 Zid stores lacked Sitemap in robots.txt; 0/10 Salla stores had Brand in Product JSON-LD; 8/11 English pages kept Arabic-script titles.
