# Evidence Register & Source Boundaries — `FW-075` (`AMP-388`)

- **Framework Title (EN)**: Checkout Phone, OTP & Quantity Arabic-Indic Numeral (`٠١٢٣٤٥٦٧٨٩`) Auto-Conversion Checklist
- **عنوان الأصل (AR)**: قائمة فحص وكود التحويل التلقائي للأرقام العربية-الهندية (`٠١٢٣٤٥٦٧٨٩`) في حقول الهاتف ورموز التحقق (`OTP`) بصفحة الدفع
- **Channel**: CRO - Conversion Rate Optimization
- **Last Reviewed Date**: `2026-10-25`
- **Verification Gate Status**: `READY_FOR_REVIEW`

## 1. Problem & Empirical Evidence (What Proves the Failure Mechanism in Egypt & GCC)

| Source ID | Title & Direct Link | Publisher | Published | Accessed | Type & Confidence | What This Source Supports | Support Boundary |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `SRC-041` | [Arabic Site Search Normalization: 20 Arab Online Stores Tested](https://voctos.net/arabic-site-search-normalization/) | VOCTOS | `2026-10-08` | `2026-10-25` | `EMPIRICAL_AUDIT` (`RESEARCH_FINDING`) | Internal site search on Salla and Zid stores fails when shoppers use variant Arabic spellings (Hamza أ/ا, Taa Marbuta ة/ه, Alef Maqsura ى/ي) or Arabic-Indic digits (٠-٩ vs 0-9) that differ from catalog product titles. | 20 Arab e-commerce storefronts tested in Oct 2026. |
| `SRC-061` | [The Arabic SEO in Saudi Arabia Mistakes Costing Riyadh Brands Rankings](https://digistreetmedia.com/blog/the-arabic-seo-in-saudi-arabia-mistakes-costing-riyadh-brands-rankings/) | DigiStreet Media | `2026-09-29` | `2026-10-25` | `PRACTITIONER_GUIDE` (`REPEATED_SIGNAL`) | Identifies 5 recurring KSA SEO failures: treating Arabic as translation, running one strategy across Arabic/English, broken hreflang/RTL mobile UX, ignoring Vision 2030 sector context, and chasing non-local backlinks while treating Riyadh, Jeddah, and Dammam as homogeneous. | Saudi Arabia B2B and B2C SEO. |

## 2. Official Platform Capability, Regulatory & Advice Evidence

| Source ID | Title & Direct Link | Publisher | Published | Accessed | Status / Confidence | Official Capability or Rule Verified | Fallback / Operational Boundary |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `SRC-041` | [Arabic Site Search Normalization: 20 Arab Online Stores Tested](https://voctos.net/arabic-site-search-normalization/) | VOCTOS | `2026-10-08` | `2026-10-25` | `OFFICIAL_CAPABILITY_CHECK` (`supported`) | Arabic mobile keyboards emit `٠–٩` and iOS clipboard operations around phone numbers inject invisible directional formatting characters (`‪`, `‬`, `‎`). | Fallback: Strip `[‎‏‪-‮⁦-⁩]` and map `[٠-٩]` -> `[0-9]` on every numeric input. |

## 3. Counterevidence, Exceptions & When This Pattern Does NOT Apply

- In strictly single-language English B2B niches or fully prepaid digital-product flows, the severity of this CRO - Conversion Rate Optimization mismatch is lower provided manual QA is still performed.
- ** Operational Boundary**: Never display an error message saying `'Please enter English numbers only'`—convert the digits silently in the background on `input` so the user never sees an error! / لا تُظهر للمستخدم رسالة خطأ تطالبه «بإدخال الأرقام باللغة الإنجليزية فقط»؛ بل قم بتحويل الأرقام برمجياً في الخلفية أثناء الكتابة دون إزعاجه بأي خطأ!

## 4. Claims Remaining Uncertain & Update Triggers

- **Verification Requirement**: Verify live store/account configuration and current 2026/2027 platform UI settings for CRO - Conversion Rate Optimization before deploying changes.
- **Verification Requirement**: Confirm current statutory penalty thresholds and licensing rules with qualified local counsel in KSA, UAE, or Egypt.
- **No Guaranteed Outcomes**: Per Agent 2 v1.2 boundaries, this asset defines operational controls and testable measurement hypotheses; it does not promise guaranteed rankings, virality, or fixed ROAS lift.
- **Update Triggers**: Re-verify this framework whenever platform UI/API schemas change, prior to major Hijri/seasonal peaks (Ramadan/White Friday), or within 90 days of `2026-10-25`.
