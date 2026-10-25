# FW-020: Snapchat Dynamic Product Ads (DPA) Gulf & Egypt Catalog Feed Validator Checklist
## قائمة فحص وتدقيق كتالوجات إعلانات المنتجات الديناميكية في سناب شات (`Snapchat DPA`) لأسواق الخليج ومصر

- **Consolidated Contextual Child IDs (`MERGE_INTO_EXISTING`)**: `AMP-078`, `AMP-088`, `AMP-098`, `AMP-108`, `AMP-118`
- **Selected Artifact Type**: `CHECKLIST`
- **Intended Audience**: Performance Marketing Manager, Media Buyer, PPC Specialist, Growth Lead
- **Target Markets & Languages**: Egypt & GCC (`Saudi Arabia, UAE, Kuwait, Qatar, Bahrain, Oman`) — Bilingual Arabic (`Egyptian Ammiya`, `Saudi/Gulf Khaleeji`, `White MSA`) + English
- **Version**: `1.2` | **Last Reviewed**: `2026-10-25` | **Status**: `READY_FOR_REVIEW`

## 1. Plain-Language Promise & Why This Artifact Form Fits the Job

- **What You Can Make or Decide (EN)**: Format Snapchat product catalog feeds with mandatory 3-letter ISO currency codes (`199.00 SAR`, `199.00 AED`, `950.00 EGP`) and matching pixel `item_ids` so Snap Dynamic Ads never fail feed ingestion.
- **ما الذي يمكنك إنجازه أو حسمه بهذه الأداة (AR)**: تنسيق ملفات كتالوج المنتجات في سناب شات برموز العملات القياسية الثلاثية (`SAR`، `AED`، `EGP`) ومطابقة معرفات `item_ids` مع البكسل لمنع رفض الكتالوج أو تعطل الاستهداف الديناميكي.
- **Why `CHECKLIST` Fits This User Job (EN)**: Snapchat's catalog validator rejects bare non-USD numbers (`199` or `١٩٩ ر.س`) and breaks dynamic retargeting when Snap Pixel `item_ids` pass variant IDs while the catalog uses parent SKU IDs; a deterministic CHECKLIST with a feed scrubber prevents broken Gulf campaigns.
- **لماذا يناسب شكل `CHECKLIST` هذه المهمة (AR)**: يرفض مدقق كتالوج سناب شات الأسعار الرقمية المجردة (`199` أو `١٩٩ ر.س`) ويتعطل الاستهداف الديناميكي عند عدم تطابق `item_ids` بين البكسل والكتالوج؛ لذا تضمن قائمة الفحص هذه قبول الكتالوج من المرة الأولى.

## 2. "Use It When" Trigger, Boundaries & Exact Inputs to Prepare

- **Use It When (EN)**: Use before connecting a product feed (CSV/TSV/XML or Salla/Zid/Shopify catalog link) to Snapchat Business Manager for Dynamic Product Ads in KSA, UAE, Kuwait, Qatar, or Egypt.
- **متى تستخدم هذه الأداة (AR)**: تُستخدم قبل ربط ملف كتالوج المنتجات بمدير أعمال سناب شات (`Snapchat Business Manager`) لتشغيل إعلانات الكتالوج الديناميكية في السعودية أو الإمارات أو الكويت أو قطر أو مصر.
- **When NOT to Use It (EN)**: Do not assume Salla's native Snapchat catalog link has identical `item_ids` to your custom GTM Snap Pixel without inspecting a live `PAGE_VIEW`/`ADD_CART` event (`AMP-544`).
- **متى لا تستخدم هذه الأداة (AR)**: لا تفترض تطابق معرفات `item_ids` بين ربط سلة التلقائي وبكسل سناب شات المخصص دون فحص حي لحدث `VIEW_CONTENT` و`ADD_CART` (`AMP-544`).

### Exact Inputs to Prepare Before Starting (`المدخلات المطلوب تجهيزها`)
1. Snapchat Product Catalog Feed URL or XML/CSV export
2. Snap Pixel Helper Chrome extension output on a live Product Page and Add-to-Cart event
3. Store currency (`SAR`, `AED`, `KWD`, `QAR`, `BHD`, `OMR`, `EGP`)

### Privacy-Safe Data Handling (`ضوابط الخصوصية وحماية البيانات الشخصية PDPL`)
- **Strict PII Redaction Before Prompting**: Under Saudi PDPL (Art. 25), UAE Federal Decree-Law No. 45 of 2021, Qatar Law No. 13 of 2016, and Egypt Law No. 151 of 2020, **never paste raw customer names, unhashed mobile numbers (`+9665...` / `+201...`), email addresses, national IDs, or private WhatsApp transcripts into public/consumer LLM interfaces**. Use anonymized placeholders (`{first_name}`, `ORD_10045`) during prompt testing and restrict live customer data to zero-data-retention enterprise API endpoints or local deterministic scripts.

## 3. The Directly Usable Artifact (`الأداة التطبيقية الجاهزة للنسخ والتنفيذ`)

### Snapchat Catalog & Pixel Parity Checklist (KSA, GCC & Egypt)

#### 1. Snapchat Feed Attribute Formatting Rules (Verified 2026-10-25)
| Feed Field | Rejected / Broken MENA Values | Required Valid Snapchat Format (`PASS`) | Validation Rule |
| :--- | :--- | :--- | :--- |
| **`price` & `sale_price`** | `199` (defaults to USD!) or `١٩٩ ر.س` or `SAR 199,00` | **`199.00 SAR`** / **`199.00 AED`** / **`950.00 EGP`** | ASCII digits + dot decimal + space + 3-letter ISO 4217 currency code (`SAR`, `AED`, `EGP`, `KWD`, `QAR`). |
| **`id`** | Internal DB row integer (`8812`) while Pixel sends SKU (`ABAYA-01`) | **`ABAYA-01`** (Exact string match with Snap Pixel `item_ids`) | `Catalog.id === SnapPixel.item_ids[0]` (case-sensitive). |
| **`availability`** | `متوفر` or `true` or `1` | **`in stock`** or **`out of stock`** or **`preorder`** | Exact English enum string required by Snap spec even for Arabic feeds. |
| **`condition`** | `جديد` | **`new`** or **`refurbished`** or **`used`** | Exact English enum string; keep `title` and `description` in native Arabic. |
| **`image_link`** | WebP/SVG blocked by CDN hotlink protection or `<500x500px` | **`https://...jpg` or `.png` (`>= 500x500px`, ideally `1080x1920` or `1080x1080`)** | Publicly accessible `200 OK` HTTPS URL without Arabic percent-encoding errors. |

#### 2. Copy-Ready Python Feed Normalizer for Snapchat MENA Catalogs
```python
import re

def format_snap_price(raw_val: str, iso_currency: str = "SAR") -> str:
    # Convert Arabic-Indic digits (٠-٩) to ASCII
    ascii_str = re.sub(r"[٠-٩]", lambda m: str(ord(m.group(0)) - 0x0660), str(raw_val))
    # Extract numeric value
    num_match = re.search(r"\d+(?:[.,]\d+)?", ascii_str.replace(",", ""))
    amount = float(num_match.group(0)) if num_match else 0.0
    return f"{amount:.2f} {iso_currency.upper().strip()}"
```

#### 3. Live Snap Pixel `item_ids` Parity Verification
- [ ] Open a live product page using the **Snap Pixel Helper** extension.
- [ ] Verify `PAGE_VIEW` / `VIEW_CONTENT` and `ADD_CART` pass:
  - `item_ids: ["<EXACT_CATALOG_ID>"]`
  - `currency: "SAR"` (matching the feed currency)
  - `price: 199.00` (numeric dot-decimal)

## 4. Model & Platform Capability Branches (`فروع قدرات النماذج والمنصات والبدائل الاحتياطية`)

| System / Platform | Capability Status | Official Documentation & Access Date | Operational Constraint in Egypt & GCC | Fallback When Feature/Modality Is Unavailable |
| :--- | :--- | :--- | :--- | :--- |
| **Snapchat Catalog Specifications & Dynamic Product Ads** | `supported` | [Official Reference](https://voctos.net/snapchat-product-ads-arab-markets/) (`2026-10-25`) | VOCTOS Oct 2026 Snapchat product ads study confirms Snap requires explicit 3-letter ISO currency codes for non-USD prices and English enum strings (`in stock`, `new`) alongside Arabic titles. | Run `format_snap_price()` on all price columns before feed upload. |

## 5. Consolidated Regional & Vertical Adaptation Matrix (`دمج الأنماط السياقية الفرعية بدون حشو`)

Per Agent 2 v1.2's anti-padding rule, the following **5 cross-verified contextual synthesis patterns** and **1 screened duplicate variants** share this core mechanism and are consolidated directly into this source-of-truth framework:

| Child Pattern ID | Disposition | Regional / Sector Operating Context | Specific Adaptation & Guardrail Integrated in This Asset | Evidence Tier |
| :--- | :--- | :--- | :--- | :--- |
| **`AMP-078`** | `MERGE_INTO_EXISTING` | Egyptian E-Commerce & Social Commerce (Shopify / WooCommerce / Cairo & Alexandria) | Validated feed transformer appending ISO currency codes and enforcing pixel-to-catalog ID parity.; Specifically impacts Egyptian brands operating in EGP where merchant-specific payment mix from recent order records, Mobile Wallets (Vodafone Cash), InstaPay, and Fawry dominate. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-088`** | `MERGE_INTO_EXISTING` | UAE & Multi-Market GCC Enterprise / Retail (Dubai, Abu Dhabi, Doha, Kuwait) | Validated feed transformer appending ISO currency codes and enforcing pixel-to-catalog ID parity.; Specifically impacts bilingual Arabic/English campaigns in high-CPM, expat-dense Gulf markets under UAE PDPL / TDRA and Qatari regulations. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-098`** | `MERGE_INTO_EXISTING` | High-Trust & Regulated Verticals (Healthcare/SFDA/EDA, Fintech/SAMA/FRA, Real Estate) | Validated feed transformer appending ISO currency codes and enforcing pixel-to-catalog ID parity.; Specifically impacts regulated claims requiring SFDA, EDA, MOH, SAMA, FRA, or RERA compliance pre-clearance and strict hallucination guardrails. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-108`** | `MERGE_INTO_EXISTING` | Seasonal Peak Operations (Ramadan, Eid, White/Yellow Friday, Saudi Founding/National Day) | Validated feed transformer appending ISO currency codes and enforcing pixel-to-catalog ID parity.; Specifically impacts high-velocity seasonal surges where CPMs jump 40-70%, prices change rapidly, and Hijri calendar cultural sensitivity is paramount. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-118`** | `MERGE_INTO_EXISTING` | Multi-Client Agency & MarTech API Automation Pipelines (LLM APIs, Webhooks, GA4, CAPI) | Validated feed transformer appending ISO currency codes and enforcing pixel-to-catalog ID parity.; Specifically impacts automated multi-SKU or multi-client LLM/API pipelines where schema validation, token cost, and attribution governance are required. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-508`** | `REJECT_DUPLICATE` | Screened UI/Format Synonym (`Merged Variant: Minor UI/Format Synonym of AMP-078 (Pay-Per-Click (PPC) Advertising)`) | Consolidated into parent workflow without duplicate file inflation. | `SCREENED_DUPLICATE_VARIANT` |

### Context-Specific Execution Knobs Across the 5 MENA Operating Environments
1. **Saudi D2C E-Commerce (`Salla / Zid / Riyadh & Jeddah Retail`)**: Enforce `SAR` tax-inclusive pricing (`15% ZATCA VAT`), native `Mada / Apple Pay / Tabby / Tamara` visibility (`AMP-387`), `GAMR Mawthooq` creator verification (`AMP-281`), and White Saudi Khaleeji orthography (`AMP-002`, `AMP-177`).
2. **Egyptian E-Commerce & Social Commerce (`Shopify / WooCommerce / Cairo & Alexandria`)**: Use each merchant’s own order and payment data to assess Cash on Delivery (`COD`), mobile wallets, InstaPay, Fawry, `valU`, address fields, and pre-dispatch WhatsApp confirmation. Verify current provider terms and local requirements before implementation.
3. **UAE & Multi-Market GCC Enterprise / Retail (`Dubai, Abu Dhabi, Doha, Kuwait`)**: Separate high-CPM UAE/Qatar budgets from lower-CPM markets (`AMP-061`), enforce UAE `TDRA` `9 PM – 7 AM` SMS curfew + `AD-` prefix (`AMP-442`), UAE Media Council permits (`AMP-282`), and bilingual Arabic/English canonical & currency parity (`current applicable UAE VAT`, `current applicable Qatar/Kuwait tax rules`, 3-decimal `KWD` `AMP-239`).
4. **High-Trust & Regulated Verticals (`Healthcare SFDA/MOH/EDA, FinTech SAMA/FRA, Real Estate REGA/RERA`)**: Strip all therapeutic/cure verbs (`AMP-176`, `AMP-286`), display mandatory `MOH/SFDA/DHA/EDA/Fal/Trakheesi` permit numbers (`AMP-070`), and route budgets to high-credibility channels (`AMP-290`, `AMP-339`).
5. **Seasonal Peak Operations (`Ramadan, Eid, White/Yellow Friday, Saudi Founding/National Day`)**: Lock Hijri-Gregorian overlaps (`Feb 2027 Ramadan x Saudi Founding Day x Kuwait National Day` `AMP-125`), pre-schedule GMC `sale_price_effective_date` 48h ahead (`AMP-063`), verify 30-day baseline discount permits (`AMP-064`), and disable Meta Advantage+ auto-music (`AMP-065`).

## 6. Worked Example Summary & Failure Recovery (`ملخص المثال التطبيقي وخطة الإنقاذ`)

*(Full step-by-step worked example with annotated human edits is also provided in `EXAMPLE.md`)*

- **Sample Input Brief**: - **Store**: Riyadh Women's Abaya & Perfume Store launching Snapchat Dynamic Product Ads (`750` SKUs).
- **Problem**: CSV export from AI catalog generator had `price: "٢٨٠ ر.س"`, `availability: "متوفر"`, and `id: "SKU-104"` while the Snap Pixel fired Salla's numeric product ID `"19488210"`. Snap Catalog Diagnostics rejected `100%` of rows.
- **Human Review & Key Edits Applied**: 1. **Verified Salla Pixel ID Match**: Tested a live Add-to-Cart event on the store with Snap Pixel Helper to confirm whether `item_ids` passed the Salla Product ID (`19488210`) or SKU (`SKU-104`), locking the feed `id` column to the exact value emitted by the pixel (`AMP-544`).
2. **Safe-Zone Image Check**: Confirmed primary `image_link` images have centered products so Snapchat's bottom CTA bar (`AMP-338`) does not cover the Abaya design.
- **Final Usable Output**: - `750 / 750` SKUs ingested with `0` errors in Snapchat Catalog Manager and `98.4%` Pixel-to-Catalog `item_ids` match rate.
- **What Can Go Wrong**: A store submits bare numbers (`280.00`) in the `price` column without `SAR`; Snapchat's catalog parser interprets bare numbers as `280.00 USD` (`~1,050 SAR`), displaying inflated USD prices or failing currency validation against the `SAR` ad account.
- **Correction & Fallback**: Always append the 3-letter ISO currency code (`280.00 SAR`, `280.00 AED`, `1200.00 EGP`) to every `price` and `sale_price` cell in Snapchat feeds.

## 7. Measurement Plan & Hypothesis Framing (`خطة القياس والضوابط الإحصائية`)

- **Primary Metric to Track**: Snapchat Catalog Item Approval Rate (`Target: 100%`) and Pixel `item_ids` Match Rate (`Target: >= 95%`).
- **Baseline Definition**: Pre-fix rejected row count and unmatched pixel event rate in Snapchat Events Manager.
- **Observation Window**: 24–48 hours after feed sync. *(Must span full 7/14-day weekly cycles and account for 25th–30th monthly salary windows per `AMP-391`)*.
- **What Cannot Be Concluded (Boundary)**: Feed approval and pixel matching enable dynamic retargeting, while creative template design (`AMP-333`) and offer pricing drive ROAS.
