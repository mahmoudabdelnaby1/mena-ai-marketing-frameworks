# FW-058: Creator Health, Beauty & Supplement Script Review Checklist
## قائمة مراجعة نصوص المؤثرين في الصحة والتجميل والمكملات

- **Consolidated Contextual Child IDs (`MERGE_INTO_EXISTING`)**: `AMP-296`, `AMP-306`, `AMP-316`, `AMP-326`
- **Selected Artifact Type**: `CHECKLIST`
- **Intended Audience**: Influencer Marketing Manager, PR & Communications Lead, Talent Coordinator, Legal & Compliance Lead
- **Target Markets & Languages**: Egypt & GCC (`Saudi Arabia, UAE, Kuwait, Qatar, Bahrain, Oman`) — Bilingual Arabic (`Egyptian Ammiya`, `Saudi/Gulf Khaleeji`, `White MSA`) + English
- **Version**: `1.2` | **Last Reviewed**: `2026-10-25` | **Status**: `READY_FOR_REVIEW`

## 1. Plain-Language Promise & Why This Artifact Form Fits the Job

- **What You Can Make or Decide (EN)**: Review creator scripts and on-screen claims, record supporting evidence, and route regulated or health-related claims for separate market-specific review before publication.
- **ما الذي يمكنك إنجازه أو حسمه بهذه الأداة (AR)**: الفحص والاعتماد المسبق لما يقوله المؤثر أو يكتبه على الشاشة في إعلانات التجميل والمكملات والعيادات لمنع إطلاق ادعاءات علاجية غير مرخصة تعرض المعلن والمؤثر للمساءلة التضامنية وغرامات هيئة الغذاء والدواء (حتى 5 ملايين ريال).
- **Why `CHECKLIST` Fits This User Job (EN)**: Even when a brand's own website copy is compliant (`AMP-176`), creators improvising on Snapchat or TikTok frequently exaggerate (`'والله هالكريم عالج لي الأكزيما والحروق نهائياً!'` or `'هالفيتامين ينزل الوزن 10 كيلو بدون رجيم!'`); under Saudi SFDA & GAMR rules and Egyptian EDA/CPA laws, both the advertiser and the endorser face liability for unapproved therapeutic claims—making a pre-publish video review CHECKLIST mandatory.
- **لماذا يناسب شكل `CHECKLIST` هذه المهمة (AR)**: حتى عندما يكون موقع المتجر ملتزماً (`AMP-176`)، قد يرتجل المؤثر أثناء التصوير فيطلق وعوداً طبية مبالغاً فيها («هذا الكريم عالج لي الأكزيما نهائياً!» أو «ينزل 10 كيلو في أسبوع!»)، مما يوقع العلامة التجارية والمؤثر تحت طائلة غرامات هيئة الغذاء والدواء؛ لذا تفرض قائمة الفحص هذه المراجعة المسبقة للفيديو قبل نشره.

## 2. "Use It When" Trigger, Boundaries & Exact Inputs to Prepare

- **Use It When (EN)**: Use when a creator or affiliate prepares health-related, product-performance, or regulated-category claims that need evidence and market-specific review.
- **متى تستخدم هذه الأداة (AR)**: تُستخدم عند مراجعة ادعاءات المنتج أو الأداء أو الصحة التي يقدمها مؤثر أو شريك تسويق، مع إحالة الفئات المنظمة للمراجعة الخاصة بكل سوق.
- **When NOT to Use It (EN)**: Never allow a creator in the health, beauty, food/honey, or supplement vertical to publish a 'Live / Direct Story Upload' without submitting the recorded video for pre-publication compliance sign-off first.
- **متى لا تستخدم هذه الأداة (AR)**: لا تسمح لأي مؤثر في قطاعات التجميل أو المكملات أو العسل والأغذية أو العيادات بالنشر المباشر الفوري دون إرسال الفيديو المسجل لمراجعته واعتماده أولاً قبل النشر.

### Exact Inputs to Prepare Before Starting (`المدخلات المطلوب تجهيزها`)
1. Recorded Creator Draft Video + Audio Transcript + On-Screen Captions (submitted 24–48h before scheduled posting)
2. Product SFDA `eCosma` / Food / Supplement Notification Certificate or MOH/DHA/EDA Ad License
3. SFDA/EDA Forbidden Claims Scanner (`AMP-176`)

### Privacy-Safe Data Handling (`ضوابط الخصوصية وحماية البيانات الشخصية PDPL`)
- **Strict PII Redaction Before Prompting**: Under Saudi PDPL (Art. 25), UAE Federal Decree-Law No. 45 of 2021, Qatar Law No. 13 of 2016, and Egypt Law No. 151 of 2020, **never paste raw customer names, unhashed mobile numbers (`+9665...` / `+201...`), email addresses, national IDs, or private WhatsApp transcripts into public/consumer LLM interfaces**. Use anonymized placeholders (`{first_name}`, `ORD_10045`) during prompt testing and restrict live customer data to zero-data-retention enterprise API endpoints or local deterministic scripts.

## 3. The Directly Usable Artifact (`الأداة التطبيقية الجاهزة للنسخ والتنفيذ`)

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

## 4. Model & Platform Capability Branches (`فروع قدرات النماذج والمنصات والبدائل الاحتياطية`)

| System / Platform | Capability Status | Official Documentation & Access Date | Operational Constraint in Egypt & GCC | Fallback When Feature/Modality Is Unavailable |
| :--- | :--- | :--- | :--- | :--- |
| **Saudi SFDA Cosmetic & Food Advertising Enforcement (market-specific claims review) & Egypt EDA** | `supported` | [Official Reference](https://www.sfda.gov.sa/en/news/19412) (`2026-10-25`) | SFDA actively monitors social media influencer endorsements and enforces penalties under applicable local rules; confirm scope and current requirements with qualified review for misleading cosmetic/therapeutic claims. | Always transcribe and scan creator draft videos 24 hours before scheduled publication. |

## 5. Consolidated Regional & Vertical Adaptation Matrix (`دمج الأنماط السياقية الفرعية بدون حشو`)

Per Agent 2 v1.2's anti-padding rule, the following **4 cross-verified contextual synthesis patterns** and **0 screened duplicate variants** share this core mechanism and are consolidated directly into this source-of-truth framework:

| Child Pattern ID | Disposition | Regional / Sector Operating Context | Specific Adaptation & Guardrail Integrated in This Asset | Evidence Tier |
| :--- | :--- | :--- | :--- | :--- |
| **`AMP-296`** | `MERGE_INTO_EXISTING` | Egyptian E-Commerce & Social Commerce (Shopify / WooCommerce / Cairo & Alexandria) | Strict 'claims requiring substantiation and market-specific review' redline table attached to every creator contract.; Specifically impacts Egyptian brands operating in EGP where merchant-specific payment mix from recent order records, Mobile Wallets (Vodafone Cash), InstaPay, and Fawry dominate. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-306`** | `MERGE_INTO_EXISTING` | UAE & Multi-Market GCC Enterprise / Retail (Dubai, Abu Dhabi, Doha, Kuwait) | Strict 'claims requiring substantiation and market-specific review' redline table attached to every creator contract.; Specifically impacts bilingual Arabic/English campaigns in high-CPM, expat-dense Gulf markets under UAE PDPL / TDRA and Qatari regulations. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-316`** | `MERGE_INTO_EXISTING` | High-Trust & Regulated Verticals (Healthcare/SFDA/EDA, Fintech/SAMA/FRA, Real Estate) | Strict 'claims requiring substantiation and market-specific review' redline table attached to every creator contract.; Specifically impacts regulated claims requiring SFDA, EDA, MOH, SAMA, FRA, or RERA compliance pre-clearance and strict hallucination guardrails. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-326`** | `MERGE_INTO_EXISTING` | Seasonal Peak Operations (Ramadan, Eid, White/Yellow Friday, Saudi Founding/National Day) | Strict 'claims requiring substantiation and market-specific review' redline table attached to every creator contract.; Specifically impacts high-velocity seasonal surges where CPMs jump 40-70%, prices change rapidly, and Hijri calendar cultural sensitivity is paramount. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |

### Context-Specific Execution Knobs Across the 5 MENA Operating Environments
1. **Saudi D2C E-Commerce (`Salla / Zid / Riyadh & Jeddah Retail`)**: Enforce `SAR` tax-inclusive pricing (`15% ZATCA VAT`), native `Mada / Apple Pay / Tabby / Tamara` visibility (`AMP-387`), `GAMR Mawthooq` creator verification (`AMP-281`), and White Saudi Khaleeji orthography (`AMP-002`, `AMP-177`).
2. **Egyptian E-Commerce & Social Commerce (`Shopify / WooCommerce / Cairo & Alexandria`)**: Use each merchant’s own order and payment data to assess Cash on Delivery (`COD`), mobile wallets, InstaPay, Fawry, `valU`, address fields, and pre-dispatch WhatsApp confirmation. Verify current provider terms and local requirements before implementation.
3. **UAE & Multi-Market GCC Enterprise / Retail (`Dubai, Abu Dhabi, Doha, Kuwait`)**: Separate high-CPM UAE/Qatar budgets from lower-CPM markets (`AMP-061`), enforce UAE `TDRA` `9 PM – 7 AM` SMS curfew + `AD-` prefix (`AMP-442`), UAE Media Council permits (`AMP-282`), and bilingual Arabic/English canonical & currency parity (`current applicable UAE VAT`, `current applicable Qatar/Kuwait tax rules`, 3-decimal `KWD` `AMP-239`).
4. **High-Trust & Regulated Verticals (`Healthcare SFDA/MOH/EDA, FinTech SAMA/FRA, Real Estate REGA/RERA`)**: Strip all therapeutic/cure verbs (`AMP-176`, `AMP-286`), display mandatory `MOH/SFDA/DHA/EDA/Fal/Trakheesi` permit numbers (`AMP-070`), and route budgets to high-credibility channels (`AMP-290`, `AMP-339`).
5. **Seasonal Peak Operations (`Ramadan, Eid, White/Yellow Friday, Saudi Founding/National Day`)**: Lock Hijri-Gregorian overlaps (`Feb 2027 Ramadan x Saudi Founding Day x Kuwait National Day` `AMP-125`), pre-schedule GMC `sale_price_effective_date` 48h ahead (`AMP-063`), verify 30-day baseline discount permits (`AMP-064`), and disable Meta Advantage+ auto-music (`AMP-065`).

## 6. Worked Example Summary & Failure Recovery (`ملخص المثال التطبيقي وخطة الإنقاذ`)

*(Full step-by-step worked example with annotated human edits is also provided in `EXAMPLE.md`)*

- **Sample Input Brief**: - **Brand**: Saudi Artisanal Sidr Honey & Wellness Store (`مدرج غذائياً`).
- **Creator Submitted Draft Video (Snapchat)**: Creator filmed a 30-second video saying: `"يا جماعة هذا العسل الملكي معجزة، والله الوالد كان عنده التهاب حاد في المعدة وسكر واستخدمه أسبوعين وترك أدوية المستشفى نهائياً! ومعتمد طبياً من الغذاء والدواء!"`
- **Human Review & Key Edits Applied**: 1. **Requested Immediate Audio/Snap Reshoot (Took 15 Minutes)**: Provided the creator with the substantiated product description for qualified review (`عسل سدر طبيعي مفحوص مخبرياً، غني بالطعم الأصيل ومثالي للتحلية اليومية والضيافة`) and strictly forbade any mention of diseases or replacing medication.
2. **Verified Reshot Clip**: Confirmed 0 medical claims and clear `#إعلان` tag before granting written approval to post.
- **Final Usable Output**: - Reshot compliant Snapchat story published safely with zero SFDA/GAMR violations, highlighting laboratory purity tests and taste rather than illegal medical claims.
- **What Can Go Wrong**: An agency lets a beauty influencer post directly to Snapchat without pre-review; the influencer claims a Vitamin C serum 'permanently removes melasma and replaces laser surgery', triggering an SFDA inspection and fine against both the brand and the influencer.
- **Correction & Fallback**: Include a **'Mandatory Pre-Publication Video Approval (`الاعتماد المسبق للفيديو قبل النشر`)'** clause in 100% of health, beauty, food/honey, and supplement creator contracts—stating that posting without written brand compliance sign-off forfeits payment and shifts liability.

## 7. Measurement Plan & Hypothesis Framing (`خطة القياس والضوابط الإحصائية`)

- **Primary Metric to Track**: 100% of creator videos transcribed and cleared prior to publication (`0` unreviewed live posts in health/beauty/food) and `0` SFDA/EDA/GAMR notices.
- **Baseline Definition**: Prior percentage of creator videos reviewed before vs. after posting.
- **Observation Window**: Enforced on 100% of creator deliverables. *(Must span full 7/14-day weekly cycles and account for 25th–30th monthly salary windows per `AMP-391`)*.
- **What Cannot Be Concluded (Boundary)**: Pre-publication script review prevents severe statutory fines, while product demonstration quality drives sales.
