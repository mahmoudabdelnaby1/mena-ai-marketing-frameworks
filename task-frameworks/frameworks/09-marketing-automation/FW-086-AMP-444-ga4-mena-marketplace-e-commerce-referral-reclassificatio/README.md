# `FW-086` — GA4 MENA Marketplace & E-Commerce Referral Reclassification Checklist (`amazon.sa`, `amazon.ae`, `amazon.eg`, `noon.com`, `salla.sa`, `zid.sa`)
## قائمة فحص إعادة تصنيف المتاجر والأسواق العربية (`amazon.sa`, `amazon.eg`, `noon.com`, `salla.sa`, `zid.sa`) في `GA4` بدلاً من ضياعها في `Referral`

- **One-Sentence Promise (EN)**: Rescue traffic from `amazon.sa`, `amazon.ae`, `amazon.eg`, `noon.com`, `salla.sa`, `zid.sa`, `haraj.com.sa`, `dubizzle`, and `instashop` that Google's 819-domain default GA4 source list misclassifies as generic `Referral` instead of `Shopping`.
- **الوعد التطبيقي في جملة واحدة (AR)**: إنقاذ الزيارات القادمة من منصات التجارة العربية (`amazon.sa`, `amazon.ae`, `amazon.eg`, `noon.com`, `salla.sa`, `zid.sa`, `حراج`, `دوبيزل`) التي تصنفها قائمة جوجل الافتراضية في `GA4` كإحالات عادية (`Referral`) بدلاً من قنوات التسوق (`Shopping`).
- **Selected Artifact Type**: `CHECKLIST` *(Chosen because: VOCTOS's October 2026 line-by-line inspection of all 819 entries in Google's official GA4 `Source Categories` PDF confirmed that while `amazon.com` and `amazon.co.uk` are classified as `SOURCE_CATEGORY_SHOPPING`, **`amazon.sa`, `amazon.ae`, `amazon.eg`, `noon.com`, `salla.sa`, `zid.sa`, and `haraj.com.sa` are completely absent from Google's list**—causing GA4 to dump all traffic from regional marketplaces into generic `Referral` (and causing self-referrals when customers return from `salla.sa`/`zid.sa` checkout sub-routes)!)*
- **Consolidated Child Pattern IDs (`MERGE_INTO_EXISTING`)**: `AMP-454`, `AMP-464`, `AMP-474`, `AMP-484`, `AMP-494`
- **Screened Duplicate IDs (`REJECT_DUPLICATE`)**: None
- **Intended Audience**: Marketing Operations Manager, CRM & Automation Architect, Data Analyst, Growth Engineer
- **Markets & Languages**: Egypt & GCC (`KSA, UAE, Kuwait, Qatar, Bahrain, Oman`) | Arabic (`Egyptian Ammiya, Saudi/Gulf Khaleeji, White MSA`) & English

## When to Use This Asset (`متى تستخدم هذه الأداة؟`)

- **Trigger (EN)**: Use when auditing GA4 properties for any brand, marketplace seller, or e-commerce store operating in Saudi Arabia, UAE, or Egypt.
- **داعي الاستخدام (AR)**: تُستخدم عند ضبط أو تدقيق حساب `GA4` لأي علامة تجارية أو متجر إلكتروني يعمل في السعودية أو الإمارات أو مصر.
- **Do NOT Use When**: Be careful to distinguish **External Regional Marketplaces** (which belong in `Organic Shopping` / `Paid Shopping`) from **Your Own Storefront Checkout/Payment Domains** (`salla.sa`, `zid.sa`, `tabby.ai`, `tamara.co`, `paymob.com` — which belong in **`List Unwanted Referrals`** so they don't overwrite the original ad source!).

## Quick Start (3 Steps for a Non-Expert Marketer)

1. **Prepare Your Inputs (`جهّز المدخلات`)**:
   - GA4 Admin access (`Data Streams -> Configure tag settings -> List unwanted referrals` AND `Data display -> Channel groups`)
   - List of active payment gateways (`Tabby`, `Tamara`, `Moyasar`, `HyperPay`, `Tap`, `Paymob`, `Fawry`, `Kashier`) and storefront domains
2. **Copy or Run the Artifact (`انسخ القالب أو طبّق قائمة الفحص`)**:
   - Open [`ASSET.md`](./ASSET.md) and copy the ready-to-use `CHECKLIST` block (or run the included validation snippet).
3. **Compare Against the Worked Example & Verify (`قارن بالمثال العملي وتجنب الأخطاء`)**:
   - Review [`EXAMPLE.md`](./EXAMPLE.md) to see the realistic input brief → raw output → human review edits → final usable result, plus the common failure mode and recovery step.
   - Check [`SOURCES.md`](./SOURCES.md) for primary official documentation, access dates (`2026-10-25`), and regulatory/technical boundaries.

## Files in This Folder

- [`README.md`](./README.md): Plain-language overview, selected artifact type, use trigger, and 3-step quick start.
- [`ASSET.md`](./ASSET.md): The complete, copy-ready `CHECKLIST` (bilingual Arabic + English), model capability branches, regional adaptation matrix, and measurement plan.
- [`EXAMPLE.md`](./EXAMPLE.md): End-to-end worked example with human review pass and failure/recovery scenario.
- [`SOURCES.md`](./SOURCES.md): Direct primary references (`2026-10-25`), separating problem evidence from official capability/regulatory evidence.
- [`PUBLIC-PAGE-CONTENT.md`](./PUBLIC-PAGE-CONTENT.md): Complete user-facing web publication page containing both the full working artifact and the complete worked example.
