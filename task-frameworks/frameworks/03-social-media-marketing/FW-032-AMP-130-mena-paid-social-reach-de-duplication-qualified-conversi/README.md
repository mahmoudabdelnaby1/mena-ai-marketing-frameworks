# `FW-032` — MENA Paid Social Reach De-Duplication & Qualified Conversion Evaluation Aid (TikTok/Snap KSA & UAE)
## أداة تقييم الوصول الفعلي والتحويلات المؤهلة في إعلانات التواصل الاجتماعي (معالجة تضخم أرقام الوصول في تيك توك وسناب شات بالخليج)

- **One-Sentence Promise (EN)**: Calibrate paid social media plans and executive reports in KSA and UAE where platform-reported ad reach exceeds 100% of the adult population due to multi-account and device duplication.
- **الوعد التطبيقي في جملة واحدة (AR)**: معايرة خطط وتقارير الإعلانات الاجتماعية في السعودية والإمارات حيث يتجاوز «الوصول الإعلاني المعلن» 100% من عدد السكان البالغين بسبب تعدد الحسابات والأجهزة.
- **Selected Artifact Type**: `DECISION_AID` *(Chosen because: DataReportal Digital 2026 explicitly notes that reported social ad reach in KSA (e.g., TikTok's 38.6M reported reach vs. ~34.4M total population) and UAE (TikTok 118.8%) exceeds 100% of the population due to duplicate accounts, SIMs, and tourist/visitor churn; a DECISION_AID stops AI reporting agents from presenting vanity reach as unique humans.)*
- **Consolidated Child Pattern IDs (`MERGE_INTO_EXISTING`)**: `AMP-140`, `AMP-150`, `AMP-160`, `AMP-170`
- **Screened Duplicate IDs (`REJECT_DUPLICATE`)**: None
- **Intended Audience**: Social Media Manager, Community Manager, Brand Strategist, Account Director
- **Markets & Languages**: Egypt & GCC (`KSA, UAE, Kuwait, Qatar, Bahrain, Oman`) | Arabic (`Egyptian Ammiya, Saudi/Gulf Khaleeji, White MSA`) & English

## When to Use This Asset (`متى تستخدم هذه الأداة؟`)

- **Trigger (EN)**: Use when evaluating media agency proposals, forecasting reach/frequency in KSA/UAE/Qatar/Kuwait, or building executive AI marketing performance reports.
- **داعي الاستخدام (AR)**: تُستخدم عند مراجعة عروض الوكالات الإعلانية أو التنبؤ بالوصول والتكرار (`Reach & Frequency`) في السعودية والإمارات وقطر والكويت أو إعداد تقارير الأداء التنفيذية.
- **Do NOT Use When**: Do not sum 'Unique Reach' across TikTok + Snapchat + Instagram + YouTube in KSA or UAE and claim you reached '85 million people in Saudi Arabia' (`AMP-564`).

## Quick Start (3 Steps for a Non-Expert Marketer)

1. **Prepare Your Inputs (`جهّز المدخلات`)**:
   - Platform-reported `Reach`, `Impressions`, `3-Second / 6-Second Focused Views`, and `Conversions` per channel
   - Official Population / Target Demographic Ceiling (GASTAT KSA / UAE FCSC / CAPMAS Egypt)
   - First-party verified downstream metrics (Unique Engaged Sessions in GA4, OTP-Verified Leads, or Net Delivered Orders)
2. **Copy or Run the Artifact (`انسخ القالب أو طبّق قائمة الفحص`)**:
   - Open [`ASSET.md`](./ASSET.md) and copy the ready-to-use `DECISION_AID` block (or run the included validation snippet).
3. **Compare Against the Worked Example & Verify (`قارن بالمثال العملي وتجنب الأخطاء`)**:
   - Review [`EXAMPLE.md`](./EXAMPLE.md) to see the realistic input brief → raw output → human review edits → final usable result, plus the common failure mode and recovery step.
   - Check [`SOURCES.md`](./SOURCES.md) for primary official documentation, access dates (`2026-10-25`), and regulatory/technical boundaries.

## Files in This Folder

- [`README.md`](./README.md): Plain-language overview, selected artifact type, use trigger, and 3-step quick start.
- [`ASSET.md`](./ASSET.md): The complete, copy-ready `DECISION_AID` (bilingual Arabic + English), model capability branches, regional adaptation matrix, and measurement plan.
- [`EXAMPLE.md`](./EXAMPLE.md): End-to-end worked example with human review pass and failure/recovery scenario.
- [`SOURCES.md`](./SOURCES.md): Direct primary references (`2026-10-25`), separating problem evidence from official capability/regulatory evidence.
- [`PUBLIC-PAGE-CONTENT.md`](./PUBLIC-PAGE-CONTENT.md): Complete user-facing web publication page containing both the full working artifact and the complete worked example.
