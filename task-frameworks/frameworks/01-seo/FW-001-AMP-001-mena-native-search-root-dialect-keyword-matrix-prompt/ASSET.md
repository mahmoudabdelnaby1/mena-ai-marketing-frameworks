# FW-001: MENA Native Search Root & Dialect Keyword Matrix Prompt
## قالب هندسة الكلمات المفتاحية العربية حسب الجذر اللغوي واللهجة المحلية (مصر والخليج)

- **Consolidated Contextual Child IDs (`MERGE_INTO_EXISTING`)**: `AMP-013`, `AMP-025`, `AMP-037`, `AMP-049`
- **Selected Artifact Type**: `PROMPT_TEMPLATE`
- **Intended Audience**: SEO Specialist, E-Commerce Manager, Content Strategist, Technical SEO Lead
- **Target Markets & Languages**: Egypt & GCC (`Saudi Arabia, UAE, Kuwait, Qatar, Bahrain, Oman`) — Bilingual Arabic (`Egyptian Ammiya`, `Saudi/Gulf Khaleeji`, `White MSA`) + English
- **Version**: `1.2` | **Last Reviewed**: `2026-10-25` | **Status**: `READY_FOR_REVIEW`

## 1. Plain-Language Promise & Why This Artifact Form Fits the Job

- **What You Can Make or Decide (EN)**: Generate intent-grouped Arabic and bilingual keyword clusters from native Saudi, Emirati, and Egyptian search roots instead of zero-volume literal English translations.
- **ما الذي يمكنك إنجازه أو حسمه بهذه الأداة (AR)**: توليد مجموعات كلمات مفتاحية عربية وثنائية اللغة مبنية على الجذور الصرفية ومصطلحات البحث الفعلية في السعودية والإمارات ومصر بدلاً من الترجمة الحرفية عديمة الجدوى.
- **Why `PROMPT_TEMPLATE` Fits This User Job (EN)**: Keyword ideation from English seed lists is a recurring generative task; a structured PROMPT_TEMPLATE with locked lexical-root rules, regional synonym tables, and output verification prevents literal calques at generation time.
- **لماذا يناسب شكل `PROMPT_TEMPLATE` هذه المهمة (AR)**: تحويل قوائم الكلمات من الإنجليزية إلى العربية مهمة توليدية متكررة؛ لذا فإن قالب البرومبت المهيكل المقيد بالجذور الصرفية ومصفوفة المرادفات الإقليمية يمنع الترجمة الحرفية من المصدر.

## 2. "Use It When" Trigger, Boundaries & Exact Inputs to Prepare

- **Use It When (EN)**: Use when launching or localizing product, category, or service pages for Saudi Arabia (Salla/Zid/Shopify), UAE, or Egypt where seed product data is in English or MSA.
- **متى تستخدم هذه الأداة (AR)**: يُستخدم عند إطلاق أو تعريب صفحات المنتجات أو الفئات أو الخدمات لأسواق السعودية (سلة/زد/شوبيفاي) أو الإمارات أو مصر عندما تكون بيانات المنتجات الأولية بالإنجليزية أو الفصحى.
- **When NOT to Use It (EN)**: Do not use for strictly English-only technical API documentation or developer-only SaaS products where 95%+ of local queries occur in English.
- **متى لا تستخدم هذه الأداة (AR)**: لا يُستخدم لصفحات توثيق البرمجيات (APIs) الموجهة للمطورين فقط حيث يتم البحث محلياً باللغة الإنجليزية بنسبة تفوق 95%.

### Exact Inputs to Prepare Before Starting (`المدخلات المطلوب تجهيزها`)
1. Product/Service Catalog Seed List (English or MSA names, SKU category, price tier in SAR/AED/EGP)
2. Target Market & City Tier (e.g., KSA Riyadh/Jeddah/Dammam vs. Egypt Cairo/Alexandria vs. UAE Dubai/Abu Dhabi)
3. Search Console or Marketplace Autocomplete Seed Export (at least 10 verified native queries)
4. Payment & Fulfilment Hooks relevant to commercial intent (e.g., Tabby/Tamara/Mada in KSA/UAE; COD/InstaPay/Fawry/valU in Egypt)

### Privacy-Safe Data Handling (`ضوابط الخصوصية وحماية البيانات الشخصية PDPL`)
- **Strict PII Redaction Before Prompting**: Under Saudi PDPL (Art. 25), UAE Federal Decree-Law No. 45 of 2021, Qatar Law No. 13 of 2016, and Egypt Law No. 151 of 2020, **never paste raw customer names, unhashed mobile numbers (`+9665...` / `+201...`), email addresses, national IDs, or private WhatsApp transcripts into public/consumer LLM interfaces**. Use anonymized placeholders (`{first_name}`, `ORD_10045`) during prompt testing and restrict live customer data to zero-data-retention enterprise API endpoints or local deterministic scripts.

## 3. The Directly Usable Artifact (`الأداة التطبيقية الجاهزة للنسخ والتنفيذ`)

### Copy-Ready Prompt Template (Arabic & English System/User Prompt)

```xml
<system_role>
You are a Senior MENA Search & Localization Architect specializing in Saudi (Khaleeji/MSA), Emirati (UAE Bilingual), and Egyptian (Ammiya/MSA) search behavior.
STRICT PROHIBITION: Never translate English keywords word-for-word into Modern Standard Arabic calques (e.g., never translate "cheap mobile phones" as "هواتف محمولة رخيصة" for Saudi Arabia where buyers search "افضل جوال بسعر رخيص" or "عروض جوالات بالتقسيط تابي", or Egypt where buyers search "ارخص موبايل في مصر بالتقسيط").
</system_role>

<task_context>
- Target Market(s): {{TARGET_MARKET: KSA | UAE | Egypt | Multi-GCC}}
- Storefront Platform: {{PLATFORM: Salla | Zid | Shopify | WooCommerce | Amazon.sa | Noon}}
- Product / Category Concept: {{PRODUCT_CONCEPT}}
- Price & Payment Context: {{CURRENCY_AND_PAYMENT_RAILS: e.g., SAR + 15% VAT + Tabby/Tamara | EGP + COD/InstaPay/valU}}
- Verified Native Seed Terms (from GSC / Autocomplete): {{VERIFIED_SEEDS}}
</task_context>

<lexical_rules>
1. Deconstruct {{PRODUCT_CONCEPT}} into its native Arabic root (الجذر الثلاثي/الرباعي) and map how real buyers name the object in each target market:
   - KSA Lexicon: جوال، عباية، عطور، مكيف سبليت، شحن سريع الرياض، تقسيط تابي وتمارا.
   - Egypt Lexicon: موبايل، دريسات/عبايات، برفان، تكييف، الدفع عند الاستلام، تقسيط فاليو.
   - UAE Lexicon: Bilingual English + Gulf Arabic (e.g., "same day delivery Dubai", "توصيل سريع دبي").
2. Generate 4 distinct Search Intent Buckets:
   - Bucket A: Transactional & Price-Modifier Queries (اسعار، عروض، كود خصم، بالتقسيط، شراء).
   - Bucket B: Commercial Comparison Queries (افضل، الفرق بين، تجربتي مع، اصلي).
   - Bucket C: Orthographic & Mobile-Keyboard Variants (without Hamza ا/أ/إ, Taa Marbuta ة/ه swaps, Franco-Arabic/Brand transliterations).
   - Bucket D: Prohibited Literal Calques (explicitly list the literal translations writers MUST NOT use).
</lexical_rules>

<output_schema>
Return a Markdown table with columns:
| Cluster ID | Native Arabic Query | Market & Register (KSA/UAE/EG) | Intent Stage | Orthographic Variants (Hamza/Taa) | Literal Translation Rejected | Target Page Element (H1, Title, FAQ, Hidden Tags) |
Followed by a 5-point Human GSC/Autocomplete Verification Checklist before publishing.
</output_schema>
```

## 4. Model & Platform Capability Branches (`فروع قدرات النماذج والمنصات والبدائل الاحتياطية`)

| System / Platform | Capability Status | Official Documentation & Access Date | Operational Constraint in Egypt & GCC | Fallback When Feature/Modality Is Unavailable |
| :--- | :--- | :--- | :--- | :--- |
| **OpenAI GPT-4o / GPT-4.1 & Anthropic Claude 3.7/4 Sonnet** | `supported` | [Official Reference](https://platform.claude.com/docs/en/build-with-claude/prompt-engineering/claude-prompting-best-practices) (`2026-10-25`) | Both models support Arabic root decomposition and XML-structured constraints (`<lexical_rules>`), but neither has real-time search volume data built into weights. | Pair the prompt output with a CSV export from Google Keyword Planner / GSC or manual Google Autocomplete check in incognito (`gl=sa&hl=ar` or `gl=eg&hl=ar`). |

## 5. Consolidated Regional & Vertical Adaptation Matrix (`دمج الأنماط السياقية الفرعية بدون حشو`)

Per Agent 2 v1.2's anti-padding rule, the following **4 cross-verified contextual synthesis patterns** and **1 screened duplicate variants** share this core mechanism and are consolidated directly into this source-of-truth framework:

| Child Pattern ID | Disposition | Regional / Sector Operating Context | Specific Adaptation & Guardrail Integrated in This Asset | Evidence Tier |
| :--- | :--- | :--- | :--- | :--- |
| **`AMP-013`** | `MERGE_INTO_EXISTING` | Egyptian E-Commerce & Social Commerce (Shopify / WooCommerce / Cairo & Alexandria) | When an industry term is universally searched in English (e.g., B2B SaaS API names or developer tools).; Specifically impacts Egyptian brands operating in EGP where merchant-specific payment mix from recent order records, Mobile Wallets (Vodafone Cash), InstaPay, and Fawry dominate. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-025`** | `MERGE_INTO_EXISTING` | UAE & Multi-Market GCC Enterprise / Retail (Dubai, Abu Dhabi, Doha, Kuwait) | When an industry term is universally searched in English (e.g., B2B SaaS API names or developer tools).; Specifically impacts bilingual Arabic/English campaigns in high-CPM, expat-dense Gulf markets under UAE PDPL / TDRA and Qatari regulations. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-037`** | `MERGE_INTO_EXISTING` | High-Trust & Regulated Verticals (Healthcare/SFDA/EDA, Fintech/SAMA/FRA, Real Estate) | When an industry term is universally searched in English (e.g., B2B SaaS API names or developer tools).; Specifically impacts regulated claims requiring SFDA, EDA, MOH, SAMA, FRA, or RERA compliance pre-clearance and strict hallucination guardrails. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-049`** | `MERGE_INTO_EXISTING` | Seasonal Peak Operations (Ramadan, Eid, White/Yellow Friday, Saudi Founding/National Day) | When an industry term is universally searched in English (e.g., B2B SaaS API names or developer tools).; Specifically impacts high-velocity seasonal surges where CPMs jump 40-70%, prices change rapidly, and Hijri calendar cultural sensitivity is paramount. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-501`** | `REJECT_DUPLICATE` | Screened UI/Format Synonym (`Merged Variant: Minor UI/Format Synonym of AMP-001 (Search Engine Optimization (SEO))`) | Consolidated into parent workflow without duplicate file inflation. | `SCREENED_DUPLICATE_VARIANT` |

### Context-Specific Execution Knobs Across the 5 MENA Operating Environments
1. **Saudi D2C E-Commerce (`Salla / Zid / Riyadh & Jeddah Retail`)**: Enforce `SAR` tax-inclusive pricing (`15% ZATCA VAT`), native `Mada / Apple Pay / Tabby / Tamara` visibility (`AMP-387`), `GAMR Mawthooq` creator verification (`AMP-281`), and White Saudi Khaleeji orthography (`AMP-002`, `AMP-177`).
2. **Egyptian E-Commerce & Social Commerce (`Shopify / WooCommerce / Cairo & Alexandria`)**: Use each merchant’s own order and payment data to assess Cash on Delivery (`COD`), mobile wallets, InstaPay, Fawry, `valU`, address fields, and pre-dispatch WhatsApp confirmation. Verify current provider terms and local requirements before implementation.
3. **UAE & Multi-Market GCC Enterprise / Retail (`Dubai, Abu Dhabi, Doha, Kuwait`)**: Separate high-CPM UAE/Qatar budgets from lower-CPM markets (`AMP-061`), enforce UAE `TDRA` `9 PM – 7 AM` SMS curfew + `AD-` prefix (`AMP-442`), UAE Media Council permits (`AMP-282`), and bilingual Arabic/English canonical & currency parity (`current applicable UAE VAT`, `current applicable Qatar/Kuwait tax rules`, 3-decimal `KWD` `AMP-239`).
4. **High-Trust & Regulated Verticals (`Healthcare SFDA/MOH/EDA, FinTech SAMA/FRA, Real Estate REGA/RERA`)**: Strip all therapeutic/cure verbs (`AMP-176`, `AMP-286`), display mandatory `MOH/SFDA/DHA/EDA/Fal/Trakheesi` permit numbers (`AMP-070`), and route budgets to high-credibility channels (`AMP-290`, `AMP-339`).
5. **Seasonal Peak Operations (`Ramadan, Eid, White/Yellow Friday, Saudi Founding/National Day`)**: Lock Hijri-Gregorian overlaps (`Feb 2027 Ramadan x Saudi Founding Day x Kuwait National Day` `AMP-125`), pre-schedule GMC `sale_price_effective_date` 48h ahead (`AMP-063`), verify 30-day baseline discount permits (`AMP-064`), and disable Meta Advantage+ auto-music (`AMP-065`).

## 6. Worked Example Summary & Failure Recovery (`ملخص المثال التطبيقي وخطة الإنقاذ`)

*(Full step-by-step worked example with annotated human edits is also provided in `EXAMPLE.md`)*

- **Sample Input Brief**: - **Target Market**: Saudi Arabia (Riyadh & Jeddah) + Egypt (Cairo & Alexandria)
- **Platform**: Salla (KSA store) & WooCommerce (Egypt store)
- **Product Concept**: "Cordless Hair Straightener Brush" (فرشاة فرد الشعر اللاسلكية)
- **Price & Payment**: KSA: 299 SAR (incl. 15% VAT, Tabby/Tamara 4 payments); Egypt: 2,450 EGP (COD + InstaPay + valU)
- **Verified Seeds**: فرشاه شعر لاسلكيه، مشط حراري لاسلكي، سيراميك شعر بدون سلك
- **Human Review & Key Edits Applied**: 1. **Lexical Validation (KSA)**: Verified in Saudi Google Autocomplete that shoppers search `"استشوار مشط لاسلكي"` and `"فرشاة سيراميك لاسلكية"` more frequently than `"فرشاة فرد"`. Added `"استشوار مشط لاسلكي"` as secondary H2 keyword for the Salla KSA storefront.
2. **Regulatory Guardrail (SFDA/EDA)**: Removed an AI-suggested FAQ phrase `"يعالج تقصف الشعر نهائياً"` (therapeutic claim risk under SFDA cosmetic rules) and replaced it with `"تصفيف سريع مع التحكم في درجات الحرارة"`.
3. **Slug Hygiene**: Kept the URL slug in clean ASCII (`/ar/cordless-hair-straightener-brush`) per `AMP-008` to avoid UTF-8 percent-encoding bloat while keeping `<title>` and `<h1>` in native Arabic.
- **Final Usable Output**: - **KSA Salla `<title>` (58 chars)**: `مشط حراري وفرشاة شعر لاسلكية | تقسيط تابي وتمارا - متجرنا`
- **KSA Salla `<h1>`**: `فرشاة فرد الشعر الحرارية اللاسلكية (شحن USB-C)`
- **Egypt WooCommerce `<title>` (61 chars)**: `فرشاة فرد الشعر الحرارية اللاسلكية | شحن لجميع محافظات مصر`
- **Egypt WooCommerce `<h1>`**: `مكواة وفرشاة فرد الشعر اللاسلكية - الدفع عند الاستلام أو إنستاباي`
- **What Can Go Wrong**: An SEO specialist runs the prompt without supplying `VERIFIED_SEEDS` from Google Search Console or Autocomplete, causing the LLM to invent plausible-sounding Gulf slang that has zero actual monthly search volume.
- **Correction & Fallback**: Enforce the Pre-Flight Rule: never accept an AI keyword table into production until at least 3 top terms per cluster are cross-checked against Google Search Console Performance queries, Google Autocomplete (set to KSA/Egypt locale), or Salla/Amazon.sa search bar suggestions.

## 7. Measurement Plan & Hypothesis Framing (`خطة القياس والضوابط الإحصائية`)

- **Primary Metric to Track**: Non-branded organic impressions, CTR, and engaged sessions per landing page in Google Search Console & GA4.
- **Baseline Definition**: Compare against pages using translated English titles over the prior 28-day cycle.
- **Observation Window**: 28 days post-reindexing (to account for crawl delay and weekly Fri/Sat search swings). *(Must span full 7/14-day weekly cycles and account for 25th–30th monthly salary windows per `AMP-391`)*.
- **What Cannot Be Concluded (Boundary)**: Do not promise guaranteed Top-3 rankings from keyword rewriting alone; domain authority, technical indexability (`AMP-003`/`AMP-004`), and pricing competitiveness co-determine ranking.
