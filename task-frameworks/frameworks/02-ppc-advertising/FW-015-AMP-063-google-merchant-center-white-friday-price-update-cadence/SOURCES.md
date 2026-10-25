# Evidence Register & Source Boundaries — `FW-015` (`AMP-063`)

- **Framework Title (EN)**: Google Merchant Center White Friday Price-Update Cadence & Sale-Price Schema Checklist
- **عنوان الأصل (AR)**: قائمة فحص وتوقيت تحديث الأسعار في Google Merchant Center خلال الجمعة البيضاء والمواسم لمنع رفض المنتجات
- **Channel**: Pay-Per-Click (PPC) Advertising
- **Last Reviewed Date**: `2026-10-25`
- **Verification Gate Status**: `READY_FOR_REVIEW`

## 1. Problem & Empirical Evidence (What Proves the Failure Mechanism in Egypt & GCC)

| Source ID | Title & Direct Link | Publisher | Published | Accessed | Type & Confidence | What This Source Supports | Support Boundary |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `SRC-043` | [Merchant Center May Now Disapprove Products Whose Price Changes More Than Once a Day: A White Friday Price-Markup Audit of Arab Online Stores](https://voctos.net/merchant-center-price-changes-white-friday-arab-stores/) | VOCTOS | `2026-10-15` | `2026-10-25` | `EMPIRICAL_AUDIT` (`RESEARCH_FINDING`) | Google Merchant Center (updated 27 Sep 2026) warns automatic item updates fail and products risk disapproval when prices change >1x/day; in an audit of 40 Arab stores (Salla, Zid, Shopify, WooCommerce across KSA, UAE, Egypt), 0 of 24 discounted pages included readable sale_price_effective_date schema markup. | 40 Arab online stores audited on 11 Oct 2026. |
| `SRC-044` | [False Discounts in Arab Markets: What Saudi, UAE and Egyptian Law Say Before White Friday](https://voctos.net/false-discount-advertising-law-arab-markets-white-friday/) | VOCTOS | `2026-10-22` | `2026-10-25` | `LEGAL_ANALYSIS` (`RESEARCH_FINDING`) | Fake reference prices violate law across all 3 markets: KSA fines up to SAR 1,000,000 and requires a Ministry of Commerce discount license + old/new price tag; Egypt Law 181/2018 fines EGP 50,000 to EGP 2,000,000; UAE fines AED 100,000. | Read from primary statutory texts on 22 Oct 2026. |

## 2. Official Platform Capability, Regulatory & Advice Evidence

| Source ID | Title & Direct Link | Publisher | Published | Accessed | Status / Confidence | Official Capability or Rule Verified | Fallback / Operational Boundary |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `SRC-043` | [Merchant Center May Now Disapprove Products Whose Price Changes More Than Once a Day: A White Friday Price-Markup Audit of Arab Online Stores](https://voctos.net/merchant-center-price-changes-white-friday-arab-stores/) | VOCTOS | `2026-10-15` | `2026-10-25` | `OFFICIAL_CAPABILITY_CHECK` (`supported`) | Google's 27 Sep 2026 Merchant Center guidance warns against updating prices >1x/day and recommends `sale_price` + `sale_price_effective_date`. | Fallback: Use promo codes / Merchant Promotions for short intraday offers instead of mutating product page prices. |

## 3. Counterevidence, Exceptions & When This Pattern Does NOT Apply

- In strictly single-language English B2B niches or fully prepaid digital-product flows, the severity of this Pay-Per-Click (PPC) Advertising mismatch is lower provided manual QA is still performed.
- ** Operational Boundary**: Do not use dynamic hourly repricing scripts or countdown-timer price mutations on URLs submitted to Google Merchant Center. / لا تقم بتشغيل إضافات التغيير الساعي للأسعار على صفحات المنتجات المربوطة بـ Google Merchant Center.

## 4. Claims Remaining Uncertain & Update Triggers

- **Verification Requirement**: Verify live store/account configuration and current 2026/2027 platform UI settings for Pay-Per-Click (PPC) Advertising before deploying changes.
- **Verification Requirement**: Confirm current statutory penalty thresholds and licensing rules with qualified local counsel in KSA, UAE, or Egypt.
- **No Guaranteed Outcomes**: Per Agent 2 v1.2 boundaries, this asset defines operational controls and testable measurement hypotheses; it does not promise guaranteed rankings, virality, or fixed ROAS lift.
- **Update Triggers**: Re-verify this framework whenever platform UI/API schemas change, prior to major Hijri/seasonal peaks (Ramadan/White Friday), or within 90 days of `2026-10-25`.
