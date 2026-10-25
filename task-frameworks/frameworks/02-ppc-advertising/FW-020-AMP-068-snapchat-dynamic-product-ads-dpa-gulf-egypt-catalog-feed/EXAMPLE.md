# End-to-End Worked Example & Failure Recovery — `FW-020` (`AMP-068`)

- **Framework**: Snapchat Dynamic Product Ads (DPA) Gulf & Egypt Catalog Feed Validator Checklist
- **العنوان بالعربية**: قائمة فحص وتدقيق كتالوجات إعلانات المنتجات الديناميكية في سناب شات (`Snapchat DPA`) لأسواق الخليج ومصر
- **Selected Artifact Type**: `CHECKLIST`
- **Disclaimer**: *All scenarios, brand names, SKU codes, and metrics below are original, realistic illustrative examples for MENA practitioner training and are never represented as verified client outcomes.*

## 1. Realistic Sample Brief / Input (`المدخلات وموجز الحالة العملية`)

- **Store**: Riyadh Women's Abaya & Perfume Store launching Snapchat Dynamic Product Ads (`750` SKUs).
- **Problem**: CSV export from AI catalog generator had `price: "٢٨٠ ر.س"`, `availability: "متوفر"`, and `id: "SKU-104"` while the Snap Pixel fired Salla's numeric product ID `"19488210"`. Snap Catalog Diagnostics rejected `100%` of rows.

## 2. Initial Generated / Completed Output (`المخرج الأولي عند تطبيق الأداة`)

- **Feed Scrubber Output**:
  - `id`: `"19488210"` (Synced to match Salla's native Snap Pixel `item_ids`)
  - `title`: `"عباية كريب ملكي سوداء بتطريز يدوي على الأكمام"`
  - `price`: `"280.00 SAR"`
  - `sale_price`: `"239.00 SAR"`
  - `availability`: `"in stock"`
  - `condition`: `"new"`

## 3. Human Review & Localization/Technical Edits (`المراجعة البشرية والتعديلات الرقابية والتقنية`)

1. **Verified Salla Pixel ID Match**: Tested a live Add-to-Cart event on the store with Snap Pixel Helper to confirm whether `item_ids` passed the Salla Product ID (`19488210`) or SKU (`SKU-104`), locking the feed `id` column to the exact value emitted by the pixel (`AMP-544`).
2. **Safe-Zone Image Check**: Confirmed primary `image_link` images have centered products so Snapchat's bottom CTA bar (`AMP-338`) does not cover the Abaya design.

## 4. Final Reviewed Example Outcome (`النتيجة النهائية الجاهزة للتنفيذ`)

- `750 / 750` SKUs ingested with `0` errors in Snapchat Catalog Manager and `98.4%` Pixel-to-Catalog `item_ids` match rate.

## 5. What Can Go Wrong & Specific Correction / Fallback (`حالة الفشل المحتملة وخطة الإنقاذ والبديل`)

- **Common Failure Mode (`ما الذي قد يسير بشكل خاطئ؟`)**:
  A store submits bare numbers (`280.00`) in the `price` column without `SAR`; Snapchat's catalog parser interprets bare numbers as `280.00 USD` (`~1,050 SAR`), displaying inflated USD prices or failing currency validation against the `SAR` ad account.
- **Specific Correction & Non-AI / Platform Fallback (`الإصلاح المحدد والبديل الآمن`)**:
  Always append the 3-letter ISO currency code (`280.00 SAR`, `280.00 AED`, `1200.00 EGP`) to every `price` and `sale_price` cell in Snapchat feeds.
