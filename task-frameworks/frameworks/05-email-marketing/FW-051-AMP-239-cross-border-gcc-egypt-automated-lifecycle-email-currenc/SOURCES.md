# Evidence Register & Source Boundaries — `FW-051` (`AMP-239`)

- **Framework Title (EN)**: Cross-Border GCC & Egypt Automated Lifecycle Email Currency, VAT & BNPL Localization Checklist
- **عنوان الأصل (AR)**: قائمة فحص توطين العملات وضريبة القيمة المضافة (`15% KSA / 5% UAE / 0% Qatar / 14% Egypt`) وخيارات الدفع في الرسائل الآلية
- **Channel**: Email Marketing
- **Last Reviewed Date**: `2026-10-25`
- **Verification Gate Status**: `READY_FOR_REVIEW`

## 1. Problem & Empirical Evidence (What Proves the Failure Mechanism in Egypt & GCC)

| Source ID | Title & Direct Link | Publisher | Published | Accessed | Type & Confidence | What This Source Supports | Support Boundary |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `SRC-044` | [False Discounts in Arab Markets: What Saudi, UAE and Egyptian Law Say Before White Friday](https://voctos.net/false-discount-advertising-law-arab-markets-white-friday/) | VOCTOS | `2026-10-22` | `2026-10-25` | `LEGAL_ANALYSIS` (`RESEARCH_FINDING`) | Fake reference prices violate law across all 3 markets: KSA fines up to SAR 1,000,000 and requires a Ministry of Commerce discount license + old/new price tag; Egypt Law 181/2018 fines EGP 50,000 to EGP 2,000,000; UAE fines AED 100,000. | Read from primary statutory texts on 22 Oct 2026. |
| `SRC-056` | [GCC Marketing Playbook: UAE, Saudi Arabia and Qatar](https://thegrower.ai/gcc-marketing) | Grower AI | `2026-10-12` | `2026-10-25` | `MARKET_BENCHMARK` (`RESEARCH_FINDING`) | Secondary regional reach material; its localization discussion is not treated as a universal quota or wage rule. | Check current activity- and workforce-specific requirements with the official HRSD calculator. |

## 2. Official Platform Capability, Regulatory & Advice Evidence

| Source ID | Title & Direct Link | Publisher | Published | Accessed | Status / Confidence | Official Capability or Rule Verified | Fallback / Operational Boundary |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `SRC-044` | [False Discounts in Arab Markets: What Saudi, UAE and Egyptian Law Say Before White Friday](https://voctos.net/false-discount-advertising-law-arab-markets-white-friday/) | VOCTOS | `2026-10-22` | `2026-10-25` | `OFFICIAL_CAPABILITY_CHECK` (`supported`) | Checkout and cart events carry both `shop_currency` (base) and `presentment_currency` (customer-facing); templates must explicitly reference `presentment` fields. | Fallback: If `Browse Viewed Product` events only pass base currency, use a Liquid lookup table keyed by `person.country_code`. |

## 3. Counterevidence, Exceptions & When This Pattern Does NOT Apply

- In strictly single-language English B2B niches or fully prepaid digital-product flows, the severity of this Email Marketing mismatch is lower provided manual QA is still performed.
- ** Operational Boundary**: Never display consumer product prices in Saudi Arabia or UAE as 'Tax-Exclusive' (`السعر غير شامل الضريبة`) in marketing emails only to add 15% or 5% VAT as a surprise at checkout. / يُحظر عرض أسعار المستهلكين في رسائل البريد بالسعودية أو الإمارات «بدون ضريبة» ثم مفاجأة العميل بإضافة 15% أو 5% عند الدفع؛ فالأسعار المعلنة للمستهلك يجب أن تكون شاملة للضريبة.

## 4. Claims Remaining Uncertain & Update Triggers

- **Verification Requirement**: Verify live store/account configuration and current 2026/2027 platform UI settings for Email Marketing before deploying changes.
- **Verification Requirement**: Confirm current statutory penalty thresholds and licensing rules with qualified local counsel in KSA, UAE, or Egypt.
- **No Guaranteed Outcomes**: Per Agent 2 v1.2 boundaries, this asset defines operational controls and testable measurement hypotheses; it does not promise guaranteed rankings, virality, or fixed ROAS lift.
- **Update Triggers**: Re-verify this framework whenever platform UI/API schemas change, prior to major Hijri/seasonal peaks (Ramadan/White Friday), or within 90 days of `2026-10-25`.
