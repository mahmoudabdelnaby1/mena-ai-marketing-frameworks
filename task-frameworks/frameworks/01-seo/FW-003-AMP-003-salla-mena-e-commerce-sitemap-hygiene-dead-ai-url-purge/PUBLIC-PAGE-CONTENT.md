# Salla & MENA E-Commerce Sitemap Hygiene & Dead-AI-URL Purge Checklist
## <span dir="rtl">قائمة فحص وتطهير خرائط المواقع (`sitemap.xml`) في متاجر سلة والتجارة الإلكترونية من الروابط المعطوبة والمحذوفة</span>

> **Asset ID**: `FW-003` (`AMP-003`) | **Artifact Type**: `CHECKLIST` | **Channel**: Search Engine Optimization (SEO) | **Markets**: Egypt & GCC (`KSA, UAE, Kuwait, Qatar, Bahrain, Oman`) | **Version**: `1.2` (`Reviewed 2026-10-25`)

**What You Can Do With This (`ماذا يمكنك أن تنجز بهذه الأداة؟`)**:
- **EN**: Audit and clean `sitemap.xml` files so Googlebot stops wasting up to 60% of crawl budget on 302/301 redirected or 410 Gone AI-generated product URLs.
- **AR**: <span dir="rtl">تدقيق وتنظيف ملفات `sitemap.xml` لمنع استنزاف 60% من ميزانية الزحف (Crawl Budget) في جوجل على روابط منتجات محذوفة أو محولة (`302/301/410`).</span>

## 1. Use It When & Required Inputs (`متى تستخدمها وما المدخلات المطلوبة؟`)

- **Use It When (EN)**: Use after bulk-importing AI-generated product listings, hiding seasonal SKUs (Ramadan/White Friday), or diagnosing 'Page with redirect' and 'Not found (404/410)' spikes in Google Search Console.
- **متى تستخدمها (AR)**: <span dir="rtl">تُستخدم بعد الاستيراد الجماعي للمنتجات المولدة بالذكاء الاصطناعي، أو إخفاء منتجات المواسم (رمضان/الجمعة البيضاء)، أو عند ظهور تنبيهات التحويل (`302/410`) في Google Search Console.</span>
- **When NOT to Use It (EN)**: Do not delete URLs of temporarily out-of-stock evergreen products that will restock within 30 days—keep them `200 OK` with an in-stock notification capture instead of unpublishing.
- **متى لا تستخدمها (AR)**: <span dir="rtl">لا تحذف روابط المنتجات الدائمة التي نفدت مؤقتاً وستتوفر خلال 30 يوماً؛ أبقِ صفحتها نشطة (`200 OK`) مع تفعيل زر «أعلمني عند التوفر».</span>

### Exact Inputs to Prepare (`المدخلات المطلوب تجهيزها قبل البدء`)
- Live store `sitemap.xml` URL (e.g., `https://store.com/sitemap.xml`)
- Google Search Console Page Indexing export (`Excluded by redirect`, `404`, `410`, `Crawled - currently not indexed`)
- Catalog export of Hidden / Draft / Deleted SKUs from Salla, Zid, Shopify, or WooCommerce

## 2. The Working `CHECKLIST` (`الأداة الكاملة الجاهزة للنسخ والتطبيق الفوري`)

### Sitemap Crawl-Health Audit Checklist & Automated Validator

#### Step 1: Run the Sitemap HTTP Status Audit
- [ ] **Extract all `<loc>` URLs** from `sitemap.xml` (and child product sitemaps).
- [ ] **Check HTTP Status Codes without following redirects (`max_redirects=0`)**:
  - **Pass Target**: `>= 98%` of URLs in `sitemap.xml` MUST return direct `200 OK` and contain a self-referencing `<link rel="canonical">`.
  - **Fail Condition (Salla Specific)**: Unpublished or hidden products in Salla frequently remain listed in `sitemap.xml` while returning `302 Found` (redirecting to homepage) or `410 Gone` (VOCTOS Oct 2026 audit: 60% failure rate across 10 sampled Salla stores).

#### Step 2: Copy-Ready Python Sitemap Health Checker (Run in Terminal/CI)
```python
import urllib.request
import urllib.error
import xml.etree.ElementTree as ET

class NoRedirectHandler(urllib.request.HTTPRedirectHandler):
    def http_error_302(self, req, fp, code, msg, headers):
        return fp
    http_error_301 = http_error_303 = http_error_307 = http_error_308 = http_error_302

opener = urllib.request.build_opener(NoRedirectHandler)

def audit_sitemap(sitemap_url, sample_limit=200):
    req = urllib.request.Request(sitemap_url, headers={"User-Agent": "Mozilla/5.0 (compatible; SitemapAudit/1.2)"})
    xml_bytes = urllib.request.urlopen(req, timeout=15).read()
    root = ET.fromstring(xml_bytes)
    ns = {"sm": "http://www.sitemaps.org/schemas/sitemap/0.9"}
    urls = [el.text.strip() for el in root.findall(".//sm:loc", ns) if el.text][:sample_limit]
    report = {"200_OK": [], "301_302_REDIRECT": [], "404_410_DEAD": [], "OTHER": []}
    for u in urls:
        try:
            r = opener.open(urllib.request.Request(u, headers={"User-Agent": "Mozilla/5.0"}), timeout=10)
            code = r.getcode()
        except urllib.error.HTTPError as e:
            code = e.code
        if code == 200:
            report["200_OK"].append(u)
        elif code in (301, 302, 307, 308):
            report["301_302_REDIRECT"].append((u, code))
        elif code in (404, 410):
            report["404_410_DEAD"].append((u, code))
        else:
            report["OTHER"].append((u, code))
    return report
```

#### Step 3: Platform-Specific Remediation Protocol
- [ ] **For Evergreen Products Temporarily Out of Stock**: Keep product status **Active/Visible** (`متاح للعرض` with quantity `0` and "Notify Me" enabled) so the URL stays `200 OK` and preserves rankings.
- [ ] **For Permanently Discontinued AI-Generated Test/Seasonal SKUs**:
  - In **Salla / Zid**: Permanently delete discontinued test drafts rather than leaving them in hidden/draft state if they leak into the sitemap, then trigger a Sitemap refresh in Merchant Dashboard (`إعدادات SEO -> تحديث خريطة الموقع`) and resubmit in Google Search Console.
  - In **Shopify / WooCommerce / Custom**: Configure 301 redirect to the parent category page AND ensure the SEO plugin (RankMath/Yoast) excludes redirected/noindex items from `product-sitemap.xml`.

## 3. Complete End-to-End Worked Example (`مثال تطبيقي متكامل من المدخلات حتى المراجعة البشرية والنتيجة النهائية`)

*(Illustrative scenario — original example for training, never represented as a verified client outcome)*

### Step A: Sample Brief / Input (`موجز المدخلات`)
- **Store**: Riyadh Home Perfumes D2C store on Salla (`180` total URLs in `sitemap.xml`).
- **Context**: Team used an AI catalog tool to generate 95 Ramadan gift bundle SKUs, then hid all 95 bundles after Eid without auditing `sitemap.xml`.

### Step B: Initial Output (`المخرج الأولي`)
- Total Sitemap `<loc>` URLs tested: `180`
- `200 OK`: `85` (47.2%)
- `302 Redirect to Homepage`: `79` (43.9% — hidden Ramadan bundles still listed in `sitemap.xml`)
- `410 Gone`: `16` (8.9% — deleted AI draft SKUs still cached in `sitemap.xml`)

### Step C: Human Review & Edits (`التدقيق البشري والتعديلات`)
1. **Evergreen Retention**: Identified 12 top-selling Oud gift boxes among the 79 hidden SKUs; switched them back to Active with "Available for Pre-Order / Back in Stock Soon" instead of hiding them, restoring `200 OK` on high-backlink URLs.
2. **Sitemap Cache Purge**: Purged the remaining 67 one-off test SKUs, triggered Salla SEO sitemap regeneration, and verified that `sitemap.xml` dropped from 180 URLs to 97 clean `200 OK` URLs.

### Step D: Final Reviewed Example Outcome (`النتيجة النهائية المعتمدة`)
- Post-remediation `sitemap.xml` audit: `97/97` URLs (`100%`) return `200 OK` with self-referencing canonicals.
- Resubmitted `sitemap.xml` in Google Search Console (`تاريخ الإرسال: 2026-10-25`).

## 4. What Can Go Wrong & How to Fix It (`الأخطاء الشائعة وخطة الإنقاذ`)

- **Failure Case (`المشكلة المحتملة`)**: A merchant hides 100 seasonal White Friday pages at midnight after the sale ends; Salla's homepage 302 redirect triggers Google Search Console 'Soft 404' errors across all 100 URLs.
- **Correction & Fallback (`الحل الإجرائي والبديل الآمن`)**: Maintain a single evergreen `/ar/white-friday-offers` hub page year-round (`200 OK`) and attach seasonal SKU cards dynamically rather than creating and hiding disposable URLs every season.

## 5. Model & Platform Capability Matrix (`مصفوفة قدرات النماذج والمنصات — 2026-10-25`)

| Platform / Model | Status | Official Documentation | MENA Operational Constraint | Fallback |
| :--- | :--- | :--- | :--- | :--- |
| **Salla Native `sitemap.xml` Generator** | `plan/region dependent` | [Official Docs](https://voctos.net/salla-zid-store-seo-audit/) (`2026-10-25`) | VOCTOS Oct 2026 audit of 10 Salla stores found 60% (88/146) of sampled sitemap product URLs redirected (302/301) or returned 410 Gone. | Audit `sitemap.xml` monthly using the HTTP status script and avoid mass-creating disposable product URLs for short promotions. |

## 6. How to Measure Success (`خطة القياس والضوابط`)

- **Primary Metric**: Ratio of Indexed vs. Excluded ('Page with redirect' / 'Soft 404' / '410') URLs in Google Search Console Sitemaps report.
- **Baseline**: Pre-audit % of non-200 URLs inside `sitemap.xml`.
- **Observation Window**: 14–21 days after sitemap resubmission in GSC.
- **Interpretation Boundary**: Cleaning `sitemap.xml` recovers wasted crawl budget and fixes indexation hygiene, but does not automatically boost rankings for uncompetitive pages.

## 7. Primary Sources & Evidence Boundaries (`المصادر الموثقة وحدود الأدلة`)

- [أدوات السيو في متجرك: دليل شامل - مركز المساعدة - سلة](https://help.salla.sa/article/%D8%AA%D8%AD%D8%B3%D9%8A%D9%86-%D8%B8%D9%87%D9%88%D8%B1-%D9%85%D8%AA%D8%AC%D8%B1%D9%83-%D8%B9%D9%84%D9%89-%D9%85%D8%AD%D8%B1%D9%83%D8%A7%D8%AA-%D8%A7%D9%84%D8%A8%D8%AD%D8%AB-seo/oi134aj2ud6ts12ysumrm5za) — *Salla Help Center* (Published `2026-10-18`, Accessed `2026-10-25`): Documents Salla's built-in SEO settings, AI prompt assistant for product descriptions, custom metadata_url fields, and Search Console sitemap submission.
- [تحسين ظهور متجرك في محركات البحث SEO - مركز المساعدة - سلة](https://help.salla.sa/article/-%D8%AA%D8%AD%D8%B3%D9%8A%D9%86-%D8%B8%D9%87%D9%88%D8%B1-%D9%85%D8%AA%D8%AC%D8%B1%D9%83-%D8%B9%D9%84%D9%89-%D9%85%D8%AD%D8%B1%D9%83%D8%A7%D8%AA-%D8%A7%D9%84%D8%A8%D8%AD%D8%AB-seo/gmzx0xblr3ajerkciyoxke1e) — *Salla Help Center* (Published `2026-08-18`, Accessed `2026-10-25`): Explains 'Crawled - currently not indexed' status on Salla stores when product pages contain thin, duplicated, or unedited manufacturer/AI descriptions.
- [We Audited 20 Salla and Zid Stores: The SEO Defaults Saudi Merchants Inherit (2026)](https://voctos.net/salla-zid-store-seo-audit/) — *VOCTOS* (Published `2026-10-08`, Accessed `2026-10-25`): Audit of 20 Saudi stores (10 Salla, 10 Zid): 60% of sampled Salla sitemap URLs (88/146) redirected or returned 410; 6/6 Salla English pages canonicalized to Arabic; 9/10 Zid stores lacked Sitemap in robots.txt; 0/10 Salla stores had Brand in Product JSON-LD; 8/11 English pages kept Arabic-script titles.
