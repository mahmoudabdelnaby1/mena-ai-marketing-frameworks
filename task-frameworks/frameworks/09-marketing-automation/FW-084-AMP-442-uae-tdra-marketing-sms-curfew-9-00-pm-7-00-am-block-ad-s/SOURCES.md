# Evidence Register & Source Boundaries — `FW-084` (`AMP-442`)

- **Framework Title (EN)**: UAE TDRA Marketing SMS Curfew (`9:00 PM – 7:00 AM` Block), `AD-` Sender Prefix & Opt-Out Compliance Checklist
- **عنوان الأصل (AR)**: قائمة فحص الامتثال للوائح هيئة تنظيم الاتصالات الإماراتية (`TDRA` — حظر الرسائل الترويجية من `9 مساءً حتى 7 صباحاً` وبادئة `AD-`)
- **Channel**: Marketing Automation
- **Last Reviewed Date**: `2026-10-25`
- **Verification Gate Status**: `READY_FOR_REVIEW`

## 1. Problem & Empirical Evidence (What Proves the Failure Mechanism in Egypt & GCC)

| Source ID | Title & Direct Link | Publisher | Published | Accessed | Type & Confidence | What This Source Supports | Support Boundary |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `SRC-034` | [Data protection laws | The Official Portal of the UAE Government](https://u.ae/en/about-the-uae/digital-uae/data/data-protection-laws) | UAE Government Portal | `2025-12-04` | `2026-10-25` | `REGULATORY_POLICY` (`CONFIRMED_CAPABILITY`) | UAE Federal Decree-Law No. 45 of 2021 (PDPL) prohibits personal data processing without owner consent and grants the right to object to direct marketing. | Mainland UAE; DIFC and ADGM operate parallel frameworks. |
| `SRC-049` | [UAE PDPL Marketing Rules for Email and SMS | Kaelo Global](https://kaeloglobal.com/digital-marketing/uae-data-protection-marketing/) | Kaelo Global | `2026-10-22` | `2026-10-25` | `LEGAL_ANALYSIS` (`RESEARCH_FINDING`) | UAE PDPL (Decree-Law 45/2021 Art. 4 & 17) has no general legitimate-interest exception for direct marketing; TDRA Spam Policy v1.1 mandates opt-in, 'AD-' sender prefix, free opt-out, a strict 9:00 PM to 7:00 AM curfew on marketing SMS, and 2-year consent record retention. | UAE Mainland, TDRA telecom rules, DIFC, and ADGM. |

## 2. Official Platform Capability, Regulatory & Advice Evidence

| Source ID | Title & Direct Link | Publisher | Published | Accessed | Status / Confidence | Official Capability or Rule Verified | Fallback / Operational Boundary |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `SRC-049` | [UAE PDPL Marketing Rules for Email and SMS | Kaelo Global](https://kaeloglobal.com/digital-marketing/uae-data-protection-marketing/) | Kaelo Global | `2026-10-22` | `2026-10-25` | `OFFICIAL_CAPABILITY_CHECK` (`supported`) | Kaelo Global Oct 2026 review confirms TDRA's 9:00 PM – 7:00 AM marketing SMS curfew (s. 8.8), `AD-` prefix mandate, prior consent requirement (s. 8.3), and ban on re-prompting unsubscribed users (s. 9.2.5). | Fallback: Enforce `get_tdra_safe_send_timestamp()` at the SMS gateway wrapper level so no upstream tool can accidentally fire a promotional SMS to `+971` during curfew hours. |

## 3. Counterevidence, Exceptions & When This Pattern Does NOT Apply

- In strictly single-language English B2B niches or fully prepaid digital-product flows, the severity of this Marketing Automation mismatch is lower provided manual QA is still performed.
- ** Operational Boundary**: Never allow an automated `'Wait 1 Hour -> Send Abandoned Cart SMS'` workflow to fire at `10:15 PM` Dubai time when a shopper abandons their cart at `9:15 PM`—queue it until `7:15 AM` (or `9:00 AM`) the next morning! / لا تسمح أبداً لتدفق آلي («انتظر ساعة واحدة ثم أرسل SMS للسلة المتروكة») بالإرسال في الساعة `10:15 مساءً` بتوقيت دبي؛ بل اضبط النظام لتأجيل الإرسال تلقائياً إلى الصباح التالي بعد الساعة `7:00 صباحاً`!

## 4. Claims Remaining Uncertain & Update Triggers

- **Verification Requirement**: Verify live store/account configuration and current 2026/2027 platform UI settings for Marketing Automation before deploying changes.
- **Verification Requirement**: Confirm current statutory penalty thresholds and licensing rules with qualified local counsel in KSA, UAE, or Egypt.
- **No Guaranteed Outcomes**: Per Agent 2 v1.2 boundaries, this asset defines operational controls and testable measurement hypotheses; it does not promise guaranteed rankings, virality, or fixed ROAS lift.
- **Update Triggers**: Re-verify this framework whenever platform UI/API schemas change, prior to major Hijri/seasonal peaks (Ramadan/White Friday), or within 90 days of `2026-10-25`.
