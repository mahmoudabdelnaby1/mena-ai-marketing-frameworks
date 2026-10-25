# FW-017: Meta Advantage+ Creative Auto-Enhancement Guardrail Checklist for Arab & Ramadan Campaigns
## قائمة فحص وضبط التحسينات التلقائية (`Meta Advantage+ Creative`) لحماية الهوية البصرية والنصوص العربية وحملات رمضان

- **Consolidated Contextual Child IDs (`MERGE_INTO_EXISTING`)**: `AMP-075`, `AMP-085`, `AMP-095`, `AMP-105`, `AMP-115`
- **Selected Artifact Type**: `CHECKLIST`
- **Intended Audience**: Performance Marketing Manager, Media Buyer, PPC Specialist, Growth Lead
- **Target Markets & Languages**: Egypt & GCC (`Saudi Arabia, UAE, Kuwait, Qatar, Bahrain, Oman`) — Bilingual Arabic (`Egyptian Ammiya`, `Saudi/Gulf Khaleeji`, `White MSA`) + English
- **Version**: `1.2` | **Last Reviewed**: `2026-10-25` | **Status**: `READY_FOR_REVIEW`

## 1. Plain-Language Promise & Why This Artifact Form Fits the Job

- **What You Can Make or Decide (EN)**: Disable destructive Meta Advantage+ Creative auto-enhancements that inject unapproved music during Ramadan, warp Arabic typography, or shift luxury brand colors.
- **ما الذي يمكنك إنجازه أو حسمه بهذه الأداة (AR)**: تعطيل التحسينات التلقائية الضارة في `Meta Advantage+ Creative` التي تضيف موسيقى غير ملائمة في حملات رمضان أو تشوه الخطوط العربية أو تغير ألوان العلامة التجارية.
- **Why `CHECKLIST` Fits This User Job (EN)**: Meta Ads Manager enables Advantage+ Creative enhancements by default on new ads, silently adding AI music tracks, expanding backgrounds with hallucinated artifacts, and swapping Arabic headline positions; a toggle-by-toggle CHECKLIST gives media buyers exact control before hitting Publish.
- **لماذا يناسب شكل `CHECKLIST` هذه المهمة (AR)**: تفعّل منصة Meta تحسينات `Advantage+ Creative` افتراضياً، مما يؤدي إلى إضافة موسيقى صاخبة لحملات رمضان أو تشويه الخط العربي وتغيير ألوان المنتجات؛ وتمنح قائمة الفحص هذه المشتري الإعلاني تحكماً كاملاً قبل النشر.

## 2. "Use It When" Trigger, Boundaries & Exact Inputs to Prepare

- **Use It When (EN)**: Use at the Ad level in Meta Ads Manager before publishing any image, video, or catalog ad in KSA, UAE, Egypt, or wider MENA.
- **متى تستخدم هذه الأداة (AR)**: تُستخدم على مستوى الإعلان (`Ad Level`) في مدير إعلانات Meta قبل نشر أي إعلان مصور أو فيديو أو كتالوج في أسواق المنطقة.
- **When NOT to Use It (EN)**: Do not leave 'All optimizations ON' when advertising culturally sensitive categories (Ramadan/Hajj, Islamic finance, luxury fashion, SFDA-regulated healthcare/cosmetics).
- **متى لا تستخدم هذه الأداة (AR)**: لا تترك خيار «تفعيل كافة التحسينات» مفعلاً في حملات المواسم الدينية (رمضان/الحج) أو التمويل الإسلامي أو المنتجات الفاخرة أو القطاع الصحي الخاضع لهيئة الغذاء والدواء.

### Exact Inputs to Prepare Before Starting (`المدخلات المطلوب تجهيزها`)
1. Meta Ads Manager Ad-Level Creative Setup screen
2. Brand Audio & Cultural Policy (e.g., voiceover/nasheed/percussion-only rule for KSA/Ramadan campaigns)
3. Native 9:16 (`1080x1920`) and 1:1 (`1080x1080`) Arabic creative assets

### Privacy-Safe Data Handling (`ضوابط الخصوصية وحماية البيانات الشخصية PDPL`)
- **Strict PII Redaction Before Prompting**: Under Saudi PDPL (Art. 25), UAE Federal Decree-Law No. 45 of 2021, Qatar Law No. 13 of 2016, and Egypt Law No. 151 of 2020, **never paste raw customer names, unhashed mobile numbers (`+9665...` / `+201...`), email addresses, national IDs, or private WhatsApp transcripts into public/consumer LLM interfaces**. Use anonymized placeholders (`{first_name}`, `ORD_10045`) during prompt testing and restrict live customer data to zero-data-retention enterprise API endpoints or local deterministic scripts.

## 3. The Directly Usable Artifact (`الأداة التطبيقية الجاهزة للنسخ والتنفيذ`)

### Meta Advantage+ Creative Toggle Governance Matrix (Ad Level)

| Advantage+ Creative Toggle in Meta Ads Manager | Default Meta State | Mandatory MENA Action (`TURN OFF` vs `SAFE`) | Why (MENA & Arabic Failure Mechanism) |
| :--- | :--- | :--- | :--- |
| **1. Add Music (`إضافة موسيقى`)** | Often `ON` | **`TURN OFF (حرج جداً)`** | Automatically overlays Western pop/electronic tracks onto silent or voice-only Arabic graphics—provoking severe audience backlash in Saudi Arabia, Ramadan/Eid campaigns, and Islamic finance/charity ads. |
| **2. Image Expansion / Outpainting (`توسيع الصورة`)** | `ON` | **`TURN OFF` (Supply native 9:16 & 1:1 instead)** | AI outpainting hallucinates distorted borders, extra fingers, or garbled pseudo-Arabic calligraphy around product packaging. |
| **3. Visual Touch-ups / Brightness & Contrast (`اللمسات المرئية وتعديل الألوان`)** | `ON` | **`TURN OFF` for Fashion, Cosmetics, Jewelry & Real Estate** | Alters true fabric/skin/gold shades, causing high COD return rates (`"اللون في الحقيقة غير الإعلان"`). |
| **4. Text Improvements / Headline Swaps (`تحسينات النص وتبديل العناوين`)** | `ON` | **`TURN OFF` for Regulated Copy (`SFDA/EDA/PDPL/Discounts`)** | Moves disclaimers or pulls random comment/caption fragments into the headline slot, breaking Arabic grammar or detaching statutory permit numbers (`AMP-064`). |
| **5. Add Overlays / Info Labels (`إضافة طبقات نصية / شارات`)** | `ON` | **`TURN OFF` if image already contains Arabic price/offer badges** | Renders awkward LTR overlays on top of existing Arabic typography or covers `Tabby/Tamara` badges. |
| **6. Relevant Comments (`التعليقات ذات الصلة`)** | `ON` | **Review / `TURN OFF` if unmoderated dialectal sarcasm exists** | Can pin a sarcastic Egyptian or Gulf comment below the ad. |

#### Pre-Publish Verification Steps
- [ ] Click **`Edit` (`تعديل`)** inside the `Advantage+ creative` panel on every ad (and inside Catalog Dynamic Templates).
- [ ] Click **`Preview all enhancements`** and inspect both Instagram Reels (`9:16`) and Facebook Feed (`1:1`/`4:5`) previews with audio unmuted.
- [ ] When cloning ad sets or importing via bulk sheet, re-verify toggles (Meta frequently resets enhancements to `ON` on new placements).

## 4. Model & Platform Capability Branches (`فروع قدرات النماذج والمنصات والبدائل الاحتياطية`)

| System / Platform | Capability Status | Official Documentation & Access Date | Operational Constraint in Egypt & GCC | Fallback When Feature/Modality Is Unavailable |
| :--- | :--- | :--- | :--- | :--- |
| **Meta Ads Manager Advantage+ Creative Enhancements** | `supported` | [Official Reference](https://www.hyperfx.ai/blog/meta-advantage-creative-enhancements-issues) (`2026-10-25`) | Meta enables multiple generative creative enhancements by default; individual toggles must be manually disabled at the Ad level. | Always supply native 1:1, 4:5, and 9:16 placement ratios so `Expand Image` is never required. |

## 5. Consolidated Regional & Vertical Adaptation Matrix (`دمج الأنماط السياقية الفرعية بدون حشو`)

Per Agent 2 v1.2's anti-padding rule, the following **5 cross-verified contextual synthesis patterns** and **0 screened duplicate variants** share this core mechanism and are consolidated directly into this source-of-truth framework:

| Child Pattern ID | Disposition | Regional / Sector Operating Context | Specific Adaptation & Guardrail Integrated in This Asset | Evidence Tier |
| :--- | :--- | :--- | :--- | :--- |
| **`AMP-075`** | `MERGE_INTO_EXISTING` | Egyptian E-Commerce & Social Commerce (Shopify / WooCommerce / Cairo & Alexandria) | Explicitly toggling off all 7+ ad-level Advantage+ Creative auto-enhancements and account-level AI testing before publishing.; Specifically impacts Egyptian brands operating in EGP where merchant-specific payment mix from recent order records, Mobile Wallets (Vodafone Cash), InstaPay, and Fawry dominate. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-085`** | `MERGE_INTO_EXISTING` | UAE & Multi-Market GCC Enterprise / Retail (Dubai, Abu Dhabi, Doha, Kuwait) | Explicitly toggling off all 7+ ad-level Advantage+ Creative auto-enhancements and account-level AI testing before publishing.; Specifically impacts bilingual Arabic/English campaigns in high-CPM, expat-dense Gulf markets under UAE PDPL / TDRA and Qatari regulations. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-095`** | `MERGE_INTO_EXISTING` | High-Trust & Regulated Verticals (Healthcare/SFDA/EDA, Fintech/SAMA/FRA, Real Estate) | Explicitly toggling off all 7+ ad-level Advantage+ Creative auto-enhancements and account-level AI testing before publishing.; Specifically impacts regulated claims requiring SFDA, EDA, MOH, SAMA, FRA, or RERA compliance pre-clearance and strict hallucination guardrails. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-105`** | `MERGE_INTO_EXISTING` | Seasonal Peak Operations (Ramadan, Eid, White/Yellow Friday, Saudi Founding/National Day) | Explicitly toggling off all 7+ ad-level Advantage+ Creative auto-enhancements and account-level AI testing before publishing.; Specifically impacts high-velocity seasonal surges where CPMs jump 40-70%, prices change rapidly, and Hijri calendar cultural sensitivity is paramount. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-115`** | `MERGE_INTO_EXISTING` | Multi-Client Agency & MarTech API Automation Pipelines (LLM APIs, Webhooks, GA4, CAPI) | Explicitly toggling off all 7+ ad-level Advantage+ Creative auto-enhancements and account-level AI testing before publishing.; Specifically impacts automated multi-SKU or multi-client LLM/API pipelines where schema validation, token cost, and attribution governance are required. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |

### Context-Specific Execution Knobs Across the 5 MENA Operating Environments
1. **Saudi D2C E-Commerce (`Salla / Zid / Riyadh & Jeddah Retail`)**: Enforce `SAR` tax-inclusive pricing (`15% ZATCA VAT`), native `Mada / Apple Pay / Tabby / Tamara` visibility (`AMP-387`), `GAMR Mawthooq` creator verification (`AMP-281`), and White Saudi Khaleeji orthography (`AMP-002`, `AMP-177`).
2. **Egyptian E-Commerce & Social Commerce (`Shopify / WooCommerce / Cairo & Alexandria`)**: Use each merchant’s own order and payment data to assess Cash on Delivery (`COD`), mobile wallets, InstaPay, Fawry, `valU`, address fields, and pre-dispatch WhatsApp confirmation. Verify current provider terms and local requirements before implementation.
3. **UAE & Multi-Market GCC Enterprise / Retail (`Dubai, Abu Dhabi, Doha, Kuwait`)**: Separate high-CPM UAE/Qatar budgets from lower-CPM markets (`AMP-061`), enforce UAE `TDRA` `9 PM – 7 AM` SMS curfew + `AD-` prefix (`AMP-442`), UAE Media Council permits (`AMP-282`), and bilingual Arabic/English canonical & currency parity (`current applicable UAE VAT`, `current applicable Qatar/Kuwait tax rules`, 3-decimal `KWD` `AMP-239`).
4. **High-Trust & Regulated Verticals (`Healthcare SFDA/MOH/EDA, FinTech SAMA/FRA, Real Estate REGA/RERA`)**: Strip all therapeutic/cure verbs (`AMP-176`, `AMP-286`), display mandatory `MOH/SFDA/DHA/EDA/Fal/Trakheesi` permit numbers (`AMP-070`), and route budgets to high-credibility channels (`AMP-290`, `AMP-339`).
5. **Seasonal Peak Operations (`Ramadan, Eid, White/Yellow Friday, Saudi Founding/National Day`)**: Lock Hijri-Gregorian overlaps (`Feb 2027 Ramadan x Saudi Founding Day x Kuwait National Day` `AMP-125`), pre-schedule GMC `sale_price_effective_date` 48h ahead (`AMP-063`), verify 30-day baseline discount permits (`AMP-064`), and disable Meta Advantage+ auto-music (`AMP-065`).

## 6. Worked Example Summary & Failure Recovery (`ملخص المثال التطبيقي وخطة الإنقاذ`)

*(Full step-by-step worked example with annotated human edits is also provided in `EXAMPLE.md`)*

- **Sample Input Brief**: - **Campaign**: Saudi Ramadan Oud & Gift Box Campaign on Instagram Reels & Facebook Feed (`SAR 150,000` budget).
- **Incident Prevented**: Media buyer uploaded a serene 1:1 static graphic with Arabic calligraphy (`"رمضان يجمعنا على الطيب"`). Meta Advantage+ Creative defaulted `Add Music` (`ON`) with an upbeat Western dance track and `Image Expansion` (`ON`) which stretched the top of the Oud bottle into a crooked shape.
- **Human Review & Key Edits Applied**: 1. **Disabled All 3 Destructive Toggles**: Turned OFF `Add Music`, `Expand Image`, and `Visual Touch-ups`.
2. **Uploaded Native Placement Assets**: Supplied a dedicated `1080x1920` (9:16) graphic and a `1080x1080` (1:1) graphic created by the design team so no AI outpainting was needed.
- **Final Usable Output**: - Campaign launched across KSA with 100% brand-faithful colors, native 9:16/1:1 geometry, and zero unapproved audio tracks.
- **What Can Go Wrong**: An agency turns off Advantage+ Creative toggles on Ad #1, then uses 'Duplicate Ad' and changes the media file—Meta Ads Manager silently re-enables `Expand Image` and `Visual Touch-ups` when new media is selected.
- **Correction & Fallback**: Always make the Advantage+ Creative toggle check the **very last step after uploading final media**, immediately before clicking the green `Publish` button.

## 7. Measurement Plan & Hypothesis Framing (`خطة القياس والضوابط الإحصائية`)

- **Primary Metric to Track**: Zero negative brand/audio sentiment comments on ads and reduced post-delivery 'item looks different from photo' COD return rate.
- **Baseline Definition**: Comment sentiment and return reason log from prior campaigns.
- **Observation Window**: Checked at launch + day 3 of every campaign. *(Must span full 7/14-day weekly cycles and account for 25th–30th monthly salary windows per `AMP-391`)*.
- **What Cannot Be Concluded (Boundary)**: Disabling destructive auto-enhancements protects brand trust and compliance, while creative hook quality drives CTR.
