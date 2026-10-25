# End-to-End Worked Example & Failure Recovery — `FW-007` (`AMP-007`)

- **Framework**: Salla & MENA E-Commerce Product JSON-LD `brand` & Merchant Schema Injection Checklist
- **العنوان بالعربية**: قائمة فحص وحقن خاصية العلامة التجارية (`brand`) والبيانات المهيكلة `Product JSON-LD` في متاجر سلة والمنطقة
- **Selected Artifact Type**: `CHECKLIST`
- **Disclaimer**: *All scenarios, brand names, SKU codes, and metrics below are original, realistic illustrative examples for MENA practitioner training and are never represented as verified client outcomes.*

## 1. Realistic Sample Brief / Input (`المدخلات وموجز الحالة العملية`)

- **Store**: Saudi Skincare D2C Brand on Salla (`https://glow-example.sa/vitamin-c-serum`).
- **Issue**: Google Search Console flags `84/84` products with `Missing field "brand"` under Merchant Listings.

## 2. Initial Generated / Completed Output (`المخرج الأولي عند تطبيق الأداة`)

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

## 3. Human Review & Localization/Technical Edits (`المراجعة البشرية والتعديلات الرقابية والتقنية`)

1. **Added Brand & SKU Properties**: Injected `"brand": {"@type": "Brand", "name": "Glow Arabia | قلو أرابيا"}` and `"sku": "GLW-VITC-30ML"`.
2. **Verified Price Formatting**: Confirmed `price` uses standard ASCII `"145.00"` with `"priceCurrency": "SAR"` (15% VAT inclusive).

## 4. Final Reviewed Example Outcome (`النتيجة النهائية الجاهزة للتنفيذ`)

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

## 5. What Can Go Wrong & Specific Correction / Fallback (`حالة الفشل المحتملة وخطة الإنقاذ والبديل`)

- **Common Failure Mode (`ما الذي قد يسير بشكل خاطئ؟`)**:
  A developer adds a second standalone `<script type="application/ld+json">` containing only `@type: Product` and `brand` without `name` or `offers`, triggering a new GSC critical error ('Either offers, review, or aggregateRating should be specified').
- **Specific Correction & Non-AI / Platform Fallback (`الإصلاح المحدد والبديل الآمن`)**:
  Always merge `brand` into the existing `Product` JSON-LD object (or link via identical `@id`), never emit an incomplete orphan `Product` node.
