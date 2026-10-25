# Evidence Register & Source Boundaries — `FW-049` (`AMP-237`)

- **Framework Title (EN)**: Transactional vs. Promotional Email Template Separation Checklist (Saudi & UAE PDPL Compliance)
- **عنوان الأصل (AR)**: قائمة فحص الفصل بين رسائل المعاملات (`الفواتير وتأكيد الطلب`) والرسائل الترويجية (الامتثال لنظام `PDPL` السعودي والإماراتي)
- **Channel**: Email Marketing
- **Last Reviewed Date**: `2026-10-25`
- **Verification Gate Status**: `READY_FOR_REVIEW`

## 1. Problem & Empirical Evidence (What Proves the Failure Mechanism in Egypt & GCC)

| Source ID | Title & Direct Link | Publisher | Published | Accessed | Type & Confidence | What This Source Supports | Support Boundary |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `SRC-048` | [Saudi PDPL for Marketers: Email, SMS and WhatsApp Rules](https://voctos.net/saudi-pdpl-marketing-compliance/) | VOCTOS | `2026-10-01` | `2026-10-25` | `LEGAL_ANALYSIS` (`RESEARCH_FINDING`) | Saudi PDPL enforcement requires granular per-channel opt-in logs, clear sender identity, and immediate cessation upon withdrawal of consent across email, SMS, and WhatsApp. | Saudi Arabia PDPL compliance. |
| `SRC-049` | [UAE PDPL Marketing Rules for Email and SMS | Kaelo Global](https://kaeloglobal.com/digital-marketing/uae-data-protection-marketing/) | Kaelo Global | `2026-10-22` | `2026-10-25` | `LEGAL_ANALYSIS` (`RESEARCH_FINDING`) | UAE PDPL (Decree-Law 45/2021 Art. 4 & 17) has no general legitimate-interest exception for direct marketing; TDRA Spam Policy v1.1 mandates opt-in, 'AD-' sender prefix, free opt-out, a strict 9:00 PM to 7:00 AM curfew on marketing SMS, and 2-year consent record retention. | UAE Mainland, TDRA telecom rules, DIFC, and ADGM. |

## 2. Official Platform Capability, Regulatory & Advice Evidence

| Source ID | Title & Direct Link | Publisher | Published | Accessed | Status / Confidence | Official Capability or Rule Verified | Fallback / Operational Boundary |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `SRC-048` | [Saudi PDPL for Marketers: Email, SMS and WhatsApp Rules](https://voctos.net/saudi-pdpl-marketing-compliance/) | VOCTOS | `2026-10-01` | `2026-10-25` | `OFFICIAL_CAPABILITY_CHECK` (`supported`) | Contract fulfillment allows sending order receipts and shipping notices without separate marketing consent ONLY if the communication remains strictly operational and non-promotional. | Fallback: Send cross-sell offers in a separate marketing email filtered exclusively to `marketing_consent == true`. |

## 3. Counterevidence, Exceptions & When This Pattern Does NOT Apply

- In strictly single-language English B2B niches or fully prepaid digital-product flows, the severity of this Email Marketing mismatch is lower provided manual QA is still performed.
- ** Operational Boundary**: Do not send a single template to all buyers if it contains cross-sell discounts; either strip promotional blocks from transactional receipts OR conditionally render them ONLY when `customer.marketing_consent == true`. / لا ترسل قالباً موحداً يحتوي على عروض بيع متقاطع (`Cross-sell`) لجميع المشترين؛ إما أن تجعل رسالة الفاتورة خدمية خالصة بنسبة 100% أو تقصر ظهور العرض الإضافي بشرط برمجي (`if marketing_consent == true`).

## 4. Claims Remaining Uncertain & Update Triggers

- **Verification Requirement**: Verify live store/account configuration and current 2026/2027 platform UI settings for Email Marketing before deploying changes.
- **Verification Requirement**: Confirm current statutory penalty thresholds and licensing rules with qualified local counsel in KSA, UAE, or Egypt.
- **No Guaranteed Outcomes**: Per Agent 2 v1.2 boundaries, this asset defines operational controls and testable measurement hypotheses; it does not promise guaranteed rankings, virality, or fixed ROAS lift.
- **Update Triggers**: Re-verify this framework whenever platform UI/API schemas change, prior to major Hijri/seasonal peaks (Ramadan/White Friday), or within 90 days of `2026-10-25`.
