# FW-036: Vision 2030, GASTAT, CAPMAS & Central Bank Citation Grounding Workflow (Anti-Hallucination)
## مسار عمل توثيق إحصاءات رؤية 2030 والهيئة العامة للإحصاء (`GASTAT`) والجهاز المركزي (`CAPMAS`) ومنع هلوسة الأرقام

- **Consolidated Contextual Child IDs (`MERGE_INTO_EXISTING`)**: `AMP-189`, `AMP-199`, `AMP-209`, `AMP-219`, `AMP-229`
- **Selected Artifact Type**: `OPERATING_FRAMEWORK`
- **Intended Audience**: Content Manager, Arabic Copywriter, Editorial Lead, Compliance Reviewer
- **Target Markets & Languages**: Egypt & GCC (`Saudi Arabia, UAE, Kuwait, Qatar, Bahrain, Oman`) — Bilingual Arabic (`Egyptian Ammiya`, `Saudi/Gulf Khaleeji`, `White MSA`) + English
- **Version**: `1.2` | **Last Reviewed**: `2026-10-25` | **Status**: `READY_FOR_REVIEW`

## 1. Plain-Language Promise & Why This Artifact Form Fits the Job

- **What You Can Make or Decide (EN)**: Prevent LLMs from fabricating fake percentages attributed to Saudi Vision 2030, GASTAT, SAMA, CST, UAE FCSC, or Egypt CAPMAS/CBE by enforcing quote-first retrieval and an explicit `'UNVERIFIED_STAT'` abstain gate.
- **ما الذي يمكنك إنجازه أو حسمه بهذه الأداة (AR)**: منع النماذج اللغوية من اختلاق نسب مئوية وإحصاءات وهمية ونسبتها زوراً لرؤية السعودية 2030 أو الهيئة العامة للإحصاء (`GASTAT`) أو البنك المركزي أو الجهاز المركزي للتعبئة العامة والإحصاء (`CAPMAS`).
- **Why `OPERATING_FRAMEWORK` Fits This User Job (EN)**: When writers ask an LLM for 'a statistic about Saudi e-commerce growth under Vision 2030 or Egyptian fintech adoption', the model fabricates plausible percentages (`'84.3% according to GASTAT 2026'`) unless constrained by Anthropic/OpenAI's quote-first grounding workflow; an OPERATING_FRAMEWORK enforces verbatim source extraction first.
- **لماذا يناسب شكل `OPERATING_FRAMEWORK` هذه المهمة (AR)**: عند مطالبة النموذج اللغوي بإحصائية عن نمو التجارة الإلكترونية في السعودية أو مصر دون إرفاق التقرير الرسمي، يختلق النموذج نسباً مئوية دقيقة وينسبها لجهات حكومية؛ لذا يلزم هذا الإطار التشغيلي بالاقتباس الحرفي المسبق من المصدر الموثق.

## 2. "Use It When" Trigger, Boundaries & Exact Inputs to Prepare

- **Use It When (EN)**: Use when drafting B2B whitepapers, investor/board decks, PR press releases, LinkedIn thought leadership, or SEO authority articles citing MENA economic/market statistics.
- **متى تستخدم هذه الأداة (AR)**: تُستخدم عند كتابة التقارير، العروض التقديمية، البيانات الصحفية، أو المقالات المتخصصة التي تستشهد بإحصاءات اقتصادية أو حكومية في السعودية والإمارات ومصر.
- **When NOT to Use It (EN)**: Never allow an LLM to generate a statistic from its internal weights without a verified URL/PDF excerpt attached in the context window.
- **متى لا تستخدم هذه الأداة (AR)**: لا تسمح أبداً للنموذج اللغوي بإيراد أي رقم إحصائي من ذاكرته الداخلية دون وجود النص الأصلي للتقرير أو رابطه الموثق داخل سياق المحادثة.

### Exact Inputs to Prepare Before Starting (`المدخلات المطلوب تجهيزها`)
1. Verified Primary Source Excerpts or PDFs (e.g., official GASTAT, SAMA, CST, Vision 2030 Annual Report, CAPMAS, CBE, DataReportal, or VOCTOS/23HubLab study text)
2. Topic & Target Audience of the article or whitepaper

### Privacy-Safe Data Handling (`ضوابط الخصوصية وحماية البيانات الشخصية PDPL`)
- **Strict PII Redaction Before Prompting**: Under Saudi PDPL (Art. 25), UAE Federal Decree-Law No. 45 of 2021, Qatar Law No. 13 of 2016, and Egypt Law No. 151 of 2020, **never paste raw customer names, unhashed mobile numbers (`+9665...` / `+201...`), email addresses, national IDs, or private WhatsApp transcripts into public/consumer LLM interfaces**. Use anonymized placeholders (`{first_name}`, `ORD_10045`) during prompt testing and restrict live customer data to zero-data-retention enterprise API endpoints or local deterministic scripts.

## 3. The Directly Usable Artifact (`الأداة التطبيقية الجاهزة للنسخ والتنفيذ`)

### 3-Step Quote-First Statistical Grounding Workflow (Anthropic Guardrail Standard)

#### Step 1: Enforce the Quote-First + Abstain Prompt Architecture
Per Anthropic's official hallucination-reduction documentation (`https://platform.claude.com/docs/en/test-and-evaluate/strengthen-guardrails/reduce-hallucinations`), force the model to extract verbatim `<verified_quotes>` **before** drafting prose, and explicitly authorize it to output `[STAT_NEEDED: No verified figure in supplied sources]` rather than guessing:

```xml
<system_role>
You are an Evidence-Grounded MENA Research Writer.
ABSOLUTE ANTI-HALLUCINATION RULE:
1. You may ONLY cite numbers, percentages, dates, and institutional names (Vision 2030, GASTAT, SAMA, CST, Monsha'at, UAE Ministry of Economy, CAPMAS, Central Bank of Egypt) that appear VERBATIM inside <supplied_evidence_pack>.
2. Do NOT use your internal pre-training memory to fill in any statistic, CAGR, or survey percentage.
3. If a paragraph would benefit from a statistic that is NOT present in <supplied_evidence_pack>, write qualitative prose OR insert the exact placeholder `[STAT_NEEDED: Verify directly from official GASTAT/CAPMAS portal]`—NEVER invent a number.
</system_role>

<supplied_evidence_pack>
{{PASTE_VERIFIED_SOURCE_EXCERPTS_AND_URLS_HERE}}
</supplied_evidence_pack>

<execution_steps>
Step 1: Output a `<verbatim_evidence_extractions>` block listing each exact number, its verbatim quote from <supplied_evidence_pack>, publication date, and source URL.
Step 2: Draft the Arabic/English article using ONLY the numbers extracted in Step 1, linking each claim inline to its exact source URL.
</execution_steps>
```

#### Step 2: Mandatory Pre-Publish Fact-Table Verification
- [ ] Every numeric claim (`%`, `SAR`, `AED`, `EGP`, `Million`) in the draft maps 1:1 to a row in `<verbatim_evidence_extractions>`.
- [ ] Any figure lacking a direct clickable URL or attached PDF page number is deleted or rephrased qualitatively before publication.

## 4. Model & Platform Capability Branches (`فروع قدرات النماذج والمنصات والبدائل الاحتياطية`)

| System / Platform | Capability Status | Official Documentation & Access Date | Operational Constraint in Egypt & GCC | Fallback When Feature/Modality Is Unavailable |
| :--- | :--- | :--- | :--- | :--- |
| **Anthropic Claude / OpenAI GPT-4o Quote-First Grounding & Abstention** | `supported` | [Official Reference](https://platform.claude.com/docs/en/test-and-evaluate/strengthen-guardrails/reduce-hallucinations) (`2026-10-25`) | Explicitly instructing the model to extract verbatim quotes before drafting and permitting 'I don't know / Not in supplied sources' drastically reduces fabricated citations. | Strip any numeric claim that cannot be traced to a line in the supplied evidence pack. |

## 5. Consolidated Regional & Vertical Adaptation Matrix (`دمج الأنماط السياقية الفرعية بدون حشو`)

Per Agent 2 v1.2's anti-padding rule, the following **5 cross-verified contextual synthesis patterns** and **1 screened duplicate variants** share this core mechanism and are consolidated directly into this source-of-truth framework:

| Child Pattern ID | Disposition | Regional / Sector Operating Context | Specific Adaptation & Guardrail Integrated in This Asset | Evidence Tier |
| :--- | :--- | :--- | :--- | :--- |
| **`AMP-189`** | `MERGE_INTO_EXISTING` | Egyptian E-Commerce & Social Commerce (Shopify / WooCommerce / Cairo & Alexandria) | Quote-first RAG/grounding workflows (per Anthropic hallucination guidelines) where every figure must link to an attached official PDF/URL.; Specifically impacts Egyptian brands operating in EGP where Cash on Delivery (merchant-measured payment mix from recent order records), Mobile Wallets (Vodafone Cash), InstaPay, and Fawry dominate. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-199`** | `MERGE_INTO_EXISTING` | UAE & Multi-Market GCC Enterprise / Retail (Dubai, Abu Dhabi, Doha, Kuwait) | Quote-first RAG/grounding workflows (per Anthropic hallucination guidelines) where every figure must link to an attached official PDF/URL.; Specifically impacts bilingual Arabic/English campaigns in high-CPM, expat-dense Gulf markets under UAE PDPL / TDRA and Qatari regulations. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-209`** | `MERGE_INTO_EXISTING` | High-Trust & Regulated Verticals (Healthcare/SFDA/EDA, Fintech/SAMA/FRA, Real Estate) | Quote-first RAG/grounding workflows (per Anthropic hallucination guidelines) where every figure must link to an attached official PDF/URL.; Specifically impacts regulated claims requiring SFDA, EDA, MOH, SAMA, FRA, or RERA compliance pre-clearance and strict hallucination guardrails. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-219`** | `MERGE_INTO_EXISTING` | Seasonal Peak Operations (Ramadan, Eid, White/Yellow Friday, Saudi Founding/National Day) | Quote-first RAG/grounding workflows (per Anthropic hallucination guidelines) where every figure must link to an attached official PDF/URL.; Specifically impacts high-velocity seasonal surges where CPMs jump 40-70%, prices change rapidly, and Hijri calendar cultural sensitivity is paramount. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-229`** | `MERGE_INTO_EXISTING` | Multi-Client Agency & MarTech API Automation Pipelines (LLM APIs, Webhooks, GA4, CAPI) | Quote-first RAG/grounding workflows (per Anthropic hallucination guidelines) where every figure must link to an attached official PDF/URL.; Specifically impacts automated multi-SKU or multi-client LLM/API pipelines where schema validation, token cost, and attribution governance are required. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-519`** | `REJECT_DUPLICATE` | Screened UI/Format Synonym (`Merged Variant: Minor UI/Format Synonym of AMP-199 (Content Marketing)`) | Consolidated into parent workflow without duplicate file inflation. | `SCREENED_DUPLICATE_VARIANT` |

### Context-Specific Execution Knobs Across the 5 MENA Operating Environments
1. **Saudi D2C E-Commerce (`Salla / Zid / Riyadh & Jeddah Retail`)**: Enforce `SAR` tax-inclusive pricing (`15% ZATCA VAT`), native `Mada / Apple Pay / Tabby / Tamara` visibility (`AMP-387`), `GAMR Mawthooq` creator verification (`AMP-281`), and White Saudi Khaleeji orthography (`AMP-002`, `AMP-177`).
2. **Egyptian E-Commerce & Social Commerce (`Shopify / WooCommerce / Cairo & Alexandria`)**: Use each merchant’s own order and payment data to assess Cash on Delivery (`COD`), mobile wallets, InstaPay, Fawry, `valU`, address fields, and pre-dispatch WhatsApp confirmation. Verify current provider terms and local requirements before implementation.
3. **UAE & Multi-Market GCC Enterprise / Retail (`Dubai, Abu Dhabi, Doha, Kuwait`)**: Separate high-CPM UAE/Qatar budgets from lower-CPM markets (`AMP-061`), enforce UAE `TDRA` `9 PM – 7 AM` SMS curfew + `AD-` prefix (`AMP-442`), UAE Media Council permits (`AMP-282`), and bilingual Arabic/English canonical & currency parity (`current applicable UAE VAT`, `current applicable Qatar/Kuwait tax rules`, 3-decimal `KWD` `AMP-239`).
4. **High-Trust & Regulated Verticals (`Healthcare SFDA/MOH/EDA, FinTech SAMA/FRA, Real Estate REGA/RERA`)**: Strip all therapeutic/cure verbs (`AMP-176`, `AMP-286`), display mandatory `MOH/SFDA/DHA/EDA/Fal/Trakheesi` permit numbers (`AMP-070`), and route budgets to high-credibility channels (`AMP-290`, `AMP-339`).
5. **Seasonal Peak Operations (`Ramadan, Eid, White/Yellow Friday, Saudi Founding/National Day`)**: Lock Hijri-Gregorian overlaps (`Feb 2027 Ramadan x Saudi Founding Day x Kuwait National Day` `AMP-125`), pre-schedule GMC `sale_price_effective_date` 48h ahead (`AMP-063`), verify 30-day baseline discount permits (`AMP-064`), and disable Meta Advantage+ auto-music (`AMP-065`).

## 6. Worked Example Summary & Failure Recovery (`ملخص المثال التطبيقي وخطة الإنقاذ`)

*(Full step-by-step worked example with annotated human edits is also provided in `EXAMPLE.md`)*

- **Sample Input Brief**: - **Task**: Write an executive LinkedIn & Blog introduction on E-Commerce Payment & BNPL Adoption in Saudi Arabia, UAE, and Egypt.
- **Supplied Evidence Pack**:
  1. `SRC-083` (Digitology 2026 Egypt Payment Benchmark): Use the merchant’s recent order records to estimate payment mix.
  2. `SRC-082` (Huptech 2026 UAE/KSA BNPL Study): BNPL (Tabby/Tamara) accounts for `~14%` of UAE Shopify checkout volume.
  3. **Missing Data**: Exact Q3 2026 SAMA Mada transaction growth rate (not in supplied pack).
- **Human Review & Key Edits Applied**: 1. **Verified Abstention**: Confirmed the model did NOT fabricate a SAMA percentage and instead wrote `"مع الانتشار الواسع لبطاقات مدى والمدفوعات الرقمية في المملكة"` while citing the verified `~14%` BNPL figure and `merchant-measured payment mix from recent order records` Egypt COD figure with exact links.
2. **Checked Date Attribution**: Preserved the `2026` benchmark year and publisher attribution inline.
- **Final Usable Output**: - Published bilingual industry brief with `100%` source-verified statistics and `0` fabricated Vision 2030 / GASTAT / CAPMAS citations.
- **What Can Go Wrong**: A copywriter prompts ChatGPT `'Write an article about real estate growth in Riyadh with 5 statistics from GASTAT and Knight Frank'`; ChatGPT invents 5 realistic-looking percentages and fake report titles that embarrass the brokerage when a client asks for the link.
- **Correction & Fallback**: Never prompt an LLM to `'find or include X statistics'` without either (a) running live web search + browsing the primary page first, or (b) pasting the verified source excerpts into `<supplied_evidence_pack>`.

## 7. Measurement Plan & Hypothesis Framing (`خطة القياس والضوابط الإحصائية`)

- **Primary Metric to Track**: Citation Verification Rate (`100%` of published numbers traced to a primary URL/PDF) and `0` post-publication factual retractions.
- **Baseline Definition**: Audit of unverified statistics in prior blog/social drafts.
- **Observation Window**: Enforced on 100% of published content. *(Must span full 7/14-day weekly cycles and account for 25th–30th monthly salary windows per `AMP-391`)*.
- **What Cannot Be Concluded (Boundary)**: Verified statistics build executive credibility and AEO citation trust (`AMP-180`), while distribution and SEO structure drive reach.
