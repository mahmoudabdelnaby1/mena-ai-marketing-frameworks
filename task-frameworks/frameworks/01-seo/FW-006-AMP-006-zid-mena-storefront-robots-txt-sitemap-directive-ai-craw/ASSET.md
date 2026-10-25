# FW-006: Zid & MENA Storefront `robots.txt` Sitemap Directive & AI-Crawler Governance Checklist
## قائمة فحص ملف `robots.txt` وإعلان `Sitemap:` وضبط زواحف الذكاء الاصطناعي في متاجر زد والمنطقة

- **Consolidated Contextual Child IDs (`MERGE_INTO_EXISTING`)**: `AMP-018`, `AMP-030`, `AMP-042`, `AMP-054`
- **Selected Artifact Type**: `CHECKLIST`
- **Intended Audience**: SEO Specialist, E-Commerce Manager, Content Strategist, Technical SEO Lead
- **Target Markets & Languages**: Egypt & GCC (`Saudi Arabia, UAE, Kuwait, Qatar, Bahrain, Oman`) — Bilingual Arabic (`Egyptian Ammiya`, `Saudi/Gulf Khaleeji`, `White MSA`) + English
- **Version**: `1.2` | **Last Reviewed**: `2026-10-25` | **Status**: `READY_FOR_REVIEW`

## 1. Plain-Language Promise & Why This Artifact Form Fits the Job

- **What You Can Make or Decide (EN)**: Verify `Sitemap:` directive presence and intentional AI-crawler rules (`GPTBot`, `ClaudeBot`, `Google-Extended`, `PerplexityBot`) in storefront `robots.txt` files.
- **ما الذي يمكنك إنجازه أو حسمه بهذه الأداة (AR)**: التحقق من وجود سطر `Sitemap:` في ملف `robots.txt` وضبط صلاحيات زواحف الذكاء الاصطناعي (`GPTBot`، `ClaudeBot`، `Google-Extended`) بوعي.
- **Why `CHECKLIST` Fits This User Job (EN)**: VOCTOS's Oct 2026 audit of 10 Zid stores proved that 9 of 10 stores lacked a `Sitemap:` line in their 1,268-line default `robots.txt` (while allowing `GPTBot`/`ClaudeBot` and blocking `PetalBot`); a concise CHECKLIST prevents blind assumptions and ensures proper sitemap discovery.
- **لماذا يناسب شكل `CHECKLIST` هذه المهمة (AR)**: أثبت فحص VOCTOS (أكتوبر 2026) أن 9 من 10 متاجر زد تفتقر لسطر `Sitemap:` في ملف `robots.txt` الافتراضي البالغ 1,268 سطراً؛ لذا توفر قائمة الفحص هذه خطوات تحقق فورية.

## 2. "Use It When" Trigger, Boundaries & Exact Inputs to Prepare

- **Use It When (EN)**: Use during technical SEO onboarding for any Zid, Salla, Shopify, or WooCommerce store in KSA, UAE, or Egypt.
- **متى تستخدم هذه الأداة (AR)**: تُستخدم عند التهيئة التقنية للـ SEO لأي متجر على زد أو سلة أو شوبيفاي أو ووكومرس في السعودية أو الإمارات أو مصر.
- **When NOT to Use It (EN)**: Do not assume blocking `Google-Extended` blocks Google Search indexing—`Googlebot` controls Search & AI Overviews indexing, while `Google-Extended` controls Gemini training/grounding.
- **متى لا تستخدم هذه الأداة (AR)**: لا تفترض أن حظر `Google-Extended` يمنع أرشفة المتجر في بحث جوجل؛ فزاحف `Googlebot` هو المسؤول عن البحث وAI Overviews.

### Exact Inputs to Prepare Before Starting (`المدخلات المطلوب تجهيزها`)
1. Live `https://store-domain.com/robots.txt` output
2. Verified `sitemap.xml` URL (`200 OK`)
3. Google Search Console & Bing Webmaster Tools property access

### Privacy-Safe Data Handling (`ضوابط الخصوصية وحماية البيانات الشخصية PDPL`)
- **Strict PII Redaction Before Prompting**: Under Saudi PDPL (Art. 25), UAE Federal Decree-Law No. 45 of 2021, Qatar Law No. 13 of 2016, and Egypt Law No. 151 of 2020, **never paste raw customer names, unhashed mobile numbers (`+9665...` / `+201...`), email addresses, national IDs, or private WhatsApp transcripts into public/consumer LLM interfaces**. Use anonymized placeholders (`{first_name}`, `ORD_10045`) during prompt testing and restrict live customer data to zero-data-retention enterprise API endpoints or local deterministic scripts.

## 3. The Directly Usable Artifact (`الأداة التطبيقية الجاهزة للنسخ والتنفيذ`)

### `robots.txt` & Sitemap Discovery Checklist

#### 1. Instant Terminal Diagnostic
```bash
curl -sL "https://your-store.sa/robots.txt" | grep -iE "^(Sitemap|User-agent|Disallow):" | tail -n 30
```

#### 2. Verification & Action Checklist
- [ ] **Check 1 — `Sitemap:` Directive Presence**:
  - Run `curl -sL https://your-store.sa/robots.txt | grep -i '^Sitemap:'`.
  - **If Missing (Observed on 9/10 Zid stores)**:
    1. Submit `https://your-store.sa/sitemap.xml` manually inside **Google Search Console -> Sitemaps** AND **Bing Webmaster Tools -> Sitemaps** (critical because ChatGPT Search relies heavily on Bing's index alongside `OAI-SearchBot`).
    2. If `robots.txt` is editable (or routed via Cloudflare Worker on custom domain), append `Sitemap: https://your-store.sa/sitemap.xml` at the bottom of `robots.txt`.
- [ ] **Check 2 — Verify Actual AI Crawler Rules (Do Not Guess)**:
  - Check explicit rules for:
    - `Googlebot` (Google Search + AI Overviews)
    - `OAI-SearchBot` & `ChatGPT-User` (ChatGPT Search citations)
    - `GPTBot` (OpenAI model training)
    - `ClaudeBot` / `Claude-SearchBot` (Anthropic)
    - `PerplexityBot` (Perplexity AI)
  - *Empirical Note*: Zid's 1,268-line default `robots.txt` (observed on 8/10 Zid stores in Oct 2026) blocks 627 scrapers and `PetalBot`, but **allows** `GPTBot`, `ClaudeBot`, and `Google-Extended`. Always inspect the live file rather than assuming a platform blocks AI bots.
- [ ] **Check 3 — Verify Cart/Checkout Disallows Do Not Block JS/CSS Assets**:
  - Confirm `/cart`, `/checkout`, and internal unnormalized search result URLs (`/?q=*` or `/search*`) are disallowed to save crawl budget, while `/assets/`, `/*.js`, and `/*.css` remain allowed for Googlebot mobile rendering.

## 4. Model & Platform Capability Branches (`فروع قدرات النماذج والمنصات والبدائل الاحتياطية`)

| System / Platform | Capability Status | Official Documentation & Access Date | Operational Constraint in Egypt & GCC | Fallback When Feature/Modality Is Unavailable |
| :--- | :--- | :--- | :--- | :--- |
| **Zid Default `robots.txt` Template** | `supported` | [Official Reference](https://voctos.net/salla-zid-store-seo-audit/) (`2026-10-25`) | 9 of 10 audited Zid stores omitted the `Sitemap:` directive in `robots.txt`, while 10 of 10 Salla stores included it. | Submit `sitemap.xml` directly in GSC and Bing Webmaster Tools, or append `Sitemap:` via Cloudflare on custom domains. |

## 5. Consolidated Regional & Vertical Adaptation Matrix (`دمج الأنماط السياقية الفرعية بدون حشو`)

Per Agent 2 v1.2's anti-padding rule, the following **4 cross-verified contextual synthesis patterns** and **0 screened duplicate variants** share this core mechanism and are consolidated directly into this source-of-truth framework:

| Child Pattern ID | Disposition | Regional / Sector Operating Context | Specific Adaptation & Guardrail Integrated in This Asset | Evidence Tier |
| :--- | :--- | :--- | :--- | :--- |
| **`AMP-018`** | `MERGE_INTO_EXISTING` | Egyptian E-Commerce & Social Commerce (Shopify / WooCommerce / Cairo & Alexandria) | Googlebot can still discover the sitemap if manually submitted inside Google Search Console.; Specifically impacts Egyptian brands operating in EGP where merchant-specific payment mix from recent order records, Mobile Wallets (Vodafone Cash), InstaPay, and Fawry dominate. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-030`** | `MERGE_INTO_EXISTING` | UAE & Multi-Market GCC Enterprise / Retail (Dubai, Abu Dhabi, Doha, Kuwait) | Googlebot can still discover the sitemap if manually submitted inside Google Search Console.; Specifically impacts bilingual Arabic/English campaigns in high-CPM, expat-dense Gulf markets under UAE PDPL / TDRA and Qatari regulations. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-042`** | `MERGE_INTO_EXISTING` | High-Trust & Regulated Verticals (Healthcare/SFDA/EDA, Fintech/SAMA/FRA, Real Estate) | Googlebot can still discover the sitemap if manually submitted inside Google Search Console.; Specifically impacts regulated claims requiring SFDA, EDA, MOH, SAMA, FRA, or RERA compliance pre-clearance and strict hallucination guardrails. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-054`** | `MERGE_INTO_EXISTING` | Seasonal Peak Operations (Ramadan, Eid, White/Yellow Friday, Saudi Founding/National Day) | Googlebot can still discover the sitemap if manually submitted inside Google Search Console.; Specifically impacts high-velocity seasonal surges where CPMs jump 40-70%, prices change rapidly, and Hijri calendar cultural sensitivity is paramount. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |

### Context-Specific Execution Knobs Across the 5 MENA Operating Environments
1. **Saudi D2C E-Commerce (`Salla / Zid / Riyadh & Jeddah Retail`)**: Enforce `SAR` tax-inclusive pricing (`15% ZATCA VAT`), native `Mada / Apple Pay / Tabby / Tamara` visibility (`AMP-387`), `GAMR Mawthooq` creator verification (`AMP-281`), and White Saudi Khaleeji orthography (`AMP-002`, `AMP-177`).
2. **Egyptian E-Commerce & Social Commerce (`Shopify / WooCommerce / Cairo & Alexandria`)**: Use each merchant’s own order and payment data to assess Cash on Delivery (`COD`), mobile wallets, InstaPay, Fawry, `valU`, address fields, and pre-dispatch WhatsApp confirmation. Verify current provider terms and local requirements before implementation.
3. **UAE & Multi-Market GCC Enterprise / Retail (`Dubai, Abu Dhabi, Doha, Kuwait`)**: Separate high-CPM UAE/Qatar budgets from lower-CPM markets (`AMP-061`), enforce UAE `TDRA` `9 PM – 7 AM` SMS curfew + `AD-` prefix (`AMP-442`), UAE Media Council permits (`AMP-282`), and bilingual Arabic/English canonical & currency parity (`current applicable UAE VAT`, `current applicable Qatar/Kuwait tax rules`, 3-decimal `KWD` `AMP-239`).
4. **High-Trust & Regulated Verticals (`Healthcare SFDA/MOH/EDA, FinTech SAMA/FRA, Real Estate REGA/RERA`)**: Strip all therapeutic/cure verbs (`AMP-176`, `AMP-286`), display mandatory `MOH/SFDA/DHA/EDA/Fal/Trakheesi` permit numbers (`AMP-070`), and route budgets to high-credibility channels (`AMP-290`, `AMP-339`).
5. **Seasonal Peak Operations (`Ramadan, Eid, White/Yellow Friday, Saudi Founding/National Day`)**: Lock Hijri-Gregorian overlaps (`Feb 2027 Ramadan x Saudi Founding Day x Kuwait National Day` `AMP-125`), pre-schedule GMC `sale_price_effective_date` 48h ahead (`AMP-063`), verify 30-day baseline discount permits (`AMP-064`), and disable Meta Advantage+ auto-music (`AMP-065`).

## 6. Worked Example Summary & Failure Recovery (`ملخص المثال التطبيقي وخطة الإنقاذ`)

*(Full step-by-step worked example with annotated human edits is also provided in `EXAMPLE.md`)*

- **Sample Input Brief**: - **Store**: Saudi Electronics & Accessories Store on Zid (`https://tech-example.sa`).
- **Diagnostic Output**: `robots.txt` is 1,268 lines long, contains `0` `Sitemap:` lines, blocks `PetalBot`, and allows `Googlebot`, `GPTBot`, and `ClaudeBot`.
- **Human Review & Key Edits Applied**: 1. **Manual Sitemap Registration**: Submitted `https://tech-example.sa/sitemap.xml` directly in both Google Search Console and Bing Webmaster Tools.
2. **Cloudflare Edge Append**: Added a lightweight Cloudflare Worker rule on `/robots.txt` appending `\nSitemap: https://tech-example.sa/sitemap.xml\n` so all compliant crawlers discover the sitemap automatically.
- **Final Usable Output**: ```text
# Appended to https://tech-example.sa/robots.txt via Edge / Platform Settings
Sitemap: https://tech-example.sa/sitemap.xml
```
- Verified `200 OK` and `Sitemap:` line readable by `Googlebot`, `Bingbot`, and `OAI-SearchBot`.
- **What Can Go Wrong**: An agency tells a Zid merchant 'your store is invisible in ChatGPT because Zid blocks GPTBot in robots.txt' without reading the file, wasting engineering hours on a falsified assumption (`AMP-565`).
- **Correction & Fallback**: Always run `curl -s https://domain/robots.txt | grep -i -A 3 'GPTBot'` first; in 8 of 10 Zid stores audited by VOCTOS (Oct 2026), `GPTBot` is allowed and the actual gap was missing `Sitemap:` registration in Bing/GSC.

## 7. Measurement Plan & Hypothesis Framing (`خطة القياس والضوابط الإحصائية`)

- **Primary Metric to Track**: Time-to-discovery of newly published product URLs in Google Search Console & Bing Webmaster Tools.
- **Baseline Definition**: Pre-fix crawl discovery latency for new SKUs.
- **Observation Window**: 14 days after sitemap submission. *(Must span full 7/14-day weekly cycles and account for 25th–30th monthly salary windows per `AMP-391`)*.
- **What Cannot Be Concluded (Boundary)**: Adding `Sitemap:` ensures crawlers find URLs, but does not override `noindex` tags or poor content quality.
