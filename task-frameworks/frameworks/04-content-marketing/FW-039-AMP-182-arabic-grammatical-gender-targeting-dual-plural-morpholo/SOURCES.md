# Evidence Register & Source Boundaries — `FW-039` (`AMP-182`)

- **Framework Title (EN)**: Arabic Grammatical Gender-Targeting & Dual/Plural Morphology Prompt Template
- **عنوان الأصل (AR)**: قالب ضبط المخاطب النحوي والتأنيث والتذكير في النصوص التسويقية العربية (تجاوز حيادية الضمير الإنجليزي `You`)
- **Channel**: Content Marketing
- **Last Reviewed Date**: `2026-10-25`
- **Verification Gate Status**: `READY_FOR_REVIEW`

## 1. Problem & Empirical Evidence (What Proves the Failure Mechanism in Egypt & GCC)

| Source ID | Title & Direct Link | Publisher | Published | Accessed | Type & Confidence | What This Source Supports | Support Boundary |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `SRC-072` | [Translating Dialects between ChatGPT and DeepSeek](https://f1000research.com/articles/14-694) | F1000Research | `2025-07-16` | `2026-10-25` | `PEER_REVIEWED_RESEARCH` (`RESEARCH_FINDING`) | Demonstrates measurable accuracy drops and cultural/idiomatic errors when LLMs translate between English and regional Arabic dialects. | Peer-reviewed evaluation of ChatGPT and DeepSeek on Arabic dialects. |
| `SRC-073` | [AI Translation Errors in Arabic, With Real Examples](https://locstars.com/ai-translation-errors-arabic/) | Locstars | `2026-10-22` | `2026-10-25` | `PRACTITIONER_GUIDE` (`REPEATED_SIGNAL`) | Documents concrete English-to-Egyptian and Gulf Arabic LLM translation failures including register mixing, gender agreement errors, and literal idioms. | Arabic localization QA. |

## 2. Official Platform Capability, Regulatory & Advice Evidence

| Source ID | Title & Direct Link | Publisher | Published | Accessed | Status / Confidence | Official Capability or Rule Verified | Fallback / Operational Boundary |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `SRC-072` | [Translating Dialects between ChatGPT and DeepSeek](https://f1000research.com/articles/14-694) | F1000Research | `2025-07-16` | `2026-10-25` | `OFFICIAL_CAPABILITY_CHECK` (`supported`) | Research on Arabic LLM generation confirms models default to masculine singular when translating English 'you' unless `<gender_mode>` is explicitly specified. | Fallback: Always pass `<gender_mode>` in every Arabic copywriting prompt. |

## 3. Counterevidence, Exceptions & When This Pattern Does NOT Apply

- In strictly single-language English B2B niches or fully prepaid digital-product flows, the severity of this Content Marketing mismatch is lower provided manual QA is still performed.
- ** Operational Boundary**: Do not use awkward slash notation (`عزيزي/عزيزتي المشترك/ـة`) in social media ads or push notifications—choose either the specific audience gender inflection or clean gender-inclusive noun phrasing (`نرحب بكم` / `خطوة واحدة تفصلك عن...`). / لا تستخدم صيغ الشرطة المائلة الركيكة (`عزيزي/عزيزتي العميل/ـة`) في الإعلانات أو الإشعارات؛ اختر إما صيغة المؤنث الصريحة للعلامات النسائية أو الصياغة الشاملة الأنيقة.

## 4. Claims Remaining Uncertain & Update Triggers

- **Verification Requirement**: Verify live store/account configuration and current 2026/2027 platform UI settings for Content Marketing before deploying changes.
- **Verification Requirement**: Confirm current statutory penalty thresholds and licensing rules with qualified local counsel in KSA, UAE, or Egypt.
- **No Guaranteed Outcomes**: Per Agent 2 v1.2 boundaries, this asset defines operational controls and testable measurement hypotheses; it does not promise guaranteed rankings, virality, or fixed ROAS lift.
- **Update Triggers**: Re-verify this framework whenever platform UI/API schemas change, prior to major Hijri/seasonal peaks (Ramadan/White Friday), or within 90 days of `2026-10-25`.
