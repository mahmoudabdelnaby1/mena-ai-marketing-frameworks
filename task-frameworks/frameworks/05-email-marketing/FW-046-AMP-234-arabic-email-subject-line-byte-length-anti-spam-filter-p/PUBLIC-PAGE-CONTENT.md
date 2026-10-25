# Arabic Email Subject-Line Byte-Length & Anti-Spam Filter Prompt Template
## <span dir="rtl">قالب صياغة عناوين رسائل البريد الإلكتروني العربية (ضبط طول البايتات `UTF-8` وتجنب فلاتر السبام والوعود المضللة)</span>

> **Asset ID**: `FW-046` (`AMP-234`) | **Artifact Type**: `PROMPT_TEMPLATE` | **Channel**: Email Marketing | **Markets**: Egypt & GCC (`KSA, UAE, Kuwait, Qatar, Bahrain, Oman`) | **Version**: `1.2` (`Reviewed 2026-10-25`)

**What You Can Do With This (`ماذا يمكنك أن تنجز بهذه الأداة؟`)**:
- **EN**: Write high-open-rate Arabic email subject lines and preheaders (`<= 38` Arabic chars) that never clip on iOS/Android mobile inboxes or trigger Gmail/Outlook spam filters.
- **AR**: <span dir="rtl">كتابة عناوين رسائل بريد إلكتروني (`Subject Lines`) ونصوص معاينة (`Preheaders`) عربية موجزة (`38 حرفاً كحد أقصى`) لا تنقطع في شاشات الجوال ولا تستثير فلاتر البريد المزعج (`Spam`).</span>

## 1. Use It When & Required Inputs (`متى تستخدمها وما المدخلات المطلوبة؟`)

- **Use It When (EN)**: Use when generating Arabic or bilingual email subject lines (`Subject`) and preview texts (`Preheader`) for newsletters, cart recovery, or promotional campaigns.
- **متى تستخدمها (AR)**: <span dir="rtl">تُستخدم عند صياغة عناوين الرسائل البريدية (`Subject Line`) ونص المعاينة (`Preheader`) للحملات والنشرات البريدية وسلاسل السلات المتروكة.</span>
- **When NOT to Use It (EN)**: Do not put more than 1 emoji in an Arabic subject line, never use `RE:` / `رد:` or `FWD:` on a marketing email to fake a personal reply, and never exceed 42 Arabic characters.
- **متى لا تستخدمها (AR)**: <span dir="rtl">لا تضع أكثر من رمز تعبيري واحد (`Emoji`) في العنوان، ولا تضف بادئة `رد:` أو `RE:` للإيهام بأنها مراسلة شخصية، ولا تتجاوز 42 حرفاً عربياً.</span>

### Exact Inputs to Prepare (`المدخلات المطلوب تجهيزها قبل البدء`)
- Core Email Offer / Topic
- Target Dialect/Register (`Saudi White Khaleeji`, `Egyptian Polite Ammiya`, or `Modern White MSA`)
- Mandatory Prefix Requirement (e.g., if sending in UAE under TDRA promotional rules where applicable)

## 2. The Working `PROMPT_TEMPLATE` (`الأداة الكاملة الجاهزة للنسخ والتطبيق الفوري`)

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

## 3. Complete End-to-End Worked Example (`مثال تطبيقي متكامل من المدخلات حتى المراجعة البشرية والنتيجة النهائية`)

*(Illustrative scenario — original example for training, never represented as a verified client outcome)*

### Step A: Sample Brief / Input (`موجز المدخلات`)
- **Campaign**: Restock notification for a sold-out Ethiopian Specialty Coffee (`250g`, `79 SAR`) in Saudi Arabia.
- **Bad AI Draft (`74` chars + Spam Triggers)**: `"🔥🚨 عاجل جداً!! قهوتك الإثيوبية المفضلة عادت للمخزون الآن بخصم مجاني وشحن مجاني 100% لا تفوت الفرصة!!!"`

### Step B: Initial Output (`المخرج الأولي`)
| Angle | `subject_ar` (<= 38 chars) | Char Count | UTF-8 Bytes | `preheader_ar` (45-70 chars) | Spam Risk Check |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **1. Direct Restock** | `رجعت محمصة إثيوبيا قوجي من جديد ☕` | `33` | `61 B` | `الحمصة الجديدة وصلت اليوم بكمية محدودة — متاح التقسيط عبر تابي` | `PASS (0 spam tokens)` |
| **2. VIP Personal** | `حجزنا لك كيسك من محصول إثيوبيا` | `30` | `55 B` | `محصول قوجي المجفف متوفر الحين بـ 79 ر.س مع توصيل سريع للرياض وجدة` | `PASS (0 spam tokens)` |
| **3. Sensory / Curiosity** | `حمصة هذا الأسبوع وصلت للتو` | `26` | `48 B` | `إيحاءات التوت والشوكولاتة في محصول قوجي الجديد — اطلبه قبل النفاد` | `PASS (0 spam tokens)` |

### Step C: Human Review & Edits (`التدقيق البشري والتعديلات`)
1. **BiDi Emoji Placement Check**: Confirmed the coffee emoji `☕` is placed at the **end** of the Arabic string (left side in RTL) rather than the beginning, because leading emojis next to English merge tags can flip alignment on older Android clients.
2. **Verified Mobile Preview**: Confirmed all 3 subject lines render completely without `...` truncation on a 375px iPhone screen.

### Step D: Final Reviewed Example Outcome (`النتيجة النهائية المعتمدة`)
- Selected Subject Line #2 (`"حجزنا لك كيسك من محصول إثيوبيا"` — `30` chars, `55` UTF-8 bytes) paired with the 65-char preheader.

## 4. What Can Go Wrong & How to Fix It (`الأخطاء الشائعة وخطة الإنقاذ`)

- **Failure Case (`المشكلة المحتملة`)**: A marketer puts a Latin brand name or number at the very beginning of an Arabic subject line (`'50% خصم على عطور الشتاء'`); on Gmail iOS, the subject line aligns left-to-right and pushes the Arabic words off-screen.
- **Correction & Fallback (`الحل الإجرائي والبديل الآمن`)**: Always **start an Arabic subject line with an Arabic word** (e.g., `'خصم 50% على عطور الشتاء'` instead of `'50% خصم...'`) so the inbox client detects the first strong directional character as Right-to-Left (`RTL`)!

## 5. Model & Platform Capability Matrix (`مصفوفة قدرات النماذج والمنصات — 2026-10-25`)

| Platform / Model | Status | Official Documentation | MENA Operational Constraint | Fallback |
| :--- | :--- | :--- | :--- | :--- |
| **Gmail, Apple Mail & Outlook Mobile Subject Line Character & BiDi First-Strong-Character Detection** | `supported` | [Official Docs](https://mailtester.com/blog/right-to-left-email-rendering-problems-gmail-outlook/) (`2026-10-25`) | Unicode BiDi standard (UAX #9) sets paragraph direction from the first strong directional character; starting an Arabic subject line with an Arabic word ensures proper RTL inbox alignment. | If a subject line must begin with a Latin brand name, prepend the Unicode Right-to-Left Mark (`‏`) as the first character. |

## 6. How to Measure Success (`خطة القياس والضوابط`)

- **Primary Metric**: Inbox Placement Rate (`Primary/Inbox` vs. `Spam/Promotions`), Open Rate, and Click-to-Open Rate (`CTOR`).
- **Baseline**: Prior 30-day campaign average with long/unconstrained subject lines.
- **Observation Window**: Measured 48 hours after campaign send.
- **Interpretation Boundary**: Short, spam-free subject lines prevent mobile clipping and spam-folder routing, while sender domain reputation (`AMP-236`) and list hygiene (`AMP-232`) co-determine inbox placement.

## 7. Primary Sources & Evidence Boundaries (`المصادر الموثقة وحدود الأدلة`)

- [Translating Dialects between ChatGPT and DeepSeek](https://f1000research.com/articles/14-694) — *F1000Research* (Published `2025-07-16`, Accessed `2026-10-25`): Demonstrates measurable accuracy drops and cultural/idiomatic errors when LLMs translate between English and regional Arabic dialects.
- [Solving Right-to-Left Email Rendering Problems in Gmail and Outlook](https://mailtester.com/blog/right-to-left-email-rendering-problems-gmail-outlook/) — *MailTester* (Published `2026-09-24`, Accessed `2026-10-25`): Documents how missing dir='rtl' attributes, inline CSS overrides, and mixed bidirectional strings cause broken Arabic email rendering in Outlook and Gmail across Klaviyo, HubSpot, and Mailchimp.
