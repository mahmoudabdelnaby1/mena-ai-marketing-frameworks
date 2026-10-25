# Snapchat Dynamic Product Ads (DPA) Gulf & Egypt Catalog Feed Validator Checklist
## <span dir="rtl">قائمة فحص وتدقيق كتالوجات إعلانات المنتجات الديناميكية في سناب شات (`Snapchat DPA`) لأسواق الخليج ومصر</span>

> **Asset ID**: `FW-020` (`AMP-068`) | **Artifact Type**: `CHECKLIST` | **Channel**: Pay-Per-Click (PPC) Advertising | **Markets**: Egypt & GCC (`KSA, UAE, Kuwait, Qatar, Bahrain, Oman`) | **Version**: `1.2` (`Reviewed 2026-10-25`)

**What You Can Do With This (`ماذا يمكنك أن تنجز بهذه الأداة؟`)**:
- **EN**: Format Snapchat product catalog feeds with mandatory 3-letter ISO currency codes (`199.00 SAR`, `199.00 AED`, `950.00 EGP`) and matching pixel `item_ids` so Snap Dynamic Ads never fail feed ingestion.
- **AR**: <span dir="rtl">تنسيق ملفات كتالوج المنتجات في سناب شات برموز العملات القياسية الثلاثية (`SAR`، `AED`، `EGP`) ومطابقة معرفات `item_ids` مع البكسل لمنع رفض الكتالوج أو تعطل الاستهداف الديناميكي.</span>

## 1. Use It When & Required Inputs (`متى تستخدمها وما المدخلات المطلوبة؟`)

- **Use It When (EN)**: Use before connecting a product feed (CSV/TSV/XML or Salla/Zid/Shopify catalog link) to Snapchat Business Manager for Dynamic Product Ads in KSA, UAE, Kuwait, Qatar, or Egypt.
- **متى تستخدمها (AR)**: <span dir="rtl">تُستخدم قبل ربط ملف كتالوج المنتجات بمدير أعمال سناب شات (`Snapchat Business Manager`) لتشغيل إعلانات الكتالوج الديناميكية في السعودية أو الإمارات أو الكويت أو قطر أو مصر.</span>
- **When NOT to Use It (EN)**: Do not assume Salla's native Snapchat catalog link has identical `item_ids` to your custom GTM Snap Pixel without inspecting a live `PAGE_VIEW`/`ADD_CART` event (`AMP-544`).
- **متى لا تستخدمها (AR)**: <span dir="rtl">لا تفترض تطابق معرفات `item_ids` بين ربط سلة التلقائي وبكسل سناب شات المخصص دون فحص حي لحدث `VIEW_CONTENT` و`ADD_CART` (`AMP-544`).</span>

### Exact Inputs to Prepare (`المدخلات المطلوب تجهيزها قبل البدء`)
- Snapchat Product Catalog Feed URL or XML/CSV export
- Snap Pixel Helper Chrome extension output on a live Product Page and Add-to-Cart event
- Store currency (`SAR`, `AED`, `KWD`, `QAR`, `BHD`, `OMR`, `EGP`)

## 2. The Working `CHECKLIST` (`الأداة الكاملة الجاهزة للنسخ والتطبيق الفوري`)

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

## 3. Complete End-to-End Worked Example (`مثال تطبيقي متكامل من المدخلات حتى المراجعة البشرية والنتيجة النهائية`)

*(Illustrative scenario — original example for training, never represented as a verified client outcome)*

### Step A: Sample Brief / Input (`موجز المدخلات`)
- **Store**: Riyadh Women's Abaya & Perfume Store launching Snapchat Dynamic Product Ads (`750` SKUs).
- **Problem**: CSV export from AI catalog generator had `price: "٢٨٠ ر.س"`, `availability: "متوفر"`, and `id: "SKU-104"` while the Snap Pixel fired Salla's numeric product ID `"19488210"`. Snap Catalog Diagnostics rejected `100%` of rows.

### Step B: Initial Output (`المخرج الأولي`)
- **Feed Scrubber Output**:
  - `id`: `"19488210"` (Synced to match Salla's native Snap Pixel `item_ids`)
  - `title`: `"عباية كريب ملكي سوداء بتطريز يدوي على الأكمام"`
  - `price`: `"280.00 SAR"`
  - `sale_price`: `"239.00 SAR"`
  - `availability`: `"in stock"`
  - `condition`: `"new"`

### Step C: Human Review & Edits (`التدقيق البشري والتعديلات`)
1. **Verified Salla Pixel ID Match**: Tested a live Add-to-Cart event on the store with Snap Pixel Helper to confirm whether `item_ids` passed the Salla Product ID (`19488210`) or SKU (`SKU-104`), locking the feed `id` column to the exact value emitted by the pixel (`AMP-544`).
2. **Safe-Zone Image Check**: Confirmed primary `image_link` images have centered products so Snapchat's bottom CTA bar (`AMP-338`) does not cover the Abaya design.

### Step D: Final Reviewed Example Outcome (`النتيجة النهائية المعتمدة`)
- `750 / 750` SKUs ingested with `0` errors in Snapchat Catalog Manager and `98.4%` Pixel-to-Catalog `item_ids` match rate.

## 4. What Can Go Wrong & How to Fix It (`الأخطاء الشائعة وخطة الإنقاذ`)

- **Failure Case (`المشكلة المحتملة`)**: A store submits bare numbers (`280.00`) in the `price` column without `SAR`; Snapchat's catalog parser interprets bare numbers as `280.00 USD` (`~1,050 SAR`), displaying inflated USD prices or failing currency validation against the `SAR` ad account.
- **Correction & Fallback (`الحل الإجرائي والبديل الآمن`)**: Always append the 3-letter ISO currency code (`280.00 SAR`, `280.00 AED`, `1200.00 EGP`) to every `price` and `sale_price` cell in Snapchat feeds.

## 5. Model & Platform Capability Matrix (`مصفوفة قدرات النماذج والمنصات — 2026-10-25`)

| Platform / Model | Status | Official Documentation | MENA Operational Constraint | Fallback |
| :--- | :--- | :--- | :--- | :--- |
| **Snapchat Catalog Specifications & Dynamic Product Ads** | `supported` | [Official Docs](https://voctos.net/snapchat-product-ads-arab-markets/) (`2026-10-25`) | VOCTOS Oct 2026 Snapchat product ads study confirms Snap requires explicit 3-letter ISO currency codes for non-USD prices and English enum strings (`in stock`, `new`) alongside Arabic titles. | Run `format_snap_price()` on all price columns before feed upload. |

## 6. How to Measure Success (`خطة القياس والضوابط`)

- **Primary Metric**: Snapchat Catalog Item Approval Rate (`Target: 100%`) and Pixel `item_ids` Match Rate (`Target: >= 95%`).
- **Baseline**: Pre-fix rejected row count and unmatched pixel event rate in Snapchat Events Manager.
- **Observation Window**: 24–48 hours after feed sync.
- **Interpretation Boundary**: Feed approval and pixel matching enable dynamic retargeting, while creative template design (`AMP-333`) and offer pricing drive ROAS.

## 7. Primary Sources & Evidence Boundaries (`المصادر الموثقة وحدود الأدلة`)

- [Snapchat Product Ads in Arab Markets: Catalog Rules for Arabic Titles and White Friday](https://voctos.net/snapchat-product-ads-arab-markets/) — *VOCTOS* (Published `2026-10-08`, Accessed `2026-10-25`): Snap catalog feeds require explicit ISO currency codes ('199 SAR', '199 AED', '199 EGP'—never bare numbers), strict ID parity with Snap Pixel item IDs (<=128 chars), and front-loaded Arabic titles within the 40-character display guide.
- [Snapchat Ads Guide for Online Stores in Saudi Arabia and the Gulf](https://esafqa.com/en/blog/snapchat-ads-guide-saudi-gulf/) — *Esafqa* (Published `2026-10-09`, Accessed `2026-10-25`): Details Snapchat's official creative rules for Gulf stores: 9:16 native shoot, hero message in second 1, brand before second 2 (no static logo opening), 5-6s duration with offer in seconds 2-3, natural Saudi/Gulf dialect + captions, and zero recycled TikTok/Reels watermarks.
