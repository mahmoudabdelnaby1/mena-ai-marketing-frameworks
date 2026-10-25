# FW-085: GA4 AI Search & Regional AI Assistant Attribution Workflow (Capturing the 96.9% in Organic Search + Custom Regex for Perplexity, Claude & HUMAIN Chat)
## مسار عمل تتبع إحالات محركات الذكاء الاصطناعي في `GA4` (رصد الـ `96.9%` المسجلة داخل البحث العضوي + فصل `Perplexity` و`Claude` و`HUMAIN Chat` من الإحالات)

- **Consolidated Contextual Child IDs (`MERGE_INTO_EXISTING`)**: `AMP-453`, `AMP-463`, `AMP-473`, `AMP-483`, `AMP-493`
- **Selected Artifact Type**: `OPERATING_FRAMEWORK`
- **Intended Audience**: Marketing Operations Manager, CRM & Automation Architect, Data Analyst, Growth Engineer
- **Target Markets & Languages**: Egypt & GCC (`Saudi Arabia, UAE, Kuwait, Qatar, Bahrain, Oman`) — Bilingual Arabic (`Egyptian Ammiya`, `Saudi/Gulf Khaleeji`, `White MSA`) + English
- **Version**: `1.2` | **Last Reviewed**: `2026-10-25` | **Status**: `READY_FOR_REVIEW`

## 1. Plain-Language Promise & Why This Artifact Form Fits the Job

- **What You Can Make or Decide (EN)**: Stop under-counting AI search traffic by 30x in GA4 by combining a Custom Channel Group regex (capturing `Perplexity`, `Claude`, `HUMAIN Chat`, `Poe`, `You.com` alongside `ChatGPT`/`Gemini`/`DeepSeek`/`Copilot`/`Grok`) with a Google Search Console AI-Overview landing-page join.
- **ما الذي يمكنك إنجازه أو حسمه بهذه الأداة (AR)**: إيقاف فقدان 96.9% من زيارات بحث الذكاء الاصطناعي في تقارير `GA4` عبر الجمع بين قاعدة Regex مخصصة (تلتقط `Perplexity` و`Claude` و`HUMAIN Chat` التي تسقط في `Referral`) وربط صفحات الهبوط مع تقارير `Search Console`.
- **Why `OPERATING_FRAMEWORK` Fits This User Job (EN)**: VOCTOS's landmark October 2026 GA4 study in Arab markets proved two critical facts: (1) GA4's default `AI Assistant` channel (introduced 13 May 2026) only matches a narrow list of chatbot referrers (`ChatGPT`, `Gemini`, `DeepSeek`, `Copilot`, `Grok`) while dropping `Perplexity.ai`, `Claude.ai`, and Saudi Arabia's `HUMAIN Chat` into generic `Referral`, and (2) **96.9% of measured AI search clicks** for studied Saudi properties arrived from **Google `AI Overviews` and `AI Mode`**, which Google records inside **`Organic Search`** (NOT in `AI Assistant`!)! Looking only at GA4's default `AI Assistant` row misses 96.9% of AI search traffic.
- **لماذا يناسب شكل `OPERATING_FRAMEWORK` هذه المهمة (AR)**: أثبتت دراسة VOCTOS الميدانية (أكتوبر 2026) حقيقتين حاسمتين: (1) أن قناة `AI Assistant` الافتراضية في GA4 (المضافة في 13 مايو 2026) تغفل محركات رئيسية مثل `Perplexity.ai` و`Claude.ai` و`HUMAIN Chat` السعودي فترميها داخل `Referral` العام، و(2) أن **96.9% من نقرات بحث الذكاء الاصطناعي الفعلية** في المواقع السعودية المفحوصة تأتي من **`Google AI Overviews` و`AI Mode`** والتي يسجلها جوجل داخل **`Organic Search`** وليس داخل قناة `AI Assistant`! لذا يبني هذا الإطار التشغيلي لوحة القياس الكاملة.

## 2. "Use It When" Trigger, Boundaries & Exact Inputs to Prepare

- **Use It When (EN)**: Use whenever configuring Google Analytics 4 (`GA4`) or reporting on AI Search (`AEO / GEO`) traffic and conversions in KSA, UAE, or Egypt.
- **متى تستخدم هذه الأداة (AR)**: تُستخدم عند إعداد تقارير `GA4` أو قياس زيارات وتحويلات محركات الذكاء الاصطناعي في السعودية والإمارات ومصر.
- **When NOT to Use It (EN)**: Never show a client GA4's default `AI Assistant` channel row (`e.g., 45 sessions`) and tell them 'that is 100% of your AI search traffic'—that omits 96.9% of AI citations coming through Google `AI Overviews` / `AI Mode` + `Perplexity`/`Claude`/`HUMAIN`!
- **متى لا تستخدم هذه الأداة (AR)**: لا تعرض للعميل صف قناة `AI Assistant` الافتراضي في GA4 وتخبره أن هذا هو إجمالي زيارات الذكاء الاصطناعي؛ لأن ذلك يغفل 96.9% من النقرات القادمة عبر `AI Overviews` في البحث العضوي بالإضافة إلى `Perplexity` و`Claude` و`HUMAIN Chat`!

### Exact Inputs to Prepare Before Starting (`المدخلات المطلوب تجهيزها`)
1. GA4 Admin access (`Admin -> Data display -> Channel groups -> Create new channel group`)
2. Google Search Console (`GSC`) linked to GA4 / BigQuery export
3. List of informational/comparison landing pages optimized for AEO (`AMP-180`)

### Privacy-Safe Data Handling (`ضوابط الخصوصية وحماية البيانات الشخصية PDPL`)
- **Strict PII Redaction Before Prompting**: Under Saudi PDPL (Art. 25), UAE Federal Decree-Law No. 45 of 2021, Qatar Law No. 13 of 2016, and Egypt Law No. 151 of 2020, **never paste raw customer names, unhashed mobile numbers (`+9665...` / `+201...`), email addresses, national IDs, or private WhatsApp transcripts into public/consumer LLM interfaces**. Use anonymized placeholders (`{first_name}`, `ORD_10045`) during prompt testing and restrict live customer data to zero-data-retention enterprise API endpoints or local deterministic scripts.

## 3. The Directly Usable Artifact (`الأداة التطبيقية الجاهزة للنسخ والتنفيذ`)

### 2-Layer GA4 MENA AI Search Attribution Architecture (Verified 2026-10-25)

#### Layer 1: Custom GA4 Channel Group (`Extended AI Assistants & Answer Engines`)
In `GA4 Admin -> Data display -> Channel groups`, copy the default channel group, create a custom channel named **`AI Assistants & Answer Engines (Extended MENA)`**, **move it ABOVE `Referral` and `Organic Search` in priority order**, and apply this exact **Source** regex:
```regex
(?i).*(chatgpt\.com|openai\.com|gemini\.google\.com|bard\.google\.com|deepseek\.com|copilot\.microsoft\.com|edgeservices\.bing\.com|grok\.com|x\.ai|perplexity\.ai|claude\.ai|anthropic\.com|humain\.ai|chat\.humain\.com|poe\.com|you\.com|phind\.com|mistral\.ai|lechat\.mistral\.ai|meta\.ai|qwenlm\.ai|kimi\.moonshot\.cn).*
```
- **Why Priority Order Matters**: In GA4 Channel Groups, rules evaluate top-to-bottom. Placing this rule **above `Referral`** rescues `perplexity.ai`, `claude.ai`, `humain.ai`, `poe.com`, and `you.com` from being swallowed by the generic `Referral` bucket!

#### Layer 2: Measuring the `96.9%` Google `AI Overviews` & `AI Mode` Traffic Inside `Organic Search`
Because Google Search Console and GA4 record clicks from **Google `AI Overviews` and `AI Mode`** under standard `google / organic` (`Organic Search`):
1. **In Google Search Console (`Performance -> Search results`)**:
   - Filter queries by **Informational & Comparison Question Stems (`كيف، افضل، الفرق بين، كم سعر، ما هو، مقارنة`)** (`AMP-001`, `AMP-180`) on Web Search where `AI Overviews` trigger.
2. **In GA4 / Looker Studio Executive Reporting**:
   - Present AI-driven discovery as a **2-Part Scorecard**:
     - **Part A (`Direct Chatbot Referrals`)**: Tracked via the Layer 1 Custom Channel Group (`ChatGPT`, `Gemini`, `Perplexity`, `Claude`, `DeepSeek`, `Copilot`, `Grok`, `HUMAIN Chat`).
     - **Part B (`Google AI Overviews / AI Mode Organic Citations — ~96.9% of Volume`)**: Tracked via `google / organic` sessions landing on your AEO comparison/guide pages (`AMP-180`) cross-referenced with GSC query data.
     - **Explicit Boundary Note (`AMP-543`)**: Note transparently in reports that links copied from AI apps and pasted into private WhatsApp chats open in WhatsApp's in-app browser without an HTTP referrer and land in `Direct` (an industry-wide `Unknown` that cannot be fabricated).

## 4. Model & Platform Capability Branches (`فروع قدرات النماذج والمنصات والبدائل الاحتياطية`)

| System / Platform | Capability Status | Official Documentation & Access Date | Operational Constraint in Egypt & GCC | Fallback When Feature/Modality Is Unavailable |
| :--- | :--- | :--- | :--- | :--- |
| **Google Analytics 4 Default `AI Assistant` Channel (13 May 2026) vs. Custom Channel Groups** | `supported` | [Official Reference](https://voctos.net/ga4-ai-traffic-arab-markets/) (`2026-10-25`) | VOCTOS Oct 2026 audit proved that GA4's default AI Assistant channel misses Perplexity, Claude, and regional tools, while 96.9% of measured AI search clicks come via Google Organic Search (AI Overviews / AI Mode). | Use GA4 Custom Channel Groups (which evaluate retroactively!) placed above `Referral`. |

## 5. Consolidated Regional & Vertical Adaptation Matrix (`دمج الأنماط السياقية الفرعية بدون حشو`)

Per Agent 2 v1.2's anti-padding rule, the following **5 cross-verified contextual synthesis patterns** and **0 screened duplicate variants** share this core mechanism and are consolidated directly into this source-of-truth framework:

| Child Pattern ID | Disposition | Regional / Sector Operating Context | Specific Adaptation & Guardrail Integrated in This Asset | Evidence Tier |
| :--- | :--- | :--- | :--- | :--- |
| **`AMP-453`** | `MERGE_INTO_EXISTING` | Egyptian E-Commerce & Social Commerce (Shopify / WooCommerce / Cairo & Alexandria) | Implementing VOCTOS's 8-step Arab GA4 protocol: custom channel group regex covering `chatgpt|openai|perplexity|claude|gemini\.google|copilot\.microsoft|deepseek|grok|humain|fanar` plus Search Console generative AI impression reporting.; Specifically impacts Egyptian brands operating in EGP where merchant-specific payment mix from recent order records, Mobile Wallets (Vodafone Cash), InstaPay, and Fawry dominate. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-463`** | `MERGE_INTO_EXISTING` | UAE & Multi-Market GCC Enterprise / Retail (Dubai, Abu Dhabi, Doha, Kuwait) | Implementing VOCTOS's 8-step Arab GA4 protocol: custom channel group regex covering `chatgpt|openai|perplexity|claude|gemini\.google|copilot\.microsoft|deepseek|grok|humain|fanar` plus Search Console generative AI impression reporting.; Specifically impacts bilingual Arabic/English campaigns in high-CPM, expat-dense Gulf markets under UAE PDPL / TDRA and Qatari regulations. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-473`** | `MERGE_INTO_EXISTING` | High-Trust & Regulated Verticals (Healthcare/SFDA/EDA, Fintech/SAMA/FRA, Real Estate) | Implementing VOCTOS's 8-step Arab GA4 protocol: custom channel group regex covering `chatgpt|openai|perplexity|claude|gemini\.google|copilot\.microsoft|deepseek|grok|humain|fanar` plus Search Console generative AI impression reporting.; Specifically impacts regulated claims requiring SFDA, EDA, MOH, SAMA, FRA, or RERA compliance pre-clearance and strict hallucination guardrails. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-483`** | `MERGE_INTO_EXISTING` | Seasonal Peak Operations (Ramadan, Eid, White/Yellow Friday, Saudi Founding/National Day) | Implementing VOCTOS's 8-step Arab GA4 protocol: custom channel group regex covering `chatgpt|openai|perplexity|claude|gemini\.google|copilot\.microsoft|deepseek|grok|humain|fanar` plus Search Console generative AI impression reporting.; Specifically impacts high-velocity seasonal surges where CPMs jump 40-70%, prices change rapidly, and Hijri calendar cultural sensitivity is paramount. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-493`** | `MERGE_INTO_EXISTING` | Multi-Client Agency & MarTech API Automation Pipelines (LLM APIs, Webhooks, GA4, CAPI) | Implementing VOCTOS's 8-step Arab GA4 protocol: custom channel group regex covering `chatgpt|openai|perplexity|claude|gemini\.google|copilot\.microsoft|deepseek|grok|humain|fanar` plus Search Console generative AI impression reporting.; Specifically impacts automated multi-SKU or multi-client LLM/API pipelines where schema validation, token cost, and attribution governance are required. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |

### Context-Specific Execution Knobs Across the 5 MENA Operating Environments
1. **Saudi D2C E-Commerce (`Salla / Zid / Riyadh & Jeddah Retail`)**: Enforce `SAR` tax-inclusive pricing (`15% ZATCA VAT`), native `Mada / Apple Pay / Tabby / Tamara` visibility (`AMP-387`), `GAMR Mawthooq` creator verification (`AMP-281`), and White Saudi Khaleeji orthography (`AMP-002`, `AMP-177`).
2. **Egyptian E-Commerce & Social Commerce (`Shopify / WooCommerce / Cairo & Alexandria`)**: Use each merchant’s own order and payment data to assess Cash on Delivery (`COD`), mobile wallets, InstaPay, Fawry, `valU`, address fields, and pre-dispatch WhatsApp confirmation. Verify current provider terms and local requirements before implementation.
3. **UAE & Multi-Market GCC Enterprise / Retail (`Dubai, Abu Dhabi, Doha, Kuwait`)**: Separate high-CPM UAE/Qatar budgets from lower-CPM markets (`AMP-061`), enforce UAE `TDRA` `9 PM – 7 AM` SMS curfew + `AD-` prefix (`AMP-442`), UAE Media Council permits (`AMP-282`), and bilingual Arabic/English canonical & currency parity (`current applicable UAE VAT`, `current applicable Qatar/Kuwait tax rules`, 3-decimal `KWD` `AMP-239`).
4. **High-Trust & Regulated Verticals (`Healthcare SFDA/MOH/EDA, FinTech SAMA/FRA, Real Estate REGA/RERA`)**: Strip all therapeutic/cure verbs (`AMP-176`, `AMP-286`), display mandatory `MOH/SFDA/DHA/EDA/Fal/Trakheesi` permit numbers (`AMP-070`), and route budgets to high-credibility channels (`AMP-290`, `AMP-339`).
5. **Seasonal Peak Operations (`Ramadan, Eid, White/Yellow Friday, Saudi Founding/National Day`)**: Lock Hijri-Gregorian overlaps (`Feb 2027 Ramadan x Saudi Founding Day x Kuwait National Day` `AMP-125`), pre-schedule GMC `sale_price_effective_date` 48h ahead (`AMP-063`), verify 30-day baseline discount permits (`AMP-064`), and disable Meta Advantage+ auto-music (`AMP-065`).

## 6. Worked Example Summary & Failure Recovery (`ملخص المثال التطبيقي وخطة الإنقاذ`)

*(Full step-by-step worked example with annotated human edits is also provided in `EXAMPLE.md`)*

- **Sample Input Brief**: - **Property**: Saudi B2B & Consumer E-Commerce Platform (`180,000` monthly sessions in GA4).
- **Problem**: Default GA4 `AI Assistant` channel showed only `112` sessions (`ChatGPT` + `Gemini`), while `340` sessions from `perplexity.ai`, `claude.ai`, and `humain.ai` were hidden inside `Referral`, and `3,850` clicks from Google `AI Overviews` on comparison guides were lumped undifferentiated inside `Organic Search`.
- **Human Review & Key Edits Applied**: 1. **Added Known Caveats Box on Dashboard (`AMP-543`, `AMP-545`, `AMP-549`)**: Documented on the executive dashboard that (a) Google keeps its internal default AI hostname list unpublished (`AMP-549`), and (b) AI links shared via private WhatsApp arrive as `Direct` (`AMP-543`).
2. **Verified Retroactive Channel Group Application**: Confirmed in GA4 `Traffic Acquisition` that custom channel groups apply retroactively to historical property data.
- **Final Usable Output**: - Complete, non-deceptive GA4 AI Search & Assistant measurement framework deployed with custom MENA regex (`including Perplexity, Claude & HUMAIN Chat`) and GSC AI-Overview organic reconciliation.
- **What Can Go Wrong**: An analyst adds the custom AI regex channel at the **bottom** of the GA4 Channel Group list (below `Referral`); because GA4 stops at the first matching rule, `Referral` matches `perplexity.ai` and `claude.ai` first, and the new channel shows `0` sessions!
- **Correction & Fallback**: In `GA4 Admin -> Channel groups -> Reorder`, always drag **`AI Assistants & Answer Engines (Extended MENA)`** to **Position #1 or #2 (strictly ABOVE `Referral` and `Organic Search`)** before saving!

## 7. Measurement Plan & Hypothesis Framing (`خطة القياس والضوابط الإحصائية`)

- **Primary Metric to Track**: Reclassified `Perplexity / Claude / HUMAIN / Poe` sessions rescued from `Referral`, plus Conversion Rate of `AI Assistants (Extended)` vs. site average.
- **Baseline Definition**: Default GA4 `AI Assistant` channel session count.
- **Observation Window**: Immediate (retroactive in GA4 Custom Channel Groups) + ongoing 28-day tracking. *(Must span full 7/14-day weekly cycles and account for 25th–30th monthly salary windows per `AMP-391`)*.
- **What Cannot Be Concluded (Boundary)**: Custom channel regex captures browser-referred chatbot clicks, but cannot measure dark-social WhatsApp pastes (`AMP-543`) or zero-click AI answers.
