# Evidence Register & Source Boundaries — `FW-047` (`AMP-235`)

- **Framework Title (EN)**: MENA Payment-Rail Specific Abandoned Checkout Recovery Workflow (COD vs. Tabby/Tamara BNPL vs. Fawry/InstaPay)
- **عنوان الأصل (AR)**: مسار عمل استرداد السلات المتروكة المخصص حسب وسيلة الدفع في مصر والخليج (`COD` مقابل `Tabby/Tamara` مقابل كود `فوري/إنستاباي`)
- **Channel**: Email Marketing
- **Last Reviewed Date**: `2026-10-25`
- **Verification Gate Status**: `READY_FOR_REVIEW`

## 1. Problem & Empirical Evidence (What Proves the Failure Mechanism in Egypt & GCC)

| Source ID | Title & Direct Link | Publisher | Published | Accessed | Type & Confidence | What This Source Supports | Support Boundary |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `SRC-081` | [Conversion Rate Optimization for UAE E-Commerce (2026)](https://soluvide.com/blog/conversion-rate-optimization-uae-ecommerce-2026) | Soluvide | `2026-02-19` | `2026-10-25` | `PRACTITIONER_GUIDE` (`REPEATED_SIGNAL`) | Shows how Cash on Delivery (COD) and Buy Now Pay Later (Tabby and Tamara) reduce checkout friction and lift AOV in UAE/GCC e-commerce. | UAE and GCC e-commerce CRO. |
| `SRC-083` | [Payment Gateway Egypt: Fees, Comparison & Best Providers (2026)](https://digitology.co/payment-gateway-egypt/) | Digitology Egypt | `2026-08-07` | `2026-10-25` | `MARKET_BENCHMARK` (`RESEARCH_FINDING`) | Secondary payment-provider article; not treated as representative national payment-share evidence. | Use current merchant order and session records to assess payment mix and checkout decisions. |
| `SRC-084` | [Payment Gateways in Egypt 2026: Paymob, Fawry, InstaPay](https://nilexdigitalsystems.com/articles/payment-gateways-egypt-paymob-fawry-instapay) | Nilex Digital Systems | `2026-09-26` | `2026-10-25` | `PRACTITIONER_GUIDE` (`REPEATED_SIGNAL`) | Details checkout UX, reconciliation, and conversion fixes for Paymob, Fawry reference codes, Meeza, InstaPay, and valU in Egypt. | Egyptian online store checkout architecture. |

## 2. Official Platform Capability, Regulatory & Advice Evidence

| Source ID | Title & Direct Link | Publisher | Published | Accessed | Status / Confidence | Official Capability or Rule Verified | Fallback / Operational Boundary |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `SRC-084` | [Payment Gateways in Egypt 2026: Paymob, Fawry, InstaPay](https://nilexdigitalsystems.com/articles/payment-gateways-egypt-paymob-fawry-instapay) | Nilex Digital Systems | `2026-09-26` | `2026-10-25` | `OFFICIAL_CAPABILITY_CHECK` (`supported`) | Egyptian and Gulf payment gateways emit `pending` webhook events containing the OTC reference number (`bill_reference`) and selected payment rail (`fawry`, `valu`, `tabby`, `tamara`). | Fallback: Pass `selected_payment_method` and `fawry_reference_code` as custom event properties in the `Started Checkout` / `Placed Pending Order` event. |

## 3. Counterevidence, Exceptions & When This Pattern Does NOT Apply

- In strictly single-language English B2B niches or fully prepaid digital-product flows, the severity of this Email Marketing mismatch is lower provided manual QA is still performed.
- ** Operational Boundary**: Do not send an 'Abandoned Cart 10% Discount Code' to a customer who already generated a Pending Fawry Reference Code or Pending Bank/InstaPay Transfer—that cannibalizes margin on an already-committed order! / لا ترسل «كود خصم 10% للسلة المتروكة» لعميل قام بالفعل بإصدار كود دفع «فوري» معلق أو تحويل «إنستاباي»؛ لأن ذلك يهدر هامش الربح لطلب تم تأكيده بالفعل وينتظر السداد النقدي.

## 4. Claims Remaining Uncertain & Update Triggers

- **Verification Requirement**: Verify live store/account configuration and current 2026/2027 platform UI settings for Email Marketing before deploying changes.
- **Verification Requirement**: Confirm current statutory penalty thresholds and licensing rules with qualified local counsel in KSA, UAE, or Egypt.
- **No Guaranteed Outcomes**: Per Agent 2 v1.2 boundaries, this asset defines operational controls and testable measurement hypotheses; it does not promise guaranteed rankings, virality, or fixed ROAS lift.
- **Update Triggers**: Re-verify this framework whenever platform UI/API schemas change, prior to major Hijri/seasonal peaks (Ramadan/White Friday), or within 90 days of `2026-10-25`.
