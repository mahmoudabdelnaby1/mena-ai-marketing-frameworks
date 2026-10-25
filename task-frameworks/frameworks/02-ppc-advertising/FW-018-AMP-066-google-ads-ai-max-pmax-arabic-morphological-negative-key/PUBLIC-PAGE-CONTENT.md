# Google Ads AI Max & PMax Arabic Morphological Negative Keyword Generator Prompt
## <span dir="rtl">قالب توليد قوائم الكلمات السلبية الصرفية واللهجية لحملات Google Ads AI Max وPerformance Max بالعربية</span>

> **Asset ID**: `FW-018` (`AMP-066`) | **Artifact Type**: `PROMPT_TEMPLATE` | **Channel**: Pay-Per-Click (PPC) Advertising | **Markets**: Egypt & GCC (`KSA, UAE, Kuwait, Qatar, Bahrain, Oman`) | **Version**: `1.2` (`Reviewed 2026-10-25`)

**What You Can Do With This (`ماذا يمكنك أن تنجز بهذه الأداة؟`)**:
- **EN**: Generate comprehensive Arabic negative keyword lists covering attached prefixes (`و، ف، ب، ل، ال`), Hamza/Taa variants, and regional freebie/job slang (`بلاش، مجانا، وظائف، مستعمل`) that Google's broad matching fails to block automatically.
- **AR**: <span dir="rtl">توليد قوائم الكلمات المفتاحية السلبية الشاملة للصيغ الصرفية العربية (البوادئ المتصلة `و، ف، ب، ل، ال`، وتغيرات الهمزات، ومصطلحات المجاني والوظائف والمستعمل باللهجات) التي لا يحظرها جوجل تلقائياً.</span>

## 1. Use It When & Required Inputs (`متى تستخدمها وما المدخلات المطلوبة؟`)

- **Use It When (EN)**: Use whenever running Google Search (`Broad Match` / `AI Max for Search`) or `Performance Max` campaigns in Arabic across KSA, UAE, or Egypt.
- **متى تستخدمها (AR)**: <span dir="rtl">تُستخدم عند تشغيل حملات بحث جوجل (`Broad Match` أو `AI Max`) أو حملات `Performance Max` باللغة العربية في السعودية أو الإمارات أو مصر.</span>
- **When NOT to Use It (EN)**: Do not add broad single-word negatives that overlap with your core product noun (e.g., never add `عروض` or `سعر` as negatives on an e-commerce account).
- **متى لا تستخدمها (AR)**: <span dir="rtl">لا تضف كلمات سلبية عامة تتقاطع مع نية الشراء الفعلية (مثل `سعر` أو `عروض` أو `تخفيض`) في حسابات التجارة الإلكترونية.</span>

### Exact Inputs to Prepare (`المدخلات المطلوب تجهيزها قبل البدء`)
- Core commercial category (e.g., B2B SaaS, Private Clinic, Luxury Real Estate, New Electronics E-Commerce)
- Non-converting intent categories to block (e.g., `Free/Pirated`, `Second-hand/Used`, `Jobs/Careers`, `DIY/Repair`, `Student PDF/Research`)
- Recent Google Ads Search Terms report (`تقرير عبارات البحث`) export

## 2. The Working `PROMPT_TEMPLATE` (`الأداة الكاملة الجاهزة للنسخ والتطبيق الفوري`)

### 1. Copy-Ready Arabic Morphological Negative Keyword Generator Prompt

```xml
<system_role>
You are a Senior Arabic Paid Search Linguist & Google Ads Architect.
Because Google Ads negative keywords do not automatically block Arabic morphological inflections, attached prepositions/conjunctions (`الـ، و، ف، ب، ك، ل`), Hamza/Taa Marbuta variations (`أ/إ/ا`, `ة/ه`), or dialectal slang, you must expand every unwanted root concept into a complete negative keyword matrix.
</system_role>

<campaign_context>
- Industry / Offer: {{INDUSTRY_OFFER}}
- Target Market(s): {{MARKETS: KSA | UAE | Egypt}}
- Unwanted Intent Categories to Block: {{UNWANTED_INTENTS: Free/Cracked | Used/Haraj | Jobs/Training | Cheap/DIY | Government Portal Login}}
</campaign_context>

<morphological_expansion_rules>
For every unwanted concept (e.g., "free", "used", "jobs", "repair"):
1. Generate the MSA root nouns and adjectives (`مجاني، مجانا، مجاناً، مستعمل، وظيفة، وظائف، صيانة، تصليح`).
2. Attach prefixes: `الـ` (`المجاني`), `بـ` (`بالمجان، ببلاش`), `لـ` (`للمستعمل`), `و` (`ومجاني`).
3. Generate Orthographic Variants (without Hamza `ا`, with Haa `ه` instead of `ة`: `وظيفه، صيانه، مستعمله`).
4. Generate Regional Dialect & Platform Synonyms:
   - KSA/GCC: `حراج، مستخدم، تشليح، ببلاش، تقديم وظائف، جدارات، طاقات`.
   - Egypt: `بلاش، ابو بلاش، اوليكس، دوبيزل، كسر زيرو، استيراد، شغل، مرتبات`.
</morphological_expansion_rules>

<output_format>
Output a clean, copy-paste-ready list grouped by Negative Intent Bucket, formatted as Google Ads Phrase Match (`"keyword"`) and Exact Match (`[keyword]`), plus a Python script to audit the Search Terms CSV.
</output_format>
```

### 2. Core Starter Pack (Copy-Paste into Shared Library -> Negative Keyword Lists)
```text
# Bucket 1: Free / Gratis / Pirated (المجاني والمهكر)
"مجانا"
"مجاناً"
"مجاني"
"مجانية"
"مجانيه"
"المجاني"
"المجانية"
"بالمجان"
"ببلاش"
"بلاش"
"مهكر"
"مهكرة"
"كراك"
"بدون دفع"

# Bucket 2: Used / Second-Hand Marketplaces (المستعمل والحراج - للمنتجات الجديدة فقط)
"مستعمل"
"مستعملة"
"مستعمله"
"المستعمل"
"مستخدم"
"مستخدمة"
"حراج"
"تشليح"
"كسر زيرو"
"استعمال خارج"
"اوليكس"
"دوبيزل"

# Bucket 3: Jobs / Careers / CV (الوظائف والتوظيف - لحملات المبيعات)
"وظائف"
"وظايف"
"وظيفة"
"وظيفه"
"الوظائف"
"توظيف"
"التوظيف"
"شواغر"
"تقديم وظائف"
"راتب"
"رواتب"
"مرتبات"
"تدريب منتهي بالتوظيف"
```

## 3. Complete End-to-End Worked Example (`مثال تطبيقي متكامل من المدخلات حتى المراجعة البشرية والنتيجة النهائية`)

*(Illustrative scenario — original example for training, never represented as a verified client outcome)*

### Step A: Sample Brief / Input (`موجز المدخلات`)
- **Advertiser**: Riyadh & Cairo B2B ERP Accounting Software Provider (`SAR 12,000/year` subscription).
- **Problem**: Enabled Google Ads `AI Max for Search` on `"برنامج محاسبة للشركات"`. Search Terms report revealed `38%` of budget was spent on queries like `"تحميل برنامج محاسبة مجاني بالكراك"`, `"برنامج محاسبه ببلاش اكسيل"`, and `"وظائف محاسب في الرياض"`.

### Step B: Initial Output (`المخرج الأولي`)
- Generated `148` morphological Arabic negative keywords across 4 buckets (`Free/Excel/Crack`, `Jobs/Accountant Vacancies`, `University Homework/PDF`, `Used Hardware`) including all `ة/ه` and `أ/ا` variants and `بـ/الـ` prefixes.

### Step C: Human Review & Edits (`التدقيق البشري والتعديلات`)
1. **Protected High-Intent Trial Queries**: Made sure `"تجربة مجانية"` (Free Trial) was **NOT** blocked while blocking `"تحميل مجاني بالكراك"` and `"ببلاش مدى الحياة"`.
2. **Account-Level PMax Attachment**: Applied the shared list at the Campaign level for Search and Account-level Negative Keywords for Performance Max.

### Step D: Final Reviewed Example Outcome (`النتيجة النهائية المعتمدة`)
- `148`-term Arabic Morphological Negative List attached to Search and PMax; wasted spend on free/crack/job queries dropped from `38%` to `<2%` in the subsequent 14-day Search Terms audit.

## 4. What Can Go Wrong & How to Fix It (`الأخطاء الشائعة وخطة الإنقاذ`)

- **Failure Case (`المشكلة المحتملة`)**: A media buyer adds only the single word `-مجاني` (with Yaa) as a negative keyword; Google Ads still serves ads on `"تحميل برنامج محاسبة مجانا"` (with Alef), `"بالمجان"`, and `"ببلاش"` because negative match does not stem Arabic morphological variants.
- **Correction & Fallback (`الحل الإجرائي والبديل الآمن`)**: Always generate the full orthographic and prefix inflection family (`مجاني، مجانية، مجانيه، مجانا، مجاناً، بالمجان، المجاني، ببلاش، بلاش`) for every excluded Arabic root.

## 5. Model & Platform Capability Matrix (`مصفوفة قدرات النماذج والمنصات — 2026-10-25`)

| Platform / Model | Status | Official Documentation | MENA Operational Constraint | Fallback |
| :--- | :--- | :--- | :--- | :--- |
| **Google Ads Negative Keywords & AI Max / PMax Search Term Matching** | `supported` | [Official Docs](https://support.google.com/google-ads/answer/15913066?hl=en) (`2026-10-25`) | Google Ads official documentation confirms negative keywords do not match close variants or morphological stems automatically; every spelling/prefix variant must be added explicitly. | Audit the AI Max / Search Terms report weekly and append newly discovered dialect variants. |

## 6. How to Measure Success (`خطة القياس والضوابط`)

- **Primary Metric**: Percentage of ad spend consumed by non-commercial/irrelevant Arabic search terms in the Google Ads Search Terms report.
- **Baseline**: Pre-implementation wasted spend `%` over the prior 14 days.
- **Observation Window**: 14 days post-application.
- **Interpretation Boundary**: Negative keyword hygiene eliminates wasted clicks, while landing page conversion rate and CRM speed-to-lead determine SQL volume.

## 7. Primary Sources & Evidence Boundaries (`المصادر الموثقة وحدود الأدلة`)

- [Frequently asked questions about AI Max for Search campaigns](https://support.google.com/google-ads/answer/15913066?hl=en) — *Google Ads Help* (Published `2026-06-01`, Accessed `2026-10-25`): AI Max expands beyond exact keywords using broad match and keywordless signals; negative keywords are respected and Ad Rank governs prioritization with PMax.
- [Negative keywords in Performance Max campaigns - Google Ads Help](https://support.google.com/google-ads/answer/15726455?hl=en) — *Google Ads Help* (Published `2026-05-15`, Accessed `2026-10-25`): Campaign-level and account-level negative keywords block PMax serving on matching Search/Shopping queries.
- [Fix issues with negative keywords - Google Ads Help](https://support.google.com/google-ads/answer/9701952?hl=en) — *Google Ads Help* (Published `2026-04-10`, Accessed `2026-10-25`): Negative keywords do not match close variants automatically; Arabic spelling variants and dialectal synonyms must be added explicitly.
- [The hidden challenges of AI Max search term reporting](https://adalysis.com/blog/ai-max-search-term-reporting/) — *Adalysis* (Published `2025-12-02`, Accessed `2026-10-25`): Explains reporting opacity and broad query expansion in Google Ads AI Max when search term and landing page controls are not audited.
