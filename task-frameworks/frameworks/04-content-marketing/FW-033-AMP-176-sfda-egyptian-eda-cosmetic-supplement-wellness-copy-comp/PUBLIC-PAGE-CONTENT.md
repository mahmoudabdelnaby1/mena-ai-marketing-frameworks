# Beauty, Supplement & Wellness Claims Review Checklist
## <span dir="rtl">قائمة مراجعة ادعاءات منتجات الجمال والمكملات والعافية</span>

> **Asset ID**: `FW-033` (`AMP-176`) | **Artifact Type**: `CHECKLIST` | **Channel**: Content Marketing | **Markets**: Egypt & GCC (`KSA, UAE, Kuwait, Qatar, Bahrain, Oman`) | **Version**: `1.2` (`Reviewed 2026-10-25`)

**What You Can Do With This (`ماذا يمكنك أن تنجز بهذه الأداة؟`)**:
- **EN**: Use this editorial checklist to flag health or treatment claims in beauty and supplement copy and route them for separate, current market-specific review. It does not determine whether a product or claim is permitted.
- **AR**: <span dir="rtl">استخدم قائمة المراجعة لرصد ادعاءات الصحة أو العلاج في محتوى الجمال والمكملات، ثم أحِلها إلى مراجعة حديثة ومخصصة لكل سوق. لا تحدد الأداة ما إذا كان المنتج أو الادعاء مسموحًا.</span>

## 1. Use It When & Required Inputs (`متى تستخدمها وما المدخلات المطلوبة؟`)

- **Use It When (EN)**: Use before publishing any product description, blog post, landing page, or ad script for cosmetics, perfumes, skincare, haircare, or dietary supplements in KSA, UAE, or Egypt.
- **متى تستخدمها (AR)**: <span dir="rtl">تُستخدم قبل نشر أي وصف منتج أو مقال أو إعلان لمنتجات التجميل والعناية بالبشرة والشعر والعطور والمكملات الغذائية في السعودية أو الإمارات أو مصر.</span>
- **When NOT to Use It (EN)**: Do not treat this checklist as a substitute for product classification, notification, registration, or market-specific approval checks. Confirm current requirements with the appropriate authority and qualified reviewer.
- **متى لا تستخدمها (AR)**: <span dir="rtl">لا تستخدم هذه القائمة بديلًا عن مراجعة التصنيف أو الإخطار أو التسجيل أو المتطلبات التنظيمية الحالية في السوق المعني.</span>

### Exact Inputs to Prepare (`المدخلات المطلوب تجهيزها قبل البدء`)
- Product SFDA `eCosma` / EDA Notification Category (`Cosmetic / منتج تجميلي` vs. `Health Supplement / مكمل غذائي`)
- Draft AI Product Copy, Bullet Points, and Video Script
- Approved Ingredient Function List (cosmetic appearance/hydration claims only)

## 2. The Working `CHECKLIST` (`الأداة الكاملة الجاهزة للنسخ والتطبيق الفوري`)

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

## 3. Complete End-to-End Worked Example (`مثال تطبيقي متكامل من المدخلات حتى المراجعة البشرية والنتيجة النهائية`)

*(Illustrative scenario — original example for training, never represented as a verified client outcome)*

### Step A: Sample Brief / Input (`موجز المدخلات`)
- **Product**: Rosemary & Caffeine Hair Serum (`Cosmetic Notification in SFDA eCosma & Egypt EDA`).
- **Draft AI Copy**: `"سيروم الروزماري الطبي المعجزة! يعالج الصلع الوراثي وينبت الشعر من جديد خلال 14 يوماً، ويقضي نهائياً على التهابات وثعلبة فروة الرأس. معتمد طبياً من هيئة الغذاء والدواء!"`

### Step B: Initial Output (`المخرج الأولي`)
- **`scan_sfda_eda_claims()` Result**:
  - `compliant`: `False` (`BLOCK`)
  - `flagged_therapeutic_terms`: `['يعالج', 'الصلع', 'ينبت الشعر', 'يقضي نهائياً', 'معتمد طبياً']`

### Step C: Human Review & Edits (`التدقيق البشري والتعديلات`)
1. **Replaced All 5 Therapeutic Claims**: Rewrote using surface cosmetic conditioning and appearance verbs permitted for notified cosmetics.
2. **Corrected SFDA Terminology**: Removed `"معتمد طبياً"` and kept accurate notification reference in the product specification table.

### Step D: Final Reviewed Example Outcome (`النتيجة النهائية المعتمدة`)
- **Compliant SFDA / EDA Product Copy**:
  `"سيروم العناية بالشعر بخلاصة إكليل الجبل (الروزماري) والكافيين. تركيبة خفيفة تغذي فروة الرأس وترطب خصلات الشعر الجافة لتمنحكِ مظهراً أكثر كثافة ولمعاناً وحيوية مع الاستخدام المنتظم."`

## 4. What Can Go Wrong & How to Fix It (`الأخطاء الشائعة وخطة الإنقاذ`)

- **Failure Case (`المشكلة المحتملة`)**: An e-commerce store uses an AI review-summary widget that highlights a customer review saying `'هذا الكريم عالج الأكزيما عندي نهائياً'` inside a paid Meta/Snapchat ad headline; SFDA treats promotional use of third-party therapeutic claims in ads as an advertiser violation.
- **Correction & Fallback (`الحل الإجرائي والبديل الآمن`)**: Apply the `FORBIDDEN_THERAPEUTIC_RE` filter to both brand-authored copy AND any user-generated review or creator script (`AMP-286`) used in marketing.

## 5. Model & Platform Capability Matrix (`مصفوفة قدرات النماذج والمنصات — 2026-10-25`)

| Platform / Model | Status | Official Documentation | MENA Operational Constraint | Fallback |
| :--- | :--- | :--- | :--- | :--- |
| **Saudi SFDA Cosmetic Products Law (Royal Decree M/49) & Executive Regulations** | `supported` | [Official Docs](https://www.sfda.gov.sa/en/regulations/62870) (`2026-10-25`) | SFDA regulations strictly define cosmetics as products intended for cleansing, perfuming, or improving appearance, and penalize unlicensed medical claims or misleading advertising under applicable local rules; confirm scope and current requirements with qualified review. | Consult a qualified regulatory affairs specialist in KSA/Egypt before publishing functional health claims. |

## 6. How to Measure Success (`خطة القياس والضوابط`)

- **Primary Metric**: 100% pass rate on `scan_sfda_eda_claims()` pre-publish gate and zero SFDA/EDA/platform health-policy violations.
- **Baseline**: Audit of existing catalog product descriptions against `FORBIDDEN_THERAPEUTIC_RE`.
- **Observation Window**: Enforced on 100% of SKUs prior to publication.
- **Interpretation Boundary**: This checklist removes obvious prohibited therapeutic verbs; formal regulatory classification of borderline cosmeceuticals or supplements requires official SFDA/EDA clearance.

## 7. Primary Sources & Evidence Boundaries (`المصادر الموثقة وحدود الأدلة`)

- [SFDA Detects Misleading Claims in Medical Device Advertisement](https://www.sfda.gov.sa/en/news/19412) — *Saudi Food and Drug Authority (SFDA)* (Published `2026-09-06`, Accessed `2026-10-25`): Active SFDA enforcement against unauthorized or exaggerated pain-relief/therapeutic claims in digital advertisements.
- [Violations Schedule of Cosmetic Products Law and Its Implementing Regulation and Penalties](https://www.sfda.gov.sa/en/regulations/62870) — *Saudi Food and Drug Authority (SFDA)* (Published `2026-09-02`, Accessed `2026-10-25`): Lists statutory penalties (that may apply to violations of the cosmetics law or its regulation, depending on the case under Cosmetic Products Law) for advertising unlisted cosmetics or making medical/therapeutic claims for cosmetic products.
- [SFDA Outlines Products Requiring Approval Before Advertising](https://www.sfda.gov.sa/en/news/17433) — *Saudi Food and Drug Authority (SFDA)* (Published `2024-07-27`, Accessed `2026-10-25`): Requires prior SFDA advertising clearance for regulated food, drug, supplement, and medical device promotions.
