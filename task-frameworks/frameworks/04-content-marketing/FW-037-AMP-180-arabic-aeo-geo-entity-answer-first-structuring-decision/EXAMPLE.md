# End-to-End Worked Example & Failure Recovery — `FW-037` (`AMP-180`)

- **Framework**: Arabic AEO / GEO Entity & Answer-First Structuring Decision Aid (Beyond the `llms.txt` Myth)
- **العنوان بالعربية**: أداة القرار لهيكلة المحتوى العربي لمحركات إجابات الذكاء الاصطناعي (`AEO / GEO` — بدلاً من وهم ملف `llms.txt`)
- **Selected Artifact Type**: `DECISION_AID`
- **Disclaimer**: *All scenarios, brand names, SKU codes, and metrics below are original, realistic illustrative examples for MENA practitioner training and are never represented as verified client outcomes.*

## 1. Realistic Sample Brief / Input (`المدخلات وموجز الحالة العملية`)

- **Client**: Riyadh & Dubai B2B Cloud HR & Payroll SaaS Platform (targeting Saudi Labor Law / GOSI / WPS compliance queries).
- **Vendor Pitch Received**: A vendor quoted `$8,000` to 'install `llms.txt` and optimize AI metadata for guaranteed ChatGPT #1 citations'.

## 2. Initial Generated / Completed Output (`المخرج الأولي عند تطبيق الأداة`)

- **Decision Aid Evaluation**:
  - **Rejected `$8,000` `llms.txt` pitch** (`P4 Negligible / Unverified`).
  - **Executed P0–P1 AEO Plan**:
    1. Submitted sitemap to Bing Webmaster Tools (previously unsubmitted!) and verified `OAI-SearchBot` + `Googlebot` access.
    2. Built 10 Answer-First Arabic & English comparison pages (`"مقارنة أنظمة حماية الأجور ومدد والتأمينات الاجتماعية في السعودية 2026"`) featuring a clean HTML comparison table (`السعر بالريال`, `الربط مع قوى ومدد`, `حاسبة نهاية الخدمة`) in the top 200 words.

## 3. Human Review & Localization/Technical Edits (`المراجعة البشرية والتعديلات الرقابية والتقنية`)

1. **Added Bilingual Entity Disambiguation**: Added `"name": "Jisr HR"`, `"alternateName": "جسر للموارد البشرية"` in `Organization` and `SoftwareApplication` JSON-LD so Arabic and English queries resolve to the same entity.
2. **Paired with GA4 AI Traffic Tracking (`AMP-443`)**: Configured GA4 custom exploration and Search Console cross-referencing to measure actual AI referral and AI Overview organic clicks.

## 4. Final Reviewed Example Outcome (`النتيجة النهائية الجاهزة للتنفيذ`)

- Saved `$8,000` on unverified `llms.txt` tooling and deployed 10 server-rendered, schema-backed bilingual comparison hubs indexed in both Google and Bing.

## 5. What Can Go Wrong & Specific Correction / Fallback (`حالة الفشل المحتملة وخطة الإنقاذ والبديل`)

- **Common Failure Mode (`ما الذي قد يسير بشكل خاطئ؟`)**:
  A site blocks `Bingbot` or renders all product pricing inside a client-side React modal requiring a click; the brand disappears completely from ChatGPT Search and Perplexity product comparisons even though it uploaded an `llms.txt` file.
- **Specific Correction & Non-AI / Platform Fallback (`الإصلاح المحدد والبديل الآمن`)**:
  Verify with `curl -sL https://your-url` that product names, Arabic/English brand names, prices (`SAR/AED/EGP`), and comparison tables exist in raw server HTML and that `Googlebot`, `Bingbot`, and `OAI-SearchBot` receive `200 OK`.
