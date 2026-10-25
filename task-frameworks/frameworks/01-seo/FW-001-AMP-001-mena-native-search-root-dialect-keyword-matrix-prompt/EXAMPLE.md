# End-to-End Worked Example & Failure Recovery — `FW-001` (`AMP-001`)

- **Framework**: MENA Native Search Root & Dialect Keyword Matrix Prompt
- **العنوان بالعربية**: قالب هندسة الكلمات المفتاحية العربية حسب الجذر اللغوي واللهجة المحلية (مصر والخليج)
- **Selected Artifact Type**: `PROMPT_TEMPLATE`
- **Disclaimer**: *All scenarios, brand names, SKU codes, and metrics below are original, realistic illustrative examples for MENA practitioner training and are never represented as verified client outcomes.*

## 1. Realistic Sample Brief / Input (`المدخلات وموجز الحالة العملية`)

- **Target Market**: Saudi Arabia (Riyadh & Jeddah) + Egypt (Cairo & Alexandria)
- **Platform**: Salla (KSA store) & WooCommerce (Egypt store)
- **Product Concept**: "Cordless Hair Straightener Brush" (فرشاة فرد الشعر اللاسلكية)
- **Price & Payment**: KSA: 299 SAR (incl. 15% VAT, Tabby/Tamara 4 payments); Egypt: 2,450 EGP (COD + InstaPay + valU)
- **Verified Seeds**: فرشاه شعر لاسلكيه، مشط حراري لاسلكي، سيراميك شعر بدون سلك

## 2. Initial Generated / Completed Output (`المخرج الأولي عند تطبيق الأداة`)

| Cluster ID | Native Arabic Query | Market & Register | Intent Stage | Orthographic Variants | Literal Translation Rejected | Target Page Element |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| KW-01 | مشط حراري لاسلكي للشعر | KSA (Khaleeji/MSA) | Commercial / Transactional | مشط حرارى لاسلكى، فرشاه حراريه | فرشاة تقويم الشعر بدون حبل | H1 & Meta Title (KSA) |
| KW-02 | افضل فرشاة شعر لاسلكية بالتقسيط تابي | KSA (Riyadh/Jeddah) | High-Intent Transactional | افضل فرشاه شعر لاسلكيه تابى | شراء مملس شعر لاسلكي رخيص | Product Subtitle & FAQ |
| KW-03 | سعر فرشاة فرد الشعر اللاسلكية في مصر | Egypt (Ammiya/MSA) | Transactional Price Check | سعر فرشاه فرد الشعر اللاسلكيه | تكلفة فرشاة تنعيم الشعر | H1 & Meta Title (Egypt) |
| KW-04 | مكواة شعر فرشاه بدون سلك الدفع عند الاستلام | Egypt (Ammiya) | Transactional COD | مكواه شعر فرشاه، فرشة شعر حرارية | أداة تصفيف الشعر الخالية من الأسلاك | Collection Filter & Meta Description |

## 3. Human Review & Localization/Technical Edits (`المراجعة البشرية والتعديلات الرقابية والتقنية`)

1. **Lexical Validation (KSA)**: Verified in Saudi Google Autocomplete that shoppers search `"استشوار مشط لاسلكي"` and `"فرشاة سيراميك لاسلكية"` more frequently than `"فرشاة فرد"`. Added `"استشوار مشط لاسلكي"` as secondary H2 keyword for the Salla KSA storefront.
2. **Regulatory Guardrail (SFDA/EDA)**: Removed an AI-suggested FAQ phrase `"يعالج تقصف الشعر نهائياً"` (therapeutic claim risk under SFDA cosmetic rules) and replaced it with `"تصفيف سريع مع التحكم في درجات الحرارة"`.
3. **Slug Hygiene**: Kept the URL slug in clean ASCII (`/ar/cordless-hair-straightener-brush`) per `AMP-008` to avoid UTF-8 percent-encoding bloat while keeping `<title>` and `<h1>` in native Arabic.

## 4. Final Reviewed Example Outcome (`النتيجة النهائية الجاهزة للتنفيذ`)

- **KSA Salla `<title>` (58 chars)**: `مشط حراري وفرشاة شعر لاسلكية | تقسيط تابي وتمارا - متجرنا`
- **KSA Salla `<h1>`**: `فرشاة فرد الشعر الحرارية اللاسلكية (شحن USB-C)`
- **Egypt WooCommerce `<title>` (61 chars)**: `فرشاة فرد الشعر الحرارية اللاسلكية | شحن لجميع محافظات مصر`
- **Egypt WooCommerce `<h1>`**: `مكواة وفرشاة فرد الشعر اللاسلكية - الدفع عند الاستلام أو إنستاباي`

## 5. What Can Go Wrong & Specific Correction / Fallback (`حالة الفشل المحتملة وخطة الإنقاذ والبديل`)

- **Common Failure Mode (`ما الذي قد يسير بشكل خاطئ؟`)**:
  An SEO specialist runs the prompt without supplying `VERIFIED_SEEDS` from Google Search Console or Autocomplete, causing the LLM to invent plausible-sounding Gulf slang that has zero actual monthly search volume.
- **Specific Correction & Non-AI / Platform Fallback (`الإصلاح المحدد والبديل الآمن`)**:
  Enforce the Pre-Flight Rule: never accept an AI keyword table into production until at least 3 top terms per cluster are cross-checked against Google Search Console Performance queries, Google Autocomplete (set to KSA/Egypt locale), or Salla/Amazon.sa search bar suggestions.
