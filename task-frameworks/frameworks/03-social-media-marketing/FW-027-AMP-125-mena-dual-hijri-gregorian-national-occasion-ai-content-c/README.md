# `FW-027` — MENA Dual Hijri-Gregorian & National-Occasion AI Content Calendar Workflow
## مسار عمل بناء خطط المحتوى بالذكاء الاصطناعي بالتقويمين الهجري والميلادي (رصد تداخل رمضان مع الأعياد الوطنية والمواسم)

- **One-Sentence Promise (EN)**: Build quarterly and annual MENA content calendars anchored to verified Hijri-Gregorian dates, payday windows, and overlapping national occasions (such as February 2027 when Ramadan, Saudi Founding Day, and Kuwait National Day converge in the same month).
- **الوعد التطبيقي في جملة واحدة (AR)**: بناء خطط المحتوى السنوية والربع سنوية بربط التقويمين الهجري والميلادي ومواسم الرواتب وتداخل المناسبات الوطنية والدينية (مثل فبراير 2027 حيث يتقاطع رمضان مع يوم التأسيس السعودي والعيد الوطني الكويتي).
- **Selected Artifact Type**: `OPERATING_FRAMEWORK` *(Chosen because: Generic LLMs build Gregorian-only calendars based on Western retail holidays (or outdated Hijri dates from prior years because the lunar calendar shifts ~11 days earlier each year); an OPERATING_FRAMEWORK with a verified 2026–2027 Hijri-Gregorian anchor table prevents embarrassing scheduling collisions.)*
- **Consolidated Child Pattern IDs (`MERGE_INTO_EXISTING`)**: `AMP-135`, `AMP-145`, `AMP-155`, `AMP-165`, `AMP-175`
- **Screened Duplicate IDs (`REJECT_DUPLICATE`)**: `AMP-515`
- **Intended Audience**: Social Media Manager, Community Manager, Brand Strategist, Account Director
- **Markets & Languages**: Egypt & GCC (`KSA, UAE, Kuwait, Qatar, Bahrain, Oman`) | Arabic (`Egyptian Ammiya, Saudi/Gulf Khaleeji, White MSA`) & English

## When to Use This Asset (`متى تستخدم هذه الأداة؟`)

- **Trigger (EN)**: Use when planning monthly, quarterly, or annual content, social, email, and promotional calendars for Saudi Arabia, UAE, Kuwait, Qatar, Bahrain, Oman, or Egypt.
- **داعي الاستخدام (AR)**: تُستخدم عند إعداد خطط المحتوى والحملات الشهرية أو الربع سنوية أو السنوية لأسواق الخليج ومصر.
- **Do NOT Use When**: Do not let an LLM guess Hijri dates from its internal memory—always inject the verified Umm al-Qura / local astronomical reference table into the prompt context first.

## Quick Start (3 Steps for a Non-Expert Marketer)

1. **Prepare Your Inputs (`جهّز المدخلات`)**:
   - Verified Umm al-Qura (`تقويم أم القرى`) & National Holiday Reference Table for Q4 2026 – Q2 2027
   - Target Markets (`KSA`, `UAE`, `Egypt`, `Kuwait`, `Qatar`) and Monthly Payday Windows (`25th–30th` Gregorian + `27th` Saudi government salary date)
   - Lead-time requirements for Regulatory Permits (`AMP-064` KSA Discount Permit, `AMP-281` Mawthooq Creator Booking)
2. **Copy or Run the Artifact (`انسخ القالب أو طبّق قائمة الفحص`)**:
   - Open [`ASSET.md`](./ASSET.md) and copy the ready-to-use `OPERATING_FRAMEWORK` block (or run the included validation snippet).
3. **Compare Against the Worked Example & Verify (`قارن بالمثال العملي وتجنب الأخطاء`)**:
   - Review [`EXAMPLE.md`](./EXAMPLE.md) to see the realistic input brief → raw output → human review edits → final usable result, plus the common failure mode and recovery step.
   - Check [`SOURCES.md`](./SOURCES.md) for primary official documentation, access dates (`2026-10-25`), and regulatory/technical boundaries.

## Files in This Folder

- [`README.md`](./README.md): Plain-language overview, selected artifact type, use trigger, and 3-step quick start.
- [`ASSET.md`](./ASSET.md): The complete, copy-ready `OPERATING_FRAMEWORK` (bilingual Arabic + English), model capability branches, regional adaptation matrix, and measurement plan.
- [`EXAMPLE.md`](./EXAMPLE.md): End-to-end worked example with human review pass and failure/recovery scenario.
- [`SOURCES.md`](./SOURCES.md): Direct primary references (`2026-10-25`), separating problem evidence from official capability/regulatory evidence.
- [`PUBLIC-PAGE-CONTENT.md`](./PUBLIC-PAGE-CONTENT.md): Complete user-facing web publication page containing both the full working artifact and the complete worked example.
