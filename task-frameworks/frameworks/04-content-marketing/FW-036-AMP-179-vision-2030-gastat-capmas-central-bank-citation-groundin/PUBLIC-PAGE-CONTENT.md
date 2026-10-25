# Vision 2030, GASTAT, CAPMAS & Central Bank Citation Grounding Workflow (Anti-Hallucination)
## <span dir="rtl">مسار عمل توثيق إحصاءات رؤية 2030 والهيئة العامة للإحصاء (`GASTAT`) والجهاز المركزي (`CAPMAS`) ومنع هلوسة الأرقام</span>

> **Asset ID**: `FW-036` (`AMP-179`) | **Artifact Type**: `OPERATING_FRAMEWORK` | **Channel**: Content Marketing | **Markets**: Egypt & GCC (`KSA, UAE, Kuwait, Qatar, Bahrain, Oman`) | **Version**: `1.2` (`Reviewed 2026-10-25`)

**What You Can Do With This (`ماذا يمكنك أن تنجز بهذه الأداة؟`)**:
- **EN**: Prevent LLMs from fabricating fake percentages attributed to Saudi Vision 2030, GASTAT, SAMA, CST, UAE FCSC, or Egypt CAPMAS/CBE by enforcing quote-first retrieval and an explicit `'UNVERIFIED_STAT'` abstain gate.
- **AR**: <span dir="rtl">منع النماذج اللغوية من اختلاق نسب مئوية وإحصاءات وهمية ونسبتها زوراً لرؤية السعودية 2030 أو الهيئة العامة للإحصاء (`GASTAT`) أو البنك المركزي أو الجهاز المركزي للتعبئة العامة والإحصاء (`CAPMAS`).</span>

## 1. Use It When & Required Inputs (`متى تستخدمها وما المدخلات المطلوبة؟`)

- **Use It When (EN)**: Use when drafting B2B whitepapers, investor/board decks, PR press releases, LinkedIn thought leadership, or SEO authority articles citing MENA economic/market statistics.
- **متى تستخدمها (AR)**: <span dir="rtl">تُستخدم عند كتابة التقارير، العروض التقديمية، البيانات الصحفية، أو المقالات المتخصصة التي تستشهد بإحصاءات اقتصادية أو حكومية في السعودية والإمارات ومصر.</span>
- **When NOT to Use It (EN)**: Never allow an LLM to generate a statistic from its internal weights without a verified URL/PDF excerpt attached in the context window.
- **متى لا تستخدمها (AR)**: <span dir="rtl">لا تسمح أبداً للنموذج اللغوي بإيراد أي رقم إحصائي من ذاكرته الداخلية دون وجود النص الأصلي للتقرير أو رابطه الموثق داخل سياق المحادثة.</span>

### Exact Inputs to Prepare (`المدخلات المطلوب تجهيزها قبل البدء`)
- Verified Primary Source Excerpts or PDFs (e.g., official GASTAT, SAMA, CST, Vision 2030 Annual Report, CAPMAS, CBE, DataReportal, or VOCTOS/23HubLab study text)
- Topic & Target Audience of the article or whitepaper

## 2. The Working `OPERATING_FRAMEWORK` (`الأداة الكاملة الجاهزة للنسخ والتطبيق الفوري`)

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

## 3. Complete End-to-End Worked Example (`مثال تطبيقي متكامل من المدخلات حتى المراجعة البشرية والنتيجة النهائية`)

*(Illustrative scenario — original example for training, never represented as a verified client outcome)*

### Step A: Sample Brief / Input (`موجز المدخلات`)
- **Task**: Write an executive LinkedIn & Blog introduction on E-Commerce Payment & BNPL Adoption in Saudi Arabia, UAE, and Egypt.
- **Supplied Evidence Pack**:
  1. `SRC-083` (Digitology 2026 Egypt Payment Benchmark): Use the merchant’s recent order records to estimate payment mix.
  2. `SRC-082` (Huptech 2026 UAE/KSA BNPL Study): BNPL (Tabby/Tamara) accounts for `~14%` of UAE Shopify checkout volume.
  3. **Missing Data**: Exact Q3 2026 SAMA Mada transaction growth rate (not in supplied pack).

### Step B: Initial Output (`المخرج الأولي`)
```xml
<verbatim_evidence_extractions>
1. Egypt Payment Split: "merchant-measured Cash on Delivery, merchant-measured mobile-wallet use, 10–20% Cards" — Source: Digitology (2026), https://digitology.co/payment-gateway-egypt/
2. UAE BNPL Share: "~14% of UAE checkout volume via Tabby and Tamara" — Source: Huptech (2026), https://www.huptechweb.com/blogs/tabby-vs-tamara-shopify-uae-bnpl-2026
3. SAMA Q3 2026 Mada Growth Rate: [ABSTAINED — Not present in <supplied_evidence_pack>; phrased qualitatively without inventing a percentage].
</verbatim_evidence_extractions>
```

### Step C: Human Review & Edits (`التدقيق البشري والتعديلات`)
1. **Verified Abstention**: Confirmed the model did NOT fabricate a SAMA percentage and instead wrote `"مع الانتشار الواسع لبطاقات مدى والمدفوعات الرقمية في المملكة"` while citing the verified `~14%` BNPL figure and `merchant-measured payment mix from recent order records` Egypt COD figure with exact links.
2. **Checked Date Attribution**: Preserved the `2026` benchmark year and publisher attribution inline.

### Step D: Final Reviewed Example Outcome (`النتيجة النهائية المعتمدة`)
- Published bilingual industry brief with `100%` source-verified statistics and `0` fabricated Vision 2030 / GASTAT / CAPMAS citations.

## 4. What Can Go Wrong & How to Fix It (`الأخطاء الشائعة وخطة الإنقاذ`)

- **Failure Case (`المشكلة المحتملة`)**: A copywriter prompts ChatGPT `'Write an article about real estate growth in Riyadh with 5 statistics from GASTAT and Knight Frank'`; ChatGPT invents 5 realistic-looking percentages and fake report titles that embarrass the brokerage when a client asks for the link.
- **Correction & Fallback (`الحل الإجرائي والبديل الآمن`)**: Never prompt an LLM to `'find or include X statistics'` without either (a) running live web search + browsing the primary page first, or (b) pasting the verified source excerpts into `<supplied_evidence_pack>`.

## 5. Model & Platform Capability Matrix (`مصفوفة قدرات النماذج والمنصات — 2026-10-25`)

| Platform / Model | Status | Official Documentation | MENA Operational Constraint | Fallback |
| :--- | :--- | :--- | :--- | :--- |
| **Anthropic Claude / OpenAI GPT-4o Quote-First Grounding & Abstention** | `supported` | [Official Docs](https://platform.claude.com/docs/en/test-and-evaluate/strengthen-guardrails/reduce-hallucinations) (`2026-10-25`) | Explicitly instructing the model to extract verbatim quotes before drafting and permitting 'I don't know / Not in supplied sources' drastically reduces fabricated citations. | Strip any numeric claim that cannot be traced to a line in the supplied evidence pack. |

## 6. How to Measure Success (`خطة القياس والضوابط`)

- **Primary Metric**: Citation Verification Rate (`100%` of published numbers traced to a primary URL/PDF) and `0` post-publication factual retractions.
- **Baseline**: Audit of unverified statistics in prior blog/social drafts.
- **Observation Window**: Enforced on 100% of published content.
- **Interpretation Boundary**: Verified statistics build executive credibility and AEO citation trust (`AMP-180`), while distribution and SEO structure drive reach.

## 7. Primary Sources & Evidence Boundaries (`المصادر الموثقة وحدود الأدلة`)

- [Reduce hallucinations - Claude Platform Docs](https://platform.claude.com/docs/en/test-and-evaluate/strengthen-guardrails/reduce-hallucinations) — *Anthropic* (Published `2026-08-15`, Accessed `2026-10-25`): Instructing the model to allow 'I do not know', extract verbatim quotes first, and restrict claims to supplied documents measurably reduces hallucinated facts.
- [Context windows - Claude Platform Docs](https://platform.claude.com/docs/en/build-with-claude/context-windows) — *Anthropic* (Published `2026-08-15`, Accessed `2026-10-25`): Larger context windows do not guarantee uniform recall; dumping unindexed guidelines and noisy history degrades instruction adherence.
- [The Arabic SEO in Saudi Arabia Mistakes Costing Riyadh Brands Rankings](https://digistreetmedia.com/blog/the-arabic-seo-in-saudi-arabia-mistakes-costing-riyadh-brands-rankings/) — *DigiStreet Media* (Published `2026-09-29`, Accessed `2026-10-25`): Identifies 5 recurring KSA SEO failures: treating Arabic as translation, running one strategy across Arabic/English, broken hreflang/RTL mobile UX, ignoring Vision 2030 sector context, and chasing non-local backlinks while treating Riyadh, Jeddah, and Dammam as homogeneous.
