# Evidence Register & Source Boundaries — `FW-090` (`AMP-448`)

- **Framework Title (EN)**: Automated WhatsApp COD Order Confirmation, Address-Pin & Prepaid-Switch Workflow (Egypt & KSA)
- **عنوان الأصل (AR)**: مسار عمل التأكيد الآلي لطلبات الدفع عند الاستلام (`COD`) والتحقق من موقع التوصيل عبر واتساب قبل تسليم الشحنة للمندوب (مصر والسعودية)
- **Channel**: Marketing Automation
- **Last Reviewed Date**: `2026-10-25`
- **Verification Gate Status**: `READY_FOR_REVIEW`

## 1. Problem & Empirical Evidence (What Proves the Failure Mechanism in Egypt & GCC)

| Source ID | Title & Direct Link | Publisher | Published | Accessed | Type & Confidence | What This Source Supports | Support Boundary |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `SRC-050` | [Digital Advertising Landscape in Egypt (2026)](https://23hublab.com/digital-advertising-landscape-in-egypt/) | 23HubLab | `2026-03-15` | `2026-10-25` | `MARKET_BENCHMARK` (`RESEARCH_FINDING`) | In Egypt, standard Meta Pixel captures only 60-75% of conversions (25-40% lost to in-app browsers, iOS ATT, and ad blockers), while platform-reported conversions overstate actual revenue by 20-40% due to COD cancellations and last-click inflation; provides 2026 EGP CPM/CPC/CPL benchmarks and notes Snapchat is niche in Egypt vs TikTok/Meta. | Egyptian digital advertising market 2026. |
| `SRC-083` | [Payment Gateway Egypt: Fees, Comparison & Best Providers (2026)](https://digitology.co/payment-gateway-egypt/) | Digitology Egypt | `2026-08-07` | `2026-10-25` | `MARKET_BENCHMARK` (`RESEARCH_FINDING`) | Secondary payment-provider article; not treated as representative national payment-share evidence. | Use current merchant order and session records to assess payment mix and checkout decisions. |
| `SRC-084` | [Payment Gateways in Egypt 2026: Paymob, Fawry, InstaPay](https://nilexdigitalsystems.com/articles/payment-gateways-egypt-paymob-fawry-instapay) | Nilex Digital Systems | `2026-09-26` | `2026-10-25` | `PRACTITIONER_GUIDE` (`REPEATED_SIGNAL`) | Details checkout UX, reconciliation, and conversion fixes for Paymob, Fawry reference codes, Meeza, InstaPay, and valU in Egypt. | Egyptian online store checkout architecture. |

## 2. Official Platform Capability, Regulatory & Advice Evidence

| Source ID | Title & Direct Link | Publisher | Published | Accessed | Status / Confidence | Official Capability or Rule Verified | Fallback / Operational Boundary |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `SRC-009` | [Template messages - Meta for Developers](https://developers.facebook.com/documentation/business-messaging/whatsapp/messages/template-messages) | Meta for Developers | `2026-04-23` | `2026-10-25` | `OFFICIAL_CAPABILITY_CHECK` (`supported`) | WhatsApp Cloud API supports up to 3 Quick-Reply buttons on `UTILITY` templates and receives native GPS `location` objects (`latitude`, `longitude`, `address`) when a customer shares their pin. | Fallback: If WhatsApp number is unreachable (landline or non-WhatsApp SIM), fall back automatically to an SMS confirmation link after 2 hours. |

## 3. Counterevidence, Exceptions & When This Pattern Does NOT Apply

- In strictly single-language English B2B niches or fully prepaid digital-product flows, the severity of this Marketing Automation mismatch is lower provided manual QA is still performed.
- ** Operational Boundary**: Do not put already-paid orders (`Apple Pay`, `Mada`, `Card`, `InstaPay Verified`, `Tabby`, `Tamara`) on hold waiting for WhatsApp confirmation—ship prepaid orders immediately and send them a standard shipping notification! / لا تقم أبداً بتجميد أو تعليق الشحن للطلبات المدفوعة مسبقاً (`مدى`، `Apple Pay`، `تابي`، `تمارا`، `إنستاباي`) بانتظار تأكيد واتساب؛ اشحن الطلبات المدفوعة فوراً، وطبّق شرط التأكيد على طلبات `COD` فقط!

## 4. Claims Remaining Uncertain & Update Triggers

- **Verification Requirement**: Verify live store/account configuration and current 2026/2027 platform UI settings for Marketing Automation before deploying changes.
- **Verification Requirement**: Confirm current statutory penalty thresholds and licensing rules with qualified local counsel in KSA, UAE, or Egypt.
- **No Guaranteed Outcomes**: Per Agent 2 v1.2 boundaries, this asset defines operational controls and testable measurement hypotheses; it does not promise guaranteed rankings, virality, or fixed ROAS lift.
- **Update Triggers**: Re-verify this framework whenever platform UI/API schemas change, prior to major Hijri/seasonal peaks (Ramadan/White Friday), or within 90 days of `2026-10-25`.
