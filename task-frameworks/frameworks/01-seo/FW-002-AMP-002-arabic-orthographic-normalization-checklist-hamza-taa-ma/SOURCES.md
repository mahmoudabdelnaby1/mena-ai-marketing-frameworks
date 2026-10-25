# Evidence Register & Source Boundaries — `FW-002` (`AMP-002`)

- **Framework Title (EN)**: Arabic Orthographic Normalization Checklist (Hamza, Taa Marbuta, Alef Maqsura & Indic Digits)
- **عنوان الأصل (AR)**: قائمة فحص تطبيع الحروف والأرقام العربية في البحث الداخلي والـ SEO (الهمزات، التاء المربوطة، الألف المقصورة، والأرقام الهندية)
- **Channel**: Search Engine Optimization (SEO)
- **Last Reviewed Date**: `2026-10-25`
- **Verification Gate Status**: `READY_FOR_REVIEW`

## 1. Problem & Empirical Evidence (What Proves the Failure Mechanism in Egypt & GCC)

| Source ID | Title & Direct Link | Publisher | Published | Accessed | Type & Confidence | What This Source Supports | Support Boundary |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `SRC-041` | [Arabic Site Search Normalization: 20 Arab Online Stores Tested](https://voctos.net/arabic-site-search-normalization/) | VOCTOS | `2026-10-08` | `2026-10-25` | `EMPIRICAL_AUDIT` (`RESEARCH_FINDING`) | Internal site search on Salla and Zid stores fails when shoppers use variant Arabic spellings (Hamza أ/ا, Taa Marbuta ة/ه, Alef Maqsura ى/ي) or Arabic-Indic digits (٠-٩ vs 0-9) that differ from catalog product titles. | 20 Arab e-commerce storefronts tested in Oct 2026. |
| `SRC-060` | [Arabic Keyword Research for Online Stores: A Practical Guide](https://esafqa.com/en/blog/arabic-keyword-research-guide/) | Esafqa | `2026-10-08` | `2026-10-25` | `PRACTITIONER_GUIDE` (`REPEATED_SIGNAL`) | Demonstrates how a single product concept splits across MSA vs dialect, spelling variants, and lexical differences between Saudi Arabia, UAE, and Egypt. | Arabic e-commerce keyword research. |
| `SRC-062` | [The State of Arabic SEO in 2026: What Most Tools Miss](https://crawlix.app/blog/arabic-seo-2026/) | Crawlix | `2026-04-15` | `2026-10-25` | `PRACTITIONER_GUIDE` (`REPEATED_SIGNAL`) | Explains why standard western SEO tools undercount Arabic search demand by failing to group morphological prefixes/suffixes and dialect-MSA code-switching ('أفضل سيارة' vs 'أحسن سيارة'). | Arabic keyword tooling and technical SEO. |

## 2. Official Platform Capability, Regulatory & Advice Evidence

| Source ID | Title & Direct Link | Publisher | Published | Accessed | Status / Confidence | Official Capability or Rule Verified | Fallback / Operational Boundary |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `SRC-041` | [Arabic Site Search Normalization: 20 Arab Online Stores Tested](https://voctos.net/arabic-site-search-normalization/) | VOCTOS | `2026-10-08` | `2026-10-25` | `OFFICIAL_CAPABILITY_CHECK` (`supported`) | Native `arabic_normalization` token filter handles Alef, Taa Marbuta, Alef Maqsura, Tatweel, and Indic digits out-of-the-box when enabled on the index. | Fallback: On hosted SaaS platforms (Salla/Zid) where index settings are locked, inject normalized orthographic variants into Product Tags (`الوسوم`) and Meta Keywords. |

## 3. Counterevidence, Exceptions & When This Pattern Does NOT Apply

- In strictly single-language English B2B niches or fully prepaid digital-product flows, the severity of this Search Engine Optimization (SEO) mismatch is lower provided manual QA is still performed.
- ** Operational Boundary**: Do not strip Hamzas or Taa Marbuta from visible H1 headings or formal brand copy—normalization happens in the search index, backend tags, and query parser, while visible prose stays grammatically correct. / لا تحذف الهمزات أو التاء المربوطة من العناوين المرئية (`H1`) أو النصوص الرسمية للعلامة؛ التطبيع يتم في فهرس البحث والوسوم الخلفية، بينما يبقى النص المرئي صحيحاً إملائياً.

## 4. Claims Remaining Uncertain & Update Triggers

- **Verification Requirement**: Verify live store/account configuration and current 2026/2027 platform UI settings for Search Engine Optimization (SEO) before deploying changes.
- **Verification Requirement**: Confirm current statutory penalty thresholds and licensing rules with qualified local counsel in KSA, UAE, or Egypt.
- **No Guaranteed Outcomes**: Per Agent 2 v1.2 boundaries, this asset defines operational controls and testable measurement hypotheses; it does not promise guaranteed rankings, virality, or fixed ROAS lift.
- **Update Triggers**: Re-verify this framework whenever platform UI/API schemas change, prior to major Hijri/seasonal peaks (Ramadan/White Friday), or within 90 days of `2026-10-25`.
