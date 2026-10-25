# Evidence Register & Source Boundaries — `FW-006` (`AMP-006`)

- **Framework Title (EN)**: Zid & MENA Storefront `robots.txt` Sitemap Directive & AI-Crawler Governance Checklist
- **عنوان الأصل (AR)**: قائمة فحص ملف `robots.txt` وإعلان `Sitemap:` وضبط زواحف الذكاء الاصطناعي في متاجر زد والمنطقة
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
| `SRC-028` | [تحسين محركات البحث للمتاجر الإلكترونية | زد المدونة](https://zid.sa/ar/blog/%D8%AA%D8%AD%D8%B3%D9%8A%D9%86-%D9%85%D8%AD%D8%B1%D9%83%D8%A7%D8%AA_%D8%A7%D9%84%D8%A8%D8%AD%D8%AB/) | Zid | `2023-03-26` | `2026-10-25` | `OFFICIAL_DOCUMENTATION` (`CONFIRMED_CAPABILITY`) | Outlines Zid's e-commerce SEO structure for product titles, meta descriptions, and category taxonomy. | Requires manual English content creation when multi-language storefront is enabled. |
| `SRC-038` | [We Audited 20 Salla and Zid Stores: The SEO Defaults Saudi Merchants Inherit (2026)](https://voctos.net/salla-zid-store-seo-audit/) | VOCTOS | `2026-10-08` | `2026-10-25` | `OFFICIAL_CAPABILITY_CHECK` (`supported`) | 9 of 10 audited Zid stores omitted the `Sitemap:` directive in `robots.txt`, while 10 of 10 Salla stores included it. | Fallback: Submit `sitemap.xml` directly in GSC and Bing Webmaster Tools, or append `Sitemap:` via Cloudflare on custom domains. |

## 3. Counterevidence, Exceptions & When This Pattern Does NOT Apply

- In strictly single-language English B2B niches or fully prepaid digital-product flows, the severity of this Search Engine Optimization (SEO) mismatch is lower provided manual QA is still performed.
- ** Operational Boundary**: Do not assume blocking `Google-Extended` blocks Google Search indexing—`Googlebot` controls Search & AI Overviews indexing, while `Google-Extended` controls Gemini training/grounding. / لا تفترض أن حظر `Google-Extended` يمنع أرشفة المتجر في بحث جوجل؛ فزاحف `Googlebot` هو المسؤول عن البحث وAI Overviews.

## 4. Claims Remaining Uncertain & Update Triggers

- **Verification Requirement**: Verify live store/account configuration and current 2026/2027 platform UI settings for Search Engine Optimization (SEO) before deploying changes.
- **Verification Requirement**: Confirm current statutory penalty thresholds and licensing rules with qualified local counsel in KSA, UAE, or Egypt.
- **No Guaranteed Outcomes**: Per Agent 2 v1.2 boundaries, this asset defines operational controls and testable measurement hypotheses; it does not promise guaranteed rankings, virality, or fixed ROAS lift.
- **Update Triggers**: Re-verify this framework whenever platform UI/API schemas change, prior to major Hijri/seasonal peaks (Ramadan/White Friday), or within 90 days of `2026-10-25`.
