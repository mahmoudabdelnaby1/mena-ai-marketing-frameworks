# FW-013: MENA Cross-Market Budget Isolation Decision Aid (Preventing the 4–5x Egypt vs. GCC CPM Arbitrage Trap)
## أداة قرار فصل الميزانيات الإعلانية بين مصر والخليج (منع فخ التهام الميزانية بسبب فارق الـ CPM البالغ 4–5 أضعاف)

- **Consolidated Contextual Child IDs (`MERGE_INTO_EXISTING`)**: `AMP-071`, `AMP-081`, `AMP-091`, `AMP-101`, `AMP-111`
- **Selected Artifact Type**: `DECISION_AID`
- **Intended Audience**: Performance Marketing Manager, Media Buyer, PPC Specialist, Growth Lead
- **Target Markets & Languages**: Egypt & GCC (`Saudi Arabia, UAE, Kuwait, Qatar, Bahrain, Oman`) — Bilingual Arabic (`Egyptian Ammiya`, `Saudi/Gulf Khaleeji`, `White MSA`) + English
- **Version**: `1.2` | **Last Reviewed**: `2026-10-25` | **Status**: `READY_FOR_REVIEW`

## 1. Plain-Language Promise & Why This Artifact Form Fits the Job

- **What You Can Make or Decide (EN)**: Structure Meta Advantage+ and Google PMax campaign budgets by CPM/AOV tier so automated bidding does not dump 85%+ of regional spend into the lowest-CPM country while starving high-AOV GCC buyers.
- **ما الذي يمكنك إنجازه أو حسمه بهذه الأداة (AR)**: هيكلة ميزانيات حملات Meta Advantage+ وGoogle PMax حسب شريحة تكلفة الظهور (CPM) ومتوسط سلة الشراء (AOV) لمنع الخوارزمية من ضخ 85%+ من الميزانية في السوق الأرخص وحرمان أسواق الخليج ذات العائد المرتفع.
- **Why `DECISION_AID` Fits This User Job (EN)**: Campaign budget pooling across countries with a 4–5x CPM gap is a structural media-buying architecture decision; a quantitative DECISION_AID with CPM/AOV isolation tiers and budget allocation formulas prevents algorithmic spend starvation.
- **لماذا يناسب شكل `DECISION_AID` هذه المهمة (AR)**: دمج ميزانيات دول تتفاوت فيها تكلفة الألف ظهور (CPM) بمقدار 4 إلى 5 أضعاف هو خطأ هيكلي في إعداد الحملات؛ وتوفر أداة القرار هذه معادلة فصل الميزانيات وتوزيعها بدقة.

## 2. "Use It When" Trigger, Boundaries & Exact Inputs to Prepare

- **Use It When (EN)**: Use whenever launching Meta Advantage+ Shopping/App/Leads, Google Performance Max, TikTok Smart+, or Snapchat campaigns across 2 or more MENA countries (e.g., UAE + KSA + Egypt).
- **متى تستخدم هذه الأداة (AR)**: تُستخدم عند إطلاق حملات Meta Advantage+ أو Google PMax أو TikTok أو Snapchat تستهدف أكثر من دولة عربية (مثل الإمارات والسعودية ومصر معاً).
- **When NOT to Use It (EN)**: Do not split cities within the same country into micro-budgets if total daily spend cannot support ~50 conversions/week per campaign—isolate by country/CPM tier first.
- **متى لا تستخدم هذه الأداة (AR)**: لا تقم بتفتيت الميزانية الصغيرة جداً بين عشرات المدن داخل الدولة الواحدة إذا لم تكفِ لتحقيق 50 تحويلاً أسبوعياً؛ افصل أولاً على مستوى الدول/شرائح الـ CPM.

### Exact Inputs to Prepare Before Starting (`المدخلات المطلوب تجهيزها`)
1. Target countries and historical CPM / CPC / CPA benchmarks per country
2. Net Delivered Average Order Value (AOV) and Gross Margin per country (accounting for COD return rate in Egypt/KSA)
3. Total monthly media budget and minimum conversion volume threshold (50 conversions/week per campaign)

### Privacy-Safe Data Handling (`ضوابط الخصوصية وحماية البيانات الشخصية PDPL`)
- **Strict PII Redaction Before Prompting**: Under Saudi PDPL (Art. 25), UAE Federal Decree-Law No. 45 of 2021, Qatar Law No. 13 of 2016, and Egypt Law No. 151 of 2020, **never paste raw customer names, unhashed mobile numbers (`+9665...` / `+201...`), email addresses, national IDs, or private WhatsApp transcripts into public/consumer LLM interfaces**. Use anonymized placeholders (`{first_name}`, `ORD_10045`) during prompt testing and restrict live customer data to zero-data-retention enterprise API endpoints or local deterministic scripts.

## 3. The Directly Usable Artifact (`الأداة التطبيقية الجاهزة للنسخ والتنفيذ`)

### MENA Multi-Country Campaign Isolation Matrix & Budget Calculator

#### 1. Empirical Cost & Auction Asymmetry Table (23HubLab 2026 MENA Benchmarks)
| Tier | Markets Included | Relative Meta/Google CPM & CPC Index | Dominant Payment & Margin Profile | Mandatory Campaign Architecture Rule |
| :--- | :--- | :--- | :--- | :--- |
| **Tier 1 (High CPM / High AOV)** | **UAE & Qatar** | **1.00x (Baseline Highest — 4x to 5x Egypt CPM)** | High card/Apple Pay/Tabby share; low COD return rate; English + Gulf Arabic | **Dedicated Campaign / CBO Pool #1** (Never pool with Egypt, Levant, or North Africa). |
| **Tier 2 (Mid-High CPM / High Volume)** | **Saudi Arabia & Kuwait** | **0.60x – 0.80x of UAE CPM (3x to 4x Egypt CPM)** | Mada + Tabby/Tamara + COD; Arabic-first (Khaleeji) + Snapchat/TikTok/Meta | **Dedicated Campaign / CBO Pool #2** (Isolate KSA in its own budget whenever KSA spend `>= $100/day`). |
| **Tier 3 (Low CPM / High COD Volume)** | **Egypt** | **0.20x – 0.25x of UAE CPM (1/4th to 1/5th of UAE)** | merchant-measured payment mix from recent order records(`AMP-386`), 20–40% COD return/cancellation gap (`AMP-062`); EGP pricing | **Dedicated Campaign / CBO Pool #3** (Strictly isolated with COD-adjusted Value/tROAS bidding). |

#### 2. Decision Tree for Budget Allocation
1. **IF optimizing for Volume (`Maximize Conversions` or `Maximize Clicks`) across Tier 1/2 + Tier 3 in one campaign**:
   - **STOP IMMEDIATELY**: The algorithm will allocate `80–95%` of spend to Tier 3 (Egypt) because clicks and raw front-end leads cost `75–80%` less there. Split into separate campaigns by Tier before launching.
2. **IF total regional budget is `< $60/day` and cannot sustain 3 separate campaigns**:
   - **DO NOT pool**: Concentrate 100% of the budget into your single highest-margin target market until conversion volume reaches `>= 50/week`, then launch Market #2 in a separate campaign.
3. **IF running GCC-only (`UAE + KSA + Kuwait + Qatar`) under Value-Based Bidding (`tROAS`)**:
   - Only pool if all countries share the same currency feed conversion AND net delivered margin is passed back via CAPI/Offline Conversions (`AMP-062`); otherwise keep KSA and UAE in separate campaigns because dialect, creative (`AMP-121`), and VAT (`15%` vs `5%`) differ.

## 4. Model & Platform Capability Branches (`فروع قدرات النماذج والمنصات والبدائل الاحتياطية`)

| System / Platform | Capability Status | Official Documentation & Access Date | Operational Constraint in Egypt & GCC | Fallback When Feature/Modality Is Unavailable |
| :--- | :--- | :--- | :--- | :--- |
| **Meta Advantage+ Campaign Budget (CBO) & Google Performance Max Geo-Targeting** | `supported` | [Official Reference](https://23hublab.com/paid-media-cost-comparison-egypt-vs-uae-vs-saudi-arabia/) (`2026-10-25`) | 23HubLab 2026 benchmarks document a 4–5x CPM gap between UAE/KSA and Egypt; automated budget optimizers prioritize lowest-cost auctions when countries are pooled. | Separate campaigns by CPM/country tier at the campaign level. |

## 5. Consolidated Regional & Vertical Adaptation Matrix (`دمج الأنماط السياقية الفرعية بدون حشو`)

Per Agent 2 v1.2's anti-padding rule, the following **5 cross-verified contextual synthesis patterns** and **1 screened duplicate variants** share this core mechanism and are consolidated directly into this source-of-truth framework:

| Child Pattern ID | Disposition | Regional / Sector Operating Context | Specific Adaptation & Guardrail Integrated in This Asset | Evidence Tier |
| :--- | :--- | :--- | :--- | :--- |
| **`AMP-071`** | `MERGE_INTO_EXISTING` | Egyptian E-Commerce & Social Commerce (Shopify / WooCommerce / Cairo & Alexandria) | Strict single-country campaign/budget segmentation with market-specific CPA/ROAS targets.; Specifically impacts Egyptian brands operating in EGP where Cash on Delivery (merchant-measured payment mix from recent order records), Mobile Wallets (Vodafone Cash), InstaPay, and Fawry dominate. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-081`** | `MERGE_INTO_EXISTING` | UAE & Multi-Market GCC Enterprise / Retail (Dubai, Abu Dhabi, Doha, Kuwait) | Strict single-country campaign/budget segmentation with market-specific CPA/ROAS targets.; Specifically impacts bilingual Arabic/English campaigns in high-CPM, expat-dense Gulf markets under UAE PDPL / TDRA and Qatari regulations. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-091`** | `MERGE_INTO_EXISTING` | High-Trust & Regulated Verticals (Healthcare/SFDA/EDA, Fintech/SAMA/FRA, Real Estate) | Strict single-country campaign/budget segmentation with market-specific CPA/ROAS targets.; Specifically impacts regulated claims requiring SFDA, EDA, MOH, SAMA, FRA, or RERA compliance pre-clearance and strict hallucination guardrails. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-101`** | `MERGE_INTO_EXISTING` | Seasonal Peak Operations (Ramadan, Eid, White/Yellow Friday, Saudi Founding/National Day) | Strict single-country campaign/budget segmentation with market-specific CPA/ROAS targets.; Specifically impacts high-velocity seasonal surges where CPMs jump 40-70%, prices change rapidly, and Hijri calendar cultural sensitivity is paramount. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-111`** | `MERGE_INTO_EXISTING` | Multi-Client Agency & MarTech API Automation Pipelines (LLM APIs, Webhooks, GA4, CAPI) | Strict single-country campaign/budget segmentation with market-specific CPA/ROAS targets.; Specifically impacts automated multi-SKU or multi-client LLM/API pipelines where schema validation, token cost, and attribution governance are required. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-511`** | `REJECT_DUPLICATE` | Screened UI/Format Synonym (`Merged Variant: Minor UI/Format Synonym of AMP-111 (Pay-Per-Click (PPC) Advertising)`) | Consolidated into parent workflow without duplicate file inflation. | `SCREENED_DUPLICATE_VARIANT` |

### Context-Specific Execution Knobs Across the 5 MENA Operating Environments
1. **Saudi D2C E-Commerce (`Salla / Zid / Riyadh & Jeddah Retail`)**: Enforce `SAR` tax-inclusive pricing (`15% ZATCA VAT`), native `Mada / Apple Pay / Tabby / Tamara` visibility (`AMP-387`), `GAMR Mawthooq` creator verification (`AMP-281`), and White Saudi Khaleeji orthography (`AMP-002`, `AMP-177`).
2. **Egyptian E-Commerce & Social Commerce (`Shopify / WooCommerce / Cairo & Alexandria`)**: Use each merchant’s own order and payment data to assess Cash on Delivery (`COD`), mobile wallets, InstaPay, Fawry, `valU`, address fields, and pre-dispatch WhatsApp confirmation. Verify current provider terms and local requirements before implementation.
3. **UAE & Multi-Market GCC Enterprise / Retail (`Dubai, Abu Dhabi, Doha, Kuwait`)**: Separate high-CPM UAE/Qatar budgets from lower-CPM markets (`AMP-061`), enforce UAE `TDRA` `9 PM – 7 AM` SMS curfew + `AD-` prefix (`AMP-442`), UAE Media Council permits (`AMP-282`), and bilingual Arabic/English canonical & currency parity (`current applicable UAE VAT`, `current applicable Qatar/Kuwait tax rules`, 3-decimal `KWD` `AMP-239`).
4. **High-Trust & Regulated Verticals (`Healthcare SFDA/MOH/EDA, FinTech SAMA/FRA, Real Estate REGA/RERA`)**: Strip all therapeutic/cure verbs (`AMP-176`, `AMP-286`), display mandatory `MOH/SFDA/DHA/EDA/Fal/Trakheesi` permit numbers (`AMP-070`), and route budgets to high-credibility channels (`AMP-290`, `AMP-339`).
5. **Seasonal Peak Operations (`Ramadan, Eid, White/Yellow Friday, Saudi Founding/National Day`)**: Lock Hijri-Gregorian overlaps (`Feb 2027 Ramadan x Saudi Founding Day x Kuwait National Day` `AMP-125`), pre-schedule GMC `sale_price_effective_date` 48h ahead (`AMP-063`), verify 30-day baseline discount permits (`AMP-064`), and disable Meta Advantage+ auto-music (`AMP-065`).

## 6. Worked Example Summary & Failure Recovery (`ملخص المثال التطبيقي وخطة الإنقاذ`)

*(Full step-by-step worked example with annotated human edits is also provided in `EXAMPLE.md`)*

- **Sample Input Brief**: - **Advertiser**: Regional D2C Modest Fashion Brand shipping to UAE, Saudi Arabia, and Egypt.
- **Total Monthly Budget**: `$30,000/month` (`$1,000/day`).
- **Previous Mistake**: Ran 1 global Meta Advantage+ Shopping Campaign (`Maximize Conversions`) targeting `UAE + KSA + Egypt` together. Result: `88%` of budget (`$26,400`) was spent in Egypt (where AOV was `$28` with `32%` COD returns), while UAE (`$145` AOV) received only `3%` of spend.
- **Human Review & Key Edits Applied**: 1. **Catalog Feed Separation**: Linked each of the 3 campaigns to its country-specific catalog feed (`SAR`, `AED`, `EGP`) so dynamic product overlays never display `EGP` prices to Dubai shoppers or `AED` prices to Cairo shoppers.
2. **Ad Set Minimums Check**: Confirmed each isolated campaign generates `>65` conversions/week, clearing Meta's learning-phase threshold without cross-country cannibalization.
- **Final Usable Output**: - 3 Country-Isolated Campaigns live with locked daily caps (`KSA: $500/d`, `UAE: $300/d`, `EGY: $200/d`), localized currencies, and zero cross-border CPM arbitrage leakage.
- **What Can Go Wrong**: A media buyer separates Egypt and UAE into two Ad Sets inside the SAME Meta Campaign with Advantage+ Campaign Budget (`CBO`) turned ON; CBO still shifts 85% of the campaign budget into the Egypt Ad Set.
- **Correction & Fallback**: Enforce isolation at the **Campaign level** (or disable Campaign Budget Optimization and lock Ad Set daily budgets explicitly)—never rely on CBO across countries with >30% CPM divergence.

## 7. Measurement Plan & Hypothesis Framing (`خطة القياس والضوابط الإحصائية`)

- **Primary Metric to Track**: Spend share vs. Net Delivered Revenue share per country (`Net Delivered ROAS` / `MER` by country).
- **Baseline Definition**: Prior 14-day pooled campaign country spend breakdown.
- **Observation Window**: 14–21 days post-split (allowing 7 days for learning phase stabilization). *(Must span full 7/14-day weekly cycles and account for 25th–30th monthly salary windows per `AMP-391`)*.
- **What Cannot Be Concluded (Boundary)**: Budget isolation guarantees spend reaches high-AOV GCC auctions, but creative resonance and checkout UX (`AMP-386`/`AMP-387`) determine conversion rate.
