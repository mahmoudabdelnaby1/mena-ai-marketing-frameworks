# Evidence Register & Source Boundaries — `FW-001` (`AMP-001`)

- **Framework Title (EN)**: MENA Native Search Root & Dialect Keyword Matrix Prompt
- **عنوان الأصل (AR)**: قالب هندسة الكلمات المفتاحية العربية حسب الجذر اللغوي واللهجة المحلية (مصر والخليج)
- **Channel**: Search Engine Optimization (SEO)
- **Last Reviewed Date**: `2026-10-25`
- **Verification Gate Status**: `READY_FOR_REVIEW`

## 1. Problem & Empirical Evidence (What Proves the Failure Mechanism in Egypt & GCC)

| Source ID | Title & Direct Link | Publisher | Published | Accessed | Type & Confidence | What This Source Supports | Support Boundary |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `SRC-053` | [Why Direct Translation Fails in MENA SEO](https://23hublab.com/why-direct-translation-fails-in-mena-seo/) | 23HubLab | `2026-04-01` | `2026-10-25` | `PRACTITIONER_GUIDE` (`REPEATED_SIGNAL`) | AI/machine translations of English keyword lists fail in MENA because native searchers use distinct Arabic lexical roots and phrasing, leading to high bounce rates and poor dwell time. | Arabic SEO across MENA. |
| `SRC-060` | [Arabic Keyword Research for Online Stores: A Practical Guide](https://esafqa.com/en/blog/arabic-keyword-research-guide/) | Esafqa | `2026-10-08` | `2026-10-25` | `PRACTITIONER_GUIDE` (`REPEATED_SIGNAL`) | Demonstrates how a single product concept splits across MSA vs dialect, spelling variants, and lexical differences between Saudi Arabia, UAE, and Egypt. | Arabic e-commerce keyword research. |
| `SRC-061` | [The Arabic SEO in Saudi Arabia Mistakes Costing Riyadh Brands Rankings](https://digistreetmedia.com/blog/the-arabic-seo-in-saudi-arabia-mistakes-costing-riyadh-brands-rankings/) | DigiStreet Media | `2026-09-29` | `2026-10-25` | `PRACTITIONER_GUIDE` (`REPEATED_SIGNAL`) | Identifies 5 recurring KSA SEO failures: treating Arabic as translation, running one strategy across Arabic/English, broken hreflang/RTL mobile UX, ignoring Vision 2030 sector context, and chasing non-local backlinks while treating Riyadh, Jeddah, and Dammam as homogeneous. | Saudi Arabia B2B and B2C SEO. |

## 2. Official Platform Capability, Regulatory & Advice Evidence

| Source ID | Title & Direct Link | Publisher | Published | Accessed | Status / Confidence | Official Capability or Rule Verified | Fallback / Operational Boundary |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `SRC-021` | [Prompting best practices - Claude Platform Docs](https://platform.claude.com/docs/en/build-with-claude/prompt-engineering/claude-prompting-best-practices) | Anthropic | `2026-08-15` | `2026-10-25` | `OFFICIAL_CAPABILITY_CHECK` (`supported`) | Both models support Arabic root decomposition and XML-structured constraints (`<lexical_rules>`), but neither has real-time search volume data built into weights. | Fallback: Pair the prompt output with a CSV export from Google Keyword Planner / GSC or manual Google Autocomplete check in incognito (`gl=sa&hl=ar` or `gl=eg&hl=ar`). |

## 3. Counterevidence, Exceptions & When This Pattern Does NOT Apply

- In strictly single-language English B2B niches or fully prepaid digital-product flows, the severity of this Search Engine Optimization (SEO) mismatch is lower provided manual QA is still performed.
- ** Operational Boundary**: Do not use for strictly English-only technical API documentation or developer-only SaaS products where 95%+ of local queries occur in English. / لا يُستخدم لصفحات توثيق البرمجيات (APIs) الموجهة للمطورين فقط حيث يتم البحث محلياً باللغة الإنجليزية بنسبة تفوق 95%.

## 4. Claims Remaining Uncertain & Update Triggers

- **Verification Requirement**: Verify live store/account configuration and current 2026/2027 platform UI settings for Search Engine Optimization (SEO) before deploying changes.
- **Verification Requirement**: Confirm current statutory penalty thresholds and licensing rules with qualified local counsel in KSA, UAE, or Egypt.
- **No Guaranteed Outcomes**: Per Agent 2 v1.2 boundaries, this asset defines operational controls and testable measurement hypotheses; it does not promise guaranteed rankings, virality, or fixed ROAS lift.
- **Update Triggers**: Re-verify this framework whenever platform UI/API schemas change, prior to major Hijri/seasonal peaks (Ramadan/White Friday), or within 90 days of `2026-10-25`.
