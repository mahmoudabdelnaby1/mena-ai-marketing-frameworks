# Evidence Register & Source Boundaries — `FW-022` (`AMP-070`)

- **Framework Title (EN)**: MENA Healthcare & Pharmaceutical Paid Search Eligibility & Regulatory Routing Aid
- **عنوان الأصل (AR)**: أداة القرار الإعلاني للقطاع الصحي والدوائي في الأسواق العربية (قيود `Google AI Mode` وتصاريح `SFDA / MOH / EDA`)
- **Channel**: Pay-Per-Click (PPC) Advertising
- **Last Reviewed Date**: `2026-10-25`
- **Verification Gate Status**: `READY_FOR_REVIEW`

## 1. Problem & Empirical Evidence (What Proves the Failure Mechanism in Egypt & GCC)

| Source ID | Title & Direct Link | Publisher | Published | Accessed | Type & Confidence | What This Source Supports | Support Boundary |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `SRC-044` | [False Discounts in Arab Markets: What Saudi, UAE and Egyptian Law Say Before White Friday](https://voctos.net/false-discount-advertising-law-arab-markets-white-friday/) | VOCTOS | `2026-10-22` | `2026-10-25` | `LEGAL_ANALYSIS` (`RESEARCH_FINDING`) | Fake reference prices violate law across all 3 markets: KSA fines up to SAR 1,000,000 and requires a Ministry of Commerce discount license + old/new price tag; Egypt Law 181/2018 fines EGP 50,000 to EGP 2,000,000; UAE fines AED 100,000. | Read from primary statutory texts on 22 Oct 2026. |
| `SRC-047` | [Google Ads Channel Priority, Lead Scoring and a February 2027 Display Change: A Checklist for Arab Advertisers](https://voctos.net/google-ads-channel-priority-lead-scoring-arab-advertisers/) | VOCTOS | `2026-10-16` | `2026-10-25` | `PRACTITIONER_GUIDE` (`REPEATED_SIGNAL`) | Documents Google Ads Oct 2026 channel priority changes, offline lead-scoring requirements, and the Feb 2027 removal of current Display spend allocation controls on Search campaigns. | Google Ads campaign management in Arab markets. |

## 2. Official Platform Capability, Regulatory & Advice Evidence

| Source ID | Title & Direct Link | Publisher | Published | Accessed | Status / Confidence | Official Capability or Rule Verified | Fallback / Operational Boundary |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `SRC-047` | [Google Ads Channel Priority, Lead Scoring and a February 2027 Display Change: A Checklist for Arab Advertisers](https://voctos.net/google-ads-channel-priority-lead-scoring-arab-advertisers/) | VOCTOS | `2026-10-16` | `2026-10-25` | `OFFICIAL_CAPABILITY_CHECK` (`plan/region dependent`) | Google restricts pharmaceutical advertising formats by country list and enforces strict automated checks on prescription drug terms globally. | Fallback: Focus clinic campaigns on consultation and general dermatology/dental service terms with visible MOH/DHA/EDA permits. |

## 3. Counterevidence, Exceptions & When This Pattern Does NOT Apply

- In strictly single-language English B2B niches or fully prepaid digital-product flows, the severity of this Pay-Per-Click (PPC) Advertising mismatch is lower provided manual QA is still performed.
- ** Operational Boundary**: Do not launch any medical, pharmaceutical, or clinical procedure ad in KSA, UAE, or Egypt without an active, non-expired Ministry of Health / SFDA / EDA advertising license number displayed in the ad or landing page. / لا تطلق أي إعلان طبي أو دوائي أو تجميلي في السعودية أو الإمارات أو مصر دون رقم ترخيص إعلان صحي ساري المفعول ومكتوب بوضوح في الإعلان وصفحة الهبوط.

## 4. Claims Remaining Uncertain & Update Triggers

- **Verification Requirement**: Verify live store/account configuration and current 2026/2027 platform UI settings for Pay-Per-Click (PPC) Advertising before deploying changes.
- **Verification Requirement**: Confirm current statutory penalty thresholds and licensing rules with qualified local counsel in KSA, UAE, or Egypt.
- **No Guaranteed Outcomes**: Per Agent 2 v1.2 boundaries, this asset defines operational controls and testable measurement hypotheses; it does not promise guaranteed rankings, virality, or fixed ROAS lift.
- **Update Triggers**: Re-verify this framework whenever platform UI/API schemas change, prior to major Hijri/seasonal peaks (Ramadan/White Friday), or within 90 days of `2026-10-25`.
