# FW-007: Salla & MENA E-Commerce Product JSON-LD `brand` & Merchant Schema Injection Checklist
## قائمة فحص وحقن خاصية العلامة التجارية (`brand`) والبيانات المهيكلة `Product JSON-LD` في متاجر سلة والمنطقة

- **Consolidated Contextual Child IDs (`MERGE_INTO_EXISTING`)**: `AMP-019`, `AMP-031`, `AMP-043`, `AMP-055`
- **Selected Artifact Type**: `CHECKLIST`
- **Intended Audience**: SEO Specialist, E-Commerce Manager, Content Strategist, Technical SEO Lead
- **Target Markets & Languages**: Egypt & GCC (`Saudi Arabia, UAE, Kuwait, Qatar, Bahrain, Oman`) — Bilingual Arabic (`Egyptian Ammiya`, `Saudi/Gulf Khaleeji`, `White MSA`) + English
- **Version**: `1.2` | **Last Reviewed**: `2026-10-25` | **Status**: `READY_FOR_REVIEW`

## 1. Plain-Language Promise & Why This Artifact Form Fits the Job

- **What You Can Make or Decide (EN)**: Patch missing `brand`, `sku`, `gtin`, and `priceValidUntil` properties in Salla and regional e-commerce `Product` JSON-LD so pages qualify for full Google Merchant & AI Search rich snippets.
- **ما الذي يمكنك إنجازه أو حسمه بهذه الأداة (AR)**: استكمال حقل العلامة التجارية (`brand`) ورموز `sku/gtin` في البيانات المهيكلة `Product JSON-LD` لمتاجر سلة والمنطقة لضمان التوافق الكامل مع النتائج الغنية في جوجل ومحركات الذكاء الاصطناعي.
- **Why `CHECKLIST` Fits This User Job (EN)**: VOCTOS's Oct 2026 audit found 0 of 10 Salla stores included the `brand` property in their default `Product` JSON-LD (whereas 9 of 10 Zid stores included it); a technical CHECKLIST with a drop-in JSON-LD enrichment snippet fixes Google Search Console Merchant Listing warnings immediately.
- **لماذا يناسب شكل `CHECKLIST` هذه المهمة (AR)**: كشف فحص VOCTOS (أكتوبر 2026) أن 0 من 10 متاجر سلة تضمنت حقل `brand` في `Product JSON-LD` الافتراضي (مقابل 9 من 10 في زد)؛ وتوفر قائمة الفحص هذه كود الحقن الجاهز لمعالجة تنبيهات Search Console فوراً.

## 2. "Use It When" Trigger, Boundaries & Exact Inputs to Prepare

- **Use It When (EN)**: Use when Google Search Console shows 'Missing field "brand"' under Merchant Listings / Product snippets on Salla, WooCommerce, or Shopify stores.
- **متى تستخدم هذه الأداة (AR)**: تُستخدم عند ظهور تنبيه «الحقل المفقود brand» في تقارير المنتجات داخل Google Search Console لمتاجر سلة أو ووكومرس أو شوبيفاي.
- **When NOT to Use It (EN)**: Do not inject fabricated `aggregateRating` or fake review counts into JSON-LD (`AMP-392`)—Google issues manual actions for deceptive structured data.
- **متى لا تستخدم هذه الأداة (AR)**: لا تقم أبداً بحقن تقييمات وهمية (`aggregateRating`) غير موجودة فعلياً في الصفحة (`AMP-392`)؛ لأن جوجل يفرض عقوبات يدوية صارمة على البيانات المهيكلة المضللة.

### Exact Inputs to Prepare Before Starting (`المدخلات المطلوب تجهيزها`)
1. Live product URL and Google Rich Results Test output
2. Verified Brand Name (`Brand` object name in Arabic/English)
3. Product `sku`, `gtin13`/`mpn` (if applicable), and currency (`SAR`, `AED`, `EGP`)

### Privacy-Safe Data Handling (`ضوابط الخصوصية وحماية البيانات الشخصية PDPL`)
- **Strict PII Redaction Before Prompting**: Under Saudi PDPL (Art. 25), UAE Federal Decree-Law No. 45 of 2021, Qatar Law No. 13 of 2016, and Egypt Law No. 151 of 2020, **never paste raw customer names, unhashed mobile numbers (`+9665...` / `+201...`), email addresses, national IDs, or private WhatsApp transcripts into public/consumer LLM interfaces**. Use anonymized placeholders (`{first_name}`, `ORD_10045`) during prompt testing and restrict live customer data to zero-data-retention enterprise API endpoints or local deterministic scripts.

## 3. The Directly Usable Artifact (`الأداة التطبيقية الجاهزة للنسخ والتنفيذ`)

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

## 4. Model & Platform Capability Branches (`فروع قدرات النماذج والمنصات والبدائل الاحتياطية`)

| System / Platform | Capability Status | Official Documentation & Access Date | Operational Constraint in Egypt & GCC | Fallback When Feature/Modality Is Unavailable |
| :--- | :--- | :--- | :--- | :--- |
| **Salla vs. Zid Default Product JSON-LD** | `plan/region dependent` | [Official Reference](https://voctos.net/salla-zid-store-seo-audit/) (`2026-10-25`) | In VOCTOS's Oct 2026 audit, 0/10 Salla stores included `brand` in Product JSON-LD, whereas 9/10 Zid stores included `brand` natively. | Enrich Salla's JSON-LD via theme script or Cloudflare edge HTMLRewriter. |

## 5. Consolidated Regional & Vertical Adaptation Matrix (`دمج الأنماط السياقية الفرعية بدون حشو`)

Per Agent 2 v1.2's anti-padding rule, the following **4 cross-verified contextual synthesis patterns** and **0 screened duplicate variants** share this core mechanism and are consolidated directly into this source-of-truth framework:

| Child Pattern ID | Disposition | Regional / Sector Operating Context | Specific Adaptation & Guardrail Integrated in This Asset | Evidence Tier |
| :--- | :--- | :--- | :--- | :--- |
| **`AMP-019`** | `MERGE_INTO_EXISTING` | Egyptian E-Commerce & Social Commerce (Shopify / WooCommerce / Cairo & Alexandria) | Unbranded generic commodities where brand queries do not drive search.; Specifically impacts Egyptian brands operating in EGP where merchant-specific payment mix from recent order records, Mobile Wallets (Vodafone Cash), InstaPay, and Fawry dominate. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-031`** | `MERGE_INTO_EXISTING` | UAE & Multi-Market GCC Enterprise / Retail (Dubai, Abu Dhabi, Doha, Kuwait) | Unbranded generic commodities where brand queries do not drive search.; Specifically impacts bilingual Arabic/English campaigns in high-CPM, expat-dense Gulf markets under UAE PDPL / TDRA and Qatari regulations. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-043`** | `MERGE_INTO_EXISTING` | High-Trust & Regulated Verticals (Healthcare/SFDA/EDA, Fintech/SAMA/FRA, Real Estate) | Unbranded generic commodities where brand queries do not drive search.; Specifically impacts regulated claims requiring SFDA, EDA, MOH, SAMA, FRA, or RERA compliance pre-clearance and strict hallucination guardrails. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-055`** | `MERGE_INTO_EXISTING` | Seasonal Peak Operations (Ramadan, Eid, White/Yellow Friday, Saudi Founding/National Day) | Unbranded generic commodities where brand queries do not drive search.; Specifically impacts high-velocity seasonal surges where CPMs jump 40-70%, prices change rapidly, and Hijri calendar cultural sensitivity is paramount. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |

### Context-Specific Execution Knobs Across the 5 MENA Operating Environments
1. **Saudi D2C E-Commerce (`Salla / Zid / Riyadh & Jeddah Retail`)**: Enforce `SAR` tax-inclusive pricing (`15% ZATCA VAT`), native `Mada / Apple Pay / Tabby / Tamara` visibility (`AMP-387`), `GAMR Mawthooq` creator verification (`AMP-281`), and White Saudi Khaleeji orthography (`AMP-002`, `AMP-177`).
2. **Egyptian E-Commerce & Social Commerce (`Shopify / WooCommerce / Cairo & Alexandria`)**: Use each merchant’s own order and payment data to assess Cash on Delivery (`COD`), mobile wallets, InstaPay, Fawry, `valU`, address fields, and pre-dispatch WhatsApp confirmation. Verify current provider terms and local requirements before implementation.
3. **UAE & Multi-Market GCC Enterprise / Retail (`Dubai, Abu Dhabi, Doha, Kuwait`)**: Separate high-CPM UAE/Qatar budgets from lower-CPM markets (`AMP-061`), enforce UAE `TDRA` `9 PM – 7 AM` SMS curfew + `AD-` prefix (`AMP-442`), UAE Media Council permits (`AMP-282`), and bilingual Arabic/English canonical & currency parity (`current applicable UAE VAT`, `current applicable Qatar/Kuwait tax rules`, 3-decimal `KWD` `AMP-239`).
4. **High-Trust & Regulated Verticals (`Healthcare SFDA/MOH/EDA, FinTech SAMA/FRA, Real Estate REGA/RERA`)**: Strip all therapeutic/cure verbs (`AMP-176`, `AMP-286`), display mandatory `MOH/SFDA/DHA/EDA/Fal/Trakheesi` permit numbers (`AMP-070`), and route budgets to high-credibility channels (`AMP-290`, `AMP-339`).
5. **Seasonal Peak Operations (`Ramadan, Eid, White/Yellow Friday, Saudi Founding/National Day`)**: Lock Hijri-Gregorian overlaps (`Feb 2027 Ramadan x Saudi Founding Day x Kuwait National Day` `AMP-125`), pre-schedule GMC `sale_price_effective_date` 48h ahead (`AMP-063`), verify 30-day baseline discount permits (`AMP-064`), and disable Meta Advantage+ auto-music (`AMP-065`).

## 6. Worked Example Summary & Failure Recovery (`ملخص المثال التطبيقي وخطة الإنقاذ`)

*(Full step-by-step worked example with annotated human edits is also provided in `EXAMPLE.md`)*

- **Sample Input Brief**: - **Store**: Saudi Skincare D2C Brand on Salla (`https://glow-example.sa/vitamin-c-serum`).
- **Issue**: Google Search Console flags `84/84` products with `Missing field "brand"` under Merchant Listings.
- **Human Review & Key Edits Applied**: 1. **Added Brand & SKU Properties**: Injected `"brand": {"@type": "Brand", "name": "Glow Arabia | قلو أرابيا"}` and `"sku": "GLW-VITC-30ML"`.
2. **Verified Price Formatting**: Confirmed `price` uses standard ASCII `"145.00"` with `"priceCurrency": "SAR"` (15% VAT inclusive).
- **Final Usable Output**: ```json
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
- **What Can Go Wrong**: A developer adds a second standalone `<script type="application/ld+json">` containing only `@type: Product` and `brand` without `name` or `offers`, triggering a new GSC critical error ('Either offers, review, or aggregateRating should be specified').
- **Correction & Fallback**: Always merge `brand` into the existing `Product` JSON-LD object (or link via identical `@id`), never emit an incomplete orphan `Product` node.

## 7. Measurement Plan & Hypothesis Framing (`خطة القياس والضوابط الإحصائية`)

- **Primary Metric to Track**: Count of 'Missing field "brand"' warnings in Google Search Console Merchant Listings report.
- **Baseline Definition**: Pre-fix warning count in GSC.
- **Observation Window**: 14 days after clicking 'Validate Fix' in GSC. *(Must span full 7/14-day weekly cycles and account for 25th–30th monthly salary windows per `AMP-391`)*.
- **What Cannot Be Concluded (Boundary)**: Valid Product schema enables rich result eligibility but does not guarantee Google displays rich snippets on every query.
