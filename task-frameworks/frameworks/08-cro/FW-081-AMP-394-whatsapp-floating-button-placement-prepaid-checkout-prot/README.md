# `FW-081` — WhatsApp Floating-Button Placement & Prepaid-Checkout Protection Decision Aid
## أداة قرار ضبط ظهور زر «واتساب العائم» لمنع خطف متسوقي الدفع الإلكتروني الجاهزين للشراء (`Prepaid Checkout Hijack`)

- **One-Sentence Promise (EN)**: Prevent intrusive floating WhatsApp buttons from pulling ready-to-pay Apple Pay, Mada, Tabby, and Card shoppers out of your self-serve checkout funnel into slow, unattributed manual chat queues.
- **الوعد التطبيقي في جملة واحدة (AR)**: منع أزرار واتساب العائمة المزعجة من سحب المتسوقين الجاهزين للدفع الذاتي الفوري (عبر `Apple Pay` أو `مدى` أو `تابي` أو البطاقة) إلى طوابير محادثات يدوية بطيئة تفقد الإحالة وتؤجل البيع.
- **Selected Artifact Type**: `DECISION_AID` *(Chosen because: Many MENA stores place a giant pulsing `'اطلب عبر واتساب الآن!'` button right next to (or larger than) the `'Add to Cart'` and `'Checkout'` buttons on every page, even for simple 150 SAR/800 EGP items; ready-to-pay Apple Pay/Mada shoppers click WhatsApp instead, wait 25 minutes for a human agent to reply, lose their attribution cookie (`AMP-126`), or switch from Prepaid to COD! A contextual DECISION_AID shows when to display WhatsApp and when to hide it.)*
- **Consolidated Child Pattern IDs (`MERGE_INTO_EXISTING`)**: `AMP-404`, `AMP-414`, `AMP-424`, `AMP-434`
- **Screened Duplicate IDs (`REJECT_DUPLICATE`)**: None
- **Intended Audience**: CRO Specialist, UX/UI Designer, E-Commerce Product Manager, Frontend Developer
- **Markets & Languages**: Egypt & GCC (`KSA, UAE, Kuwait, Qatar, Bahrain, Oman`) | Arabic (`Egyptian Ammiya, Saudi/Gulf Khaleeji, White MSA`) & English

## When to Use This Asset (`متى تستخدم هذه الأداة؟`)

- **Trigger (EN)**: Use when configuring WhatsApp chat widgets on e-commerce stores and landing pages in KSA, UAE, and Egypt.
- **داعي الاستخدام (AR)**: تُستخدم عند إعداد أزرار وودجات واتساب في المتاجر الإلكترونية وصفحات الهبوط في السعودية والإمارات ومصر.
- **Do NOT Use When**: Never display a floating `'Order on WhatsApp'` button on the `/checkout` page unless an actual payment failure or idle timeout (`>90 seconds` stalled on an error) has occurred!

## Quick Start (3 Steps for a Non-Expert Marketer)

1. **Prepare Your Inputs (`جهّز المدخلات`)**:
   - Product AOV & Customization Complexity (`Standard Self-Serve SKU < 1,000 SAR / 4,000 EGP` vs. `Bespoke / High-Ticket > 2,000 SAR / 10,000 EGP`)
   - Page Route (`/`, `/collections/*`, `/products/*`, `/cart`, `/checkout`)
   - Cart Context Deep-Link Generator (`AMP-126`)
2. **Copy or Run the Artifact (`انسخ القالب أو طبّق قائمة الفحص`)**:
   - Open [`ASSET.md`](./ASSET.md) and copy the ready-to-use `DECISION_AID` block (or run the included validation snippet).
3. **Compare Against the Worked Example & Verify (`قارن بالمثال العملي وتجنب الأخطاء`)**:
   - Review [`EXAMPLE.md`](./EXAMPLE.md) to see the realistic input brief → raw output → human review edits → final usable result, plus the common failure mode and recovery step.
   - Check [`SOURCES.md`](./SOURCES.md) for primary official documentation, access dates (`2026-10-25`), and regulatory/technical boundaries.

## Files in This Folder

- [`README.md`](./README.md): Plain-language overview, selected artifact type, use trigger, and 3-step quick start.
- [`ASSET.md`](./ASSET.md): The complete, copy-ready `DECISION_AID` (bilingual Arabic + English), model capability branches, regional adaptation matrix, and measurement plan.
- [`EXAMPLE.md`](./EXAMPLE.md): End-to-end worked example with human review pass and failure/recovery scenario.
- [`SOURCES.md`](./SOURCES.md): Direct primary references (`2026-10-25`), separating problem evidence from official capability/regulatory evidence.
- [`PUBLIC-PAGE-CONTENT.md`](./PUBLIC-PAGE-CONTENT.md): Complete user-facing web publication page containing both the full working artifact and the complete worked example.
