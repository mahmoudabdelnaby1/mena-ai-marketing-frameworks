# End-to-End Worked Example & Failure Recovery — `FW-032` (`AMP-130`)

- **Framework**: MENA Paid Social Reach De-Duplication & Qualified Conversion Evaluation Aid (TikTok/Snap KSA & UAE)
- **العنوان بالعربية**: أداة تقييم الوصول الفعلي والتحويلات المؤهلة في إعلانات التواصل الاجتماعي (معالجة تضخم أرقام الوصول في تيك توك وسناب شات بالخليج)
- **Selected Artifact Type**: `DECISION_AID`
- **Disclaimer**: *All scenarios, brand names, SKU codes, and metrics below are original, realistic illustrative examples for MENA practitioner training and are never represented as verified client outcomes.*

## 1. Realistic Sample Brief / Input (`المدخلات وموجز الحالة العملية`)

- **Scenario**: A Riyadh retail brand's monthly AI-generated agency deck claimed: `"حققنا هذا الشهر وصولاً لـ 46 مليون مستخدم فريد في المملكة العربية السعودية عبر تيك توك وسناب شات وإنستغرام!"` (claiming 46M unique Saudis when the entire population of KSA is ~34.4M).

## 2. Initial Generated / Completed Output (`المخرج الأولي عند تطبيق الأداة`)

- **Corrected Executive Scorecard (Reconciled & De-Duplicated)**:
  - **Gross Ad Impressions Across Platforms**: `68.4M`
  - **Platform Account Reach (Non-Additive)**: TikTok `14.2M` accounts | Snapchat `11.8M` accounts | Instagram `7.5M` accounts (`Estimated De-Duplicated Unique KSA Audience Reached: ~15.5M – 18.0M adults at ~3.8x–4.4x cross-platform frequency`).
  - **Verified Attention KPI**: `9.4M` 6-Second Focused Views (`Cost per 6s View: 0.04 SAR`).
  - **Verified Commercial KPI**: `312,000` Unique Engaged Storefront Sessions (`GA4`) -> `8,420` Net Delivered Orders.

## 3. Human Review & Localization/Technical Edits (`المراجعة البشرية والتعديلات الرقابية والتقنية`)

1. **Added Explicit Footnote in Monthly Report Template**: Added a permanent footnote to the automated reporting prompt forbidding cross-platform `Reach` summation and citing GASTAT/DataReportal multi-account methodology.
2. **Shifted Awareness Bidding**: Moved top-of-funnel campaigns from `Maximum Reach (Impressions)` to `6-Second Focused View / ThruPlay`.

## 4. Final Reviewed Example Outcome (`النتيجة النهائية الجاهزة للتنفيذ`)

- Executive reporting template updated to prevent `>100%` population reach hallucinations and tie media spend to 6-second attention and verified site/checkout actions.

## 5. What Can Go Wrong & Specific Correction / Fallback (`حالة الفشل المحتملة وخطة الإنقاذ والبديل`)

- **Common Failure Mode (`ما الذي قد يسير بشكل خاطئ؟`)**:
  An automated Looker Studio / LLM commentary script sums the `Reach` column across 8 campaigns within the same ad account and tells the CEO `'We reached 22 million people in Dubai this week'` (where Dubai's population is ~3.8M).
- **Specific Correction & Non-AI / Platform Fallback (`الإصلاح المحدد والبديل الآمن`)**:
  In Looker Studio, BigQuery, and AI reporting prompts, mark `Reach` as a **Non-Summable Metric (`MAX` only, never `SUM` across rows)**—summing `Reach` across campaigns or ad sets is mathematically invalid.
