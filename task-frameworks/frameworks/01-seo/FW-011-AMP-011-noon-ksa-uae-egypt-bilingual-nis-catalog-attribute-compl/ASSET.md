# FW-011: Noon KSA, UAE & Egypt Bilingual NIS Catalog & Attribute Completeness Playbook
## دليل التشغيل الثنائي اللغة لكتالوجات نون (`Noon KSA / UAE / Egypt`) لضمان الظهور في الواجهة العربية

- **Consolidated Contextual Child IDs (`MERGE_INTO_EXISTING`)**: `AMP-023`, `AMP-035`, `AMP-047`, `AMP-059`
- **Selected Artifact Type**: `PLAYBOOK`
- **Intended Audience**: SEO Specialist, E-Commerce Manager, Content Strategist, Technical SEO Lead
- **Target Markets & Languages**: Egypt & GCC (`Saudi Arabia, UAE, Kuwait, Qatar, Bahrain, Oman`) — Bilingual Arabic (`Egyptian Ammiya`, `Saudi/Gulf Khaleeji`, `White MSA`) + English
- **Version**: `1.2` | **Last Reviewed**: `2026-10-25` | **Status**: `READY_FOR_REVIEW`

## 1. Plain-Language Promise & Why This Artifact Form Fits the Job

- **What You Can Make or Decide (EN)**: Populate Noon Importer Sheet (NIS) feeds with complete Arabic + English attributes so listings never vanish from the Arabic Noon storefront.
- **ما الذي يمكنك إنجازه أو حسمه بهذه الأداة (AR)**: تعبئة قوالب رفع المنتجات في نون (`NIS`) باللغتين العربية والإنجليزية معاً لضمان عدم اختفاء المنتجات من واجهة المتجر العربية في السعودية والإمارات ومصر.
- **Why `PLAYBOOK` Fits This User Job (EN)**: Noon Partner Help Center makes English mandatory and Arabic 'optional' in NIS sheets, yet explicitly warns that English-only products can be hidden from the Arabic site (and does not machine-translate seller copy automatically); an operational PLAYBOOK prevents accidental invisibility to Arabic-browsing shoppers.
- **لماذا يناسب شكل `PLAYBOOK` هذه المهمة (AR)**: تجعل منصة نون الحقول الإنجليزية إلزامية والعربية «اختيارية» في ملفات الرفع، لكنها تحذر من أن المنتجات المكتوبة بالإنجليزية فقط قد تختفي من الواجهة العربية؛ لذا يضمن دليل التشغيل هذا ظهور المنتجات لكافة المتسوقين.

## 2. "Use It When" Trigger, Boundaries & Exact Inputs to Prepare

- **Use It When (EN)**: Use whenever onboarding or updating catalog feeds on Noon (`noon.com` KSA, UAE, or Egypt) via Noon Seller Lab.
- **متى تستخدم هذه الأداة (AR)**: يُستخدم عند رفع أو تحديث كتالوجات المنتجات على منصة نون (`Noon Seller Lab`) في السعودية أو الإمارات أو مصر.
- **When NOT to Use It (EN)**: Do not claim exact percentage weights for Noon's internal organic ranking algorithm (`AMP-548` — Noon publishes eligibility and ad relevance factors, not organic rank weights).
- **متى لا تستخدم هذه الأداة (AR)**: لا تعتمد على أي ادعاءات تزعم معرفة الأوزان النسبية الدقيقة لخوارزمية الترتيب العضوي في نون (`AMP-548` — نون تنشر شروط الأهلية والملاءمة فقط ولا تنشر معادلة الترتيب).

### Exact Inputs to Prepare Before Starting (`المدخلات المطلوب تجهيزها`)
1. Noon Category-Specific NIS Template (`.xlsx` / `.tsv`) downloaded from Noon Seller Lab
2. English Master SKU Data (Brand, Title, 5 Feature Bullets, Technical Specifications)
3. Verified Arabic Keyword & Attribute Glossary (`AMP-001` & `AMP-002`)

### Privacy-Safe Data Handling (`ضوابط الخصوصية وحماية البيانات الشخصية PDPL`)
- **Strict PII Redaction Before Prompting**: Under Saudi PDPL (Art. 25), UAE Federal Decree-Law No. 45 of 2021, Qatar Law No. 13 of 2016, and Egypt Law No. 151 of 2020, **never paste raw customer names, unhashed mobile numbers (`+9665...` / `+201...`), email addresses, national IDs, or private WhatsApp transcripts into public/consumer LLM interfaces**. Use anonymized placeholders (`{first_name}`, `ORD_10045`) during prompt testing and restrict live customer data to zero-data-retention enterprise API endpoints or local deterministic scripts.

## 3. The Directly Usable Artifact (`الأداة التطبيقية الجاهزة للنسخ والتنفيذ`)

### Noon Bilingual Catalog Completeness Playbook (`Seller Lab NIS`)

#### Phase 1: Mandatory Dual-Language Column Lock (Treat Arabic as Mandatory, Never Optional)
Even though Noon Seller Lab's schema marks Arabic columns as optional on initial upload, **Noon does not automatically translate English listings and states that English-only listings may not display on the Arabic storefront (`ar-sa`, `ar-ae`, `ar-eg`)**.
Every NIS row MUST populate both pairs:
| Noon NIS Field Group | English Column (`en-sa` / `en-ae` / `en-eg`) | Arabic Column (`ar-sa` / `ar-ae` / `ar-eg`) | Validation Rule |
| :--- | :--- | :--- | :--- |
| **Partner SKU Title** | `product_title_en` | `product_title_ar` | `[Brand] + [Model] + [Product Type] + [Key Spec] + [Color]` in both languages (`50–90` chars). |
| **Feature Bullets (`1..5`)** | `feature_bullet_1_en` .. `5_en` | `feature_bullet_1_ar` .. `5_ar` | Minimum 4 bullets populated in both languages; lead each bullet with a concrete spec or benefit. |
| **Long Description** | `description_en` | `description_ar` | Clean text/allowed markup; include orthographic variants (`ة/ه`, `أ/ا`) naturally for Arabic internal search. |
| **Filterable Attributes** | `colour_name_en`, `material_en`, `size` | `colour_name_ar`, `material_ar`, `size` | Must match Noon's exact picklist values so sidebar filters on the Arabic app include the SKU. |

#### Phase 2: Copy-Ready Prompt for Noon Bilingual NIS Row Generation
```xml
<system_role>
You are a Noon Seller Lab Catalog Specialist for KSA, UAE, and Egypt.
Transform the English SKU data into a synchronized bilingual Noon NIS record (`en` + `ar`) so the listing appears on BOTH the English and Arabic Noon storefronts and passes sidebar attribute filtering.
</system_role>
<rules>
1. Never translate brand/model codes literally; keep model numbers in ASCII (`256GB`, `55-Inch`, `1800W`) inside both `en` and `ar` titles.
2. In `product_title_ar` and `description_ar`, use native Saudi/Gulf and Egyptian commercial terminology (e.g., `قلاية هوائية بدون زيت` alongside `اير فراير`).
3. Populate all 5 `feature_bullet_ar` fields with concrete specs (dimensions, warranty, box contents, power/material)—no generic filler.
</rules>
```

#### Phase 3: Post-Upload Storefront Visibility Check
- [ ] Switch Noon app / web locale to **`العربية`** (`noon.com/saudi-ar/` or `noon.com/egypt-ar/`).
- [ ] Search the Partner SKU / ZSKU and core Arabic keyword; confirm the listing renders with Arabic title, Arabic bullets, and appears when filtering by Brand and Category.

## 4. Model & Platform Capability Branches (`فروع قدرات النماذج والمنصات والبدائل الاحتياطية`)

| System / Platform | Capability Status | Official Documentation & Access Date | Operational Constraint in Egypt & GCC | Fallback When Feature/Modality Is Unavailable |
| :--- | :--- | :--- | :--- | :--- |
| **Noon Seller Lab NIS Language Visibility Rules** | `supported` | [Official Reference](https://voctos.net/amazon-sa-noon-seo-guide/) (`2026-10-25`) | Noon Partner Help Center documents that English-only listings can be hidden from the Arabic storefront and are not automatically translated by Noon. | Treat all `_ar` columns in Noon NIS templates as mandatory blocking fields before upload. |

## 5. Consolidated Regional & Vertical Adaptation Matrix (`دمج الأنماط السياقية الفرعية بدون حشو`)

Per Agent 2 v1.2's anti-padding rule, the following **4 cross-verified contextual synthesis patterns** and **1 screened duplicate variants** share this core mechanism and are consolidated directly into this source-of-truth framework:

| Child Pattern ID | Disposition | Regional / Sector Operating Context | Specific Adaptation & Guardrail Integrated in This Asset | Evidence Tier |
| :--- | :--- | :--- | :--- | :--- |
| **`AMP-023`** | `MERGE_INTO_EXISTING` | Egyptian E-Commerce & Social Commerce (Shopify / WooCommerce / Cairo & Alexandria) | Noon Egypt allows single-language listings in either Arabic or English.; Specifically impacts Egyptian brands operating in EGP where merchant-specific payment mix from recent order records, Mobile Wallets (Vodafone Cash), InstaPay, and Fawry dominate. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-035`** | `MERGE_INTO_EXISTING` | UAE & Multi-Market GCC Enterprise / Retail (Dubai, Abu Dhabi, Doha, Kuwait) | Noon Egypt allows single-language listings in either Arabic or English.; Specifically impacts bilingual Arabic/English campaigns in high-CPM, expat-dense Gulf markets under UAE PDPL / TDRA and Qatari regulations. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-047`** | `MERGE_INTO_EXISTING` | High-Trust & Regulated Verticals (Healthcare/SFDA/EDA, Fintech/SAMA/FRA, Real Estate) | Noon Egypt allows single-language listings in either Arabic or English.; Specifically impacts regulated claims requiring SFDA, EDA, MOH, SAMA, FRA, or RERA compliance pre-clearance and strict hallucination guardrails. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-059`** | `MERGE_INTO_EXISTING` | Seasonal Peak Operations (Ramadan, Eid, White/Yellow Friday, Saudi Founding/National Day) | Noon Egypt allows single-language listings in either Arabic or English.; Specifically impacts high-velocity seasonal surges where CPMs jump 40-70%, prices change rapidly, and Hijri calendar cultural sensitivity is paramount. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-503`** | `REJECT_DUPLICATE` | Screened UI/Format Synonym (`Merged Variant: Minor UI/Format Synonym of AMP-023 (Search Engine Optimization (SEO))`) | Consolidated into parent workflow without duplicate file inflation. | `SCREENED_DUPLICATE_VARIANT` |

### Context-Specific Execution Knobs Across the 5 MENA Operating Environments
1. **Saudi D2C E-Commerce (`Salla / Zid / Riyadh & Jeddah Retail`)**: Enforce `SAR` tax-inclusive pricing (`15% ZATCA VAT`), native `Mada / Apple Pay / Tabby / Tamara` visibility (`AMP-387`), `GAMR Mawthooq` creator verification (`AMP-281`), and White Saudi Khaleeji orthography (`AMP-002`, `AMP-177`).
2. **Egyptian E-Commerce & Social Commerce (`Shopify / WooCommerce / Cairo & Alexandria`)**: Use each merchant’s own order and payment data to assess Cash on Delivery (`COD`), mobile wallets, InstaPay, Fawry, `valU`, address fields, and pre-dispatch WhatsApp confirmation. Verify current provider terms and local requirements before implementation.
3. **UAE & Multi-Market GCC Enterprise / Retail (`Dubai, Abu Dhabi, Doha, Kuwait`)**: Separate high-CPM UAE/Qatar budgets from lower-CPM markets (`AMP-061`), enforce UAE `TDRA` `9 PM – 7 AM` SMS curfew + `AD-` prefix (`AMP-442`), UAE Media Council permits (`AMP-282`), and bilingual Arabic/English canonical & currency parity (`current applicable UAE VAT`, `current applicable Qatar/Kuwait tax rules`, 3-decimal `KWD` `AMP-239`).
4. **High-Trust & Regulated Verticals (`Healthcare SFDA/MOH/EDA, FinTech SAMA/FRA, Real Estate REGA/RERA`)**: Strip all therapeutic/cure verbs (`AMP-176`, `AMP-286`), display mandatory `MOH/SFDA/DHA/EDA/Fal/Trakheesi` permit numbers (`AMP-070`), and route budgets to high-credibility channels (`AMP-290`, `AMP-339`).
5. **Seasonal Peak Operations (`Ramadan, Eid, White/Yellow Friday, Saudi Founding/National Day`)**: Lock Hijri-Gregorian overlaps (`Feb 2027 Ramadan x Saudi Founding Day x Kuwait National Day` `AMP-125`), pre-schedule GMC `sale_price_effective_date` 48h ahead (`AMP-063`), verify 30-day baseline discount permits (`AMP-064`), and disable Meta Advantage+ auto-music (`AMP-065`).

## 6. Worked Example Summary & Failure Recovery (`ملخص المثال التطبيقي وخطة الإنقاذ`)

*(Full step-by-step worked example with annotated human edits is also provided in `EXAMPLE.md`)*

- **Sample Input Brief**: - **SKU**: Digital Air Fryer 6.5L 1800W Black (Uploaded to Noon KSA with English fields only).
- **Problem**: Zero impressions from Arabic-browsing Noon shoppers in Riyadh and Dammam because `product_title_ar` and `description_ar` were left blank.
- **Human Review & Key Edits Applied**: 1. **Saudi Electrical Standard Check**: Verified that Bullet 5 explicitly states `220-240 فولت 50/60 هرتز` and SASO/official 2-year KSA warranty, which is a top conversion driver on Noon KSA.
2. **Synonym Coverage**: Added `(اير فراير / Air Fryer)` inside `description_ar` so shoppers typing `اير فراير` in Arabic script match the listing.
- **Final Usable Output**: - Listing published on both `noon.com/saudi-en/` and `noon.com/saudi-ar/` with 100% attribute completeness and active Arabic category filter indexing.
- **What Can Go Wrong**: A catalog manager uploads machine-translated Arabic values into Noon's controlled picklist columns (e.g., typing `'أسود مطفي'` instead of selecting Noon's exact picklist value `'أسود'`), causing the NIS batch upload to fail validation.
- **Correction & Fallback**: Map controlled attribute columns (`colour_name_ar`, `brand_ar`, `department`) strictly against the `Valid Values` tab of the Noon NIS Excel template, using AI generation only for free-text fields (`title`, `bullets`, `description`).

## 7. Measurement Plan & Hypothesis Framing (`خطة القياس والضوابط الإحصائية`)

- **Primary Metric to Track**: Percentage of active Noon SKUs searchable and visible on `noon.com/saudi-ar/` & `noon.com/egypt-ar/`, plus Arabic storefront impression share.
- **Baseline Definition**: Pre-update count of SKUs missing `_ar` titles/bullets in Seller Lab Catalog Health.
- **Observation Window**: 14 days after NIS approval. *(Must span full 7/14-day weekly cycles and account for 25th–30th monthly salary windows per `AMP-391`)*.
- **What Cannot Be Concluded (Boundary)**: Bilingual catalog completeness unlocks Arabic storefront visibility, while Noon Express (FBN) fulfillment and pricing drive Buy Box win rate.
