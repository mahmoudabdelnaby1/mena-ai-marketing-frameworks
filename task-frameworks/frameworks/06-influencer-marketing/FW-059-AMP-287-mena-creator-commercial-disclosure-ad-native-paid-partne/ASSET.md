# FW-059: MENA Creator Commercial Disclosure (`#إعلان` / `#Ad`) & Native Paid-Partnership Tagging Checklist
## قائمة فحص الإفصاح الإعلاني الإلزامي للمؤثرين (`#إعلان` / `#Ad` ووسم الشراكة المدفوعة) في قصص وفيديوهات التواصل الاجتماعي

- **Consolidated Contextual Child IDs (`MERGE_INTO_EXISTING`)**: `AMP-297`, `AMP-307`, `AMP-317`, `AMP-327`
- **Selected Artifact Type**: `CHECKLIST`
- **Intended Audience**: Influencer Marketing Manager, PR & Communications Lead, Talent Coordinator, Legal & Compliance Lead
- **Target Markets & Languages**: Egypt & GCC (`Saudi Arabia, UAE, Kuwait, Qatar, Bahrain, Oman`) — Bilingual Arabic (`Egyptian Ammiya`, `Saudi/Gulf Khaleeji`, `White MSA`) + English
- **Version**: `1.2` | **Last Reviewed**: `2026-10-25` | **Status**: `READY_FOR_REVIEW`

## 1. Plain-Language Promise & Why This Artifact Form Fits the Job

- **What You Can Make or Decide (EN)**: Ensure every sponsored creator Story, Reel, TikTok, and X post displays an unmistakable, unhidden `#إعلان` / `#Ad` label and native platform Paid Partnership toggle in compliance with KSA GAMR, UAE Media Council, and Egypt CPA rules.
- **ما الذي يمكنك إنجازه أو حسمه بهذه الأداة (AR)**: ضمان ظهور وسم الإفصاح الإعلاني (`#إعلان` / `#Ad`) وتفعيل خيار «الشراكة المدفوعة» بوضوح تام في كافة قصص وفيديوهات المؤثرين امتثالاً لضوابط الهيئة العامة لتنظيم الإعلام السعودية ومجلس الإمارات للإعلام وجهاز حماية المستهلك المصري.
- **Why `CHECKLIST` Fits This User Job (EN)**: Creators frequently hide `#إعلان` in tiny white font on a white background in the top corner of a Snapchat story, bury it under 'See more' on TikTok/IG, or omit it on gifted/affiliate posts—violating both national media laws (KSA GAMR, UAE Media Council) and platform branded-content policies; a visual placement CHECKLIST guarantees unmistakable disclosure.
- **لماذا يناسب شكل `CHECKLIST` هذه المهمة (AR)**: يعمد بعض المؤثرين إلى تصغير وسم `#إعلان` أو تلوينه بلون مطابق للخلفية في زاوية السنابة أو إخفائه تحت «عرض المزيد»، مما يعد مخالفة صريحة لأنظمة الإعلام في السعودية والإمارات وسياسات المنصات؛ لذا تحدد قائمة الفحص هذه المواصفات البصرية الإلزامية للإفصاح.

## 2. "Use It When" Trigger, Boundaries & Exact Inputs to Prepare

- **Use It When (EN)**: Use on every paid, barter, gifted, affiliate-code, or ambassador post across Snapchat, Instagram, TikTok, YouTube, and X in MENA.
- **متى تستخدم هذه الأداة (AR)**: تُستخدم في جميع إعلانات المؤثرين (سواء كانت مدفوعة نقداً، أو مقايضة/هدايا، أو عبر كود خصم بالعمولة، أو سفراء علامة تجارية) على كافة المنصات.
- **When NOT to Use It (EN)**: Do not accept ambiguous tags like `#تعاون` (`#Collab`), `#شكراً_[اسم_البراند]`, or `#دعم` as substitutes for explicit `#إعلان` or `#مادة_إعلانية`.
- **متى لا تستخدم هذه الأداة (AR)**: لا تقبل عبارات مبهمة مثل `#تعاون` أو `#هدية` أو `#دعم` كبديل عن الوسم النظامي الصريح `#إعلان` أو `#مادة_إعلانية`.

### Exact Inputs to Prepare Before Starting (`المدخلات المطلوب تجهيزها`)
1. Creator Draft Story Frames / Video Cut (`AMP-286`)
2. Platform Branded Content / Paid Partnership partner handle (`@brand_handle`)

### Privacy-Safe Data Handling (`ضوابط الخصوصية وحماية البيانات الشخصية PDPL`)
- **Strict PII Redaction Before Prompting**: Under Saudi PDPL (Art. 25), UAE Federal Decree-Law No. 45 of 2021, Qatar Law No. 13 of 2016, and Egypt Law No. 151 of 2020, **never paste raw customer names, unhashed mobile numbers (`+9665...` / `+201...`), email addresses, national IDs, or private WhatsApp transcripts into public/consumer LLM interfaces**. Use anonymized placeholders (`{first_name}`, `ORD_10045`) during prompt testing and restrict live customer data to zero-data-retention enterprise API endpoints or local deterministic scripts.

## 3. The Directly Usable Artifact (`الأداة التطبيقية الجاهزة للنسخ والتنفيذ`)

### Visual & Technical `#إعلان` / `#Ad` Disclosure Checklist (KSA, UAE & Egypt)

#### 1. Mandatory Disclosure Placement Rules by Format
| Platform & Format | Required Visible Arabic/English Text Label | Required Native Platform Toggle | Prohibited Evasion Tactics (`FAIL — REJECT`) |
| :--- | :--- | :--- | :--- |
| **Snapchat Multi-Snap Story** | **`#إعلان`** or **`مادة إعلانية`** placed visibly inside the top safe zone of **EVERY single snap frame** in the ad sequence (not just Snap #1!). | Enable Snapchat **Paid Partnership (`شراكة مدفوعة`)** tag linking `@brand`. | Hiding `#إعلان` behind the creator's top-right avatar/name bar, shrinking font to `<14pt`, or using low-contrast white-on-beige text. |
| **TikTok Video / Shop** | **`#إعلان`** (`#Ad`) in the first line of the caption (before `'...more'`) + visible on-screen badge during the hook. | Turn ON **`Content Disclosure -> Commercial Content -> Branded Content`**. (Plus `AIGC` toggle if AI-generated `AMP-124`!). | Putting `#إعلان` at the end of 15 hashtags where it is hidden unless the viewer expands the caption. |
| **Instagram Reels & Stories** | **`#إعلان`** clearly visible inside the `1080x1350` safe zone on Stories and at the very start of the Reel caption. | Turn ON **`Add Paid Partnership Label (`إضافة وسم شراكة مدفوعة مع @brand`)`**. | Using `#تعاون` or `#Collab` without the Paid Partnership toggle or explicit `#إعلان`. |
| **X (Twitter) Thread / Post** | Start or end the main visible tweet text with **`#إعلان`** or **`(مادة إعلانية)`**. | Comply with X Paid Partnerships Policy. | Putting `#إعلان` only in the 5th reply of a thread instead of the root promoted tweet. |

#### 2. Quick Visual Contrast & Safe-Zone Check
- [ ] **Check 1 — Every Frame Rule**: On multi-part Snapchat/Instagram Stories (`Snap 1..5`), verify `#إعلان` appears on **all 5 snaps** (because users jumping in from Discovery or mid-story must see the disclosure on the frame they view).
- [ ] **Check 2 — High Contrast Pill**: Require `#إعلان` to use a solid dark/light background pill (`خلفية معتمة واضحة`) so it remains legible over bright desert/indoor video backgrounds.

## 4. Model & Platform Capability Branches (`فروع قدرات النماذج والمنصات والبدائل الاحتياطية`)

| System / Platform | Capability Status | Official Documentation & Access Date | Operational Constraint in Egypt & GCC | Fallback When Feature/Modality Is Unavailable |
| :--- | :--- | :--- | :--- | :--- |
| **GAMR Mawthooq Disclosure Rules, UAE Media Council & TikTok/Meta/Snap Branded Content Toggles** | `supported` | [Official Reference](https://gmedia.gov.sa/en/executive-regulations) (`2026-10-25`) | Both Saudi GAMR Executive Regulations and UAE Media Council guidelines require clear, unambiguous commercial disclosure (`#إعلان` / `مادة إعلانية`) on all advertising content. | Always combine the native platform `Paid Partnership` toggle with a visible `#إعلان` text badge. |

## 5. Consolidated Regional & Vertical Adaptation Matrix (`دمج الأنماط السياقية الفرعية بدون حشو`)

Per Agent 2 v1.2's anti-padding rule, the following **4 cross-verified contextual synthesis patterns** and **1 screened duplicate variants** share this core mechanism and are consolidated directly into this source-of-truth framework:

| Child Pattern ID | Disposition | Regional / Sector Operating Context | Specific Adaptation & Guardrail Integrated in This Asset | Evidence Tier |
| :--- | :--- | :--- | :--- | :--- |
| **`AMP-297`** | `MERGE_INTO_EXISTING` | Egyptian E-Commerce & Social Commerce (Shopify / WooCommerce / Cairo & Alexandria) | Pre-flight story/video review checklist verifying visible `#إعلان` or native platform paid-partnership tags.; Specifically impacts Egyptian brands operating in EGP where merchant-specific payment mix from recent order records, Mobile Wallets (Vodafone Cash), InstaPay, and Fawry dominate. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-307`** | `MERGE_INTO_EXISTING` | UAE & Multi-Market GCC Enterprise / Retail (Dubai, Abu Dhabi, Doha, Kuwait) | Pre-flight story/video review checklist verifying visible `#إعلان` or native platform paid-partnership tags.; Specifically impacts bilingual Arabic/English campaigns in high-CPM, expat-dense Gulf markets under UAE PDPL / TDRA and Qatari regulations. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-317`** | `MERGE_INTO_EXISTING` | High-Trust & Regulated Verticals (Healthcare/SFDA/EDA, Fintech/SAMA/FRA, Real Estate) | Pre-flight story/video review checklist verifying visible `#إعلان` or native platform paid-partnership tags.; Specifically impacts regulated claims requiring SFDA, EDA, MOH, SAMA, FRA, or RERA compliance pre-clearance and strict hallucination guardrails. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-327`** | `MERGE_INTO_EXISTING` | Seasonal Peak Operations (Ramadan, Eid, White/Yellow Friday, Saudi Founding/National Day) | Pre-flight story/video review checklist verifying visible `#إعلان` or native platform paid-partnership tags.; Specifically impacts high-velocity seasonal surges where CPMs jump 40-70%, prices change rapidly, and Hijri calendar cultural sensitivity is paramount. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-527`** | `REJECT_DUPLICATE` | Screened UI/Format Synonym (`Merged Variant: Minor UI/Format Synonym of AMP-287 (Influencer Marketing)`) | Consolidated into parent workflow without duplicate file inflation. | `SCREENED_DUPLICATE_VARIANT` |

### Context-Specific Execution Knobs Across the 5 MENA Operating Environments
1. **Saudi D2C E-Commerce (`Salla / Zid / Riyadh & Jeddah Retail`)**: Enforce `SAR` tax-inclusive pricing (`15% ZATCA VAT`), native `Mada / Apple Pay / Tabby / Tamara` visibility (`AMP-387`), `GAMR Mawthooq` creator verification (`AMP-281`), and White Saudi Khaleeji orthography (`AMP-002`, `AMP-177`).
2. **Egyptian E-Commerce & Social Commerce (`Shopify / WooCommerce / Cairo & Alexandria`)**: Use each merchant’s own order and payment data to assess Cash on Delivery (`COD`), mobile wallets, InstaPay, Fawry, `valU`, address fields, and pre-dispatch WhatsApp confirmation. Verify current provider terms and local requirements before implementation.
3. **UAE & Multi-Market GCC Enterprise / Retail (`Dubai, Abu Dhabi, Doha, Kuwait`)**: Separate high-CPM UAE/Qatar budgets from lower-CPM markets (`AMP-061`), enforce UAE `TDRA` `9 PM – 7 AM` SMS curfew + `AD-` prefix (`AMP-442`), UAE Media Council permits (`AMP-282`), and bilingual Arabic/English canonical & currency parity (`current applicable UAE VAT`, `current applicable Qatar/Kuwait tax rules`, 3-decimal `KWD` `AMP-239`).
4. **High-Trust & Regulated Verticals (`Healthcare SFDA/MOH/EDA, FinTech SAMA/FRA, Real Estate REGA/RERA`)**: Strip all therapeutic/cure verbs (`AMP-176`, `AMP-286`), display mandatory `MOH/SFDA/DHA/EDA/Fal/Trakheesi` permit numbers (`AMP-070`), and route budgets to high-credibility channels (`AMP-290`, `AMP-339`).
5. **Seasonal Peak Operations (`Ramadan, Eid, White/Yellow Friday, Saudi Founding/National Day`)**: Lock Hijri-Gregorian overlaps (`Feb 2027 Ramadan x Saudi Founding Day x Kuwait National Day` `AMP-125`), pre-schedule GMC `sale_price_effective_date` 48h ahead (`AMP-063`), verify 30-day baseline discount permits (`AMP-064`), and disable Meta Advantage+ auto-music (`AMP-065`).

## 6. Worked Example Summary & Failure Recovery (`ملخص المثال التطبيقي وخطة الإنقاذ`)

*(Full step-by-step worked example with annotated human edits is also provided in `EXAMPLE.md`)*

- **Sample Input Brief**: - **Campaign**: Riyadh & Dubai Electronics Brand running a 5-Snap story sequence with a tech creator.
- **Draft Submitted**: Creator put `#إعلان` in tiny translucent grey letters on Snap #1 only (right under the Snapchat close `'X'` button) and left Snaps #2–#5 completely unlabeled.
- **Human Review & Key Edits Applied**: 1. **Added High-Contrast `#إعلان` Pill Across All 5 Snaps**: Placed a clean black-pill white-text `#إعلان` badge in the top-center safe zone (`180px` below the top edge) on all 5 snaps.
2. **Enabled Native Paid Partnership Tag**: Linked the brand's official handle via the native Paid Partnership tool (which also unlocks direct Spark Ads / Branded Content ad boosting in Ads Manager!).
- **Final Usable Output**: - All 5 story frames published with unmistakable `#إعلان` badges and native Paid Partnership tags enabled.
- **What Can Go Wrong**: A creator posts a TikTok video promoting a brand's discount code without toggling `Commercial Content Disclosure` ON; TikTok's automated commercial-content detector flags the promo code in the audio/caption and suppresses the video's For You feed distribution.
- **Correction & Fallback**: Remind creators that enabling the native **`Commercial Content / Paid Partnership`** toggle **protects** their account from undisclosed-commercial-content suppression and allows the brand to boost the post with paid media budget.

## 7. Measurement Plan & Hypothesis Framing (`خطة القياس والضوابط الإحصائية`)

- **Primary Metric to Track**: 100% of live creator frames/posts passing the `#إعلان` visibility and native Paid Partnership toggle audit within 15 minutes of going live.
- **Baseline Definition**: Prior campaign audit of unlabeled or partially labeled story frames.
- **Observation Window**: Checked at launch of every creator post. *(Must span full 7/14-day weekly cycles and account for 25th–30th monthly salary windows per `AMP-391`)*.
- **What Cannot Be Concluded (Boundary)**: Clear `#إعلان` disclosure satisfies statutory and platform rules and unlocks native Branded Content ad boosting.
