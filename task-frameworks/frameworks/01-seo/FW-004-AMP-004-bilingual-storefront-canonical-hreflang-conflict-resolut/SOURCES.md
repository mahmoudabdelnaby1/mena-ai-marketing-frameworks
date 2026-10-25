# Evidence Register & Source Boundaries — `FW-004` (`AMP-004`)

- **Framework Title (EN)**: Bilingual Storefront Canonical & Hreflang Conflict Resolution Checklist (Salla, Zid & Custom MENA Stores)
- **عنوان الأصل (AR)**: قائمة فحص وإصلاح تضارب `canonical` و`hreflang` في المتاجر ثنائية اللغة (العربية والإنجليزية)
- **Channel**: Search Engine Optimization (SEO)
- **Last Reviewed Date**: `2026-10-25`
- **Verification Gate Status**: `READY_FOR_REVIEW`

## 1. Problem & Empirical Evidence (What Proves the Failure Mechanism in Egypt & GCC)

| Source ID | Title & Direct Link | Publisher | Published | Accessed | Type & Confidence | What This Source Supports | Support Boundary |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `SRC-038` | [We Audited 20 Salla and Zid Stores: The SEO Defaults Saudi Merchants Inherit (2026)](https://voctos.net/salla-zid-store-seo-audit/) | VOCTOS | `2026-10-08` | `2026-10-25` | `EMPIRICAL_AUDIT` (`RESEARCH_FINDING`) | Audit of 20 Saudi stores (10 Salla, 10 Zid): 60% of sampled Salla sitemap URLs (88/146) redirected or returned 410; 6/6 Salla English pages canonicalized to Arabic; 9/10 Zid stores lacked Sitemap in robots.txt; 0/10 Salla stores had Brand in Product JSON-LD; 8/11 English pages kept Arabic-script titles. | Sample of 20 live Saudi stores audited on 2 Oct 2026. |
| `SRC-061` | [The Arabic SEO in Saudi Arabia Mistakes Costing Riyadh Brands Rankings](https://digistreetmedia.com/blog/the-arabic-seo-in-saudi-arabia-mistakes-costing-riyadh-brands-rankings/) | DigiStreet Media | `2026-09-29` | `2026-10-25` | `PRACTITIONER_GUIDE` (`REPEATED_SIGNAL`) | Identifies 5 recurring KSA SEO failures: treating Arabic as translation, running one strategy across Arabic/English, broken hreflang/RTL mobile UX, ignoring Vision 2030 sector context, and chasing non-local backlinks while treating Riyadh, Jeddah, and Dammam as homogeneous. | Saudi Arabia B2B and B2C SEO. |

## 2. Official Platform Capability, Regulatory & Advice Evidence

| Source ID | Title & Direct Link | Publisher | Published | Accessed | Status / Confidence | Official Capability or Rule Verified | Fallback / Operational Boundary |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `SRC-038` | [We Audited 20 Salla and Zid Stores: The SEO Defaults Saudi Merchants Inherit (2026)](https://voctos.net/salla-zid-store-seo-audit/) | VOCTOS | `2026-10-08` | `2026-10-25` | `OFFICIAL_CAPABILITY_CHECK` (`plan/region dependent`) | VOCTOS Oct 2026 audit documented that 6 of 6 English-enabled Salla stores pointed the English page canonical back to the Arabic URL. | Fallback: Use Cloudflare `HTMLRewriter` at the DNS edge to rewrite `/en/*` canonicals, or disable `/en/` if English SEO is not actively maintained. |

## 3. Counterevidence, Exceptions & When This Pattern Does NOT Apply

- In strictly single-language English B2B niches or fully prepaid digital-product flows, the severity of this Search Engine Optimization (SEO) mismatch is lower provided manual QA is still performed.
- ** Operational Boundary**: Do not enable `/en/` storefront routes if English titles and descriptions are not actually translated (`AMP-005`)—keep the store single-language Arabic until English copy is ready. / لا تقم بتفعيل مسار اللغة الإنجليزية (`/en/`) إذا لم تكن عناوين وأوصاف المنتجات مترجمة فعلياً (`AMP-005`)؛ أبقِ المتجر أحادي اللغة حتى تكتمل الترجمة.

## 4. Claims Remaining Uncertain & Update Triggers

- **Verification Requirement**: Verify live store/account configuration and current 2026/2027 platform UI settings for Search Engine Optimization (SEO) before deploying changes.
- **Verification Requirement**: Confirm current statutory penalty thresholds and licensing rules with qualified local counsel in KSA, UAE, or Egypt.
- **No Guaranteed Outcomes**: Per Agent 2 v1.2 boundaries, this asset defines operational controls and testable measurement hypotheses; it does not promise guaranteed rankings, virality, or fixed ROAS lift.
- **Update Triggers**: Re-verify this framework whenever platform UI/API schemas change, prior to major Hijri/seasonal peaks (Ramadan/White Friday), or within 90 days of `2026-10-25`.
