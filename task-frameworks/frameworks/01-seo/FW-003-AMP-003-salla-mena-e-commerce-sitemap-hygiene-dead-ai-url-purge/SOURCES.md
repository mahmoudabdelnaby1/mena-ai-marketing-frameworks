# Evidence Register & Source Boundaries — `FW-003` (`AMP-003`)

- **Framework Title (EN)**: Salla & MENA E-Commerce Sitemap Hygiene & Dead-AI-URL Purge Checklist
- **عنوان الأصل (AR)**: قائمة فحص وتطهير خرائط المواقع (`sitemap.xml`) في متاجر سلة والتجارة الإلكترونية من الروابط المعطوبة والمحذوفة
- **Channel**: Search Engine Optimization (SEO)
- **Last Reviewed Date**: `2026-10-25`
- **Verification Gate Status**: `READY_FOR_REVIEW`

## 1. Problem & Empirical Evidence (What Proves the Failure Mechanism in Egypt & GCC)

| Source ID | Title & Direct Link | Publisher | Published | Accessed | Type & Confidence | What This Source Supports | Support Boundary |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `SRC-038` | [We Audited 20 Salla and Zid Stores: The SEO Defaults Saudi Merchants Inherit (2026)](https://voctos.net/salla-zid-store-seo-audit/) | VOCTOS | `2026-10-08` | `2026-10-25` | `EMPIRICAL_AUDIT` (`RESEARCH_FINDING`) | Audit of 20 Saudi stores (10 Salla, 10 Zid): 60% of sampled Salla sitemap URLs (88/146) redirected or returned 410; 6/6 Salla English pages canonicalized to Arabic; 9/10 Zid stores lacked Sitemap in robots.txt; 0/10 Salla stores had Brand in Product JSON-LD; 8/11 English pages kept Arabic-script titles. | Sample of 20 live Saudi stores audited on 2 Oct 2026. |

## 2. Official Platform Capability, Regulatory & Advice Evidence

| Source ID | Title & Direct Link | Publisher | Published | Accessed | Status / Confidence | Official Capability or Rule Verified | Fallback / Operational Boundary |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `SRC-026` | [أدوات السيو في متجرك: دليل شامل - مركز المساعدة - سلة](https://help.salla.sa/article/%D8%AA%D8%AD%D8%B3%D9%8A%D9%86-%D8%B8%D9%87%D9%88%D8%B1-%D9%85%D8%AA%D8%AC%D8%B1%D9%83-%D8%B9%D9%84%D9%89-%D9%85%D8%AD%D8%B1%D9%83%D8%A7%D8%AA-%D8%A7%D9%84%D8%A8%D8%AD%D8%AB-seo/oi134aj2ud6ts12ysumrm5za) | Salla Help Center | `2026-10-18` | `2026-10-25` | `OFFICIAL_DOCUMENTATION` (`CONFIRMED_CAPABILITY`) | Documents Salla's built-in SEO settings, AI prompt assistant for product descriptions, custom metadata_url fields, and Search Console sitemap submission. | Merchants must manually configure product slugs, brand schema fields, and clean up deleted products. |
| `SRC-027` | [تحسين ظهور متجرك في محركات البحث SEO - مركز المساعدة - سلة](https://help.salla.sa/article/-%D8%AA%D8%AD%D8%B3%D9%8A%D9%86-%D8%B8%D9%87%D9%88%D8%B1-%D9%85%D8%AA%D8%AC%D8%B1%D9%83-%D8%B9%D9%84%D9%89-%D9%85%D8%AD%D8%B1%D9%83%D8%A7%D8%AA-%D8%A7%D9%84%D8%A8%D8%AD%D8%AB-seo/gmzx0xblr3ajerkciyoxke1e) | Salla Help Center | `2026-08-18` | `2026-10-25` | `OFFICIAL_DOCUMENTATION` (`CONFIRMED_CAPABILITY`) | Explains 'Crawled - currently not indexed' status on Salla stores when product pages contain thin, duplicated, or unedited manufacturer/AI descriptions. | Indexing depends on Google quality evaluation, not Salla sitemap submission alone. |
| `SRC-038` | [We Audited 20 Salla and Zid Stores: The SEO Defaults Saudi Merchants Inherit (2026)](https://voctos.net/salla-zid-store-seo-audit/) | VOCTOS | `2026-10-08` | `2026-10-25` | `OFFICIAL_CAPABILITY_CHECK` (`plan/region dependent`) | VOCTOS Oct 2026 audit of 10 Salla stores found 60% (88/146) of sampled sitemap product URLs redirected (302/301) or returned 410 Gone. | Fallback: Audit `sitemap.xml` monthly using the HTTP status script and avoid mass-creating disposable product URLs for short promotions. |

## 3. Counterevidence, Exceptions & When This Pattern Does NOT Apply

- In strictly single-language English B2B niches or fully prepaid digital-product flows, the severity of this Search Engine Optimization (SEO) mismatch is lower provided manual QA is still performed.
- ** Operational Boundary**: Do not delete URLs of temporarily out-of-stock evergreen products that will restock within 30 days—keep them `200 OK` with an in-stock notification capture instead of unpublishing. / لا تحذف روابط المنتجات الدائمة التي نفدت مؤقتاً وستتوفر خلال 30 يوماً؛ أبقِ صفحتها نشطة (`200 OK`) مع تفعيل زر «أعلمني عند التوفر».

## 4. Claims Remaining Uncertain & Update Triggers

- **Verification Requirement**: Verify live store/account configuration and current 2026/2027 platform UI settings for Search Engine Optimization (SEO) before deploying changes.
- **Verification Requirement**: Confirm current statutory penalty thresholds and licensing rules with qualified local counsel in KSA, UAE, or Egypt.
- **No Guaranteed Outcomes**: Per Agent 2 v1.2 boundaries, this asset defines operational controls and testable measurement hypotheses; it does not promise guaranteed rankings, virality, or fixed ROAS lift.
- **Update Triggers**: Re-verify this framework whenever platform UI/API schemas change, prior to major Hijri/seasonal peaks (Ramadan/White Friday), or within 90 days of `2026-10-25`.
