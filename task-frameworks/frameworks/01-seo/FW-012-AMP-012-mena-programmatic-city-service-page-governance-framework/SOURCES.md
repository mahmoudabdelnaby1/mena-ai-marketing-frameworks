# Evidence Register & Source Boundaries — `FW-012` (`AMP-012`)

- **Framework Title (EN)**: MENA Programmatic City/Service Page Governance Framework (Anti-Scaled Content Abuse)
- **عنوان الأصل (AR)**: الإطار التشغيلي لحوكمة صفحات المدن والخدمات المولدة برمجياً (تجنب عقوبة `Scaled Content Abuse` في جوجل)
- **Channel**: Search Engine Optimization (SEO)
- **Last Reviewed Date**: `2026-10-25`
- **Verification Gate Status**: `READY_FOR_REVIEW`

## 1. Problem & Empirical Evidence (What Proves the Failure Mechanism in Egypt & GCC)

| Source ID | Title & Direct Link | Publisher | Published | Accessed | Type & Confidence | What This Source Supports | Support Boundary |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `SRC-061` | [The Arabic SEO in Saudi Arabia Mistakes Costing Riyadh Brands Rankings](https://digistreetmedia.com/blog/the-arabic-seo-in-saudi-arabia-mistakes-costing-riyadh-brands-rankings/) | DigiStreet Media | `2026-09-29` | `2026-10-25` | `PRACTITIONER_GUIDE` (`REPEATED_SIGNAL`) | Identifies 5 recurring KSA SEO failures: treating Arabic as translation, running one strategy across Arabic/English, broken hreflang/RTL mobile UX, ignoring Vision 2030 sector context, and chasing non-local backlinks while treating Riyadh, Jeddah, and Dammam as homogeneous. | Saudi Arabia B2B and B2C SEO. |

## 2. Official Platform Capability, Regulatory & Advice Evidence

| Source ID | Title & Direct Link | Publisher | Published | Accessed | Status / Confidence | Official Capability or Rule Verified | Fallback / Operational Boundary |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `SRC-001` | [Google Search's Guidance on Generative AI Content on Your Website](https://developers.google.com/search/docs/fundamentals/using-gen-ai-content) | Google Search Central | `2026-10-01` | `2026-10-25` | `OFFICIAL_DOCUMENTATION` (`CONFIRMED_CAPABILITY`) | Google evaluates content quality/helpfulness regardless of AI vs human authorship; using AI to generate many pages without added value violates Scaled Content Abuse. | Does not ban AI content per se; penalizes unoriginal/manipulative scale. |
| `SRC-002` | [Spam Policies for Google Web Search | Documentation](https://developers.google.com/search/docs/essentials/spam-policies) | Google Search Central | `2026-08-28` | `2026-10-25` | `OFFICIAL_DOCUMENTATION` (`CONFIRMED_CAPABILITY`) | Defines Scaled Content Abuse as generating many pages primarily to manipulate rankings or generative AI responses rather than helping users. | Applies to Google Web Search, AI Overviews, and AI Mode. |
| `SRC-001` | [Google Search's Guidance on Generative AI Content on Your Website](https://developers.google.com/search/docs/fundamentals/using-gen-ai-content) | Google Search Central | `2026-10-01` | `2026-10-25` | `OFFICIAL_CAPABILITY_CHECK` (`supported`) | Google's official policy is method-agnostic: it does not penalize AI assistance per se (`AMP-556`), but strictly penalizes generating many pages without original value or distinct user utility. | Fallback: Never create a standalone URL unless at least 3 first-party city-specific data points exist. |

## 3. Counterevidence, Exceptions & When This Pattern Does NOT Apply

- In strictly single-language English B2B niches or fully prepaid digital-product flows, the severity of this Search Engine Optimization (SEO) mismatch is lower provided manual QA is still performed.
- ** Operational Boundary**: Do not generate a standalone city URL if your business has zero distinct operational data (no specific delivery SLA, shipping cost, physical branch, local portfolio, or regulatory license) for that city. / لا تقم بإنشاء صفحة مستقلة لمدينة ليس لديك فيها أي بيانات تشغيلية حقيقية مميزة (مثل مدة التوصيل، تكلفة الشحن، فرع فعلي، أو مشاريع منفذة في تلك المدينة).

## 4. Claims Remaining Uncertain & Update Triggers

- **Verification Requirement**: Verify live store/account configuration and current 2026/2027 platform UI settings for Search Engine Optimization (SEO) before deploying changes.
- **Verification Requirement**: Confirm current statutory penalty thresholds and licensing rules with qualified local counsel in KSA, UAE, or Egypt.
- **No Guaranteed Outcomes**: Per Agent 2 v1.2 boundaries, this asset defines operational controls and testable measurement hypotheses; it does not promise guaranteed rankings, virality, or fixed ROAS lift.
- **Update Triggers**: Re-verify this framework whenever platform UI/API schemas change, prior to major Hijri/seasonal peaks (Ramadan/White Friday), or within 90 days of `2026-10-25`.
