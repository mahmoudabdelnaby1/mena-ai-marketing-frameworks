# End-to-End Worked Example & Failure Recovery — `FW-003` (`AMP-003`)

- **Framework**: Salla & MENA E-Commerce Sitemap Hygiene & Dead-AI-URL Purge Checklist
- **العنوان بالعربية**: قائمة فحص وتطهير خرائط المواقع (`sitemap.xml`) في متاجر سلة والتجارة الإلكترونية من الروابط المعطوبة والمحذوفة
- **Selected Artifact Type**: `CHECKLIST`
- **Disclaimer**: *All scenarios, brand names, SKU codes, and metrics below are original, realistic illustrative examples for MENA practitioner training and are never represented as verified client outcomes.*

## 1. Realistic Sample Brief / Input (`المدخلات وموجز الحالة العملية`)

- **Store**: Riyadh Home Perfumes D2C store on Salla (`180` total URLs in `sitemap.xml`).
- **Context**: Team used an AI catalog tool to generate 95 Ramadan gift bundle SKUs, then hid all 95 bundles after Eid without auditing `sitemap.xml`.

## 2. Initial Generated / Completed Output (`المخرج الأولي عند تطبيق الأداة`)

- Total Sitemap `<loc>` URLs tested: `180`
- `200 OK`: `85` (47.2%)
- `302 Redirect to Homepage`: `79` (43.9% — hidden Ramadan bundles still listed in `sitemap.xml`)
- `410 Gone`: `16` (8.9% — deleted AI draft SKUs still cached in `sitemap.xml`)

## 3. Human Review & Localization/Technical Edits (`المراجعة البشرية والتعديلات الرقابية والتقنية`)

1. **Evergreen Retention**: Identified 12 top-selling Oud gift boxes among the 79 hidden SKUs; switched them back to Active with "Available for Pre-Order / Back in Stock Soon" instead of hiding them, restoring `200 OK` on high-backlink URLs.
2. **Sitemap Cache Purge**: Purged the remaining 67 one-off test SKUs, triggered Salla SEO sitemap regeneration, and verified that `sitemap.xml` dropped from 180 URLs to 97 clean `200 OK` URLs.

## 4. Final Reviewed Example Outcome (`النتيجة النهائية الجاهزة للتنفيذ`)

- Post-remediation `sitemap.xml` audit: `97/97` URLs (`100%`) return `200 OK` with self-referencing canonicals.
- Resubmitted `sitemap.xml` in Google Search Console (`تاريخ الإرسال: 2026-10-25`).

## 5. What Can Go Wrong & Specific Correction / Fallback (`حالة الفشل المحتملة وخطة الإنقاذ والبديل`)

- **Common Failure Mode (`ما الذي قد يسير بشكل خاطئ؟`)**:
  A merchant hides 100 seasonal White Friday pages at midnight after the sale ends; Salla's homepage 302 redirect triggers Google Search Console 'Soft 404' errors across all 100 URLs.
- **Specific Correction & Non-AI / Platform Fallback (`الإصلاح المحدد والبديل الآمن`)**:
  Maintain a single evergreen `/ar/white-friday-offers` hub page year-round (`200 OK`) and attach seasonal SKU cards dynamically rather than creating and hiding disposable URLs every season.
