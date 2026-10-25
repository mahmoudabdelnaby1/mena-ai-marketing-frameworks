# FW-037: Arabic AEO / GEO Entity & Answer-First Structuring Decision Aid (Beyond the `llms.txt` Myth)
## أداة القرار لهيكلة المحتوى العربي لمحركات إجابات الذكاء الاصطناعي (`AEO / GEO` — بدلاً من وهم ملف `llms.txt`)

- **Consolidated Contextual Child IDs (`MERGE_INTO_EXISTING`)**: `AMP-190`, `AMP-200`, `AMP-210`, `AMP-220`, `AMP-230`
- **Selected Artifact Type**: `DECISION_AID`
- **Intended Audience**: Content Manager, Arabic Copywriter, Editorial Lead, Compliance Reviewer
- **Target Markets & Languages**: Egypt & GCC (`Saudi Arabia, UAE, Kuwait, Qatar, Bahrain, Oman`) — Bilingual Arabic (`Egyptian Ammiya`, `Saudi/Gulf Khaleeji`, `White MSA`) + English
- **Version**: `1.2` | **Last Reviewed**: `2026-10-25` | **Status**: `READY_FOR_REVIEW`

## 1. Plain-Language Promise & Why This Artifact Form Fits the Job

- **What You Can Make or Decide (EN)**: Prioritize high-impact Arabic Answer Engine Optimization (AEO/GEO) actions—crawlable HTML, `200 OK` sitemaps, `Product`/`FAQ`/`Organization` JSON-LD, and answer-first comparison tables—instead of relying on `llms.txt` files that AI search engines ignore.
- **ما الذي يمكنك إنجازه أو حسمه بهذه الأداة (AR)**: توجيه جهود تحسين الظهور في محركات الذكاء الاصطناعي (`ChatGPT / Gemini / Perplexity`) نحو العوامل الفعالة فعلياً (الفهرسة في جوجل وبنج، البيانات المهيكلة `JSON-LD`، والجداول المقارنة المباشرة) بدلاً من الاعتماد الوهمي على ملف `llms.txt`.
- **Why `DECISION_AID` Fits This User Job (EN)**: VOCTOS's Oct 2026 empirical study of Arab markets proved that (a) no major AI search engine verifies using `llms.txt` and server logs show AI bots ignore it, and (b) 96.9% of measured AI search referral clicks in studied Saudi properties arrive via Google `Organic Search` (`AI Overviews` / `AI Mode`); a DECISION_AID focuses engineering and content teams on what actually drives AI citations.
- **لماذا يناسب شكل `DECISION_AID` هذه المهمة (AR)**: أثبتت الدراسة الميدانية لـ VOCTOS (أكتوبر 2026) أن محركات البحث بالذكاء الاصطناعي تتجاهل ملف `llms.txt` في سجلات السيرفر، وأن 96.9% من نقرات بحث الذكاء الاصطناعي المرصودة في المواقع السعودية تأتي عبر `Organic Search` في جوجل (`AI Overviews / AI Mode`)؛ لذا ترتب أداة القرار هذه الأولويات الحقيقية.

## 2. "Use It When" Trigger, Boundaries & Exact Inputs to Prepare

- **Use It When (EN)**: Use when executives or agencies ask 'How do we rank in ChatGPT, Gemini, Perplexity, and Google AI Overviews in Saudi Arabia, UAE, and Egypt?' or pitch expensive `llms.txt` packages.
- **متى تستخدم هذه الأداة (AR)**: تُستخدم عندما يطلب فريق الإدارة أو الوكالة خطة للظهور في إجابات `ChatGPT` و`Gemini` و`Perplexity` و`Google AI Overviews` في أسواق المنطقة.
- **When NOT to Use It (EN)**: Do not pay vendors promising 'Guaranteed #1 ChatGPT ranking in 48 hours via `llms.txt`' (`AMP-561`).
- **متى لا تستخدم هذه الأداة (AR)**: لا تدفع لأي جهة تدعي «ضمان المركز الأول في ChatGPT خلال 48 ساعة عبر تركيب ملف `llms.txt`» (`AMP-561`).

### Exact Inputs to Prepare Before Starting (`المدخلات المطلوب تجهيزها`)
1. Current Google Search Console & Bing Webmaster Tools indexation status (`AMP-003`, `AMP-006`)
2. Site `robots.txt` AI crawler permissions (`OAI-SearchBot`, `Googlebot`, `PerplexityBot`)
3. Top 20 commercial comparison & pricing questions customers ask before buying

### Privacy-Safe Data Handling (`ضوابط الخصوصية وحماية البيانات الشخصية PDPL`)
- **Strict PII Redaction Before Prompting**: Under Saudi PDPL (Art. 25), UAE Federal Decree-Law No. 45 of 2021, Qatar Law No. 13 of 2016, and Egypt Law No. 151 of 2020, **never paste raw customer names, unhashed mobile numbers (`+9665...` / `+201...`), email addresses, national IDs, or private WhatsApp transcripts into public/consumer LLM interfaces**. Use anonymized placeholders (`{first_name}`, `ORD_10045`) during prompt testing and restrict live customer data to zero-data-retention enterprise API endpoints or local deterministic scripts.

## 3. The Directly Usable Artifact (`الأداة التطبيقية الجاهزة للنسخ والتنفيذ`)

### MENA AI Search (AEO / GEO) Priority Matrix (Empirical Reality vs. Hype)

| Proposed Action | Empirical Status (Verified Oct 2026) | Priority & ROI | Mandatory Implementation Rule |
| :--- | :--- | :--- | :--- |
| **1. Clean Google & Bing Organic Indexation (`200 OK` Sitemap, Self-Canonicals, Bing Webmaster Sync)** | **CRITICAL (`#1 Driver`)** — `96.9%` of measured AI search clicks in VOCTOS's Saudi study came through Google `AI Overviews` / `AI Mode` (`Organic Search`), while ChatGPT Search relies on Bing + `OAI-SearchBot`. | **P0 (Must Have)** | Fix broken sitemaps (`AMP-003`), `/en/` canonicals (`AMP-004`), and submit sitemaps to both GSC and Bing Webmaster Tools (`AMP-006`). |
| **2. Answer-First Bilingual Comparison Tables & Verbatim Fact Blocks** | **HIGH IMPACT** — RAG/grounding pipelines extract concise HTML `<table>` rows and 40–60 word direct answers placed immediately under question-phrased `<h2>`/`<h3>` headings. | **P1 (High ROI)** | Place a 45-word direct Arabic answer + structured Markdown/HTML spec & pricing table (`SAR`/`AED`/`EGP`, VAT, warranty, delivery SLA) at the top of commercial guides. |
| **3. Complete Entity JSON-LD (`Product`, `Organization`, `LocalBusiness`, `FAQPage`)** | **HIGH IMPACT** — Disambiguates brand name (Arabic + English `sameAs`), price currency, and stock status for search knowledge graphs. | **P1 (High ROI)** | Include `"brand"` (`AMP-007`), `alternateName` (both Arabic & English brand names), and official social/CR links in `Organization` & `Product` schema. |
| **4. Server-Side HTML Rendering (No Client-Only JS Text)** | **CRITICAL FOR AI BOTS** — Many AI retrieval bots (`OAI-SearchBot`, `ClaudeBot`, `PerplexityBot`) do not execute heavy client-side SPAs as deeply as Googlebot. | **P1 (High ROI)** | Ensure core Arabic/English product descriptions, prices, and FAQs are present in the initial server-rendered HTML response. |
| **5. Publishing `/llms.txt`** | **UNVERIFIED / IGNORED BY BOTS** — No major AI search platform documents using `llms.txt`; VOCTOS 2026 server-log audits confirm AI crawlers ignore it. | **P4 (Negligible / Do Not Rely On)** | Never treat `llms.txt` as an SEO/AEO strategy or pay vendors for it; spend 100% of effort on P0–P1 above. |

## 4. Model & Platform Capability Branches (`فروع قدرات النماذج والمنصات والبدائل الاحتياطية`)

| System / Platform | Capability Status | Official Documentation & Access Date | Operational Constraint in Egypt & GCC | Fallback When Feature/Modality Is Unavailable |
| :--- | :--- | :--- | :--- | :--- |
| **Google AI Overviews / AI Mode & ChatGPT Search / Perplexity Grounding Mechanics** | `supported` | [Official Reference](https://voctos.net/ga4-ai-traffic-arab-markets/) (`2026-10-25`) | VOCTOS Oct 2026 study confirmed 96.9% of measured AI search citations in studied Saudi sites route through Google Search (AI Overviews / AI Mode) and that `llms.txt` is ignored by crawlers. | Prioritize Google/Bing indexation, server-rendered HTML tables, and JSON-LD entity markup. |

## 5. Consolidated Regional & Vertical Adaptation Matrix (`دمج الأنماط السياقية الفرعية بدون حشو`)

Per Agent 2 v1.2's anti-padding rule, the following **5 cross-verified contextual synthesis patterns** and **1 screened duplicate variants** share this core mechanism and are consolidated directly into this source-of-truth framework:

| Child Pattern ID | Disposition | Regional / Sector Operating Context | Specific Adaptation & Guardrail Integrated in This Asset | Evidence Tier |
| :--- | :--- | :--- | :--- | :--- |
| **`AMP-190`** | `MERGE_INTO_EXISTING` | Egyptian E-Commerce & Social Commerce (Shopify / WooCommerce / Cairo & Alexandria) | Focusing on crawlable HTML, self-canonical pages, schema markup, and direct question-answer headings.; Specifically impacts Egyptian brands operating in EGP where merchant-specific payment mix from recent order records, Mobile Wallets (Vodafone Cash), InstaPay, and Fawry dominate. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-200`** | `MERGE_INTO_EXISTING` | UAE & Multi-Market GCC Enterprise / Retail (Dubai, Abu Dhabi, Doha, Kuwait) | Focusing on crawlable HTML, self-canonical pages, schema markup, and direct question-answer headings.; Specifically impacts bilingual Arabic/English campaigns in high-CPM, expat-dense Gulf markets under UAE PDPL / TDRA and Qatari regulations. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-210`** | `MERGE_INTO_EXISTING` | High-Trust & Regulated Verticals (Healthcare/SFDA/EDA, Fintech/SAMA/FRA, Real Estate) | Focusing on crawlable HTML, self-canonical pages, schema markup, and direct question-answer headings.; Specifically impacts regulated claims requiring SFDA, EDA, MOH, SAMA, FRA, or RERA compliance pre-clearance and strict hallucination guardrails. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-220`** | `MERGE_INTO_EXISTING` | Seasonal Peak Operations (Ramadan, Eid, White/Yellow Friday, Saudi Founding/National Day) | Focusing on crawlable HTML, self-canonical pages, schema markup, and direct question-answer headings.; Specifically impacts high-velocity seasonal surges where CPMs jump 40-70%, prices change rapidly, and Hijri calendar cultural sensitivity is paramount. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-230`** | `MERGE_INTO_EXISTING` | Multi-Client Agency & MarTech API Automation Pipelines (LLM APIs, Webhooks, GA4, CAPI) | Focusing on crawlable HTML, self-canonical pages, schema markup, and direct question-answer headings.; Specifically impacts automated multi-SKU or multi-client LLM/API pipelines where schema validation, token cost, and attribution governance are required. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-520`** | `REJECT_DUPLICATE` | Screened UI/Format Synonym (`Merged Variant: Minor UI/Format Synonym of AMP-210 (Content Marketing)`) | Consolidated into parent workflow without duplicate file inflation. | `SCREENED_DUPLICATE_VARIANT` |

### Context-Specific Execution Knobs Across the 5 MENA Operating Environments
1. **Saudi D2C E-Commerce (`Salla / Zid / Riyadh & Jeddah Retail`)**: Enforce `SAR` tax-inclusive pricing (`15% ZATCA VAT`), native `Mada / Apple Pay / Tabby / Tamara` visibility (`AMP-387`), `GAMR Mawthooq` creator verification (`AMP-281`), and White Saudi Khaleeji orthography (`AMP-002`, `AMP-177`).
2. **Egyptian E-Commerce & Social Commerce (`Shopify / WooCommerce / Cairo & Alexandria`)**: Use each merchant’s own order and payment data to assess Cash on Delivery (`COD`), mobile wallets, InstaPay, Fawry, `valU`, address fields, and pre-dispatch WhatsApp confirmation. Verify current provider terms and local requirements before implementation.
3. **UAE & Multi-Market GCC Enterprise / Retail (`Dubai, Abu Dhabi, Doha, Kuwait`)**: Separate high-CPM UAE/Qatar budgets from lower-CPM markets (`AMP-061`), enforce UAE `TDRA` `9 PM – 7 AM` SMS curfew + `AD-` prefix (`AMP-442`), UAE Media Council permits (`AMP-282`), and bilingual Arabic/English canonical & currency parity (`current applicable UAE VAT`, `current applicable Qatar/Kuwait tax rules`, 3-decimal `KWD` `AMP-239`).
4. **High-Trust & Regulated Verticals (`Healthcare SFDA/MOH/EDA, FinTech SAMA/FRA, Real Estate REGA/RERA`)**: Strip all therapeutic/cure verbs (`AMP-176`, `AMP-286`), display mandatory `MOH/SFDA/DHA/EDA/Fal/Trakheesi` permit numbers (`AMP-070`), and route budgets to high-credibility channels (`AMP-290`, `AMP-339`).
5. **Seasonal Peak Operations (`Ramadan, Eid, White/Yellow Friday, Saudi Founding/National Day`)**: Lock Hijri-Gregorian overlaps (`Feb 2027 Ramadan x Saudi Founding Day x Kuwait National Day` `AMP-125`), pre-schedule GMC `sale_price_effective_date` 48h ahead (`AMP-063`), verify 30-day baseline discount permits (`AMP-064`), and disable Meta Advantage+ auto-music (`AMP-065`).

## 6. Worked Example Summary & Failure Recovery (`ملخص المثال التطبيقي وخطة الإنقاذ`)

*(Full step-by-step worked example with annotated human edits is also provided in `EXAMPLE.md`)*

- **Sample Input Brief**: - **Client**: Riyadh & Dubai B2B Cloud HR & Payroll SaaS Platform (targeting Saudi Labor Law / GOSI / WPS compliance queries).
- **Vendor Pitch Received**: A vendor quoted `$8,000` to 'install `llms.txt` and optimize AI metadata for guaranteed ChatGPT #1 citations'.
- **Human Review & Key Edits Applied**: 1. **Added Bilingual Entity Disambiguation**: Added `"name": "Jisr HR"`, `"alternateName": "جسر للموارد البشرية"` in `Organization` and `SoftwareApplication` JSON-LD so Arabic and English queries resolve to the same entity.
2. **Paired with GA4 AI Traffic Tracking (`AMP-443`)**: Configured GA4 custom exploration and Search Console cross-referencing to measure actual AI referral and AI Overview organic clicks.
- **Final Usable Output**: - Saved `$8,000` on unverified `llms.txt` tooling and deployed 10 server-rendered, schema-backed bilingual comparison hubs indexed in both Google and Bing.
- **What Can Go Wrong**: A site blocks `Bingbot` or renders all product pricing inside a client-side React modal requiring a click; the brand disappears completely from ChatGPT Search and Perplexity product comparisons even though it uploaded an `llms.txt` file.
- **Correction & Fallback**: Verify with `curl -sL https://your-url` that product names, Arabic/English brand names, prices (`SAR/AED/EGP`), and comparison tables exist in raw server HTML and that `Googlebot`, `Bingbot`, and `OAI-SearchBot` receive `200 OK`.

## 7. Measurement Plan & Hypothesis Framing (`خطة القياس والضوابط الإحصائية`)

- **Primary Metric to Track**: Organic impressions/clicks on question & comparison queries in Google Search Console + Bing Webmaster Tools, plus tracked AI referral sessions (`AMP-443`).
- **Baseline Definition**: 30-day pre-implementation organic query and referral baseline.
- **Observation Window**: 28–45 days post-indexing. *(Must span full 7/14-day weekly cycles and account for 25th–30th monthly salary windows per `AMP-391`)*.
- **What Cannot Be Concluded (Boundary)**: Probabilistic LLM answers vary by user prompt and session; never promise 'Guaranteed #1 AI ranking' (`AMP-561`).
