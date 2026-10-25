# Evidence Register & Source Boundaries — `FW-008` (`AMP-008`)

- **Framework Title (EN)**: Arabic URL Slug Architecture & Percent-Encoding Length Decision Aid
- **عنوان الأصل (AR)**: أداة القرار المعماري لروابط صفحات الويب العربية (`URL Slugs`) ومنع انفجار الترميز المئوي (`%D8%`)
- **Channel**: Search Engine Optimization (SEO)
- **Last Reviewed Date**: `2026-10-25`
- **Verification Gate Status**: `READY_FOR_REVIEW`

## 1. Problem & Empirical Evidence (What Proves the Failure Mechanism in Egypt & GCC)

| Source ID | Title & Direct Link | Publisher | Published | Accessed | Type & Confidence | What This Source Supports | Support Boundary |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `SRC-040` | [Arabic URL Slugs: What 24 Arab Websites Use](https://voctos.net/arabic-url-slugs-seo/) | VOCTOS | `2026-10-11` | `2026-10-25` | `EMPIRICAL_AUDIT` (`RESEARCH_FINDING`) | Each UTF-8 Arabic letter percent-encodes to 6 characters (%D8%..), expanding 82-char Arabic slugs to 235 chars on average; 72% exceed WordPress's 200-char post_name limit (truncating after ~6 words) and risk exceeding GA4's 420-char page_referrer limit. | Sample of 245 Arabic URLs and 557 English URLs across 24 Arab websites. |
| `SRC-038` | [We Audited 20 Salla and Zid Stores: The SEO Defaults Saudi Merchants Inherit (2026)](https://voctos.net/salla-zid-store-seo-audit/) | VOCTOS | `2026-10-08` | `2026-10-25` | `EMPIRICAL_AUDIT` (`RESEARCH_FINDING`) | Audit of 20 Saudi stores (10 Salla, 10 Zid): 60% of sampled Salla sitemap URLs (88/146) redirected or returned 410; 6/6 Salla English pages canonicalized to Arabic; 9/10 Zid stores lacked Sitemap in robots.txt; 0/10 Salla stores had Brand in Product JSON-LD; 8/11 English pages kept Arabic-script titles. | Sample of 20 live Saudi stores audited on 2 Oct 2026. |

## 2. Official Platform Capability, Regulatory & Advice Evidence

| Source ID | Title & Direct Link | Publisher | Published | Accessed | Status / Confidence | Official Capability or Rule Verified | Fallback / Operational Boundary |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `SRC-040` | [Arabic URL Slugs: What 24 Arab Websites Use](https://voctos.net/arabic-url-slugs-seo/) | VOCTOS | `2026-10-11` | `2026-10-25` | `OFFICIAL_CAPABILITY_CHECK` (`supported`) | VOCTOS 2026 audit of 24 Arab websites found 72% exceeded 300 encoded chars and 13/16 bilingual brands use clean English slugs under `/ar/`. | Fallback: Enforce `validate_mena_slug()` before publishing any URL. |

## 3. Counterevidence, Exceptions & When This Pattern Does NOT Apply

- In strictly single-language English B2B niches or fully prepaid digital-product flows, the severity of this Search Engine Optimization (SEO) mismatch is lower provided manual QA is still performed.
- ** Operational Boundary**: Do not bulk-change URL slugs on existing high-ranking Arabic pages without a 1:1 `301` redirect map and canonical update—only rewrite existing slugs if they are actively truncated or broken. / لا تقم بتغيير روابط الصفحات العربية المتصدرة حالياً بشكل جماعي دون خريطة تحويل `301` دقيقة؛ طبّق القاعدة فوراً على الصفحات الجديدة أو الروابط المعطوبة فقط.

## 4. Claims Remaining Uncertain & Update Triggers

- **Verification Requirement**: Verify live store/account configuration and current 2026/2027 platform UI settings for Search Engine Optimization (SEO) before deploying changes.
- **Verification Requirement**: Confirm current statutory penalty thresholds and licensing rules with qualified local counsel in KSA, UAE, or Egypt.
- **No Guaranteed Outcomes**: Per Agent 2 v1.2 boundaries, this asset defines operational controls and testable measurement hypotheses; it does not promise guaranteed rankings, virality, or fixed ROAS lift.
- **Update Triggers**: Re-verify this framework whenever platform UI/API schemas change, prior to major Hijri/seasonal peaks (Ramadan/White Friday), or within 90 days of `2026-10-25`.
