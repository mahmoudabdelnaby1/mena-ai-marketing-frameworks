# Evidence Register & Source Boundaries — `FW-086` (`AMP-444`)

- **Framework Title (EN)**: GA4 MENA Marketplace & E-Commerce Referral Reclassification Checklist (`amazon.sa`, `amazon.ae`, `amazon.eg`, `noon.com`, `salla.sa`, `zid.sa`)
- **عنوان الأصل (AR)**: قائمة فحص إعادة تصنيف المتاجر والأسواق العربية (`amazon.sa`, `amazon.eg`, `noon.com`, `salla.sa`, `zid.sa`) في `GA4` بدلاً من ضياعها في `Referral`
- **Channel**: Marketing Automation
- **Last Reviewed Date**: `2026-10-25`
- **Verification Gate Status**: `READY_FOR_REVIEW`

## 1. Problem & Empirical Evidence (What Proves the Failure Mechanism in Egypt & GCC)

| Source ID | Title & Direct Link | Publisher | Published | Accessed | Type & Confidence | What This Source Supports | Support Boundary |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `SRC-039` | [Amazon.sa and noon SEO in 2026: How Product Search Works on Saudi and UAE Marketplaces](https://voctos.net/amazon-sa-noon-seo-guide/) | VOCTOS | `2026-10-08` | `2026-10-25` | `EMPIRICAL_AUDIT` (`RESEARCH_FINDING`) | Amazon.sa enforces a 75-character title rule (June/July 2026) and a <250-byte hidden keyword limit where UTF-8 Arabic letters consume 2 bytes each (~26 Arabic words max vs ~54 Latin); Noon requires English in KSA/UAE but hides English-only listings on its Arabic site; GA4 misclassifies amazon.sa and noon.com into Referral. | Amazon.sa, Amazon.ae, and Noon KSA/UAE/Egypt marketplace rules as of Oct 2026. |
| `SRC-045` | [How GA4 Classifies AI Traffic for Arab Websites: What Saudi, UAE and Egyptian Sites Lose (2026 Study)](https://voctos.net/ga4-ai-traffic-arab-markets/) | VOCTOS | `2026-10-18` | `2026-10-25` | `EMPIRICAL_AUDIT` (`RESEARCH_FINDING`) | GA4's AI Assistant channel (launched 13 May 2026) misses 96.9% of AI search citations (which come from Google AI Overviews and AI Mode and land in Organic Search), sends ChatGPT links with rel='noreferrer' or WhatsApp shares to Direct, and sends Perplexity, Claude, HUMAIN Chat (KSA), Fanar (Qatar), and Gulf marketplaces (amazon.sa, noon.com) to Referral. | Based on GA4 channel rules, StatCounter Sep 2026 Arab market data, and Delta Medical Labs KSA case study. |

## 2. Official Platform Capability, Regulatory & Advice Evidence

| Source ID | Title & Direct Link | Publisher | Published | Accessed | Status / Confidence | Official Capability or Rule Verified | Fallback / Operational Boundary |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `SRC-045` | [How GA4 Classifies AI Traffic for Arab Websites: What Saudi, UAE and Egyptian Sites Lose (2026 Study)](https://voctos.net/ga4-ai-traffic-arab-markets/) | VOCTOS | `2026-10-18` | `2026-10-25` | `OFFICIAL_CAPABILITY_CHECK` (`supported`) | VOCTOS Oct 2026 audit of Google's 819-entry GA4 source category list proved that `amazon.sa`, `amazon.ae`, `amazon.eg`, `noon.com`, `salla.sa`, and `zid.sa` are absent from Google's default list. | Fallback: Maintain the custom MENA Shopping Regex in GA4 Channel Groups and the MENA Payment Gateway list in Unwanted Referrals. |

## 3. Counterevidence, Exceptions & When This Pattern Does NOT Apply

- In strictly single-language English B2B niches or fully prepaid digital-product flows, the severity of this Marketing Automation mismatch is lower provided manual QA is still performed.
- ** Operational Boundary**: Be careful to distinguish **External Regional Marketplaces** (which belong in `Organic Shopping` / `Paid Shopping`) from **Your Own Storefront Checkout/Payment Domains** (`salla.sa`, `zid.sa`, `tabby.ai`, `tamara.co`, `paymob.com` — which belong in **`List Unwanted Referrals`** so they don't overwrite the original ad source!). / انتبه للتفريق الحاسم بين: (1) **الأسواق الخارجية** (`amazon.sa / noon.com / haraj.com.sa`) التي تضاف لقناة `Shopping`، وبين (2) **نطاقات الدفع وإتمام الطلب الخاصة بمتجرك** (`salla.sa / tabby.ai / tamara.co / paymob.com`) التي يجب إضافتها لقائمة **`Unwanted Referrals`** لمنع مسح مصدر الإعلان الأصلي!

## 4. Claims Remaining Uncertain & Update Triggers

- **Verification Requirement**: Verify live store/account configuration and current 2026/2027 platform UI settings for Marketing Automation before deploying changes.
- **Verification Requirement**: Confirm current statutory penalty thresholds and licensing rules with qualified local counsel in KSA, UAE, or Egypt.
- **No Guaranteed Outcomes**: Per Agent 2 v1.2 boundaries, this asset defines operational controls and testable measurement hypotheses; it does not promise guaranteed rankings, virality, or fixed ROAS lift.
- **Update Triggers**: Re-verify this framework whenever platform UI/API schemas change, prior to major Hijri/seasonal peaks (Ramadan/White Friday), or within 90 days of `2026-10-25`.
