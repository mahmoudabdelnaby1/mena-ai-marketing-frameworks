# Evidence Register & Source Boundaries — `FW-068` (`AMP-336`)

- **Framework Title (EN)**: MENA Cultural Visual Guardrail & Authentic Gulf/Egyptian Wardrobe, Architecture & Etiquette Prompt Pack (Extending `video-prompt-architect`)
- **عنوان الأصل (AR)**: حزمة الضوابط البصرية والثقافية لمشاهد الفيديو بالذكاء الاصطناعي (ضبط الزي السعودي والخليجي، العمارة، وآداب الضيافة — امتداد `video-prompt-architect`)
- **Channel**: Video Advertising
- **Last Reviewed Date**: `2026-10-25`
- **Verification Gate Status**: `READY_FOR_REVIEW`

## 1. Problem & Empirical Evidence (What Proves the Failure Mechanism in Egypt & GCC)

| Source ID | Title & Direct Link | Publisher | Published | Accessed | Type & Confidence | What This Source Supports | Support Boundary |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `SRC-030` | [Laws and Executive Regulations - General Authority for Media Regulation](https://gmedia.gov.sa/en/executive-regulations) | Saudi General Authority of Media Regulation (GAMR) | `2026-09-14` | `2026-10-25` | `REGULATORY_POLICY` (`CONFIRMED_CAPABILITY`) | Sets media content controls, cultural/religious compliance, and advertising disclosure requirements in Saudi Arabia. | KSA jurisdiction. |
| `SRC-056` | [GCC Marketing Playbook: UAE, Saudi Arabia and Qatar](https://thegrower.ai/gcc-marketing) | Grower AI | `2026-10-12` | `2026-10-25` | `MARKET_BENCHMARK` (`RESEARCH_FINDING`) | Secondary regional reach material; its localization discussion is not treated as a universal quota or wage rule. | Check current activity- and workforce-specific requirements with the official HRSD calculator. |

## 2. Official Platform Capability, Regulatory & Advice Evidence

| Source ID | Title & Direct Link | Publisher | Published | Accessed | Status / Confidence | Official Capability or Rule Verified | Fallback / Operational Boundary |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `SRC-013` | [Snap Advertising Policies - Snap Inc.](https://www.snap.com/ad-policies) | Snap Inc. | `2026-06-01` | `2026-10-25` | `OFFICIAL_DOCUMENTATION` (`CONFIRMED_CAPABILITY`) | Enforces country-specific creative, cultural sensitivity, financial, and health/cosmetic claim rules across Saudi Arabia, UAE, and Egypt. | Covers both ad creative and landing page content. |
| `SRC-030` | [Laws and Executive Regulations - General Authority for Media Regulation](https://gmedia.gov.sa/en/executive-regulations) | Saudi General Authority of Media Regulation (GAMR) | `2026-09-14` | `2026-10-25` | `OFFICIAL_CAPABILITY_CHECK` (`supported`) | Text-only prompts in global diffusion models frequently blend regional clothing details; pairing the English Visual Anatomy Tokens with 1–2 real reference images (`Ingredients / Elements`) locks authentic Gulf/Egyptian wardrobe geometry. | Fallback: Always attach a verified reference image of the exact regional wardrobe (`thobe/shimagh` or `kandura/gutra`) when generating close-up human shots. |

## 3. Counterevidence, Exceptions & When This Pattern Does NOT Apply

- In strictly single-language English B2B niches or fully prepaid digital-product flows, the severity of this Video Advertising mismatch is lower provided manual QA is still performed.
- ** Operational Boundary**: Never use vague prompt tokens like `'Middle Eastern man in traditional clothes'` or `'Arabian palace'`—they trigger Orientalist/Aladdin tropes, turbans, or South Asian kurtas. / لا تستخدم أبداً أوصافاً إنجليزية مبهمة مثل `Middle Eastern man in traditional clothes` أو `Arabian room`؛ لأنها تستدعي صور علاء الدين أو العمامة أو الأزياء الآسيوية.

## 4. Claims Remaining Uncertain & Update Triggers

- **Verification Requirement**: Verify live store/account configuration and current 2026/2027 platform UI settings for Video Advertising before deploying changes.
- **Verification Requirement**: Confirm current statutory penalty thresholds and licensing rules with qualified local counsel in KSA, UAE, or Egypt.
- **No Guaranteed Outcomes**: Per Agent 2 v1.2 boundaries, this asset defines operational controls and testable measurement hypotheses; it does not promise guaranteed rankings, virality, or fixed ROAS lift.
- **Update Triggers**: Re-verify this framework whenever platform UI/API schemas change, prior to major Hijri/seasonal peaks (Ramadan/White Friday), or within 90 days of `2026-10-25`.
