# Evidence Register & Source Boundaries — `FW-009` (`AMP-009`)

- **Framework Title (EN)**: Amazon.sa & Amazon.eg 250-Byte UTF-8 Arabic Generic Keyword Compressor Prompt & Script
- **عنوان الأصل (AR)**: قالب وأداة ضغط الكلمات المفتاحية الخفية (`Generic Keywords`) لمتاجر `Amazon.sa` و`Amazon.eg` تحت حد 250 بايت (`UTF-8`)
- **Channel**: Search Engine Optimization (SEO)
- **Last Reviewed Date**: `2026-10-25`
- **Verification Gate Status**: `READY_FOR_REVIEW`

## 1. Problem & Empirical Evidence (What Proves the Failure Mechanism in Egypt & GCC)

| Source ID | Title & Direct Link | Publisher | Published | Accessed | Type & Confidence | What This Source Supports | Support Boundary |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `SRC-039` | [Amazon.sa and noon SEO in 2026: How Product Search Works on Saudi and UAE Marketplaces](https://voctos.net/amazon-sa-noon-seo-guide/) | VOCTOS | `2026-10-08` | `2026-10-25` | `EMPIRICAL_AUDIT` (`RESEARCH_FINDING`) | Amazon.sa enforces a 75-character title rule (June/July 2026) and a <250-byte hidden keyword limit where UTF-8 Arabic letters consume 2 bytes each (~26 Arabic words max vs ~54 Latin); Noon requires English in KSA/UAE but hides English-only listings on its Arabic site; GA4 misclassifies amazon.sa and noon.com into Referral. | Amazon.sa, Amazon.ae, and Noon KSA/UAE/Egypt marketplace rules as of Oct 2026. |

## 2. Official Platform Capability, Regulatory & Advice Evidence

| Source ID | Title & Direct Link | Publisher | Published | Accessed | Status / Confidence | Official Capability or Rule Verified | Fallback / Operational Boundary |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `SRC-039` | [Amazon.sa and noon SEO in 2026: How Product Search Works on Saudi and UAE Marketplaces](https://voctos.net/amazon-sa-noon-seo-guide/) | VOCTOS | `2026-10-08` | `2026-10-25` | `OFFICIAL_CAPABILITY_CHECK` (`supported`) | Amazon counts `generic_keyword` in UTF-8 bytes (<250 bytes), where each Arabic character is 2 bytes (RFC 3629). | Fallback: Run `len(text.encode('utf-8')) < 250` in Python or cap Arabic string length at `<= 125` characters. |

## 3. Counterevidence, Exceptions & When This Pattern Does NOT Apply

- In strictly single-language English B2B niches or fully prepaid digital-product flows, the severity of this Search Engine Optimization (SEO) mismatch is lower provided manual QA is still performed.
- ** Operational Boundary**: Do not repeat words already present in the visible Product Title or Bullet Points—Amazon indexes title/bullet words automatically, so repeating them wastes scarce UTF-8 bytes. / لا تكرر الكلمات الموجودة مسبقاً في عنوان المنتج (`Title`) أو النقاط التفصيلية (`Bullet Points`)؛ لأن أمازون يفهرسها تلقائياً وتكرارها يهدر البايتات المحدودة.

## 4. Claims Remaining Uncertain & Update Triggers

- **Verification Requirement**: Verify live store/account configuration and current 2026/2027 platform UI settings for Search Engine Optimization (SEO) before deploying changes.
- **Verification Requirement**: Confirm current statutory penalty thresholds and licensing rules with qualified local counsel in KSA, UAE, or Egypt.
- **No Guaranteed Outcomes**: Per Agent 2 v1.2 boundaries, this asset defines operational controls and testable measurement hypotheses; it does not promise guaranteed rankings, virality, or fixed ROAS lift.
- **Update Triggers**: Re-verify this framework whenever platform UI/API schemas change, prior to major Hijri/seasonal peaks (Ramadan/White Friday), or within 90 days of `2026-10-25`.
