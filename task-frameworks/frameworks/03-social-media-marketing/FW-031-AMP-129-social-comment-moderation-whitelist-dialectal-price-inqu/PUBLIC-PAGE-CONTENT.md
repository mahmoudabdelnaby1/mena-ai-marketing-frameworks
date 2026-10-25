# Social Comment Moderation Whitelist & Dialectal Price-Inquiry Routing Checklist (`بكام` / `بكم`)
## <span dir="rtl">قائمة فحص وضبط الفلترة الآلية للتعليقات لحماية استفسارات الشراء باللهجات (`بكام` / `بكم` / `تفاصيل`)</span>

> **Asset ID**: `FW-031` (`AMP-129`) | **Artifact Type**: `CHECKLIST` | **Channel**: Social Media Marketing | **Markets**: Egypt & GCC (`KSA, UAE, Kuwait, Qatar, Bahrain, Oman`) | **Version**: `1.2` (`Reviewed 2026-10-25`)

**What You Can Do With This (`ماذا يمكنك أن تنجز بهذه الأداة؟`)**:
- **EN**: Configure AI comment moderation and auto-DM workflows so short colloquial buyer inquiries (`'بكام؟'`, `'بكم؟'`, `'موجود؟'`, `'تفاصيل'`) are converted into sales instead of being auto-hidden as spam or low-quality comments.
- **AR**: <span dir="rtl">ضبط أدوات إدارة التعليقات والرد الآلي بحيث تتحول استفسارات الشراء القصيرة باللهجات («بكام؟»، «بكم؟»، «موجود؟»، «تفاصيل») إلى مبيعات فورية بدلاً من إخفائها بالخطأ كرسائل مزعجة.</span>

## 1. Use It When & Required Inputs (`متى تستخدمها وما المدخلات المطلوبة؟`)

- **Use It When (EN)**: Use when configuring automated comment moderation or comment-to-DM automation tools (ManyChat, Respond.io, Meta Inbox Automations, Brandwatch, Sprinklr) on Instagram, Facebook, or TikTok.
- **متى تستخدمها (AR)**: <span dir="rtl">تُستخدم عند إعداد أدوات إخفاء التعليقات أو الرد التلقائي (ManyChat, Respond.io, Meta Suite) على إنستغرام وفيسبوك وتيك توك.</span>
- **When NOT to Use It (EN)**: Do not reply to `'بكام؟'` with `'تم الرد على الخاص (Check DM)'` if your store sells standard fixed-price retail items—hiding prices in comments frustrates GCC/Egyptian shoppers and lowers ad conversion rate.
- **متى لا تستخدمها (AR)**: <span dir="rtl">لا تكتفِ بالرد العلني المستفز «تم الرد على الخاص» للمنتجات ذات السعر الثابت؛ فإخفاء السعر يثير استياء المتسوقين في مصر والخليج ويخفض معدل التحويل.</span>

### Exact Inputs to Prepare (`المدخلات المطلوب تجهيزها قبل البدء`)
- List of active social moderation tools & Meta Page/Instagram Moderation Keyword Blocklists
- Product catalog price & payment summary for active promoted posts
- Comment-to-DM automation rules (ManyChat / Meta Inbox)

## 2. The Working `CHECKLIST` (`الأداة الكاملة الجاهزة للنسخ والتطبيق الفوري`)

### Dialectal Buyer-Intent Whitelist & Comment-to-Sale Checklist

#### 1. Mandatory High-Intent Buyer Whitelist (`NEVER Auto-Hide These Tokens`)
Configure your comment moderation tool so comments containing any of these Arabic/Franco buyer-intent tokens are **EXEMPT from "Short Comment / Repetitive Spam" auto-hiding** and routed immediately to the **High-Intent Sales Trigger**:
- **Egyptian Ammiya Price & Stock Tokens**:
  `بكام` | `بكااام` | `بكام ده` | `بكام دي` | `سعره كام` | `سعرها كام` | `التفاصيل` | `تفاصيل` | `موجود` | `متاح` | `فيه توصيل` | `الشحن بكام` | `العنوان فين` | `انستاباي` | `فاليو` | `الدفع عند الاستلام` | `bkam` | `s3r`
- **Saudi & Gulf Khaleeji Price & Stock Tokens**:
  `بكم` | `كم السعر` | `كم سعره` | `بكم هذا` | `متوفر` | `فيه شحن` | `توصيل للرياض` | `توصيل لجدة` | `عندكم تابي` | `تمارا` | `موقعكم وين` | `كيف اطلب` | `الرابط`

#### 2. The "Transparent Public Price + Private Cart Link" Dual-Reply Rule
When a user comments `"بكام؟"` or `"بكم؟"` on a product post/ad:
- [ ] **Action 1 — Public Comment Reply (Transparent Price & Trust)**:
  State the exact price (`SAR`/`AED`/`EGP`), key spec, and payment options publicly in the comment reply so every other scrolling viewer sees the price immediately!
  - *Example (Egypt)*: `"أهلاً بحضرتك! سعر الماكينة 2,450 ج.م مع ضمان سنتين، ومتاح الدفع عند الاستلام أو إنستاباي أو تقسيط فاليو. بعتنالك رابط الطلب المباشر في الرسائل الآن 📩"`
  - *Example (KSA)*: `"حياك الله! سعرها 349 ر.س شامل الضريبة مع شحن سريع، ومتاح تقسيطها على 4 دفعات عبر تابي وتمارا. أرسلنا لك رابط الطلب المباشر على الخاص 📩"`
- [ ] **Action 2 — Instant Automated DM (Direct Checkout Link)**:
  Simultaneously send the tracked product URL (`?utm_source=ig_comment_auto&utm_campaign=...`) to their Instagram/Facebook DM.

## 3. Complete End-to-End Worked Example (`مثال تطبيقي متكامل من المدخلات حتى المراجعة البشرية والنتيجة النهائية`)

*(Illustrative scenario — original example for training, never represented as a verified client outcome)*

### Step A: Sample Brief / Input (`موجز المدخلات`)
- **Store**: Cairo Women's Footwear & Handbags Brand running Instagram & Facebook Reels ads.
- **Problem Discovered**: An AI sentiment/spam plugin was set to `'Hide repetitive 1-word comments and negative slang'`. Over 30 days, it auto-hid `1,420` comments asking `"بكام"` and `"تفاصيل"`, cutting comment-driven orders in half.

### Step B: Initial Output (`المخرج الأولي`)
- **Moderation & Automation Audit**:
  1. Whitelisted all 28 Egyptian & Gulf price/stock inquiry tokens (`بكام`, `بكم`, `سعره كام`, `تفاصيل`, `موجود`, `متوفر`).
  2. Configured ManyChat / Meta Automation to reply publicly with the transparent `EGP` price + COD/InstaPay availability AND send the direct product checkout card via DM within 10 seconds.

### Step C: Human Review & Edits (`التدقيق البشري والتعديلات`)
1. **Orthographic Variant Expansion (`AMP-002`)**: Added elongated vowel variants (`بكاام`, `بكاآام`, `تفاااصيل`) and Franco-Arabic (`bkam`, `details`) to the trigger regex `ب+ك+ا+م+`.
2. **Real Spam Isolation**: Restricted auto-hide strictly to actual spam patterns (external `http`/`wa.me` links posted by third-party accounts, crypto scams, and explicit profanity).

### Step D: Final Reviewed Example Outcome (`النتيجة النهائية المعتمدة`)
- `0` legitimate `"بكام / بكم"` buyer inquiries hidden; 100% receive an instant transparent public price reply + private checkout DM link.

## 4. What Can Go Wrong & How to Fix It (`الأخطاء الشائعة وخطة الإنقاذ`)

- **Failure Case (`المشكلة المحتملة`)**: A brand uses ManyChat to reply `'تم الرد عالخاص شيك رسايلك 🌸'` to 300 comments without stating the price publicly; frustrated shoppers reply in the comments `'ما تقولوا السعر هنا ليه الكهن ده!'`, tanking ad sentiment and CTR.
- **Correction & Fallback (`الحل الإجرائي والبديل الآمن`)**: Always state the starting or exact price inside the **public comment reply** alongside the DM trigger—transparency in comments converts silent lurkers who never comment.

## 5. Model & Platform Capability Matrix (`مصفوفة قدرات النماذج والمنصات — 2026-10-25`)

| Platform / Model | Status | Official Documentation | MENA Operational Constraint | Fallback |
| :--- | :--- | :--- | :--- | :--- |
| **Meta Business Suite / ManyChat Comment-to-Messenger & Instagram DM Automation** | `supported` | [Official Docs](https://www.aisyncso.com/en/blog/gulf-arabic-dialects-enterprise-ai-agents) (`2026-10-25`) | Meta's official Private Replies API allows 1 automated DM response within 7 days of a user's comment on an IG/FB post or ad when triggered by keyword rules. | Use regex/prefix matching on normalized Arabic text (`AMP-002`) so spelling variations trigger the reply reliably. |

## 6. How to Measure Success (`خطة القياس والضوابط`)

- **Primary Metric**: False-Positive Hidden Comment Rate (`Target: 0%` of buyer inquiries hidden) and Comment-to-DM Checkout Conversion Rate.
- **Baseline**: Prior 14-day audit of the 'Hidden Comments' tab in Meta Business Suite.
- **Observation Window**: 14 days post-deployment.
- **Interpretation Boundary**: Recovering hidden price inquiries unlocks lost demand, while product price competitiveness and checkout speed (`AMP-386`) determine final purchase rate.

## 7. Primary Sources & Evidence Boundaries (`المصادر الموثقة وحدود الأدلة`)

- [Gulf Arabic Dialects: Why Generic AI Agents Fail Khaleeji Customers](https://www.aisyncso.com/en/blog/gulf-arabic-dialects-enterprise-ai-agents) — *AISyncSo* (Published `2026-09-24`, Accessed `2026-10-25`): Shows why customer-facing AI agents trained on MSA fail to parse everyday Khaleeji phrasing, politeness formulas, and intent in Riyadh, Dubai, and Doha.
- [Your Chatbot Just Offended an Arabic Customer — Here's the Data Fix](https://aitaggers.com.au/blog/chatbot-offended-arabic-customer) — *AI Taggers* (Published `2026-10-08`, Accessed `2026-10-25`): Explains how dialectal false friends (words polite in one Arab country but rude or abrupt in Gulf/Egyptian dialect) cause AI chatbots to offend customers.
