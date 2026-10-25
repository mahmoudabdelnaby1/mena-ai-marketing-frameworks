# End-to-End Worked Example & Failure Recovery — `FW-015` (`AMP-063`)

- **Framework**: Google Merchant Center White Friday Price-Update Cadence & Sale-Price Schema Checklist
- **العنوان بالعربية**: قائمة فحص وتوقيت تحديث الأسعار في Google Merchant Center خلال الجمعة البيضاء والمواسم لمنع رفض المنتجات
- **Selected Artifact Type**: `CHECKLIST`
- **Disclaimer**: *All scenarios, brand names, SKU codes, and metrics below are original, realistic illustrative examples for MENA practitioner training and are never represented as verified client outcomes.*

## 1. Realistic Sample Brief / Input (`المدخلات وموجز الحالة العملية`)

- **Store**: Saudi Home Appliances Store on Salla/Shopify syncing 600 SKUs to Google Merchant Center for White Friday (20–30 Nov 2026).
- **Previous Failure**: Team changed product prices 3 times on White Friday (Morning Deal, Afternoon Deal, Midnight Deal); GMC disapproved 410 of 600 SKUs for `Price mismatch between feed and landing page` during peak weekend traffic.

## 2. Initial Generated / Completed Output (`المخرج الأولي عند تطبيق الأداة`)

```xml
<!-- Compliant GMC XML Item Entry Pre-Scheduled 48h Before White Friday -->
<item>
  <g:id>SKU-COFF-901</g:id>
  <g:title>ماكينة قهوة إسبريسو ديلونجي ديديكا 15 بار - فضي</g:title>
  <g:price>999.00 SAR</g:price>
  <g:sale_price>749.00 SAR</g:sale_price>
  <g:sale_price_effective_date>2026-11-20T00:00+03:00/2026-11-30T23:59+03:00</g:sale_price_effective_date>
  <g:availability>in_stock</g:availability>
</item>
```

## 3. Human Review & Localization/Technical Edits (`المراجعة البشرية والتعديلات الرقابية والتقنية`)

1. **JSON-LD Sync Check**: Verified that the storefront Product JSON-LD outputs `749.00` (`SAR`) starting at `2026-11-20T00:00+03:00` and stays locked at `749.00` for the entire 10-day window.
2. **Midnight Booster Workaround**: Replaced the planned midnight price drop with a checkout promo code (`FRIDAY50`) so the landing page `<meta itemprop="price">` and JSON-LD `offers.price` never fluctuate intraday.

## 4. Final Reviewed Example Outcome (`النتيجة النهائية الجاهزة للتنفيذ`)

- All 600 SKUs pre-approved in Google Merchant Center 48 hours ahead of White Friday with `0` `[price_mismatch]` disapprovals and automatic `sale_price` badge activation at `00:00+03:00`.

## 5. What Can Go Wrong & Specific Correction / Fallback (`حالة الفشل المحتملة وخطة الإنقاذ والبديل`)

- **Common Failure Mode (`ما الذي قد يسير بشكل خاطئ؟`)**:
  A store enables a multi-currency Geo-IP switcher script that serves `USD` prices to Googlebot (crawling from a US IP) while the GMC KSA feed submits `SAR` prices, causing 100% account-wide price/currency mismatch disapproval.
- **Specific Correction & Non-AI / Platform Fallback (`الإصلاح المحدد والبديل الآمن`)**:
  Never redirect or rewrite currency based on visitor IP on country-specific Merchant Center URLs; use separate URL paths/parameters (`?currency=SAR`) or keep the `.sa` storefront locked to `SAR` regardless of crawler IP.
