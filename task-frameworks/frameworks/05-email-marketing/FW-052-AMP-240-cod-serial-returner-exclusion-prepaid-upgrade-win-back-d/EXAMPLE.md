# End-to-End Worked Example & Failure Recovery — `FW-052` (`AMP-240`)

- **Framework**: COD Serial-Returner Exclusion & Prepaid-Upgrade Win-Back Decision Aid (Egypt & KSA)
- **العنوان بالعربية**: أداة قرار استبعاد «كثيري رفض استلام طلبات COD» وتحويلهم للدفع المسبق في حملات استعادة العملاء (`Win-Back`)
- **Selected Artifact Type**: `DECISION_AID`
- **Disclaimer**: *All scenarios, brand names, SKU codes, and metrics below are original, realistic illustrative examples for MENA practitioner training and are never represented as verified client outcomes.*

## 1. Realistic Sample Brief / Input (`المدخلات وموجز الحالة العملية`)

- **Store**: Egyptian & Saudi D2C Skincare & Apparel Store (`18,000` past buyer profiles in Klaviyo).
- **Audit Discovery**: Klaviyo's default `'Win-Back Lapsed VIPs (3+ Orders)'` segment contained `1,140` profiles who had placed 3 to 6 COD orders and refused delivery on **every single one** (costing the store `~95,000 EGP` in wasted courier shipping fees), and the automated flow was emailing them `20% OFF + Free COD Shipping` every 45 days!

## 2. Initial Generated / Completed Output (`المخرج الأولي عند تطبيق الأداة`)

- **Segmentation Overhaul**:
  1. Created `TIER_3_CHRONIC_COD_RETURNER` segment (`1,140` profiles with `>=2` refused COD orders and `>=40%` refusal rate) -> **Excluded from all COD win-back emails and paid Meta/Google retargeting audiences**.
  2. Updated `VIP` and `Standard Win-Back` segments to count **strictly `Fulfilled_Delivered_Orders >= 1` AND `COD_Refusal_Rate < 0.25`**.

## 3. Human Review & Localization/Technical Edits (`المراجعة البشرية والتعديلات الرقابية والتقنية`)

1. **Added Prepaid Rehabilitation Path**: For `TIER_2` customers (`1` failed delivery, often due to courier timing while traveling), sent a polite win-back offering **`"خصم 10% إضافي + أولوية التوصيل عند الدفع المسبق عبر إنستاباي أو البطاقة البنكية أو مدى"`**.
2. **Synced Courier Webhook Status**: Verified that Bosta (Egypt) and SMSA/Aramex (KSA) `Returned_to_Sender / RTO` webhooks increment `orders_cod_refused_count` on the customer profile automatically.

## 4. Final Reviewed Example Outcome (`النتيجة النهائية الجاهزة للتنفيذ`)

- `1,140` chronic COD non-receivers suppressed from COD discount flows and paid remarketing, cutting repeat RTO courier losses while preserving VIP incentives for genuinely delivered buyers.

## 5. What Can Go Wrong & Specific Correction / Fallback (`حالة الفشل المحتملة وخطة الإنقاذ والبديل`)

- **Common Failure Mode (`ما الذي قد يسير بشكل خاطئ؟`)**:
  An ESP syncs Shopify/Salla's `Orders Count` metric when the order is initially placed (`Financial Status: Pending` for COD) and never decrements it when the courier marks the parcel `RTO / Refused` 6 days later.
- **Specific Correction & Non-AI / Platform Fallback (`الإصلاح المحدد والبديل الآمن`)**:
  Base all lifecycle segmentation on the **`Delivered / Paid & Fulfilled`** webhook event (`Fulfillment Status == Fulfilled AND Financial Status == Paid`), never on initial `Placed Order` count.
