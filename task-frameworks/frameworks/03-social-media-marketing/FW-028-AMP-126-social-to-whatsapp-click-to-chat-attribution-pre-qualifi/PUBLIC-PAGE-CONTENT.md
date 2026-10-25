# Social-to-WhatsApp Click-to-Chat Attribution & Pre-Qualification Triage Workflow
## <span dir="rtl">مسار عمل تتبع إحالات روابط «انقر للدردشة في واتساب» (`Click-to-WhatsApp`) وفرز العملاء قبل التحويل للمبيعات</span>

> **Asset ID**: `FW-028` (`AMP-126`) | **Artifact Type**: `OPERATING_FRAMEWORK` | **Channel**: Social Media Marketing | **Markets**: Egypt & GCC (`KSA, UAE, Kuwait, Qatar, Bahrain, Oman`) | **Version**: `1.2` (`Reviewed 2026-10-25`)

**What You Can Do With This (`ماذا يمكنك أن تنجز بهذه الأداة؟`)**:
- **EN**: Capture campaign attribution (`UTM` / `fbclid` / `gclid`) and pre-qualify buyers before routing social Click-to-WhatsApp traffic to human sales reps so chats do not appear as `Direct` in GA4 or overwhelm agents with unqualified `'بكام؟'` messages.
- **AR**: <span dir="rtl">الاحتفاظ ببيانات الإحالة الإعلانية (`UTM / fbclid / gclid`) وتأهيل العميل آلياً قبل تحويله لمندوب المبيعات في واتساب لمنع ضياع المصدر تحت قناة `Direct` في GA4 أو إغراق الموظفين باستفسارات غير مؤهلة.</span>

## 1. Use It When & Required Inputs (`متى تستخدمها وما المدخلات المطلوبة؟`)

- **Use It When (EN)**: Use whenever driving social media (Instagram, TikTok, Snapchat, Facebook) or paid search traffic into WhatsApp Business in Egypt, KSA, or UAE.
- **متى تستخدمها (AR)**: <span dir="rtl">يُستخدم عند توجيه زيارات الإعلانات أو الحسابات الاجتماعية (إنستغرام، تيك توك، سناب شات، فيسبوك) إلى محادثات واتساب للأعمال في مصر أو السعودية أو الإمارات.</span>
- **When NOT to Use It (EN)**: Do not count a raw 'WhatsApp Link Click' on a landing page as a completed `Purchase` or `Qualified Lead` conversion in Meta/Google Ads (`AMP-069` / `AMP-394`).
- **متى لا تستخدمها (AR)**: <span dir="rtl">لا تقم أبداً باحتساب «مجرد النقر على زر واتساب» كتحويل نهائي (`Purchase` أو `Qualified Lead`) في حملات Meta أو Google (`AMP-069` / `AMP-394`).</span>

### Exact Inputs to Prepare (`المدخلات المطلوب تجهيزها قبل البدء`)
- WhatsApp Business API (`Cloud API` / Wati / Respond.io / ManyChat / SleekFlow) webhook access
- Campaign UTM & Reference Code naming convention (`[Ref: IG-RAM-04]`)
- 3-Question Qualification Script (Product/Service interest, City/Delivery Zone, Budget/Payment Preference)

## 2. The Working `OPERATING_FRAMEWORK` (`الأداة الكاملة الجاهزة للنسخ والتطبيق الفوري`)

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

## 3. Complete End-to-End Worked Example (`مثال تطبيقي متكامل من المدخلات حتى المراجعة البشرية والنتيجة النهائية`)

*(Illustrative scenario — original example for training, never represented as a verified client outcome)*

### Step A: Sample Brief / Input (`موجز المدخلات`)
- **Business**: Cairo & Riyadh Custom Kitchens & Dressing Rooms Showroom (`Average Deal: 45,000 EGP / 14,000 SAR`).
- **Problem**: Instagram Reels ads drove `420` daily WhatsApp clicks. Sales reps spent 6 hours/day replying to `"بكام المتر؟"` from users outside their delivery governorates, and GA4 attributed `0` orders to Instagram because links sent from inside WhatsApp opened as `Direct`.

### Step B: Initial Output (`المخرج الأولي`)
- **Deployed WhatsApp Triage & Attribution Flow**:
  1. Extracted `ctwa_clid` and `[كود المرجع: IGREEL-KITCH-02]`.
  2. Instant Bot Reply delivered the transparent starting price table per meter + material guide PDF, then asked:
     - **السؤال 1**: `"في أي مدينة/محافظة يقع المشروع؟"` (`[القاهرة الكبرى / الإسكندرية]` vs `[خارج نطاق التركيب]`)
     - **السؤال 2**: `"متى ترغب في رفع المقاسات؟"` (`[خلال هذا الأسبوع]` vs `[أستكشف الأسعار فقط]`)

### Step C: Human Review & Edits (`التدقيق البشري والتعديلات`)
1. **Polite Out-of-Zone Handling**: For users selecting governorates outside the installation zone, the bot politely informs them of current coverage boundaries instead of consuming a sales engineer's phone slot.
2. **UTM Tagging on Outbound Links**: Appended `?utm_source=whatsapp_business&utm_medium=chat_concierge&utm_campaign=igreel_kitch_02` to every link sent by the bot or sales rep so GA4 never buckets WhatsApp return visits into `Direct`.

### Step D: Final Reviewed Example Outcome (`النتيجة النهائية المعتمدة`)
- Human sales engineers now receive `65` pre-qualified, in-zone measurement requests/day (with full `ctwa_clid` + campaign attribution) instead of `420` unfiltered raw chats.

## 4. What Can Go Wrong & How to Fix It (`الأخطاء الشائعة وخطة الإنقاذ`)

- **Failure Case (`المشكلة المحتملة`)**: A botWithholds the product price and forces the shopper to answer 6 mandatory personal questions (Name, Email, Budget, Company, Role, Address) before revealing the price; 85% of Arab shoppers abandon the chat immediately.
- **Correction & Fallback (`الحل الإجرائي والبديل الآمن`)**: Follow the **'Give Value First, Qualify Second' Rule**: always state the transparent price range / starting price in the very first automated reply, then ask at most 2 quick-reply button questions before routing to checkout or a human rep.

## 5. Model & Platform Capability Matrix (`مصفوفة قدرات النماذج والمنصات — 2026-10-25`)

| Platform / Model | Status | Official Documentation | MENA Operational Constraint | Fallback |
| :--- | :--- | :--- | :--- | :--- |
| **Meta WhatsApp Cloud API (`ctwa_clid` Referral Object & CAPI Business Messaging)** | `supported` | [Official Docs](https://developers.facebook.com/documentation/business-messaging/whatsapp/messages/template-messages) (`2026-10-25`) | Meta Click-to-WhatsApp ads include a `referral` object with `ctwa_clid`, `source_id`, and `headline` in the inbound webhook, enabling direct Server CAPI attribution. | For non-Meta channels (TikTok, Snap, X, website buttons), embed `[كود المرجع: SRC-CMP]` in the `wa.me/?text=` parameter. |

## 6. How to Measure Success (`خطة القياس والضوابط`)

- **Primary Metric**: Ratio of Qualified WhatsApp Conversations to Total Clicks, Human Agent Response SLA (`Target: <5 min` for qualified leads), and Attributed Revenue from `utm_source=whatsapp_business`.
- **Baseline**: Prior 14-day unattributed WhatsApp chat volume and agent response time.
- **Observation Window**: 14–21 days post-launch.
- **Interpretation Boundary**: Automated triage filters noise and restores attribution, while sales rep closing skill and pricing competitiveness determine final deal conversion.

## 7. Primary Sources & Evidence Boundaries (`المصادر الموثقة وحدود الأدلة`)

- [How GA4 Classifies AI Traffic for Arab Websites: What Saudi, UAE and Egyptian Sites Lose (2026 Study)](https://voctos.net/ga4-ai-traffic-arab-markets/) — *VOCTOS* (Published `2026-10-18`, Accessed `2026-10-25`): GA4's AI Assistant channel (launched 13 May 2026) misses 96.9% of AI search citations (which come from Google AI Overviews and AI Mode and land in Organic Search), sends ChatGPT links with rel='noreferrer' or WhatsApp shares to Direct, and sends Perplexity, Claude, HUMAIN Chat (KSA), Fanar (Qatar), and Gulf marketplaces (amazon.sa, noon.com) to Referral.
- [Digital Advertising Landscape in Egypt (2026)](https://23hublab.com/digital-advertising-landscape-in-egypt/) — *23HubLab* (Published `2026-03-15`, Accessed `2026-10-25`): In Egypt, standard Meta Pixel captures only 60-75% of conversions (25-40% lost to in-app browsers, iOS ATT, and ad blockers), while platform-reported conversions overstate actual revenue by 20-40% due to COD cancellations and last-click inflation; provides 2026 EGP CPM/CPC/CPL benchmarks and notes Snapchat is niche in Egypt vs TikTok/Meta.
