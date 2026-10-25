# Evidence Register & Source Boundaries — `FW-018` (`AMP-066`)

- **Framework Title (EN)**: Google Ads AI Max & PMax Arabic Morphological Negative Keyword Generator Prompt
- **عنوان الأصل (AR)**: قالب توليد قوائم الكلمات السلبية الصرفية واللهجية لحملات Google Ads AI Max وPerformance Max بالعربية
- **Channel**: Pay-Per-Click (PPC) Advertising
- **Last Reviewed Date**: `2026-10-25`
- **Verification Gate Status**: `READY_FOR_REVIEW`

## 1. Problem & Empirical Evidence (What Proves the Failure Mechanism in Egypt & GCC)

| Source ID | Title & Direct Link | Publisher | Published | Accessed | Type & Confidence | What This Source Supports | Support Boundary |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `SRC-070` | [The hidden challenges of AI Max search term reporting](https://adalysis.com/blog/ai-max-search-term-reporting/) | Adalysis | `2025-12-02` | `2026-10-25` | `PRACTITIONER_GUIDE` (`REPEATED_SIGNAL`) | Explains reporting opacity and broad query expansion in Google Ads AI Max when search term and landing page controls are not audited. | Google Ads Search / AI Max. |

## 2. Official Platform Capability, Regulatory & Advice Evidence

| Source ID | Title & Direct Link | Publisher | Published | Accessed | Status / Confidence | Official Capability or Rule Verified | Fallback / Operational Boundary |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `SRC-004` | [Frequently asked questions about AI Max for Search campaigns](https://support.google.com/google-ads/answer/15913066?hl=en) | Google Ads Help | `2026-06-01` | `2026-10-25` | `OFFICIAL_DOCUMENTATION` (`CONFIRMED_CAPABILITY`) | AI Max expands beyond exact keywords using broad match and keywordless signals; negative keywords are respected and Ad Rank governs prioritization with PMax. | Requires active negative keyword hygiene to prevent low-intent dialect matching. |
| `SRC-005` | [Negative keywords in Performance Max campaigns - Google Ads Help](https://support.google.com/google-ads/answer/15726455?hl=en) | Google Ads Help | `2026-05-15` | `2026-10-25` | `OFFICIAL_DOCUMENTATION` (`CONFIRMED_CAPABILITY`) | Campaign-level and account-level negative keywords block PMax serving on matching Search/Shopping queries. | Does not replace placement exclusions or brand-safety lists for Display/Video inventory. |
| `SRC-006` | [Fix issues with negative keywords - Google Ads Help](https://support.google.com/google-ads/answer/9701952?hl=en) | Google Ads Help | `2026-04-10` | `2026-10-25` | `OFFICIAL_DOCUMENTATION` (`CONFIRMED_CAPABILITY`) | Negative keywords do not match close variants automatically; Arabic spelling variants and dialectal synonyms must be added explicitly. | Search terms over 16 words or morphological variants may still trigger ads if unblocked. |
| `SRC-004` | [Frequently asked questions about AI Max for Search campaigns](https://support.google.com/google-ads/answer/15913066?hl=en) | Google Ads Help | `2026-06-01` | `2026-10-25` | `OFFICIAL_CAPABILITY_CHECK` (`supported`) | Google Ads official documentation confirms negative keywords do not match close variants or morphological stems automatically; every spelling/prefix variant must be added explicitly. | Fallback: Audit the AI Max / Search Terms report weekly and append newly discovered dialect variants. |

## 3. Counterevidence, Exceptions & When This Pattern Does NOT Apply

- In strictly single-language English B2B niches or fully prepaid digital-product flows, the severity of this Pay-Per-Click (PPC) Advertising mismatch is lower provided manual QA is still performed.
- ** Operational Boundary**: Do not add broad single-word negatives that overlap with your core product noun (e.g., never add `عروض` or `سعر` as negatives on an e-commerce account). / لا تضف كلمات سلبية عامة تتقاطع مع نية الشراء الفعلية (مثل `سعر` أو `عروض` أو `تخفيض`) في حسابات التجارة الإلكترونية.

## 4. Claims Remaining Uncertain & Update Triggers

- **Verification Requirement**: Verify live store/account configuration and current 2026/2027 platform UI settings for Pay-Per-Click (PPC) Advertising before deploying changes.
- **Verification Requirement**: Confirm current statutory penalty thresholds and licensing rules with qualified local counsel in KSA, UAE, or Egypt.
- **No Guaranteed Outcomes**: Per Agent 2 v1.2 boundaries, this asset defines operational controls and testable measurement hypotheses; it does not promise guaranteed rankings, virality, or fixed ROAS lift.
- **Update Triggers**: Re-verify this framework whenever platform UI/API schemas change, prior to major Hijri/seasonal peaks (Ramadan/White Friday), or within 90 days of `2026-10-25`.
