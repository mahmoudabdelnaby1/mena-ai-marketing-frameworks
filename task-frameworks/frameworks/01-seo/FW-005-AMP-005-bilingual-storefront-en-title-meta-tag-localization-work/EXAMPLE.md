# End-to-End Worked Example & Failure Recovery — `FW-005` (`AMP-005`)

- **Framework**: Bilingual Storefront `/en/` Title & Meta Tag Localization Workflow (Salla & Zid)
- **العنوان بالعربية**: مسار عمل تعريب وترجمة وسوم العناوين (`<title>`) والميتا للصفحات الإنجليزية في متاجر سلة وزد
- **Selected Artifact Type**: `OPERATING_FRAMEWORK`
- **Disclaimer**: *All scenarios, brand names, SKU codes, and metrics below are original, realistic illustrative examples for MENA practitioner training and are never represented as verified client outcomes.*

## 1. Realistic Sample Brief / Input (`المدخلات وموجز الحالة العملية`)

- **Store**: Saudi Oud & Bakhoor Store on Zid (`https://bakhoor-example.sa/en/products/royal-cambodi-oud`).
- **Current Broken `/en/` `<title>`**: `<title>عود كمبودي ملكي فاخر 50 جرام - متجر طيب</title>` (100% Arabic script on `/en/` URL).

## 2. Initial Generated / Completed Output (`المخرج الأولي عند تطبيق الأداة`)

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

## 3. Human Review & Localization/Technical Edits (`المراجعة البشرية والتعديلات الرقابية والتقنية`)

1. **Glossary Check**: Confirmed the brand's preferred English spelling is `"Bakhoor"` rather than `"Bukhoor"` to match their Google Merchant Center English feed.
2. **Zid Field Check**: Imported into Zid's English SEO Title field and verified live HTML `<title>` on `/en/products/royal-cambodi-oud`.

## 4. Final Reviewed Example Outcome (`النتيجة النهائية الجاهزة للتنفيذ`)

- **Live `/en/` `<title>` (60 chars)**: `Royal Cambodi Oud Wood Chips 50g | Authentic Bakhoor - Tayeb`
- **Live `/ar/` `<title>` (52 chars)**: `عود كمبودي ملكي فاخر 50 جرام | توصيل سريع - متجر طيب`

## 5. What Can Go Wrong & Specific Correction / Fallback (`حالة الفشل المحتملة وخطة الإنقاذ والبديل`)

- **Common Failure Mode (`ما الذي قد يسير بشكل خاطئ؟`)**:
  A marketer translates the main product name (`Product Title`) in the English tab of Salla/Zid, but forgets to switch the language tab inside the separate bottom `SEO Settings` box—so the page `<h1>` is in English while `<title>` remains in Arabic.
- **Specific Correction & Non-AI / Platform Fallback (`الإصلاح المحدد والبديل الآمن`)**:
  Always audit the rendered `<title>` element in raw HTML (`curl -s URL | grep '<title>'`), never just the product name column in the dashboard.
