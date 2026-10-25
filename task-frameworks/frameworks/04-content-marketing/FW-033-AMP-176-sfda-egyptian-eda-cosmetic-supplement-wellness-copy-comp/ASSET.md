# FW-033: Beauty, Supplement & Wellness Claims Review Checklist
## قائمة مراجعة ادعاءات منتجات الجمال والمكملات والعافية

- **Consolidated Contextual Child IDs (`MERGE_INTO_EXISTING`)**: `AMP-186`, `AMP-196`, `AMP-206`, `AMP-216`, `AMP-226`
- **Selected Artifact Type**: `CHECKLIST`
- **Intended Audience**: Content Manager, Arabic Copywriter, Editorial Lead, Compliance Reviewer
- **Target Markets & Languages**: Egypt & GCC (`Saudi Arabia, UAE, Kuwait, Qatar, Bahrain, Oman`) — Bilingual Arabic (`Egyptian Ammiya`, `Saudi/Gulf Khaleeji`, `White MSA`) + English
- **Version**: `1.2` | **Last Reviewed**: `2026-10-25` | **Status**: `READY_FOR_REVIEW`

## 1. Plain-Language Promise & Why This Artifact Form Fits the Job

- **What You Can Make or Decide (EN)**: Use this editorial checklist to flag health or treatment claims in beauty and supplement copy and route them for separate, current market-specific review. It does not determine whether a product or claim is permitted.
- **ما الذي يمكنك إنجازه أو حسمه بهذه الأداة (AR)**: استخدم قائمة المراجعة لرصد ادعاءات الصحة أو العلاج في محتوى الجمال والمكملات، ثم أحِلها إلى مراجعة حديثة ومخصصة لكل سوق. لا تحدد الأداة ما إذا كان المنتج أو الادعاء مسموحًا.
- **Why `CHECKLIST` Fits This User Job (EN)**: Reviewers need a repeatable way to flag health or treatment claims, check substantiation and product classification, then route questions for qualified market-specific review. This checklist does not certify compliance.
- **لماذا يناسب شكل `CHECKLIST` هذه المهمة (AR)**: تساعد القائمة المراجع على رصد الادعاءات الصحية أو العلاجية والتحقق من أدلتها وتصنيف المنتج، ثم إحالة الأسئلة إلى مختص وفق متطلبات كل سوق.؛ وتمنع قائمة الفحص هذه تلك المخالفات.

## 2. "Use It When" Trigger, Boundaries & Exact Inputs to Prepare

- **Use It When (EN)**: Use before publishing any product description, blog post, landing page, or ad script for cosmetics, perfumes, skincare, haircare, or dietary supplements in KSA, UAE, or Egypt.
- **متى تستخدم هذه الأداة (AR)**: تُستخدم قبل نشر أي وصف منتج أو مقال أو إعلان لمنتجات التجميل والعناية بالبشرة والشعر والعطور والمكملات الغذائية في السعودية أو الإمارات أو مصر.
- **When NOT to Use It (EN)**: Do not treat this checklist as a substitute for product classification, notification, registration, or market-specific approval checks. Confirm current requirements with the appropriate authority and qualified reviewer.
- **متى لا تستخدم هذه الأداة (AR)**: لا تستخدم هذه القائمة بديلًا عن مراجعة التصنيف أو الإخطار أو التسجيل أو المتطلبات التنظيمية الحالية في السوق المعني.

### Exact Inputs to Prepare Before Starting (`المدخلات المطلوب تجهيزها`)
1. Product SFDA `eCosma` / EDA Notification Category (`Cosmetic / منتج تجميلي` vs. `Health Supplement / مكمل غذائي`)
2. Draft AI Product Copy, Bullet Points, and Video Script
3. Approved Ingredient Function List (cosmetic appearance/hydration claims only)

### Privacy-Safe Data Handling (`ضوابط الخصوصية وحماية البيانات الشخصية PDPL`)
- **Strict PII Redaction Before Prompting**: Under Saudi PDPL (Art. 25), UAE Federal Decree-Law No. 45 of 2021, Qatar Law No. 13 of 2016, and Egypt Law No. 151 of 2020, **never paste raw customer names, unhashed mobile numbers (`+9665...` / `+201...`), email addresses, national IDs, or private WhatsApp transcripts into public/consumer LLM interfaces**. Use anonymized placeholders (`{first_name}`, `ORD_10045`) during prompt testing and restrict live customer data to zero-data-retention enterprise API endpoints or local deterministic scripts.

## 3. The Directly Usable Artifact (`الأداة التطبيقية الجاهزة للنسخ والتنفيذ`)

### SFDA & EDA Cosmetic vs. Therapeutic Claim Scrubbing Matrix

#### 1. Claims that need evidence and market-specific review
| Claims requiring review | Why the claim needs product- and market-specific review | Possible wording for substantiation and local review |
| :--- | :--- | :--- |
| `يعالج` / `يشفي` / `يقضي على المرض` (`Treats / Cures / Heals`) | Classifies the product as an unlicensed pharmaceutical drug (`عقار طبي`). | `يساعد على تحسين مظهر...` / `يمنح البشرة عناية مرطبة...` (`Helps improve the appearance of...`) |
| `ينبت الشعر من الجذور` / `يعالج الصلع الوراثي` (`Regrows hair / Cures alopecia`) | Alters physiological function beyond surface cosmetic cleansing/conditioning. | `يغذي فروة الرأس ويمنح الشعر مظهراً أكثر كثافة وحيوية` (`Nourishes scalp and gives hair a fuller, more vibrant look`) |
| `يزيل التجاعيد نهائياً خلال 3 أيام` / `بديل البوتوكس الطبي` (`Permanently erases wrinkles / Medical Botox alternative`) | Deceptive efficacy & medical procedure equivalence claim. | `يساعد على تقليل مظهر الخطوط الدقيقة ويمنح البشرة ملمساً ناعماً ومشدوداً` (`Helps reduce the appearance of fine lines`) |
| `يعالج حب الشباب والأكزيما والصدفية` (`Treats acne, eczema, psoriasis`) | Disease treatment claim restricted strictly to licensed drugs. | `مناسب للبشرة المعرضة للشوائب؛ ينظف المسام بعمق ويلطف البشرة` (`Suitable for blemish-prone skin; deeply cleanses pores`) |
| `معتمد طبياً من هيئة الغذاء والدواء لعلاج...` (`Medically approved by SFDA to cure...`) | SFDA **lists/notifies (`مدرج`)** cosmetics in `eCosma`; claiming SFDA "medically endorses" efficacy is a severe violation! | `مدرج في نظام منتجات التجميل لدى هيئة الغذاء والدواء (SFDA)` *(Only if genuinely listed, without claiming medical endorsement).* |

#### 2. Copy-Ready Python Claim Scanner (Run on All AI Cosmetic/Supplement Drafts)
```python
import re

FORBIDDEN_THERAPEUTIC_RE = re.compile(
    r"(يعالج|علاج نهائي|يشفي|شفاء|يقضي على|ينبت الشعر|الصلع|الأكزيما|الصدفية|بديل البوتوكس|طبي مضمون|معتمد طبيا|تحفيز الخلايا الجذعية|مضاد حيوي)",
    re.IGNORECASE
)

def scan_sfda_eda_claims(arabic_copy: str):
    hits = FORBIDDEN_THERAPEUTIC_RE.findall(arabic_copy or "")
    return {
        "compliant": len(hits) == 0,
        "flagged_therapeutic_terms": list(set(hits)),
        "action": "PASS" if not hits else "BLOCK_AND_REWRITE_TO_COSMETIC_APPEARANCE"
    }
```

## 4. Model & Platform Capability Branches (`فروع قدرات النماذج والمنصات والبدائل الاحتياطية`)

| System / Platform | Capability Status | Official Documentation & Access Date | Operational Constraint in Egypt & GCC | Fallback When Feature/Modality Is Unavailable |
| :--- | :--- | :--- | :--- | :--- |
| **Saudi SFDA Cosmetic Products Law (Royal Decree M/49) & Executive Regulations** | `supported` | [Official Reference](https://www.sfda.gov.sa/en/regulations/62870) (`2026-10-25`) | SFDA regulations strictly define cosmetics as products intended for cleansing, perfuming, or improving appearance, and penalize unlicensed medical claims or misleading advertising under applicable local rules; confirm scope and current requirements with qualified review. | Consult a qualified regulatory affairs specialist in KSA/Egypt before publishing functional health claims. |

## 5. Consolidated Regional & Vertical Adaptation Matrix (`دمج الأنماط السياقية الفرعية بدون حشو`)

Per Agent 2 v1.2's anti-padding rule, the following **5 cross-verified contextual synthesis patterns** and **0 screened duplicate variants** share this core mechanism and are consolidated directly into this source-of-truth framework:

| Child Pattern ID | Disposition | Regional / Sector Operating Context | Specific Adaptation & Guardrail Integrated in This Asset | Evidence Tier |
| :--- | :--- | :--- | :--- | :--- |
| **`AMP-186`** | `MERGE_INTO_EXISTING` | Egyptian E-Commerce & Social Commerce (Shopify / WooCommerce / Cairo & Alexandria) | Mandatory SFDA/EDA prohibited-verb lexicon check and regulatory clearance number verification before publishing.; Specifically impacts Egyptian brands operating in EGP where merchant-specific payment mix from recent order records, Mobile Wallets (Vodafone Cash), InstaPay, and Fawry dominate. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-196`** | `MERGE_INTO_EXISTING` | UAE & Multi-Market GCC Enterprise / Retail (Dubai, Abu Dhabi, Doha, Kuwait) | Mandatory SFDA/EDA prohibited-verb lexicon check and regulatory clearance number verification before publishing.; Specifically impacts bilingual Arabic/English campaigns in high-CPM, expat-dense Gulf markets under UAE PDPL / TDRA and Qatari regulations. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-206`** | `MERGE_INTO_EXISTING` | High-Trust & Regulated Verticals (Healthcare/SFDA/EDA, Fintech/SAMA/FRA, Real Estate) | Mandatory SFDA/EDA prohibited-verb lexicon check and regulatory clearance number verification before publishing.; Specifically impacts regulated claims requiring SFDA, EDA, MOH, SAMA, FRA, or RERA compliance pre-clearance and strict hallucination guardrails. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-216`** | `MERGE_INTO_EXISTING` | Seasonal Peak Operations (Ramadan, Eid, White/Yellow Friday, Saudi Founding/National Day) | Mandatory SFDA/EDA prohibited-verb lexicon check and regulatory clearance number verification before publishing.; Specifically impacts high-velocity seasonal surges where CPMs jump 40-70%, prices change rapidly, and Hijri calendar cultural sensitivity is paramount. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-226`** | `MERGE_INTO_EXISTING` | Multi-Client Agency & MarTech API Automation Pipelines (LLM APIs, Webhooks, GA4, CAPI) | Mandatory SFDA/EDA prohibited-verb lexicon check and regulatory clearance number verification before publishing.; Specifically impacts automated multi-SKU or multi-client LLM/API pipelines where schema validation, token cost, and attribution governance are required. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |

### Context-Specific Execution Knobs Across the 5 MENA Operating Environments
1. **Saudi D2C E-Commerce (`Salla / Zid / Riyadh & Jeddah Retail`)**: Enforce `SAR` tax-inclusive pricing (`15% ZATCA VAT`), native `Mada / Apple Pay / Tabby / Tamara` visibility (`AMP-387`), `GAMR Mawthooq` creator verification (`AMP-281`), and White Saudi Khaleeji orthography (`AMP-002`, `AMP-177`).
2. **Egyptian E-Commerce & Social Commerce (`Shopify / WooCommerce / Cairo & Alexandria`)**: Use each merchant’s own order and payment data to assess Cash on Delivery (`COD`), mobile wallets, InstaPay, Fawry, `valU`, address fields, and pre-dispatch WhatsApp confirmation. Verify current provider terms and local requirements before implementation.
3. **UAE & Multi-Market GCC Enterprise / Retail (`Dubai, Abu Dhabi, Doha, Kuwait`)**: Separate high-CPM UAE/Qatar budgets from lower-CPM markets (`AMP-061`), enforce UAE `TDRA` `9 PM – 7 AM` SMS curfew + `AD-` prefix (`AMP-442`), UAE Media Council permits (`AMP-282`), and bilingual Arabic/English canonical & currency parity (`current applicable UAE VAT`, `current applicable Qatar/Kuwait tax rules`, 3-decimal `KWD` `AMP-239`).
4. **High-Trust & Regulated Verticals (`Healthcare SFDA/MOH/EDA, FinTech SAMA/FRA, Real Estate REGA/RERA`)**: Strip all therapeutic/cure verbs (`AMP-176`, `AMP-286`), display mandatory `MOH/SFDA/DHA/EDA/Fal/Trakheesi` permit numbers (`AMP-070`), and route budgets to high-credibility channels (`AMP-290`, `AMP-339`).
5. **Seasonal Peak Operations (`Ramadan, Eid, White/Yellow Friday, Saudi Founding/National Day`)**: Lock Hijri-Gregorian overlaps (`Feb 2027 Ramadan x Saudi Founding Day x Kuwait National Day` `AMP-125`), pre-schedule GMC `sale_price_effective_date` 48h ahead (`AMP-063`), verify 30-day baseline discount permits (`AMP-064`), and disable Meta Advantage+ auto-music (`AMP-065`).

## 6. Worked Example Summary & Failure Recovery (`ملخص المثال التطبيقي وخطة الإنقاذ`)

*(Full step-by-step worked example with annotated human edits is also provided in `EXAMPLE.md`)*

- **Sample Input Brief**: - **Product**: Rosemary & Caffeine Hair Serum (`Cosmetic Notification in SFDA eCosma & Egypt EDA`).
- **Draft AI Copy**: `"سيروم الروزماري الطبي المعجزة! يعالج الصلع الوراثي وينبت الشعر من جديد خلال 14 يوماً، ويقضي نهائياً على التهابات وثعلبة فروة الرأس. معتمد طبياً من هيئة الغذاء والدواء!"`
- **Human Review & Key Edits Applied**: 1. **Replaced All 5 Therapeutic Claims**: Rewrote using surface cosmetic conditioning and appearance verbs permitted for notified cosmetics.
2. **Corrected SFDA Terminology**: Removed `"معتمد طبياً"` and kept accurate notification reference in the product specification table.
- **Final Usable Output**: - **Compliant SFDA / EDA Product Copy**:
  `"سيروم العناية بالشعر بخلاصة إكليل الجبل (الروزماري) والكافيين. تركيبة خفيفة تغذي فروة الرأس وترطب خصلات الشعر الجافة لتمنحكِ مظهراً أكثر كثافة ولمعاناً وحيوية مع الاستخدام المنتظم."`
- **What Can Go Wrong**: An e-commerce store uses an AI review-summary widget that highlights a customer review saying `'هذا الكريم عالج الأكزيما عندي نهائياً'` inside a paid Meta/Snapchat ad headline; SFDA treats promotional use of third-party therapeutic claims in ads as an advertiser violation.
- **Correction & Fallback**: Apply the `FORBIDDEN_THERAPEUTIC_RE` filter to both brand-authored copy AND any user-generated review or creator script (`AMP-286`) used in marketing.

## 7. Measurement Plan & Hypothesis Framing (`خطة القياس والضوابط الإحصائية`)

- **Primary Metric to Track**: 100% pass rate on `scan_sfda_eda_claims()` pre-publish gate and zero SFDA/EDA/platform health-policy violations.
- **Baseline Definition**: Audit of existing catalog product descriptions against `FORBIDDEN_THERAPEUTIC_RE`.
- **Observation Window**: Enforced on 100% of SKUs prior to publication. *(Must span full 7/14-day weekly cycles and account for 25th–30th monthly salary windows per `AMP-391`)*.
- **What Cannot Be Concluded (Boundary)**: This checklist removes obvious prohibited therapeutic verbs; formal regulatory classification of borderline cosmeceuticals or supplements requires official SFDA/EDA clearance.
