# FW-028: Social-to-WhatsApp Click-to-Chat Attribution & Pre-Qualification Triage Workflow
## مسار عمل تتبع إحالات روابط «انقر للدردشة في واتساب» (`Click-to-WhatsApp`) وفرز العملاء قبل التحويل للمبيعات

- **Consolidated Contextual Child IDs (`MERGE_INTO_EXISTING`)**: `AMP-136`, `AMP-146`, `AMP-156`, `AMP-166`
- **Selected Artifact Type**: `OPERATING_FRAMEWORK`
- **Intended Audience**: Social Media Manager, Community Manager, Brand Strategist, Account Director
- **Target Markets & Languages**: Egypt & GCC (`Saudi Arabia, UAE, Kuwait, Qatar, Bahrain, Oman`) — Bilingual Arabic (`Egyptian Ammiya`, `Saudi/Gulf Khaleeji`, `White MSA`) + English
- **Version**: `1.2` | **Last Reviewed**: `2026-10-25` | **Status**: `READY_FOR_REVIEW`

## 1. Plain-Language Promise & Why This Artifact Form Fits the Job

- **What You Can Make or Decide (EN)**: Capture campaign attribution (`UTM` / `fbclid` / `gclid`) and pre-qualify buyers before routing social Click-to-WhatsApp traffic to human sales reps so chats do not appear as `Direct` in GA4 or overwhelm agents with unqualified `'بكام؟'` messages.
- **ما الذي يمكنك إنجازه أو حسمه بهذه الأداة (AR)**: الاحتفاظ ببيانات الإحالة الإعلانية (`UTM / fbclid / gclid`) وتأهيل العميل آلياً قبل تحويله لمندوب المبيعات في واتساب لمنع ضياع المصدر تحت قناة `Direct` في GA4 أو إغراق الموظفين باستفسارات غير مؤهلة.
- **Why `OPERATING_FRAMEWORK` Fits This User Job (EN)**: Direct `wa.me/` links in social bios and ads strip HTTP referrers and flood human agents with unsegmented inquiries; an OPERATING_FRAMEWORK combining reference-code pre-filled messages, AI 3-question triage, and CAPI/GA4 server logging restores full-funnel attribution.
- **لماذا يناسب شكل `OPERATING_FRAMEWORK` هذه المهمة (AR)**: تؤدي روابط `wa.me/` المباشرة إلى فقدان مصدر الزيارة الإعلاني وإغراق فريق المبيعات برسائل عشوائية؛ لذا يعيد هذا الإطار التشغيلي ربط الإحالة وتأهيل العميل آلياً.

## 2. "Use It When" Trigger, Boundaries & Exact Inputs to Prepare

- **Use It When (EN)**: Use whenever driving social media (Instagram, TikTok, Snapchat, Facebook) or paid search traffic into WhatsApp Business in Egypt, KSA, or UAE.
- **متى تستخدم هذه الأداة (AR)**: يُستخدم عند توجيه زيارات الإعلانات أو الحسابات الاجتماعية (إنستغرام، تيك توك، سناب شات، فيسبوك) إلى محادثات واتساب للأعمال في مصر أو السعودية أو الإمارات.
- **When NOT to Use It (EN)**: Do not count a raw 'WhatsApp Link Click' on a landing page as a completed `Purchase` or `Qualified Lead` conversion in Meta/Google Ads (`AMP-069` / `AMP-394`).
- **متى لا تستخدم هذه الأداة (AR)**: لا تقم أبداً باحتساب «مجرد النقر على زر واتساب» كتحويل نهائي (`Purchase` أو `Qualified Lead`) في حملات Meta أو Google (`AMP-069` / `AMP-394`).

### Exact Inputs to Prepare Before Starting (`المدخلات المطلوب تجهيزها`)
1. WhatsApp Business API (`Cloud API` / Wati / Respond.io / ManyChat / SleekFlow) webhook access
2. Campaign UTM & Reference Code naming convention (`[Ref: IG-RAM-04]`)
3. 3-Question Qualification Script (Product/Service interest, City/Delivery Zone, Budget/Payment Preference)

### Privacy-Safe Data Handling (`ضوابط الخصوصية وحماية البيانات الشخصية PDPL`)
- **Strict PII Redaction Before Prompting**: Under Saudi PDPL (Art. 25), UAE Federal Decree-Law No. 45 of 2021, Qatar Law No. 13 of 2016, and Egypt Law No. 151 of 2020, **never paste raw customer names, unhashed mobile numbers (`+9665...` / `+201...`), email addresses, national IDs, or private WhatsApp transcripts into public/consumer LLM interfaces**. Use anonymized placeholders (`{first_name}`, `ORD_10045`) during prompt testing and restrict live customer data to zero-data-retention enterprise API endpoints or local deterministic scripts.

## 3. The Directly Usable Artifact (`الأداة التطبيقية الجاهزة للنسخ والتنفيذ`)

### 3-Step Social-to-WhatsApp Attribution & Triage Architecture

#### Step 1: Never Use Bare `wa.me` Links — Inject a Parseable Campaign Reference Token
When linking from a social bio, story sticker, or landing page button, dynamically inject the campaign/source token and short click ID into the pre-filled WhatsApp `text` parameter:
```javascript
// Landing Page -> WhatsApp Bridge Script (Preserves Attribution & GA4 Event)
function buildTrackedWhatsAppLink(phoneE164, productName, sku) {
  const params = new URLSearchParams(window.location.search);
  const src = params.get('utm_source') || 'organic_web';
  const cmp = params.get('utm_campaign') || 'general';
  const refCode = `${src.slice(0,4).toUpperCase()}-${cmp.slice(0,8).toUpperCase()}-${sku}`;
  const msg = `مرحباً، أرغب في الاستفسار عن: ${productName}
[كود المرجع: ${refCode}]`;
  return `https://wa.me/${phoneE164}?text=${encodeURIComponent(msg)}`;
}
```
- **For Paid Social Ads**: Prefer native **Click-to-WhatsApp (`CTWA`) Ads** on Meta (which pass `ctwa_clid` natively into the WhatsApp Cloud API webhook so you can send Server-Side CAPI `Lead` and `Purchase` events tied directly to the ad!).

#### Step 2: 60-Second Automated WhatsApp Pre-Qualification Flow (Before Human Handoff)
When the inbound message arrives on the WhatsApp API webhook:
1. **Regex Extract `[كود المرجع: ...]`** (or read `referral.ctwa_clid` from Meta CTWA payload) and save it to the CRM Contact record (`first_touch_campaign`).
2. **Send Instant Interactive List / Quick-Reply Menu (3 Taps Max)**:
   - **Reply 1 (Instant Price & Spec Sheet)**: Immediately answer the price (`SAR`/`AED`/`EGP`), warranty, and installment/COD availability (`"السعر 450 ر.س شامل الضريبة ومتاح تقسيط تابي على 4 دفعات"` — never hide the price!).
   - **Reply 2 (Qualification Question)**: Ask 2 quick-reply buttons:
     - `1️⃣ إتمام الطلب الآن (الدفع الإلكتروني / تابي)` → Send direct pre-filled checkout cart link with `utm_source=whatsapp&utm_medium=crm_bot`.
     - `2️⃣ التحدث مع مستشار المبيعات (للطلبات الخاصة / الجملة)` → Route to Human Agent queue **only after** capturing City & Quantity.

#### Step 3: Fire CAPI `Qualified_WhatsApp_Lead` / `Purchase` Only After Qualification
- Fire the optimization event back to Meta CAPI (`action_source: "business_messaging"`, `ctwa_clid`) ONLY when the user completes the qualification step or places an order—never on the initial link click.

## 4. Model & Platform Capability Branches (`فروع قدرات النماذج والمنصات والبدائل الاحتياطية`)

| System / Platform | Capability Status | Official Documentation & Access Date | Operational Constraint in Egypt & GCC | Fallback When Feature/Modality Is Unavailable |
| :--- | :--- | :--- | :--- | :--- |
| **Meta WhatsApp Cloud API (`ctwa_clid` Referral Object & CAPI Business Messaging)** | `supported` | [Official Reference](https://developers.facebook.com/documentation/business-messaging/whatsapp/messages/template-messages) (`2026-10-25`) | Meta Click-to-WhatsApp ads include a `referral` object with `ctwa_clid`, `source_id`, and `headline` in the inbound webhook, enabling direct Server CAPI attribution. | For non-Meta channels (TikTok, Snap, X, website buttons), embed `[كود المرجع: SRC-CMP]` in the `wa.me/?text=` parameter. |

## 5. Consolidated Regional & Vertical Adaptation Matrix (`دمج الأنماط السياقية الفرعية بدون حشو`)

Per Agent 2 v1.2's anti-padding rule, the following **4 cross-verified contextual synthesis patterns** and **1 screened duplicate variants** share this core mechanism and are consolidated directly into this source-of-truth framework:

| Child Pattern ID | Disposition | Regional / Sector Operating Context | Specific Adaptation & Guardrail Integrated in This Asset | Evidence Tier |
| :--- | :--- | :--- | :--- | :--- |
| **`AMP-136`** | `MERGE_INTO_EXISTING` | Egyptian E-Commerce & Social Commerce (Shopify / WooCommerce / Cairo & Alexandria) | Pre-filled dynamic WhatsApp reference tokens mapped to CRM webhook parsers.; Specifically impacts Egyptian brands operating in EGP where merchant-specific payment mix from recent order records, Mobile Wallets (Vodafone Cash), InstaPay, and Fawry dominate. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-146`** | `MERGE_INTO_EXISTING` | UAE & Multi-Market GCC Enterprise / Retail (Dubai, Abu Dhabi, Doha, Kuwait) | Pre-filled dynamic WhatsApp reference tokens mapped to CRM webhook parsers.; Specifically impacts bilingual Arabic/English campaigns in high-CPM, expat-dense Gulf markets under UAE PDPL / TDRA and Qatari regulations. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-156`** | `MERGE_INTO_EXISTING` | High-Trust & Regulated Verticals (Healthcare/SFDA/EDA, Fintech/SAMA/FRA, Real Estate) | Pre-filled dynamic WhatsApp reference tokens mapped to CRM webhook parsers.; Specifically impacts regulated claims requiring SFDA, EDA, MOH, SAMA, FRA, or RERA compliance pre-clearance and strict hallucination guardrails. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-166`** | `MERGE_INTO_EXISTING` | Seasonal Peak Operations (Ramadan, Eid, White/Yellow Friday, Saudi Founding/National Day) | Pre-filled dynamic WhatsApp reference tokens mapped to CRM webhook parsers.; Specifically impacts high-velocity seasonal surges where CPMs jump 40-70%, prices change rapidly, and Hijri calendar cultural sensitivity is paramount. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-516`** | `REJECT_DUPLICATE` | Screened UI/Format Synonym (`Merged Variant: Minor UI/Format Synonym of AMP-166 (Social Media Marketing)`) | Consolidated into parent workflow without duplicate file inflation. | `SCREENED_DUPLICATE_VARIANT` |

### Context-Specific Execution Knobs Across the 5 MENA Operating Environments
1. **Saudi D2C E-Commerce (`Salla / Zid / Riyadh & Jeddah Retail`)**: Enforce `SAR` tax-inclusive pricing (`15% ZATCA VAT`), native `Mada / Apple Pay / Tabby / Tamara` visibility (`AMP-387`), `GAMR Mawthooq` creator verification (`AMP-281`), and White Saudi Khaleeji orthography (`AMP-002`, `AMP-177`).
2. **Egyptian E-Commerce & Social Commerce (`Shopify / WooCommerce / Cairo & Alexandria`)**: Use each merchant’s own order and payment data to assess Cash on Delivery (`COD`), mobile wallets, InstaPay, Fawry, `valU`, address fields, and pre-dispatch WhatsApp confirmation. Verify current provider terms and local requirements before implementation.
3. **UAE & Multi-Market GCC Enterprise / Retail (`Dubai, Abu Dhabi, Doha, Kuwait`)**: Separate high-CPM UAE/Qatar budgets from lower-CPM markets (`AMP-061`), enforce UAE `TDRA` `9 PM – 7 AM` SMS curfew + `AD-` prefix (`AMP-442`), UAE Media Council permits (`AMP-282`), and bilingual Arabic/English canonical & currency parity (`current applicable UAE VAT`, `current applicable Qatar/Kuwait tax rules`, 3-decimal `KWD` `AMP-239`).
4. **High-Trust & Regulated Verticals (`Healthcare SFDA/MOH/EDA, FinTech SAMA/FRA, Real Estate REGA/RERA`)**: Strip all therapeutic/cure verbs (`AMP-176`, `AMP-286`), display mandatory `MOH/SFDA/DHA/EDA/Fal/Trakheesi` permit numbers (`AMP-070`), and route budgets to high-credibility channels (`AMP-290`, `AMP-339`).
5. **Seasonal Peak Operations (`Ramadan, Eid, White/Yellow Friday, Saudi Founding/National Day`)**: Lock Hijri-Gregorian overlaps (`Feb 2027 Ramadan x Saudi Founding Day x Kuwait National Day` `AMP-125`), pre-schedule GMC `sale_price_effective_date` 48h ahead (`AMP-063`), verify 30-day baseline discount permits (`AMP-064`), and disable Meta Advantage+ auto-music (`AMP-065`).

## 6. Worked Example Summary & Failure Recovery (`ملخص المثال التطبيقي وخطة الإنقاذ`)

*(Full step-by-step worked example with annotated human edits is also provided in `EXAMPLE.md`)*

- **Sample Input Brief**: - **Business**: Cairo & Riyadh Custom Kitchens & Dressing Rooms Showroom (`Average Deal: 45,000 EGP / 14,000 SAR`).
- **Problem**: Instagram Reels ads drove `420` daily WhatsApp clicks. Sales reps spent 6 hours/day replying to `"بكام المتر؟"` from users outside their delivery governorates, and GA4 attributed `0` orders to Instagram because links sent from inside WhatsApp opened as `Direct`.
- **Human Review & Key Edits Applied**: 1. **Polite Out-of-Zone Handling**: For users selecting governorates outside the installation zone, the bot politely informs them of current coverage boundaries instead of consuming a sales engineer's phone slot.
2. **UTM Tagging on Outbound Links**: Appended `?utm_source=whatsapp_business&utm_medium=chat_concierge&utm_campaign=igreel_kitch_02` to every link sent by the bot or sales rep so GA4 never buckets WhatsApp return visits into `Direct`.
- **Final Usable Output**: - Human sales engineers now receive `65` pre-qualified, in-zone measurement requests/day (with full `ctwa_clid` + campaign attribution) instead of `420` unfiltered raw chats.
- **What Can Go Wrong**: A botWithholds the product price and forces the shopper to answer 6 mandatory personal questions (Name, Email, Budget, Company, Role, Address) before revealing the price; 85% of Arab shoppers abandon the chat immediately.
- **Correction & Fallback**: Follow the **'Give Value First, Qualify Second' Rule**: always state the transparent price range / starting price in the very first automated reply, then ask at most 2 quick-reply button questions before routing to checkout or a human rep.

## 7. Measurement Plan & Hypothesis Framing (`خطة القياس والضوابط الإحصائية`)

- **Primary Metric to Track**: Ratio of Qualified WhatsApp Conversations to Total Clicks, Human Agent Response SLA (`Target: <5 min` for qualified leads), and Attributed Revenue from `utm_source=whatsapp_business`.
- **Baseline Definition**: Prior 14-day unattributed WhatsApp chat volume and agent response time.
- **Observation Window**: 14–21 days post-launch. *(Must span full 7/14-day weekly cycles and account for 25th–30th monthly salary windows per `AMP-391`)*.
- **What Cannot Be Concluded (Boundary)**: Automated triage filters noise and restores attribution, while sales rep closing skill and pricing competitiveness determine final deal conversion.
