# Creator Health, Beauty & Supplement Script Review Checklist
## <span dir="rtl">قائمة مراجعة نصوص المؤثرين في الصحة والتجميل والمكملات</span>

> **Asset ID**: `FW-058` (`AMP-286`) | **Artifact Type**: `CHECKLIST` | **Channel**: Influencer Marketing | **Markets**: Egypt & GCC (`KSA, UAE, Kuwait, Qatar, Bahrain, Oman`) | **Version**: `1.2` (`Reviewed 2026-10-25`)

**What You Can Do With This (`ماذا يمكنك أن تنجز بهذه الأداة؟`)**:
- **EN**: Review creator scripts and on-screen claims, record supporting evidence, and route regulated or health-related claims for separate market-specific review before publication.
- **AR**: <span dir="rtl">الفحص والاعتماد المسبق لما يقوله المؤثر أو يكتبه على الشاشة في إعلانات التجميل والمكملات والعيادات لمنع إطلاق ادعاءات علاجية غير مرخصة تعرض المعلن والمؤثر للمساءلة التضامنية وغرامات هيئة الغذاء والدواء (حتى 5 ملايين ريال).</span>

## 1. Use It When & Required Inputs (`متى تستخدمها وما المدخلات المطلوبة؟`)

- **Use It When (EN)**: Use when a creator or affiliate prepares health-related, product-performance, or regulated-category claims that need evidence and market-specific review.
- **متى تستخدمها (AR)**: <span dir="rtl">تُستخدم عند مراجعة ادعاءات المنتج أو الأداء أو الصحة التي يقدمها مؤثر أو شريك تسويق، مع إحالة الفئات المنظمة للمراجعة الخاصة بكل سوق.</span>
- **When NOT to Use It (EN)**: Never allow a creator in the health, beauty, food/honey, or supplement vertical to publish a 'Live / Direct Story Upload' without submitting the recorded video for pre-publication compliance sign-off first.
- **متى لا تستخدمها (AR)**: <span dir="rtl">لا تسمح لأي مؤثر في قطاعات التجميل أو المكملات أو العسل والأغذية أو العيادات بالنشر المباشر الفوري دون إرسال الفيديو المسجل لمراجعته واعتماده أولاً قبل النشر.</span>

### Exact Inputs to Prepare (`المدخلات المطلوب تجهيزها قبل البدء`)
- Recorded Creator Draft Video + Audio Transcript + On-Screen Captions (submitted 24–48h before scheduled posting)
- Product SFDA `eCosma` / Food / Supplement Notification Certificate or MOH/DHA/EDA Ad License
- SFDA/EDA Forbidden Claims Scanner (`AMP-176`)

## 2. The Working `CHECKLIST` (`الأداة الكاملة الجاهزة للنسخ والتطبيق الفوري`)

### Creator Health & Beauty Pre-Publication Compliance Gate

#### 1. Mandatory Pre-Post Video & Audio Audit Checklist (24h Before Going Live)
- [ ] **Check 1 — Audio Transcript Scan (`No Improvised Miracle / Disease Claims`)**:
  - Transcribe the creator's spoken audio (via Whisper/Gemini) and run `scan_sfda_eda_claims()` (`AMP-176`).
  - **Immediate Reshoot Triggers (`BLOCK POSTING`)**:
    - Claiming a cosmetic serum/cream treats a skin disease (`الأكزيما، الصدفية، الثعلبة، حب الشباب الكيسي، الكلف العميق، الحروق`).
    - Claiming a food item (e.g., Sidr honey, herbal tea, matcha) cures diabetes, cancer, infertility, or infections (`"يشفي السكر"`, `"يعالج القولون نهائياً"`, `"مضاد حيوي طبيعي يغني عن الدواء"` — strictly prosecuted by SFDA!).
    - Claiming a supplement guarantees rapid weight loss (`"ينحف 8 كيلو بالشهر بدون رياضة"`).
    - Claiming `"مرخص ومعتمد طبياً من هيئة الغذاء والدواء لعلاج..."` (Cosmetics are *notified/listed* `مدرج`, never "medically endorsed to cure" by SFDA!).
- [ ] **Check 2 — Visual Before/After & Filter Integrity**:
  - Confirm the creator is **NOT using beauty/skin-smoothing AR filters** while demonstrating a skincare/foundation product on camera.
  - Confirm no deceptive or digitally retouched Before/After photos are flashed on screen.
- [ ] **Check 3 — Mandatory Statutory Disclosures on Screen**:
  - `#إعلان` / `Paid Partnership` visible at top of every story/reel (`AMP-287`).
  - Active `Mawthooq` (KSA) or `UAE Media Council` permit verified (`AMP-281`/`AMP-282`).
  - If advertising a medical clinic/procedure or licensed OTC product, display the official `MOH / SFDA / DHA / EDA` ad license number on screen (`AMP-070`).

## 3. Complete End-to-End Worked Example (`مثال تطبيقي متكامل من المدخلات حتى المراجعة البشرية والنتيجة النهائية`)

*(Illustrative scenario — original example for training, never represented as a verified client outcome)*

### Step A: Sample Brief / Input (`موجز المدخلات`)
- **Brand**: Saudi Artisanal Sidr Honey & Wellness Store (`مدرج غذائياً`).
- **Creator Submitted Draft Video (Snapchat)**: Creator filmed a 30-second video saying: `"يا جماعة هذا العسل الملكي معجزة، والله الوالد كان عنده التهاب حاد في المعدة وسكر واستخدمه أسبوعين وترك أدوية المستشفى نهائياً! ومعتمد طبياً من الغذاء والدواء!"`

### Step B: Initial Output (`المخرج الأولي`)
- **Pre-Publication Gate Verdict**: **`CRITICAL BLOCK — DO NOT PUBLISH (SFDA Food & Drug Law Violation)`**
  - Flagged spoken violations:
    1. `"عالج التهاب حاد في المعدة وسكر"` (Unlicensed therapeutic drug claim on a food product).
    2. `"ترك أدوية المستشفى نهائياً"` (Dangerous medical advice encouraging patients to stop prescribed medication).
    3. `"معتمد طبياً من الغذاء والدواء"` (False regulatory endorsement claim).

### Step C: Human Review & Edits (`التدقيق البشري والتعديلات`)
1. **Requested Immediate Audio/Snap Reshoot (Took 15 Minutes)**: Provided the creator with the substantiated product description for qualified review (`عسل سدر طبيعي مفحوص مخبرياً، غني بالطعم الأصيل ومثالي للتحلية اليومية والضيافة`) and strictly forbade any mention of diseases or replacing medication.
2. **Verified Reshot Clip**: Confirmed 0 medical claims and clear `#إعلان` tag before granting written approval to post.

### Step D: Final Reviewed Example Outcome (`النتيجة النهائية المعتمدة`)
- Reshot compliant Snapchat story published safely with zero SFDA/GAMR violations, highlighting laboratory purity tests and taste rather than illegal medical claims.

## 4. What Can Go Wrong & How to Fix It (`الأخطاء الشائعة وخطة الإنقاذ`)

- **Failure Case (`المشكلة المحتملة`)**: An agency lets a beauty influencer post directly to Snapchat without pre-review; the influencer claims a Vitamin C serum 'permanently removes melasma and replaces laser surgery', triggering an SFDA inspection and fine against both the brand and the influencer.
- **Correction & Fallback (`الحل الإجرائي والبديل الآمن`)**: Include a **'Mandatory Pre-Publication Video Approval (`الاعتماد المسبق للفيديو قبل النشر`)'** clause in 100% of health, beauty, food/honey, and supplement creator contracts—stating that posting without written brand compliance sign-off forfeits payment and shifts liability.

## 5. Model & Platform Capability Matrix (`مصفوفة قدرات النماذج والمنصات — 2026-10-25`)

| Platform / Model | Status | Official Documentation | MENA Operational Constraint | Fallback |
| :--- | :--- | :--- | :--- | :--- |
| **Saudi SFDA Cosmetic & Food Advertising Enforcement (market-specific claims review) & Egypt EDA** | `supported` | [Official Docs](https://www.sfda.gov.sa/en/news/19412) (`2026-10-25`) | SFDA actively monitors social media influencer endorsements and enforces penalties under applicable local rules; confirm scope and current requirements with qualified review for misleading cosmetic/therapeutic claims. | Always transcribe and scan creator draft videos 24 hours before scheduled publication. |

## 6. How to Measure Success (`خطة القياس والضوابط`)

- **Primary Metric**: 100% of creator videos transcribed and cleared prior to publication (`0` unreviewed live posts in health/beauty/food) and `0` SFDA/EDA/GAMR notices.
- **Baseline**: Prior percentage of creator videos reviewed before vs. after posting.
- **Observation Window**: Enforced on 100% of creator deliverables.
- **Interpretation Boundary**: Pre-publication script review prevents severe statutory fines, while product demonstration quality drives sales.

## 7. Primary Sources & Evidence Boundaries (`المصادر الموثقة وحدود الأدلة`)

- [SFDA Detects Misleading Claims in Medical Device Advertisement](https://www.sfda.gov.sa/en/news/19412) — *Saudi Food and Drug Authority (SFDA)* (Published `2026-09-06`, Accessed `2026-10-25`): Active SFDA enforcement against unauthorized or exaggerated pain-relief/therapeutic claims in digital advertisements.
- [Violations Schedule of Cosmetic Products Law and Its Implementing Regulation and Penalties](https://www.sfda.gov.sa/en/regulations/62870) — *Saudi Food and Drug Authority (SFDA)* (Published `2026-09-02`, Accessed `2026-10-25`): Lists statutory penalties (market-specific regulatory consequences under Cosmetic Products Law) for advertising unlisted cosmetics or making medical/therapeutic claims for cosmetic products.
- [SFDA Outlines Products Requiring Approval Before Advertising](https://www.sfda.gov.sa/en/news/17433) — *Saudi Food and Drug Authority (SFDA)* (Published `2024-07-27`, Accessed `2026-10-25`): Requires prior SFDA advertising clearance for regulated food, drug, supplement, and medical device promotions.
