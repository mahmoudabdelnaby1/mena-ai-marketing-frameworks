# MENA Native Search Root & Dialect Keyword Matrix Prompt
## <span dir="rtl">قالب هندسة الكلمات المفتاحية العربية حسب الجذر اللغوي واللهجة المحلية (مصر والخليج)</span>

> **Asset ID**: `FW-001` (`AMP-001`) | **Artifact Type**: `PROMPT_TEMPLATE` | **Channel**: Search Engine Optimization (SEO) | **Markets**: Egypt & GCC (`KSA, UAE, Kuwait, Qatar, Bahrain, Oman`) | **Version**: `1.2` (`Reviewed 2026-10-25`)

**What You Can Do With This (`ماذا يمكنك أن تنجز بهذه الأداة؟`)**:
- **EN**: Generate intent-grouped Arabic and bilingual keyword clusters from native Saudi, Emirati, and Egyptian search roots instead of zero-volume literal English translations.
- **AR**: <span dir="rtl">توليد مجموعات كلمات مفتاحية عربية وثنائية اللغة مبنية على الجذور الصرفية ومصطلحات البحث الفعلية في السعودية والإمارات ومصر بدلاً من الترجمة الحرفية عديمة الجدوى.</span>

## 1. Use It When & Required Inputs (`متى تستخدمها وما المدخلات المطلوبة؟`)

- **Use It When (EN)**: Use when launching or localizing product, category, or service pages for Saudi Arabia (Salla/Zid/Shopify), UAE, or Egypt where seed product data is in English or MSA.
- **متى تستخدمها (AR)**: <span dir="rtl">يُستخدم عند إطلاق أو تعريب صفحات المنتجات أو الفئات أو الخدمات لأسواق السعودية (سلة/زد/شوبيفاي) أو الإمارات أو مصر عندما تكون بيانات المنتجات الأولية بالإنجليزية أو الفصحى.</span>
- **When NOT to Use It (EN)**: Do not use for strictly English-only technical API documentation or developer-only SaaS products where 95%+ of local queries occur in English.
- **متى لا تستخدمها (AR)**: <span dir="rtl">لا يُستخدم لصفحات توثيق البرمجيات (APIs) الموجهة للمطورين فقط حيث يتم البحث محلياً باللغة الإنجليزية بنسبة تفوق 95%.</span>

### Exact Inputs to Prepare (`المدخلات المطلوب تجهيزها قبل البدء`)
- Product/Service Catalog Seed List (English or MSA names, SKU category, price tier in SAR/AED/EGP)
- Target Market & City Tier (e.g., KSA Riyadh/Jeddah/Dammam vs. Egypt Cairo/Alexandria vs. UAE Dubai/Abu Dhabi)
- Search Console or Marketplace Autocomplete Seed Export (at least 10 verified native queries)
- Payment & Fulfilment Hooks relevant to commercial intent (e.g., Tabby/Tamara/Mada in KSA/UAE; COD/InstaPay/Fawry/valU in Egypt)

## 2. The Working `PROMPT_TEMPLATE` (`الأداة الكاملة الجاهزة للنسخ والتطبيق الفوري`)

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

## 3. Complete End-to-End Worked Example (`مثال تطبيقي متكامل من المدخلات حتى المراجعة البشرية والنتيجة النهائية`)

*(Illustrative scenario — original example for training, never represented as a verified client outcome)*

### Step A: Sample Brief / Input (`موجز المدخلات`)
- **Target Market**: Saudi Arabia (Riyadh & Jeddah) + Egypt (Cairo & Alexandria)
- **Platform**: Salla (KSA store) & WooCommerce (Egypt store)
- **Product Concept**: "Cordless Hair Straightener Brush" (فرشاة فرد الشعر اللاسلكية)
- **Price & Payment**: KSA: 299 SAR (incl. 15% VAT, Tabby/Tamara 4 payments); Egypt: 2,450 EGP (COD + InstaPay + valU)
- **Verified Seeds**: فرشاه شعر لاسلكيه، مشط حراري لاسلكي، سيراميك شعر بدون سلك

### Step B: Initial Output (`المخرج الأولي`)
| Cluster ID | Native Arabic Query | Market & Register | Intent Stage | Orthographic Variants | Literal Translation Rejected | Target Page Element |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| KW-01 | مشط حراري لاسلكي للشعر | KSA (Khaleeji/MSA) | Commercial / Transactional | مشط حرارى لاسلكى، فرشاه حراريه | فرشاة تقويم الشعر بدون حبل | H1 & Meta Title (KSA) |
| KW-02 | افضل فرشاة شعر لاسلكية بالتقسيط تابي | KSA (Riyadh/Jeddah) | High-Intent Transactional | افضل فرشاه شعر لاسلكيه تابى | شراء مملس شعر لاسلكي رخيص | Product Subtitle & FAQ |
| KW-03 | سعر فرشاة فرد الشعر اللاسلكية في مصر | Egypt (Ammiya/MSA) | Transactional Price Check | سعر فرشاه فرد الشعر اللاسلكيه | تكلفة فرشاة تنعيم الشعر | H1 & Meta Title (Egypt) |
| KW-04 | مكواة شعر فرشاه بدون سلك الدفع عند الاستلام | Egypt (Ammiya) | Transactional COD | مكواه شعر فرشاه، فرشة شعر حرارية | أداة تصفيف الشعر الخالية من الأسلاك | Collection Filter & Meta Description |

### Step C: Human Review & Edits (`التدقيق البشري والتعديلات`)
1. **Lexical Validation (KSA)**: Verified in Saudi Google Autocomplete that shoppers search `"استشوار مشط لاسلكي"` and `"فرشاة سيراميك لاسلكية"` more frequently than `"فرشاة فرد"`. Added `"استشوار مشط لاسلكي"` as secondary H2 keyword for the Salla KSA storefront.
2. **Regulatory Guardrail (SFDA/EDA)**: Removed an AI-suggested FAQ phrase `"يعالج تقصف الشعر نهائياً"` (therapeutic claim risk under SFDA cosmetic rules) and replaced it with `"تصفيف سريع مع التحكم في درجات الحرارة"`.
3. **Slug Hygiene**: Kept the URL slug in clean ASCII (`/ar/cordless-hair-straightener-brush`) per `AMP-008` to avoid UTF-8 percent-encoding bloat while keeping `<title>` and `<h1>` in native Arabic.

### Step D: Final Reviewed Example Outcome (`النتيجة النهائية المعتمدة`)
- **KSA Salla `<title>` (58 chars)**: `مشط حراري وفرشاة شعر لاسلكية | تقسيط تابي وتمارا - متجرنا`
- **KSA Salla `<h1>`**: `فرشاة فرد الشعر الحرارية اللاسلكية (شحن USB-C)`
- **Egypt WooCommerce `<title>` (61 chars)**: `فرشاة فرد الشعر الحرارية اللاسلكية | شحن لجميع محافظات مصر`
- **Egypt WooCommerce `<h1>`**: `مكواة وفرشاة فرد الشعر اللاسلكية - الدفع عند الاستلام أو إنستاباي`

## 4. What Can Go Wrong & How to Fix It (`الأخطاء الشائعة وخطة الإنقاذ`)

- **Failure Case (`المشكلة المحتملة`)**: An SEO specialist runs the prompt without supplying `VERIFIED_SEEDS` from Google Search Console or Autocomplete, causing the LLM to invent plausible-sounding Gulf slang that has zero actual monthly search volume.
- **Correction & Fallback (`الحل الإجرائي والبديل الآمن`)**: Enforce the Pre-Flight Rule: never accept an AI keyword table into production until at least 3 top terms per cluster are cross-checked against Google Search Console Performance queries, Google Autocomplete (set to KSA/Egypt locale), or Salla/Amazon.sa search bar suggestions.

## 5. Model & Platform Capability Matrix (`مصفوفة قدرات النماذج والمنصات — 2026-10-25`)

| Platform / Model | Status | Official Documentation | MENA Operational Constraint | Fallback |
| :--- | :--- | :--- | :--- | :--- |
| **OpenAI GPT-4o / GPT-4.1 & Anthropic Claude 3.7/4 Sonnet** | `supported` | [Official Docs](https://platform.claude.com/docs/en/build-with-claude/prompt-engineering/claude-prompting-best-practices) (`2026-10-25`) | Both models support Arabic root decomposition and XML-structured constraints (`<lexical_rules>`), but neither has real-time search volume data built into weights. | Pair the prompt output with a CSV export from Google Keyword Planner / GSC or manual Google Autocomplete check in incognito (`gl=sa&hl=ar` or `gl=eg&hl=ar`). |

## 6. How to Measure Success (`خطة القياس والضوابط`)

- **Primary Metric**: Non-branded organic impressions, CTR, and engaged sessions per landing page in Google Search Console & GA4.
- **Baseline**: Compare against pages using translated English titles over the prior 28-day cycle.
- **Observation Window**: 28 days post-reindexing (to account for crawl delay and weekly Fri/Sat search swings).
- **Interpretation Boundary**: Do not promise guaranteed Top-3 rankings from keyword rewriting alone; domain authority, technical indexability (`AMP-003`/`AMP-004`), and pricing competitiveness co-determine ranking.

## 7. Primary Sources & Evidence Boundaries (`المصادر الموثقة وحدود الأدلة`)

- [Why Direct Translation Fails in MENA SEO](https://23hublab.com/why-direct-translation-fails-in-mena-seo/) — *23HubLab* (Published `2026-04-01`, Accessed `2026-10-25`): AI/machine translations of English keyword lists fail in MENA because native searchers use distinct Arabic lexical roots and phrasing, leading to high bounce rates and poor dwell time.
- [Arabic Keyword Research for Online Stores: A Practical Guide](https://esafqa.com/en/blog/arabic-keyword-research-guide/) — *Esafqa* (Published `2026-10-08`, Accessed `2026-10-25`): Demonstrates how a single product concept splits across MSA vs dialect, spelling variants, and lexical differences between Saudi Arabia, UAE, and Egypt.
- [The Arabic SEO in Saudi Arabia Mistakes Costing Riyadh Brands Rankings](https://digistreetmedia.com/blog/the-arabic-seo-in-saudi-arabia-mistakes-costing-riyadh-brands-rankings/) — *DigiStreet Media* (Published `2026-09-29`, Accessed `2026-10-25`): Identifies 5 recurring KSA SEO failures: treating Arabic as translation, running one strategy across Arabic/English, broken hreflang/RTL mobile UX, ignoring Vision 2030 sector context, and chasing non-local backlinks while treating Riyadh, Jeddah, and Dammam as homogeneous.
