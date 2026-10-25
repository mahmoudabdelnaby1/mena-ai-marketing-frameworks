# End-to-End Worked Example & Failure Recovery — `FW-008` (`AMP-008`)

- **Framework**: Arabic URL Slug Architecture & Percent-Encoding Length Decision Aid
- **العنوان بالعربية**: أداة القرار المعماري لروابط صفحات الويب العربية (`URL Slugs`) ومنع انفجار الترميز المئوي (`%D8%`)
- **Selected Artifact Type**: `DECISION_AID`
- **Disclaimer**: *All scenarios, brand names, SKU codes, and metrics below are original, realistic illustrative examples for MENA practitioner training and are never represented as verified client outcomes.*

## 1. Realistic Sample Brief / Input (`المدخلات وموجز الحالة العملية`)

- **CMS**: WordPress + WooCommerce (Cairo & Riyadh E-Commerce blog).
- **AI-Generated Draft Slug**: `أفضل-فرشاة-حرارية-لاسلكية-لفرد-الشعر-في-السعودية-ومصر-بالتقسيط` (`62` visible chars).

## 2. Initial Generated / Completed Output (`المخرج الأولي عند تطبيق الأداة`)

- `validate_mena_slug("example.sa", "ar", "أفضل-فرشاة-حرارية-لاسلكية-لفرد-الشعر-في-السعودية-ومصر-بالتقسيط")`:
  - `encoded_slug_len`: **`328` chars** (`FAIL` — exceeds WordPress 200-char `post_name` limit by 128 chars; WordPress cuts it off mid-character!).
  - `ga4_projected_len_with_utms`: **`511` chars** (`FAIL` — exceeds GA4 420-char `page_location` limit, stripping `gclid` and `utm_campaign`!).

## 3. Human Review & Localization/Technical Edits (`المراجعة البشرية والتعديلات الرقابية والتقنية`)

1. **Selected Scenario A (Clean ASCII under `/ar/`)**: Changed the slug to `/ar/cordless-hair-straightener-brush` (`32` ASCII chars) while keeping the Arabic `<title>` and `<h1>` 100% localized.
2. **Provided Scenario B Alternative**: For teams requiring Arabic script in the URL, shortened to 3 words: `/ar/فرشاة-شعر-لاسلكية` (`17` visible chars = `92` encoded chars, passing both WordPress and GA4 gates).

## 4. Final Reviewed Example Outcome (`النتيجة النهائية الجاهزة للتنفيذ`)

- **Production URL**: `https://example.sa/ar/cordless-hair-straightener-brush`
- `encoded_slug_len`: `32` chars (`PASS <= 190`)
- `ga4_projected_len_with_utms`: `215` chars (`PASS <= 420`)

## 5. What Can Go Wrong & Specific Correction / Fallback (`حالة الفشل المحتملة وخطة الإنقاذ والبديل`)

- **Common Failure Mode (`ما الذي قد يسير بشكل خاطئ؟`)**:
  An AI auto-blogger plugin sets the WordPress slug directly from the full 12-word Arabic article title; WordPress truncates `post_name` at byte 200, producing a malformed trailing `%D8` byte that causes `400 Bad Request` or infinite redirect loops on Nginx/Apache.
- **Specific Correction & Non-AI / Platform Fallback (`الإصلاح المحدد والبديل الآمن`)**:
  Configure the publishing script to generate a dedicated 3–5 word English ASCII slug (`slug_ascii`) or a max-3-word Arabic root slug (`<= 25` chars) instead of copying `post_title`.
