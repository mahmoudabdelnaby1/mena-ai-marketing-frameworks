# Salla & MENA E-Commerce Product JSON-LD `brand` & Merchant Schema Injection Checklist
## <span dir="rtl">قائمة فحص وحقن خاصية العلامة التجارية (`brand`) والبيانات المهيكلة `Product JSON-LD` في متاجر سلة والمنطقة</span>

> **Asset ID**: `FW-007` (`AMP-007`) | **Artifact Type**: `CHECKLIST` | **Channel**: Search Engine Optimization (SEO) | **Markets**: Egypt & GCC (`KSA, UAE, Kuwait, Qatar, Bahrain, Oman`) | **Version**: `1.2` (`Reviewed 2026-10-25`)

**What You Can Do With This (`ماذا يمكنك أن تنجز بهذه الأداة؟`)**:
- **EN**: Patch missing `brand`, `sku`, `gtin`, and `priceValidUntil` properties in Salla and regional e-commerce `Product` JSON-LD so pages qualify for full Google Merchant & AI Search rich snippets.
- **AR**: <span dir="rtl">استكمال حقل العلامة التجارية (`brand`) ورموز `sku/gtin` في البيانات المهيكلة `Product JSON-LD` لمتاجر سلة والمنطقة لضمان التوافق الكامل مع النتائج الغنية في جوجل ومحركات الذكاء الاصطناعي.</span>

## 1. Use It When & Required Inputs (`متى تستخدمها وما المدخلات المطلوبة؟`)

- **Use It When (EN)**: Use when Google Search Console shows 'Missing field "brand"' under Merchant Listings / Product snippets on Salla, WooCommerce, or Shopify stores.
- **متى تستخدمها (AR)**: <span dir="rtl">تُستخدم عند ظهور تنبيه «الحقل المفقود brand» في تقارير المنتجات داخل Google Search Console لمتاجر سلة أو ووكومرس أو شوبيفاي.</span>
- **When NOT to Use It (EN)**: Do not inject fabricated `aggregateRating` or fake review counts into JSON-LD (`AMP-392`)—Google issues manual actions for deceptive structured data.
- **متى لا تستخدمها (AR)**: <span dir="rtl">لا تقم أبداً بحقن تقييمات وهمية (`aggregateRating`) غير موجودة فعلياً في الصفحة (`AMP-392`)؛ لأن جوجل يفرض عقوبات يدوية صارمة على البيانات المهيكلة المضللة.</span>

### Exact Inputs to Prepare (`المدخلات المطلوب تجهيزها قبل البدء`)
- Live product URL and Google Rich Results Test output
- Verified Brand Name (`Brand` object name in Arabic/English)
- Product `sku`, `gtin13`/`mpn` (if applicable), and currency (`SAR`, `AED`, `EGP`)

## 2. The Working `CHECKLIST` (`الأداة الكاملة الجاهزة للنسخ والتطبيق الفوري`)

### Product JSON-LD Completeness Checklist & Salla Patch Snippet

#### 1. Audit Current `application/ld+json` Output
- [ ] Run the product URL in Google Rich Results Test or inspect via terminal:
```bash
curl -sL "https://your-salla-store.sa/product-slug" | grep -A 25 'application/ld+json'
```
- [ ] Verify presence of these 6 critical `Product` schema properties:
  1. `@type: "Product"` with `@id`
  2. `name` and `description` (cleaned of raw HTML tags)
  3. **`brand`: `{"@type": "Brand", "name": "..."}`** *(Missing in 10/10 default Salla stores in Oct 2026 audit!)*
  4. `sku` and `gtin13` / `mpn`
  5. `offers.price` (numeric dot-decimal `199.00`, never Arabic-Indic `١٩٩`) and `offers.priceCurrency` (`SAR` | `AED` | `EGP`)
  6. `offers.availability` (`https://schema.org/InStock` or `OutOfStock`)

#### 2. Drop-In JSON-LD `brand` Patch for Salla (Custom JS / Tag Manager / Theme Snippet)
When Salla's native JSON-LD omits `"brand"`, link your supplementary JSON-LD node via the same `@id` or enrich the Product schema cleanly:
```html
<script>
(function() {
  try {
    var scripts = document.querySelectorAll('script[type="application/ld+json"]');
    scripts.forEach(function(script) {
      var data = JSON.parse(script.textContent);
      if (data && data['@type'] === 'Product' && !data.brand) {
        // Pull brand from Salla product meta/DOM or fallback to store brand name
        var brandEl = document.querySelector('.product-brand__name, [data-product-brand]');
        var brandName = brandEl ? brandEl.textContent.trim() : 'اسم العلامة التجارية';
        data.brand = {
          '@type': 'Brand',
          'name': brandName
        };
        script.textContent = JSON.stringify(data);
      }
    });
  } catch (e) {}
})();
</script>
```
*(Note: For maximum crawler reliability on custom domains, inject `"brand"` at the server/Cloudflare HTMLRewriter layer so non-JS crawlers like `OAI-SearchBot` and `ClaudeBot` also read `"brand"` in initial HTML.)*

## 3. Complete End-to-End Worked Example (`مثال تطبيقي متكامل من المدخلات حتى المراجعة البشرية والنتيجة النهائية`)

*(Illustrative scenario — original example for training, never represented as a verified client outcome)*

### Step A: Sample Brief / Input (`موجز المدخلات`)
- **Store**: Saudi Skincare D2C Brand on Salla (`https://glow-example.sa/vitamin-c-serum`).
- **Issue**: Google Search Console flags `84/84` products with `Missing field "brand"` under Merchant Listings.

### Step B: Initial Output (`المخرج الأولي`)
```json
{
  "@context": "https://schema.org/",
  "@type": "Product",
  "name": "سيروم فيتامين سي النقي 30 مل",
  "image": "https://cdn.salla.sa/example/serum.jpg",
  "offers": {
    "@type": "Offer",
    "priceCurrency": "SAR",
    "price": "145.00",
    "availability": "https://schema.org/InStock"
  }
}
```
*(Missing `"brand"` and `"sku"`)*

### Step C: Human Review & Edits (`التدقيق البشري والتعديلات`)
1. **Added Brand & SKU Properties**: Injected `"brand": {"@type": "Brand", "name": "Glow Arabia | قلو أرابيا"}` and `"sku": "GLW-VITC-30ML"`.
2. **Verified Price Formatting**: Confirmed `price` uses standard ASCII `"145.00"` with `"priceCurrency": "SAR"` (15% VAT inclusive).

### Step D: Final Reviewed Example Outcome (`النتيجة النهائية المعتمدة`)
```json
{
  "@context": "https://schema.org/",
  "@type": "Product",
  "name": "سيروم فيتامين سي النقي 30 مل",
  "sku": "GLW-VITC-30ML",
  "brand": {
    "@type": "Brand",
    "name": "Glow Arabia | قلو أرابيا"
  },
  "image": "https://cdn.salla.sa/example/serum.jpg",
  "offers": {
    "@type": "Offer",
    "priceCurrency": "SAR",
    "price": "145.00",
    "availability": "https://schema.org/InStock"
  }
}
```

## 4. What Can Go Wrong & How to Fix It (`الأخطاء الشائعة وخطة الإنقاذ`)

- **Failure Case (`المشكلة المحتملة`)**: A developer adds a second standalone `<script type="application/ld+json">` containing only `@type: Product` and `brand` without `name` or `offers`, triggering a new GSC critical error ('Either offers, review, or aggregateRating should be specified').
- **Correction & Fallback (`الحل الإجرائي والبديل الآمن`)**: Always merge `brand` into the existing `Product` JSON-LD object (or link via identical `@id`), never emit an incomplete orphan `Product` node.

## 5. Model & Platform Capability Matrix (`مصفوفة قدرات النماذج والمنصات — 2026-10-25`)

| Platform / Model | Status | Official Documentation | MENA Operational Constraint | Fallback |
| :--- | :--- | :--- | :--- | :--- |
| **Salla vs. Zid Default Product JSON-LD** | `plan/region dependent` | [Official Docs](https://voctos.net/salla-zid-store-seo-audit/) (`2026-10-25`) | In VOCTOS's Oct 2026 audit, 0/10 Salla stores included `brand` in Product JSON-LD, whereas 9/10 Zid stores included `brand` natively. | Enrich Salla's JSON-LD via theme script or Cloudflare edge HTMLRewriter. |

## 6. How to Measure Success (`خطة القياس والضوابط`)

- **Primary Metric**: Count of 'Missing field "brand"' warnings in Google Search Console Merchant Listings report.
- **Baseline**: Pre-fix warning count in GSC.
- **Observation Window**: 14 days after clicking 'Validate Fix' in GSC.
- **Interpretation Boundary**: Valid Product schema enables rich result eligibility but does not guarantee Google displays rich snippets on every query.

## 7. Primary Sources & Evidence Boundaries (`المصادر الموثقة وحدود الأدلة`)

- [أدوات السيو في متجرك: دليل شامل - مركز المساعدة - سلة](https://help.salla.sa/article/%D8%AA%D8%AD%D8%B3%D9%8A%D9%86-%D8%B8%D9%87%D9%88%D8%B1-%D9%85%D8%AA%D8%AC%D8%B1%D9%83-%D8%B9%D9%84%D9%89-%D9%85%D8%AD%D8%B1%D9%83%D8%A7%D8%AA-%D8%A7%D9%84%D8%A8%D8%AD%D8%AB-seo/oi134aj2ud6ts12ysumrm5za) — *Salla Help Center* (Published `2026-10-18`, Accessed `2026-10-25`): Documents Salla's built-in SEO settings, AI prompt assistant for product descriptions, custom metadata_url fields, and Search Console sitemap submission.
- [We Audited 20 Salla and Zid Stores: The SEO Defaults Saudi Merchants Inherit (2026)](https://voctos.net/salla-zid-store-seo-audit/) — *VOCTOS* (Published `2026-10-08`, Accessed `2026-10-25`): Audit of 20 Saudi stores (10 Salla, 10 Zid): 60% of sampled Salla sitemap URLs (88/146) redirected or returned 410; 6/6 Salla English pages canonicalized to Arabic; 9/10 Zid stores lacked Sitemap in robots.txt; 0/10 Salla stores had Brand in Product JSON-LD; 8/11 English pages kept Arabic-script titles.
