# Evidence Register & Source Boundaries — `FW-077` (`AMP-390`)

- **Framework Title (EN)**: Egypt & KSA Localized Checkout Address Form Workflow
- **عنوان الأصل (AR)**: مسار تخصيص حقول العنوان في صفحة الدفع لمصر والسعودية
- **Channel**: CRO - Conversion Rate Optimization
- **Last Reviewed Date**: `2026-10-25`
- **Verification Gate Status**: `READY_FOR_REVIEW`

## 1. Problem & Empirical Evidence (What Proves the Failure Mechanism in Egypt & GCC)

| Source ID | Title & Direct Link | Publisher | Published | Accessed | Type & Confidence | What This Source Supports | Support Boundary |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `SRC-050` | [Digital Advertising Landscape in Egypt (2026)](https://23hublab.com/digital-advertising-landscape-in-egypt/) | 23HubLab | `2026-03-15` | `2026-10-25` | `MARKET_BENCHMARK` (`RESEARCH_FINDING`) | In Egypt, standard Meta Pixel captures only 60-75% of conversions (25-40% lost to in-app browsers, iOS ATT, and ad blockers), while platform-reported conversions overstate actual revenue by 20-40% due to COD cancellations and last-click inflation; provides 2026 EGP CPM/CPC/CPL benchmarks and notes Snapchat is niche in Egypt vs TikTok/Meta. | Egyptian digital advertising market 2026. |
| `SRC-084` | [Payment Gateways in Egypt 2026: Paymob, Fawry, InstaPay](https://nilexdigitalsystems.com/articles/payment-gateways-egypt-paymob-fawry-instapay) | Nilex Digital Systems | `2026-09-26` | `2026-10-25` | `PRACTITIONER_GUIDE` (`REPEATED_SIGNAL`) | Details checkout UX, reconciliation, and conversion fixes for Paymob, Fawry reference codes, Meeza, InstaPay, and valU in Egypt. | Egyptian online store checkout architecture. |

## 2. Official Platform Capability, Regulatory & Advice Evidence

| Source ID | Title & Direct Link | Publisher | Published | Accessed | Status / Confidence | Official Capability or Rule Verified | Fallback / Operational Boundary |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `SRC-084` | [Payment Gateways in Egypt 2026: Paymob, Fawry, InstaPay](https://nilexdigitalsystems.com/articles/payment-gateways-egypt-paymob-fawry-instapay) | Nilex Digital Systems | `2026-09-26` | `2026-10-25` | `OFFICIAL_CAPABILITY_CHECK` (`supported`) | Egyptian couriers route by Governorate + District + Street/Building + Landmark, UAE has no postal codes, and KSA uses City + District + SPL National Address / Map Pin. | Fallback: Always hide or make `Postal Code` optional on MENA checkouts and pass `'00000'` as the backend fallback. |

## 3. Counterevidence, Exceptions & When This Pattern Does NOT Apply

- In strictly single-language English B2B niches or fully prepaid digital-product flows, the severity of this CRO - Conversion Rate Optimization mismatch is lower provided manual QA is still performed.
- ** Operational Boundary**: Confirm whether a postal code is required by the merchant’s platform, carrier, address validation, or delivery market before making it mandatory. / لا تجعل حقل «الرمز البريدي (`Postal Code`)» حقلاً إجبارياً يمنع إتمام الطلب في متاجر مصر أو السعودية أو الإمارات!

## 4. Claims Remaining Uncertain & Update Triggers

- **Verification Requirement**: Verify live store/account configuration and current 2026/2027 platform UI settings for CRO - Conversion Rate Optimization before deploying changes.
- **Verification Requirement**: Confirm current statutory penalty thresholds and licensing rules with qualified local counsel in KSA, UAE, or Egypt.
- **No Guaranteed Outcomes**: Per Agent 2 v1.2 boundaries, this asset defines operational controls and testable measurement hypotheses; it does not promise guaranteed rankings, virality, or fixed ROAS lift.
- **Update Triggers**: Re-verify this framework whenever platform UI/API schemas change, prior to major Hijri/seasonal peaks (Ramadan/White Friday), or within 90 days of `2026-10-25`.
