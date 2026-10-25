# Amazon.sa & Amazon.ae 75-Character Product Title Compression Prompt & Policy Template
## <span dir="rtl">قالب صياغة وضغط عناوين منتجات `Amazon.sa` و`Amazon.ae` ضمن السقف الرسمي (75 حرفاً) لمنع إعادة الكتابة الآلية</span>

> **Asset ID**: `FW-010` (`AMP-010`) | **Artifact Type**: `CONTENT_TEMPLATE` | **Channel**: Search Engine Optimization (SEO) | **Markets**: Egypt & GCC (`KSA, UAE, Kuwait, Qatar, Bahrain, Oman`) | **Version**: `1.2` (`Reviewed 2026-10-25`)

**What You Can Do With This (`ماذا يمكنك أن تنجز بهذه الأداة؟`)**:
- **EN**: Craft high-converting Arabic and English Amazon product titles strictly within the 75-character policy cap so Amazon does not truncate or auto-rewrite your title after 14 days.
- **AR**: <span dir="rtl">صياغة عناوين منتجات أمازون السعودية والإمارات ضمن السقف الرسمي (75 حرفاً) لمنع بتر العنوان أو تغييره تلقائياً بواسطة ذكاء أمازون الاصطناعي بعد 14 يوماً.</span>

## 1. Use It When & Required Inputs (`متى تستخدمها وما المدخلات المطلوبة؟`)

- **Use It When (EN)**: Use when creating or updating ASIN titles on `Amazon.sa`, `Amazon.ae`, or `Amazon.eg` via Seller Central or Vendor Central.
- **متى تستخدمها (AR)**: <span dir="rtl">يُستخدم عند إنشاء أو تحديث عناوين المنتجات (`Product Title`) على `Amazon.sa` أو `Amazon.ae` أو `Amazon.eg`.</span>
- **When NOT to Use It (EN)**: Do not stuff promotional phrases (`شحن مجاني`, `أفضل مبيعاً`, `خصم 50%`), symbols (`!`, `*`, `؟`), or repeat the same root word more than twice in an Amazon title—both violate Amazon policy regardless of character length.
- **متى لا تستخدمها (AR)**: <span dir="rtl">لا تقم بحشو عبارات ترويجية (`شحن مجاني`، `الأكثر مبيعاً`، `خصم`) أو رموز (`!`، `*`) أو تكرار نفس الكلمة أكثر من مرتين داخل عنوان أمازون.</span>

### Exact Inputs to Prepare (`المدخلات المطلوب تجهيزها قبل البدء`)
- Brand Name (Arabic & English)
- Core Product Noun (highest search-volume native term from `AMP-001`)
- 1–2 Defining Specs (Capacity/Size/Power/Material + Color/Count)
- Bullet Point #1 & Backend Generic Keywords (`AMP-009`) to hold overflow attributes

## 2. The Working `CONTENT_TEMPLATE` (`الأداة الكاملة الجاهزة للنسخ والتطبيق الفوري`)

### Amazon MENA `<= 75-Character` Product Title Formula & Prompt

#### 1. The 4-Slot Title Formula (`Max 70–75 Characters Including Spaces`)
```text
[Slot 1: Brand (6–12 chars)] + [Slot 2: Core Native Product Noun (15–22 chars)] + [Slot 3: Key Tech Spec / Size (12–18 chars)] + [Slot 4: Variant / Color / Pack (6–12 chars)]
```
- **Hard Guardrails (Amazon June/July 2026 KSA/UAE Policy)**:
  1. **Total Character Count**: `<= 75` characters (including spaces).
  2. **Word Repetition Limit**: Never repeat any word more than `2` times.
  3. **Forbidden Characters**: `! $ ? _ { } ^ ¬ ¦` and promotional claims (`Best Seller`, `Free Shipping`, `الأصلي 100%`).
  4. **Overflow Routing**: Move secondary benefits, compatibility lists, and secondary synonyms to **Bullet Point 1** and the **`<250-byte` Generic Keywords (`AMP-009`)**.

#### 2. Copy-Ready LLM Title Compression Prompt
```xml
<system_role>
You are an Amazon.sa / Amazon.ae Catalog Compliance Specialist.
Rewrite the raw product description into an Amazon-compliant Arabic title and English title.
</system_role>
<constraints>
1. HARD CAP: Every title MUST be <= 72 characters (including spaces) so it safely passes Amazon's 75-character KSA/UAE limit.
2. Follow the exact formula: [Brand] + [Core Native Noun] + [1-2 Defining Numeric Specs] + [Color/Pack].
3. Use ASCII numerals (`20000mAh`, `1.5L`, `50ml`) instead of spelled-out numbers to save characters and improve mobile scannability.
4. Zero promotional words, zero banned symbols, and no word repeated >2 times.
5. Output a JSON object with `title_ar`, `title_ar_len`, `title_en`, `title_en_len`, and `overflow_terms_for_bullets_and_backend`.
</constraints>
```

## 3. Complete End-to-End Worked Example (`مثال تطبيقي متكامل من المدخلات حتى المراجعة البشرية والنتيجة النهائية`)

*(Illustrative scenario — original example for training, never represented as a verified client outcome)*

### Step A: Sample Brief / Input (`موجز المدخلات`)
- **Raw Verbose AI Title (`164` characters)**:
  `ماكينة قهوة إسبريسو وكابتشينو احترافية من ديلونجي ديديكا، مضخة ضغط عالي 15 بار مع عصا تبخير الحليب لتحضير اللاتيه والقهوة المختصة في المنزل والمكتب، لون فضي ستانلس ستيل`

### Step B: Initial Output (`المخرج الأولي`)
```json
{
  "title_ar": "ديلونجي ماكينة إسبريسو ديديكا 15 بار مع مبخر حليب، فضي EC685.M",
  "title_ar_len": 62,
  "title_en": "De'Longhi Dedica Espresso Machine 15 Bar with Milk Frother, Silver",
  "title_en_len": 66,
  "overflow_terms_for_bullets_and_backend": [
    "ماكينة قهوة وكابتشينو",
    "تحضير لاتيه وقهوة مختصة",
    "ستانلس ستيل للمنزل والمكتب"
  ]
}
```

### Step C: Human Review & Edits (`التدقيق البشري والتعديلات`)
1. **Character Count Verification**: Verified `len(title_ar) == 62` (`<= 75` pass) and `len(title_en) == 66` (`<= 75` pass).
2. **Model Number Placement**: Kept `EC685.M` in the Arabic title because Saudi buyers frequently search the exact De'Longhi model code, and moved `"كابتشينو ولاتيه"` into `Generic Keywords` (`AMP-009`).

### Step D: Final Reviewed Example Outcome (`النتيجة النهائية المعتمدة`)
- **`Amazon.sa` Arabic Title (`62 / 75` chars)**:
  `ديلونجي ماكينة إسبريسو ديديكا 15 بار مع مبخر حليب، فضي EC685.M`
- **`Amazon.sa` English Title (`66 / 75` chars)**:
  `De'Longhi Dedica Espresso Machine 15 Bar with Milk Frother, Silver`

## 4. What Can Go Wrong & How to Fix It (`الأخطاء الشائعة وخطة الإنقاذ`)

- **Failure Case (`المشكلة المحتملة`)**: A seller uploads a 150-character keyword-stuffed title generated by a generic ChatGPT prompt; after 14 days in Seller Central's 'Review listing updates', Amazon's AI overwrites the title with an awkward machine translation that omits the pack size.
- **Correction & Fallback (`الحل الإجرائي والبديل الآمن`)**: Audit Seller Central -> `Inventory -> Review Listing Updates` weekly and proactively compress all titles to `<= 75` characters using the 4-Slot Formula.

## 5. Model & Platform Capability Matrix (`مصفوفة قدرات النماذج والمنصات — 2026-10-25`)

| Platform / Model | Status | Official Documentation | MENA Operational Constraint | Fallback |
| :--- | :--- | :--- | :--- | :--- |
| **Amazon.sa & Amazon.ae Product Title Policy (75-Char Cap & 14-Day Auto-Rewrite)** | `supported` | [Official Docs](https://voctos.net/amazon-sa-noon-seo-guide/) (`2026-10-25`) | VOCTOS's Oct 2026 marketplace study confirmed the 75-character limit on KSA and UAE policy pages and the 14-day review window before Amazon-generated titles apply. | Enforce `len(title) <= 75` in catalog flat-files before upload. |

## 6. How to Measure Success (`خطة القياس والضوابط`)

- **Primary Metric**: Zero title suppression alerts or unapproved Amazon auto-rewrites in Seller Central (`Review Listing Updates`), plus mobile search result CTR.
- **Baseline**: Count of ASINs flagged for title length violations in Seller Central Account Health / Listing Quality Dashboard.
- **Observation Window**: 14–21 days post-update.
- **Interpretation Boundary**: Compliant titles prevent suppression and truncation, while Buy Box share and ad rank still depend on fulfillment (FBA) and pricing.

## 7. Primary Sources & Evidence Boundaries (`المصادر الموثقة وحدود الأدلة`)

- [Amazon.sa and noon SEO in 2026: How Product Search Works on Saudi and UAE Marketplaces](https://voctos.net/amazon-sa-noon-seo-guide/) — *VOCTOS* (Published `2026-10-08`, Accessed `2026-10-25`): Amazon.sa enforces a 75-character title rule (June/July 2026) and a <250-byte hidden keyword limit where UTF-8 Arabic letters consume 2 bytes each (~26 Arabic words max vs ~54 Latin); Noon requires English in KSA/UAE but hides English-only listings on its Arabic site; GA4 misclassifies amazon.sa and noon.com into Referral.
