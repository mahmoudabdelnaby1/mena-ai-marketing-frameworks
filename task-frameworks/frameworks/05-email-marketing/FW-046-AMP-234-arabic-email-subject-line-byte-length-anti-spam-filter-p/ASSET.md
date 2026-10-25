# FW-046: Arabic Email Subject-Line Byte-Length & Anti-Spam Filter Prompt Template
## قالب صياغة عناوين رسائل البريد الإلكتروني العربية (ضبط طول البايتات `UTF-8` وتجنب فلاتر السبام والوعود المضللة)

- **Consolidated Contextual Child IDs (`MERGE_INTO_EXISTING`)**: `AMP-244`, `AMP-254`, `AMP-264`, `AMP-274`
- **Selected Artifact Type**: `PROMPT_TEMPLATE`
- **Intended Audience**: CRM Manager, Email Marketing Specialist, Lifecycle Marketer, Data Privacy Officer
- **Target Markets & Languages**: Egypt & GCC (`Saudi Arabia, UAE, Kuwait, Qatar, Bahrain, Oman`) — Bilingual Arabic (`Egyptian Ammiya`, `Saudi/Gulf Khaleeji`, `White MSA`) + English
- **Version**: `1.2` | **Last Reviewed**: `2026-10-25` | **Status**: `READY_FOR_REVIEW`

## 1. Plain-Language Promise & Why This Artifact Form Fits the Job

- **What You Can Make or Decide (EN)**: Write high-open-rate Arabic email subject lines and preheaders (`<= 38` Arabic chars) that never clip on iOS/Android mobile inboxes or trigger Gmail/Outlook spam filters.
- **ما الذي يمكنك إنجازه أو حسمه بهذه الأداة (AR)**: كتابة عناوين رسائل بريد إلكتروني (`Subject Lines`) ونصوص معاينة (`Preheaders`) عربية موجزة (`38 حرفاً كحد أقصى`) لا تنقطع في شاشات الجوال ولا تستثير فلاتر البريد المزعج (`Spam`).
- **Why `PROMPT_TEMPLATE` Fits This User Job (EN)**: Unguided LLMs translate 60-character English subject lines into 65–80 character Arabic sentences filled with exclamation marks, emojis, and spam-triggering words (`'مجاناً 100%!!! اربح الآن'`), which both exceed RFC 2047 MIME UTF-8 header folding limits and get clipped at ~38–42 characters on mobile Gmail/iOS Mail; a constrained PROMPT_TEMPLATE fixes both length and deliverability.
- **لماذا يناسب شكل `PROMPT_TEMPLATE` هذه المهمة (AR)**: تترجم النماذج اللغوية عناوين البريد الإنجليزية إلى جمل عربية طويلة (65–80 حرفاً) مليئة بعلامات التعجب والرموز التعبيرية وكلمات السبام («اربح مجاناً 100%!!!»)، مما يؤدي إلى بتر العنوان في تطبيقات الجوال عند الحرف 38 وتصنيف الرسالة كبريد مزعج؛ لذا يضبط هذا القالب الطول والصياغة.

## 2. "Use It When" Trigger, Boundaries & Exact Inputs to Prepare

- **Use It When (EN)**: Use when generating Arabic or bilingual email subject lines (`Subject`) and preview texts (`Preheader`) for newsletters, cart recovery, or promotional campaigns.
- **متى تستخدم هذه الأداة (AR)**: تُستخدم عند صياغة عناوين الرسائل البريدية (`Subject Line`) ونص المعاينة (`Preheader`) للحملات والنشرات البريدية وسلاسل السلات المتروكة.
- **When NOT to Use It (EN)**: Do not put more than 1 emoji in an Arabic subject line, never use `RE:` / `رد:` or `FWD:` on a marketing email to fake a personal reply, and never exceed 42 Arabic characters.
- **متى لا تستخدم هذه الأداة (AR)**: لا تضع أكثر من رمز تعبيري واحد (`Emoji`) في العنوان، ولا تضف بادئة `رد:` أو `RE:` للإيهام بأنها مراسلة شخصية، ولا تتجاوز 42 حرفاً عربياً.

### Exact Inputs to Prepare Before Starting (`المدخلات المطلوب تجهيزها`)
1. Core Email Offer / Topic
2. Target Dialect/Register (`Saudi White Khaleeji`, `Egyptian Polite Ammiya`, or `Modern White MSA`)
3. Mandatory Prefix Requirement (e.g., if sending in UAE under TDRA promotional rules where applicable)

### Privacy-Safe Data Handling (`ضوابط الخصوصية وحماية البيانات الشخصية PDPL`)
- **Strict PII Redaction Before Prompting**: Under Saudi PDPL (Art. 25), UAE Federal Decree-Law No. 45 of 2021, Qatar Law No. 13 of 2016, and Egypt Law No. 151 of 2020, **never paste raw customer names, unhashed mobile numbers (`+9665...` / `+201...`), email addresses, national IDs, or private WhatsApp transcripts into public/consumer LLM interfaces**. Use anonymized placeholders (`{first_name}`, `ORD_10045`) during prompt testing and restrict live customer data to zero-data-retention enterprise API endpoints or local deterministic scripts.

## 3. The Directly Usable Artifact (`الأداة التطبيقية الجاهزة للنسخ والتنفيذ`)

### Copy-Ready Arabic Subject Line & Preheader Generator Prompt

```xml
<system_role>
You are an Email Deliverability & Arabic Copywriting Specialist for MENA.
TECHNICAL CONSTRAINTS:
1. MOBILE CLIPPING & UTF-8 MIME LIMIT: Every Arabic character takes 2 bytes in UTF-8 and encodes into Base64/Quoted-Printable inside RFC 2047 email headers (`=?UTF-8?B?...?=`). Furthermore, iOS Mail and Gmail Android clip Arabic subject lines at ~38–42 characters.
   -> HARD RULE: `subject_ar` MUST be between 22 and 38 characters (5 to 7 words MAX, including spaces!).
2. COMPLEMENTARY PREHEADER: `preheader_ar` MUST be 45 to 70 characters and add new concrete information (e.g., payment options, expiry date, or key benefit)—never repeat the subject line.
3. SPAM FILTER BLACKLIST (ZERO TOLERANCE):
   - Never use: `مجاناً 100%`, `اربح الآن`, `اضغط هنا فوراً`, `فرصة لا تعوض!!!`, `عاجل جداً`, `مليونير`, `دخل إضافي`, `بدون شروط`, fake `رد: / Re:`.
   - Punctuation cap: Max ONE question mark `؟` or zero exclamation marks. Max ONE emoji (placed at the very end of the line so it does not break RTL BiDi alignment at the start!).
</system_role>

<email_brief>
- Campaign Goal: {{GOAL: Cart Recovery | New Collection | Educational Newsletter | VIP Restock}}
- Offer / Core Hook: {{OFFER_DETAILS}}
- Market & Register: {{MARKET: KSA | UAE | Egypt}}
</email_brief>

<output_schema>
Return 5 distinct angle options (Curiosity, Direct Value, Social Proof, Restock/Timely, VIP Personal) in a Markdown table:
| Angle | `subject_ar` (<= 38 chars) | Char Count | UTF-8 Bytes | `preheader_ar` (45-70 chars) | Spam Risk Check |
</output_schema>
```

## 4. Model & Platform Capability Branches (`فروع قدرات النماذج والمنصات والبدائل الاحتياطية`)

| System / Platform | Capability Status | Official Documentation & Access Date | Operational Constraint in Egypt & GCC | Fallback When Feature/Modality Is Unavailable |
| :--- | :--- | :--- | :--- | :--- |
| **Gmail, Apple Mail & Outlook Mobile Subject Line Character & BiDi First-Strong-Character Detection** | `supported` | [Official Reference](https://mailtester.com/blog/right-to-left-email-rendering-problems-gmail-outlook/) (`2026-10-25`) | Unicode BiDi standard (UAX #9) sets paragraph direction from the first strong directional character; starting an Arabic subject line with an Arabic word ensures proper RTL inbox alignment. | If a subject line must begin with a Latin brand name, prepend the Unicode Right-to-Left Mark (`‏`) as the first character. |

## 5. Consolidated Regional & Vertical Adaptation Matrix (`دمج الأنماط السياقية الفرعية بدون حشو`)

Per Agent 2 v1.2's anti-padding rule, the following **4 cross-verified contextual synthesis patterns** and **1 screened duplicate variants** share this core mechanism and are consolidated directly into this source-of-truth framework:

| Child Pattern ID | Disposition | Regional / Sector Operating Context | Specific Adaptation & Guardrail Integrated in This Asset | Evidence Tier |
| :--- | :--- | :--- | :--- | :--- |
| **`AMP-244`** | `MERGE_INTO_EXISTING` | Egyptian E-Commerce & Social Commerce (Shopify / WooCommerce / Cairo & Alexandria) | 35-to-45 character Arabic subject line limit with clean preview text and zero spam-trigger punctuation.; Specifically impacts Egyptian brands operating in EGP where merchant-specific payment mix from recent order records, Mobile Wallets (Vodafone Cash), InstaPay, and Fawry dominate. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-254`** | `MERGE_INTO_EXISTING` | UAE & Multi-Market GCC Enterprise / Retail (Dubai, Abu Dhabi, Doha, Kuwait) | 35-to-45 character Arabic subject line limit with clean preview text and zero spam-trigger punctuation.; Specifically impacts bilingual Arabic/English campaigns in high-CPM, expat-dense Gulf markets under UAE PDPL / TDRA and Qatari regulations. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-264`** | `MERGE_INTO_EXISTING` | High-Trust & Regulated Verticals (Healthcare/SFDA/EDA, Fintech/SAMA/FRA, Real Estate) | 35-to-45 character Arabic subject line limit with clean preview text and zero spam-trigger punctuation.; Specifically impacts regulated claims requiring SFDA, EDA, MOH, SAMA, FRA, or RERA compliance pre-clearance and strict hallucination guardrails. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-274`** | `MERGE_INTO_EXISTING` | Seasonal Peak Operations (Ramadan, Eid, White/Yellow Friday, Saudi Founding/National Day) | 35-to-45 character Arabic subject line limit with clean preview text and zero spam-trigger punctuation.; Specifically impacts high-velocity seasonal surges where CPMs jump 40-70%, prices change rapidly, and Hijri calendar cultural sensitivity is paramount. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-524`** | `REJECT_DUPLICATE` | Screened UI/Format Synonym (`Merged Variant: Minor UI/Format Synonym of AMP-254 (Email Marketing)`) | Consolidated into parent workflow without duplicate file inflation. | `SCREENED_DUPLICATE_VARIANT` |

### Context-Specific Execution Knobs Across the 5 MENA Operating Environments
1. **Saudi D2C E-Commerce (`Salla / Zid / Riyadh & Jeddah Retail`)**: Enforce `SAR` tax-inclusive pricing (`15% ZATCA VAT`), native `Mada / Apple Pay / Tabby / Tamara` visibility (`AMP-387`), `GAMR Mawthooq` creator verification (`AMP-281`), and White Saudi Khaleeji orthography (`AMP-002`, `AMP-177`).
2. **Egyptian E-Commerce & Social Commerce (`Shopify / WooCommerce / Cairo & Alexandria`)**: Use each merchant’s own order and payment data to assess Cash on Delivery (`COD`), mobile wallets, InstaPay, Fawry, `valU`, address fields, and pre-dispatch WhatsApp confirmation. Verify current provider terms and local requirements before implementation.
3. **UAE & Multi-Market GCC Enterprise / Retail (`Dubai, Abu Dhabi, Doha, Kuwait`)**: Separate high-CPM UAE/Qatar budgets from lower-CPM markets (`AMP-061`), enforce UAE `TDRA` `9 PM – 7 AM` SMS curfew + `AD-` prefix (`AMP-442`), UAE Media Council permits (`AMP-282`), and bilingual Arabic/English canonical & currency parity (`current applicable UAE VAT`, `current applicable Qatar/Kuwait tax rules`, 3-decimal `KWD` `AMP-239`).
4. **High-Trust & Regulated Verticals (`Healthcare SFDA/MOH/EDA, FinTech SAMA/FRA, Real Estate REGA/RERA`)**: Strip all therapeutic/cure verbs (`AMP-176`, `AMP-286`), display mandatory `MOH/SFDA/DHA/EDA/Fal/Trakheesi` permit numbers (`AMP-070`), and route budgets to high-credibility channels (`AMP-290`, `AMP-339`).
5. **Seasonal Peak Operations (`Ramadan, Eid, White/Yellow Friday, Saudi Founding/National Day`)**: Lock Hijri-Gregorian overlaps (`Feb 2027 Ramadan x Saudi Founding Day x Kuwait National Day` `AMP-125`), pre-schedule GMC `sale_price_effective_date` 48h ahead (`AMP-063`), verify 30-day baseline discount permits (`AMP-064`), and disable Meta Advantage+ auto-music (`AMP-065`).

## 6. Worked Example Summary & Failure Recovery (`ملخص المثال التطبيقي وخطة الإنقاذ`)

*(Full step-by-step worked example with annotated human edits is also provided in `EXAMPLE.md`)*

- **Sample Input Brief**: - **Campaign**: Restock notification for a sold-out Ethiopian Specialty Coffee (`250g`, `79 SAR`) in Saudi Arabia.
- **Bad AI Draft (`74` chars + Spam Triggers)**: `"🔥🚨 عاجل جداً!! قهوتك الإثيوبية المفضلة عادت للمخزون الآن بخصم مجاني وشحن مجاني 100% لا تفوت الفرصة!!!"`
- **Human Review & Key Edits Applied**: 1. **BiDi Emoji Placement Check**: Confirmed the coffee emoji `☕` is placed at the **end** of the Arabic string (left side in RTL) rather than the beginning, because leading emojis next to English merge tags can flip alignment on older Android clients.
2. **Verified Mobile Preview**: Confirmed all 3 subject lines render completely without `...` truncation on a 375px iPhone screen.
- **Final Usable Output**: - Selected Subject Line #2 (`"حجزنا لك كيسك من محصول إثيوبيا"` — `30` chars, `55` UTF-8 bytes) paired with the 65-char preheader.
- **What Can Go Wrong**: A marketer puts a Latin brand name or number at the very beginning of an Arabic subject line (`'50% خصم على عطور الشتاء'`); on Gmail iOS, the subject line aligns left-to-right and pushes the Arabic words off-screen.
- **Correction & Fallback**: Always **start an Arabic subject line with an Arabic word** (e.g., `'خصم 50% على عطور الشتاء'` instead of `'50% خصم...'`) so the inbox client detects the first strong directional character as Right-to-Left (`RTL`)!

## 7. Measurement Plan & Hypothesis Framing (`خطة القياس والضوابط الإحصائية`)

- **Primary Metric to Track**: Inbox Placement Rate (`Primary/Inbox` vs. `Spam/Promotions`), Open Rate, and Click-to-Open Rate (`CTOR`).
- **Baseline Definition**: Prior 30-day campaign average with long/unconstrained subject lines.
- **Observation Window**: Measured 48 hours after campaign send. *(Must span full 7/14-day weekly cycles and account for 25th–30th monthly salary windows per `AMP-391`)*.
- **What Cannot Be Concluded (Boundary)**: Short, spam-free subject lines prevent mobile clipping and spam-folder routing, while sender domain reputation (`AMP-236`) and list hygiene (`AMP-232`) co-determine inbox placement.
