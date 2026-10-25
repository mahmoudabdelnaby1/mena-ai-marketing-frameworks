# Evidence Register & Source Boundaries — `FW-036` (`AMP-179`)

- **Framework Title (EN)**: Vision 2030, GASTAT, CAPMAS & Central Bank Citation Grounding Workflow (Anti-Hallucination)
- **عنوان الأصل (AR)**: مسار عمل توثيق إحصاءات رؤية 2030 والهيئة العامة للإحصاء (`GASTAT`) والجهاز المركزي (`CAPMAS`) ومنع هلوسة الأرقام
- **Channel**: Content Marketing
- **Last Reviewed Date**: `2026-10-25`
- **Verification Gate Status**: `READY_FOR_REVIEW`

## 1. Problem & Empirical Evidence (What Proves the Failure Mechanism in Egypt & GCC)

| Source ID | Title & Direct Link | Publisher | Published | Accessed | Type & Confidence | What This Source Supports | Support Boundary |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `SRC-061` | [The Arabic SEO in Saudi Arabia Mistakes Costing Riyadh Brands Rankings](https://digistreetmedia.com/blog/the-arabic-seo-in-saudi-arabia-mistakes-costing-riyadh-brands-rankings/) | DigiStreet Media | `2026-09-29` | `2026-10-25` | `PRACTITIONER_GUIDE` (`REPEATED_SIGNAL`) | Identifies 5 recurring KSA SEO failures: treating Arabic as translation, running one strategy across Arabic/English, broken hreflang/RTL mobile UX, ignoring Vision 2030 sector context, and chasing non-local backlinks while treating Riyadh, Jeddah, and Dammam as homogeneous. | Saudi Arabia B2B and B2C SEO. |

## 2. Official Platform Capability, Regulatory & Advice Evidence

| Source ID | Title & Direct Link | Publisher | Published | Accessed | Status / Confidence | Official Capability or Rule Verified | Fallback / Operational Boundary |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `SRC-022` | [Reduce hallucinations - Claude Platform Docs](https://platform.claude.com/docs/en/test-and-evaluate/strengthen-guardrails/reduce-hallucinations) | Anthropic | `2026-08-15` | `2026-10-25` | `OFFICIAL_DOCUMENTATION` (`CONFIRMED_CAPABILITY`) | Instructing the model to allow 'I do not know', extract verbatim quotes first, and restrict claims to supplied documents measurably reduces hallucinated facts. | Critical for MENA regulatory, pricing, and medical/cosmetic marketing claims. |
| `SRC-023` | [Context windows - Claude Platform Docs](https://platform.claude.com/docs/en/build-with-claude/context-windows) | Anthropic | `2026-08-15` | `2026-10-25` | `OFFICIAL_DOCUMENTATION` (`CONFIRMED_CAPABILITY`) | Larger context windows do not guarantee uniform recall; dumping unindexed guidelines and noisy history degrades instruction adherence. | Supports modular context curation over monolithic prompt stuffing. |
| `SRC-022` | [Reduce hallucinations - Claude Platform Docs](https://platform.claude.com/docs/en/test-and-evaluate/strengthen-guardrails/reduce-hallucinations) | Anthropic | `2026-08-15` | `2026-10-25` | `OFFICIAL_CAPABILITY_CHECK` (`supported`) | Explicitly instructing the model to extract verbatim quotes before drafting and permitting 'I don't know / Not in supplied sources' drastically reduces fabricated citations. | Fallback: Strip any numeric claim that cannot be traced to a line in the supplied evidence pack. |

## 3. Counterevidence, Exceptions & When This Pattern Does NOT Apply

- In strictly single-language English B2B niches or fully prepaid digital-product flows, the severity of this Content Marketing mismatch is lower provided manual QA is still performed.
- ** Operational Boundary**: Never allow an LLM to generate a statistic from its internal weights without a verified URL/PDF excerpt attached in the context window. / لا تسمح أبداً للنموذج اللغوي بإيراد أي رقم إحصائي من ذاكرته الداخلية دون وجود النص الأصلي للتقرير أو رابطه الموثق داخل سياق المحادثة.

## 4. Claims Remaining Uncertain & Update Triggers

- **Verification Requirement**: Verify live store/account configuration and current 2026/2027 platform UI settings for Content Marketing before deploying changes.
- **Verification Requirement**: Confirm current statutory penalty thresholds and licensing rules with qualified local counsel in KSA, UAE, or Egypt.
- **No Guaranteed Outcomes**: Per Agent 2 v1.2 boundaries, this asset defines operational controls and testable measurement hypotheses; it does not promise guaranteed rankings, virality, or fixed ROAS lift.
- **Update Triggers**: Re-verify this framework whenever platform UI/API schemas change, prior to major Hijri/seasonal peaks (Ramadan/White Friday), or within 90 days of `2026-10-25`.
