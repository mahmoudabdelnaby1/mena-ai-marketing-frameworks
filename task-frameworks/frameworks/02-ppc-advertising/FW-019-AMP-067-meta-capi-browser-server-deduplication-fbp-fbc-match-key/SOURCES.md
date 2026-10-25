# Evidence Register & Source Boundaries — `FW-019` (`AMP-067`)

- **Framework Title (EN)**: Meta CAPI Browser/Server Deduplication & `fbp`/`fbc` Match-Key Checklist for MENA Checkouts
- **عنوان الأصل (AR)**: قائمة فحص منع ازدواجية التحويلات (`Deduplication`) وتمرير مفاتيح `fbp`/`fbc` في `Meta CAPI` لمتاجر المنطقة
- **Channel**: Pay-Per-Click (PPC) Advertising
- **Last Reviewed Date**: `2026-10-25`
- **Verification Gate Status**: `READY_FOR_REVIEW`

## 1. Problem & Empirical Evidence (What Proves the Failure Mechanism in Egypt & GCC)

| Source ID | Title & Direct Link | Publisher | Published | Accessed | Type & Confidence | What This Source Supports | Support Boundary |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `SRC-050` | [Digital Advertising Landscape in Egypt (2026)](https://23hublab.com/digital-advertising-landscape-in-egypt/) | 23HubLab | `2026-03-15` | `2026-10-25` | `MARKET_BENCHMARK` (`RESEARCH_FINDING`) | In Egypt, standard Meta Pixel captures only 60-75% of conversions (25-40% lost to in-app browsers, iOS ATT, and ad blockers), while platform-reported conversions overstate actual revenue by 20-40% due to COD cancellations and last-click inflation; provides 2026 EGP CPM/CPC/CPL benchmarks and notes Snapchat is niche in Egypt vs TikTok/Meta. | Egyptian digital advertising market 2026. |
| `SRC-071` | [Shopify + Meta Conversions API issue : r/FacebookAds](https://www.reddit.com/r/FacebookAds/comments/1ixwjoy/shopify_meta_conversions_api_issue/) | Reddit Practitioner Community | `2025-02-25` | `2026-10-25` | `COMMUNITY_DISCUSSION` (`OBSERVED_CASE`) | Illustrates native CAPI integration failures where server events drop fbp/fbc parameters or fail to fire on manual/third-party COD checkouts. | Observed practitioner troubleshooting case; not a prevalence statistic. |

## 2. Official Platform Capability, Regulatory & Advice Evidence

| Source ID | Title & Direct Link | Publisher | Published | Accessed | Status / Confidence | Official Capability or Rule Verified | Fallback / Operational Boundary |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `SRC-007` | [Conversions API - Meta for Developers](https://developers.facebook.com/documentation/ads-commerce/conversions-api) | Meta for Developers | `2026-09-28` | `2026-10-25` | `OFFICIAL_DOCUMENTATION` (`CONFIRMED_CAPABILITY`) | Server-side CAPI requires event_id deduplication alongside browser Pixel and customer information parameters (fbp, fbc, hashed email/phone) for Event Match Quality. | Does not automatically filter out cancelled Cash-on-Delivery orders unless offline/CRM status events are configured. |
| `SRC-008` | [Troubleshoot the Conversions API - Meta for Developers](https://developers.facebook.com/documentation/ads-commerce/conversions-api/support) | Meta for Developers | `2023-11-30` | `2026-10-25` | `OFFICIAL_DOCUMENTATION` (`CONFIRMED_CAPABILITY`) | Diagnosing payload mismatches, redundant server firing, and missing deduplication keys in Meta Events Manager. | Technical implementation reference. |
| `SRC-007` | [Conversions API - Meta for Developers](https://developers.facebook.com/documentation/ads-commerce/conversions-api) | Meta for Developers | `2026-09-28` | `2026-10-25` | `OFFICIAL_CAPABILITY_CHECK` (`supported`) | Meta requires matching `event_name` and `event_id` within 48 hours for deduplication, and E.164 country-code digits (without leading `+` or `00`) before SHA-256 hashing. | Fallback: Verify in Meta Events Manager `Test Events` tab using a real test order before scaling spend. |

## 3. Counterevidence, Exceptions & When This Pattern Does NOT Apply

- In strictly single-language English B2B niches or fully prepaid digital-product flows, the severity of this Pay-Per-Click (PPC) Advertising mismatch is lower provided manual QA is still performed.
- ** Operational Boundary**: Do not send unhashed raw phone numbers or emails to third-party endpoints—normalize and SHA-256 hash customer identifiers per Meta CAPI specification and Saudi/UAE/Egypt PDPL rules. / لا ترسل أرقام الهواتف أو البريد الإلكتروني كنص مكشوف غير مشفر؛ يجب تطبيع الأرقام وتشفيرها بـ `SHA-256` وفق معايير Meta CAPI وأنظمة حماية البيانات (`PDPL`).

## 4. Claims Remaining Uncertain & Update Triggers

- **Verification Requirement**: Verify live store/account configuration and current 2026/2027 platform UI settings for Pay-Per-Click (PPC) Advertising before deploying changes.
- **Verification Requirement**: Confirm current statutory penalty thresholds and licensing rules with qualified local counsel in KSA, UAE, or Egypt.
- **No Guaranteed Outcomes**: Per Agent 2 v1.2 boundaries, this asset defines operational controls and testable measurement hypotheses; it does not promise guaranteed rankings, virality, or fixed ROAS lift.
- **Update Triggers**: Re-verify this framework whenever platform UI/API schemas change, prior to major Hijri/seasonal peaks (Ramadan/White Friday), or within 90 days of `2026-10-25`.
