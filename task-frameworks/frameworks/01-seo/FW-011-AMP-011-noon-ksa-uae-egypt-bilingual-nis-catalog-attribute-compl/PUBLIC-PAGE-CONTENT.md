# Noon KSA, UAE & Egypt Bilingual NIS Catalog & Attribute Completeness Playbook
## <span dir="rtl">دليل التشغيل الثنائي اللغة لكتالوجات نون (`Noon KSA / UAE / Egypt`) لضمان الظهور في الواجهة العربية</span>

> **Asset ID**: `FW-011` (`AMP-011`) | **Artifact Type**: `PLAYBOOK` | **Channel**: Search Engine Optimization (SEO) | **Markets**: Egypt & GCC (`KSA, UAE, Kuwait, Qatar, Bahrain, Oman`) | **Version**: `1.2` (`Reviewed 2026-10-25`)

**What You Can Do With This (`ماذا يمكنك أن تنجز بهذه الأداة؟`)**:
- **EN**: Populate Noon Importer Sheet (NIS) feeds with complete Arabic + English attributes so listings never vanish from the Arabic Noon storefront.
- **AR**: <span dir="rtl">تعبئة قوالب رفع المنتجات في نون (`NIS`) باللغتين العربية والإنجليزية معاً لضمان عدم اختفاء المنتجات من واجهة المتجر العربية في السعودية والإمارات ومصر.</span>

## 1. Use It When & Required Inputs (`متى تستخدمها وما المدخلات المطلوبة؟`)

- **Use It When (EN)**: Use whenever onboarding or updating catalog feeds on Noon (`noon.com` KSA, UAE, or Egypt) via Noon Seller Lab.
- **متى تستخدمها (AR)**: <span dir="rtl">يُستخدم عند رفع أو تحديث كتالوجات المنتجات على منصة نون (`Noon Seller Lab`) في السعودية أو الإمارات أو مصر.</span>
- **When NOT to Use It (EN)**: Do not claim exact percentage weights for Noon's internal organic ranking algorithm (`AMP-548` — Noon publishes eligibility and ad relevance factors, not organic rank weights).
- **متى لا تستخدمها (AR)**: <span dir="rtl">لا تعتمد على أي ادعاءات تزعم معرفة الأوزان النسبية الدقيقة لخوارزمية الترتيب العضوي في نون (`AMP-548` — نون تنشر شروط الأهلية والملاءمة فقط ولا تنشر معادلة الترتيب).</span>

### Exact Inputs to Prepare (`المدخلات المطلوب تجهيزها قبل البدء`)
- Noon Category-Specific NIS Template (`.xlsx` / `.tsv`) downloaded from Noon Seller Lab
- English Master SKU Data (Brand, Title, 5 Feature Bullets, Technical Specifications)
- Verified Arabic Keyword & Attribute Glossary (`AMP-001` & `AMP-002`)

## 2. The Working `PLAYBOOK` (`الأداة الكاملة الجاهزة للنسخ والتطبيق الفوري`)

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

## 3. Complete End-to-End Worked Example (`مثال تطبيقي متكامل من المدخلات حتى المراجعة البشرية والنتيجة النهائية`)

*(Illustrative scenario — original example for training, never represented as a verified client outcome)*

### Step A: Sample Brief / Input (`موجز المدخلات`)
- **SKU**: Digital Air Fryer 6.5L 1800W Black (Uploaded to Noon KSA with English fields only).
- **Problem**: Zero impressions from Arabic-browsing Noon shoppers in Riyadh and Dammam because `product_title_ar` and `description_ar` were left blank.

### Step B: Initial Output (`المخرج الأولي`)
```json
{
  "partner_sku": "AF-65L-BLK",
  "product_title_en": "NutriCook Digital Air Fryer XL 6.5L 1800W with 10 Presets - Black",
  "product_title_ar": "نيوتري كوك قلاية هوائية ديجيتال بحجم عائلي 6.5 لتر 1800 واط بـ 10 برامج - أسود",
  "feature_bullet_1_ar": "سعة عائلية كبيرة 6.5 لتر تكفي لتحضير دجاجة كاملة أو 1.5 كجم من البطاطس دفعة واحدة.",
  "feature_bullet_2_ar": "قدرة 1800 واط مع تقنية تدوير الهواء الساخن 360 درجة لقرمشة مثالية بأقل نسبة دهون.",
  "feature_bullet_3_ar": "شاشة لمس رقمية ذكية تضم 10 برامج طهي مسبقة الإعداد (بطاطس، دجاج، لحم، سمك، مخبوزات).",
  "feature_bullet_4_ar": "سلة طهي غير لاصقة خالية من PFOA قابلة للفك والغسل في غسالة الأطباق بسهولة.",
  "feature_bullet_5_ar": "ضمان رسمي لمدة سنتين في المملكة العربية السعودية، يعمل على كهرباء 220-240 فولت 50/60 هرتز."
}
```

### Step C: Human Review & Edits (`التدقيق البشري والتعديلات`)
1. **Saudi Electrical Standard Check**: Verified that Bullet 5 explicitly states `220-240 فولت 50/60 هرتز` and SASO/official 2-year KSA warranty, which is a top conversion driver on Noon KSA.
2. **Synonym Coverage**: Added `(اير فراير / Air Fryer)` inside `description_ar` so shoppers typing `اير فراير` in Arabic script match the listing.

### Step D: Final Reviewed Example Outcome (`النتيجة النهائية المعتمدة`)
- Listing published on both `noon.com/saudi-en/` and `noon.com/saudi-ar/` with 100% attribute completeness and active Arabic category filter indexing.

## 4. What Can Go Wrong & How to Fix It (`الأخطاء الشائعة وخطة الإنقاذ`)

- **Failure Case (`المشكلة المحتملة`)**: A catalog manager uploads machine-translated Arabic values into Noon's controlled picklist columns (e.g., typing `'أسود مطفي'` instead of selecting Noon's exact picklist value `'أسود'`), causing the NIS batch upload to fail validation.
- **Correction & Fallback (`الحل الإجرائي والبديل الآمن`)**: Map controlled attribute columns (`colour_name_ar`, `brand_ar`, `department`) strictly against the `Valid Values` tab of the Noon NIS Excel template, using AI generation only for free-text fields (`title`, `bullets`, `description`).

## 5. Model & Platform Capability Matrix (`مصفوفة قدرات النماذج والمنصات — 2026-10-25`)

| Platform / Model | Status | Official Documentation | MENA Operational Constraint | Fallback |
| :--- | :--- | :--- | :--- | :--- |
| **Noon Seller Lab NIS Language Visibility Rules** | `supported` | [Official Docs](https://voctos.net/amazon-sa-noon-seo-guide/) (`2026-10-25`) | Noon Partner Help Center documents that English-only listings can be hidden from the Arabic storefront and are not automatically translated by Noon. | Treat all `_ar` columns in Noon NIS templates as mandatory blocking fields before upload. |

## 6. How to Measure Success (`خطة القياس والضوابط`)

- **Primary Metric**: Percentage of active Noon SKUs searchable and visible on `noon.com/saudi-ar/` & `noon.com/egypt-ar/`, plus Arabic storefront impression share.
- **Baseline**: Pre-update count of SKUs missing `_ar` titles/bullets in Seller Lab Catalog Health.
- **Observation Window**: 14 days after NIS approval.
- **Interpretation Boundary**: Bilingual catalog completeness unlocks Arabic storefront visibility, while Noon Express (FBN) fulfillment and pricing drive Buy Box win rate.

## 7. Primary Sources & Evidence Boundaries (`المصادر الموثقة وحدود الأدلة`)

- [Amazon.sa and noon SEO in 2026: How Product Search Works on Saudi and UAE Marketplaces](https://voctos.net/amazon-sa-noon-seo-guide/) — *VOCTOS* (Published `2026-10-08`, Accessed `2026-10-25`): Amazon.sa enforces a 75-character title rule (June/July 2026) and a <250-byte hidden keyword limit where UTF-8 Arabic letters consume 2 bytes each (~26 Arabic words max vs ~54 Latin); Noon requires English in KSA/UAE but hides English-only listings on its Arabic site; GA4 misclassifies amazon.sa and noon.com into Referral.
