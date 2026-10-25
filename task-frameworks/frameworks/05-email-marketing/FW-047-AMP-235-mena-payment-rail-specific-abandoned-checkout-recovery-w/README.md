# `FW-047` — MENA Payment-Rail Specific Abandoned Checkout Recovery Workflow (COD vs. Tabby/Tamara BNPL vs. Fawry/InstaPay)
## مسار عمل استرداد السلات المتروكة المخصص حسب وسيلة الدفع في مصر والخليج (`COD` مقابل `Tabby/Tamara` مقابل كود `فوري/إنستاباي`)

- **One-Sentence Promise (EN)**: Branch abandoned checkout emails and WhatsApp reminders by the shopper's selected payment method—separating Fawry OTC reference-code expiry reminders in Egypt from Tabby/Tamara installment nudges in KSA/UAE and COD trust reassurance.
- **الوعد التطبيقي في جملة واحدة (AR)**: تفريع رسائل استرداد السلات المتروكة وتوقيتها حسب وسيلة الدفع التي اختارها المتسوق (تذكير بصلاحية كود «فوري» قبل انتهائه في مصر، مقابل تذكير تقسيط «تابي/تمارا» في الخليج، أو طمأنة الدفع عند الاستلام).
- **Selected Artifact Type**: `OPERATING_FRAMEWORK` *(Chosen because: Standard AI abandoned-cart templates assume every shopper abandoned a credit-card form and send the same `'Did you forget something? Take 10% off'` email at 4 hours and 24 hours; in reality, an Egyptian shopper who generated a Fawry cash reference code hasn't 'abandoned'—they need their 48-hour reference code and nearest Fawry outlet reminder, while a KSA shopper who failed a Mada 3DS or Tabby split needs a 15-minute payment-switch link; an OPERATING_FRAMEWORK branches by payment rail.)*
- **Consolidated Child Pattern IDs (`MERGE_INTO_EXISTING`)**: `AMP-245`, `AMP-255`, `AMP-265`, `AMP-275`
- **Screened Duplicate IDs (`REJECT_DUPLICATE`)**: `AMP-525`
- **Intended Audience**: CRM Manager, Email Marketing Specialist, Lifecycle Marketer, Data Privacy Officer
- **Markets & Languages**: Egypt & GCC (`KSA, UAE, Kuwait, Qatar, Bahrain, Oman`) | Arabic (`Egyptian Ammiya, Saudi/Gulf Khaleeji, White MSA`) & English

## When to Use This Asset (`متى تستخدم هذه الأداة؟`)

- **Trigger (EN)**: Use when configuring abandoned checkout / pending-payment automation flows in Klaviyo, HubSpot, Omnisend, Salla, Zid, or Shopify/WooCommerce across Egypt, KSA, and UAE.
- **داعي الاستخدام (AR)**: تُستخدم عند إعداد سلاسل استرداد السلات المتروكة والدفعات المعلقة في متاجر مصر والسعودية والإمارات.
- **Do NOT Use When**: Do not send an 'Abandoned Cart 10% Discount Code' to a customer who already generated a Pending Fawry Reference Code or Pending Bank/InstaPay Transfer—that cannibalizes margin on an already-committed order!

## Quick Start (3 Steps for a Non-Expert Marketer)

1. **Prepare Your Inputs (`جهّز المدخلات`)**:
   - Checkout Event Webhook Payload containing `payment_gateway_selected` (`fawry_otc`, `instapay`, `tabby`, `tamara`, `mada_card`, `cod`, or `none`)
   - Fawry Reference Code (`{{fawry_ref_number}}`) & Expiry Timestamp (`{{fawry_expires_at}}`)
   - Customer COD Return History Score (`AMP-240`)
2. **Copy or Run the Artifact (`انسخ القالب أو طبّق قائمة الفحص`)**:
   - Open [`ASSET.md`](./ASSET.md) and copy the ready-to-use `OPERATING_FRAMEWORK` block (or run the included validation snippet).
3. **Compare Against the Worked Example & Verify (`قارن بالمثال العملي وتجنب الأخطاء`)**:
   - Review [`EXAMPLE.md`](./EXAMPLE.md) to see the realistic input brief → raw output → human review edits → final usable result, plus the common failure mode and recovery step.
   - Check [`SOURCES.md`](./SOURCES.md) for primary official documentation, access dates (`2026-10-25`), and regulatory/technical boundaries.

## Files in This Folder

- [`README.md`](./README.md): Plain-language overview, selected artifact type, use trigger, and 3-step quick start.
- [`ASSET.md`](./ASSET.md): The complete, copy-ready `OPERATING_FRAMEWORK` (bilingual Arabic + English), model capability branches, regional adaptation matrix, and measurement plan.
- [`EXAMPLE.md`](./EXAMPLE.md): End-to-end worked example with human review pass and failure/recovery scenario.
- [`SOURCES.md`](./SOURCES.md): Direct primary references (`2026-10-25`), separating problem evidence from official capability/regulatory evidence.
- [`PUBLIC-PAGE-CONTENT.md`](./PUBLIC-PAGE-CONTENT.md): Complete user-facing web publication page containing both the full working artifact and the complete worked example.
