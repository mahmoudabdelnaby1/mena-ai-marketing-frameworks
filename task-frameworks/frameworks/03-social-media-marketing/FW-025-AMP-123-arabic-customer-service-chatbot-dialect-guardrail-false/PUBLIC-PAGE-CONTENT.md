# Arabic Customer-Service Chatbot Dialect Guardrail & 'False-Friends' Lexicon Checklist
## <span dir="rtl">قائمة فحص وضبط لهجات بوتات خدمة العملاء بالعربية (منع «الأصدقاء الكاذبين» بين اللهجات والردود الفظة)</span>

> **Asset ID**: `FW-025` (`AMP-123`) | **Artifact Type**: `CHECKLIST` | **Channel**: Social Media Marketing | **Markets**: Egypt & GCC (`KSA, UAE, Kuwait, Qatar, Bahrain, Oman`) | **Version**: `1.2` (`Reviewed 2026-10-25`)

**What You Can Do With This (`ماذا يمكنك أن تنجز بهذه الأداة؟`)**:
- **EN**: Prevent AI customer-service chatbots on WhatsApp, Instagram, and web chat from offending Arab shoppers through cross-dialectal 'false friends', misread Gulf polite idioms, or robotic MSA replies.
- **AR**: <span dir="rtl">منع بوتات خدمة العملاء بالذكاء الاصطناعي على واتساب وإنستغرام والموقع من إساءة فهم تعبيرات المجاملة الخليجية والمصرية أو استخدام مفردات تحمل معاني مسيئة في لهجة أخرى.</span>

## 1. Use It When & Required Inputs (`متى تستخدمها وما المدخلات المطلوبة؟`)

- **Use It When (EN)**: Use before deploying or updating any AI customer-support agent on WhatsApp Business, Instagram DM, Facebook Messenger, or website live chat in KSA, UAE, Kuwait, Qatar, or Egypt.
- **متى تستخدمها (AR)**: <span dir="rtl">تُستخدم قبل إطلاق أو تحديث أي بوت خدمة عملاء بالذكاء الاصطناعي على واتساب أو إنستغرام أو ماسنجر أو دردشة الموقع في الخليج ومصر.</span>
- **When NOT to Use It (EN)**: Do not let an AI chatbot handle angry refund disputes, medical adverse events, or legal threats without immediate human agent handoff (`AMP-128`).
- **متى لا تستخدمها (AR)**: <span dir="rtl">لا تسمح للبوت بالتعامل الذاتي مع النزاعات المالية الحادة أو الشكاوى الطبية أو التهديدات القانونية دون تحويل فوري لموظف بشري (`AMP-128`).</span>

### Exact Inputs to Prepare (`المدخلات المطلوب تجهيزها قبل البدء`)
- Target Customer Geography (`KSA/GCC` vs. `Egypt` vs. `Multi-Country`)
- System Prompt & Knowledge Base of the WhatsApp / Social DM Agent
- List of 50 real historical customer chat transcripts (including angry, sarcastic, and polite local phrasing)

## 2. The Working `CHECKLIST` (`الأداة الكاملة الجاهزة للنسخ والتطبيق الفوري`)

### Arabic Chatbot Dialect & Politeness Safety Checklist

#### 1. High-Risk Cross-Dialectal "False Friends" & Idiom Misinterpretations to Lock
| Customer Input / Word | Actual Customer Meaning in Context | Common Uncalibrated LLM Failure | Mandatory System Prompt Rule |
| :--- | :--- | :--- | :--- |
| **`"ما قصرت"` / `"ما قصرتوا"`** (KSA/GCC) | **"Thank you very much / You did great!"** (Idiomatic praise using negation). | Literal parser reads `"ما"` (not) + `"قصرت"` (fell short/delayed) as a complaint about slow service and apologizes! | Classify `"ما قصرت / بيض الله وجهك / يعطيك العافية / لا هنت"` as **Positive Gratitude**, replying with `"الله يعافيك ويسعدك، بالخدمة دايماً!"`. |
| **`"بكام ده؟"` / `"بكم هذا؟"` / `"السعر؟"`** | **"How much is this?"** (High-intent buyer inquiry). | Generic bot replies `"يرجى توضيح سؤالك بالكامل"` instead of reading the replied-to post/product ID. | Always bind comment/DM context (`post_id` / `product_sku`) and return the exact price + link + payment options immediately. |
| **`"يا غالي"` / `"طول بالك"` / `"حضرتك"`** | Natural regional politeness markers (`Egypt` vs `GCC`). | Bot mirrors overly intimate street slang (`"يا باشا"`, `"حبيب قلبي"`, `"عيوني لك"`) to female or executive customers, causing cultural offense. | Enforce **"Warm White Professional Arabic" (عربية بيضاء مهذبة)**: use respectful gender-safe openings (`"أهلاً بك"`, `"حياك الله"`, `"أبشر"`, `"تحت أمر حضرتك"` in Egypt) without street slang. |
| **Cross-Dialectal False Friends** (`"عافية"`, `"تعبان"`, `"خربان"`, `"دغري"`, `"جدع"`) | Words whose register or connotation shifts across Gulf, Egyptian, Levantine, and Maghrebi Arabic. | Bot mixes Levantine/Maghrebi slang into a Saudi bank or clinic chat. | Lock the bot's output vocabulary strictly to **Modern White Saudi/Gulf** (for `+966/+971/+965/+974` phone prefixes) or **Polite Cairene/White Arabic** (for `+20` prefixes). |

#### 2. Copy-Ready System Prompt Guardrail Block for Arabic Support Agents
```xml
<arabic_cultural_and_dialect_guardrails>
1. TONE & REGISTER: Always reply in "Polite White Regional Arabic" (عربية بيضاء مهذبة):
   - If customer phone/locale is KSA/GCC (+966, +971, +974, +965, +973, +968) or uses Gulf dialect: use respectful Gulf hospitality markers ("حياك الله"، "أبشر"، "يسعدنا خدمتك") without heavy tribal slang or Levantine/Egyptian fillers ("هلق"، "كرمال"، "بص حضرتك").
   - If customer phone/locale is Egypt (+20) or uses Egyptian Ammiya: use polite professional Egyptian/White Arabic ("أهلاً بحضرتك"، "تحت أمرك"، "يسعدنا مساعدتك").
2. GENDER SAFETY: When customer grammatical gender is unknown, use gender-neutral plural/polite phrasing ("أهلاً بحضرتك" / "حياكم الله" / "يسعدنا خدمتك") rather than assuming masculine singular.
3. GULF IDIOM RECOGNITION: Recognize "ما قصرت"، "بيض الله وجهك"، "لا هنت"، "عساك على القوة"، "كفيت ووفيت" as expressions of THANKS, never complaints.
4. HUMAN HANDOFF TRIGGER: Immediately escalate to a human agent (status: HANDOFF_HUMAN) if the user uses frustration markers ("حسبي الله"، "نصب"، "بشتكي لوزارة التجارة"، "حماية المستهلك"، "تأخر الطلب جداً")—never argue or invent unauthorized compensation.
</arabic_cultural_and_dialect_guardrails>
```

## 3. Complete End-to-End Worked Example (`مثال تطبيقي متكامل من المدخلات حتى المراجعة البشرية والنتيجة النهائية`)

*(Illustrative scenario — original example for training, never represented as a verified client outcome)*

### Step A: Sample Brief / Input (`موجز المدخلات`)
- **Deployment**: WhatsApp Customer Support Bot for a Riyadh & Cairo E-Commerce Electronics Store.
- **Failed Transcript Before Fix**:
  - Saudi Customer (`+96650...`): `"وصلت الطلبية اليوم، صراحة ما قصرتوا والتغليف بطل"`
  - Uncalibrated Bot: `"نعتذر بشدة عن أي تقصير في خدمتكم! يرجى تزويدنا برقم الطلب لرفع شكوى عاجلة لقسم الجودة."` *(Misread `"ما قصرتوا"` as `"تقصير"` and `"بطل"` as `"باطل/معطل"`!)*

### Step B: Initial Output (`المخرج الأولي`)
- **Corrected Bot Response with `<arabic_cultural_and_dialect_guardrails>`**:
  - Intent Classified: `POSITIVE_FEEDBACK_PRAISE` (`Confidence: 0.99`)
  - Bot Reply: `"حياك الله! الله يعافيك ويسعدك، شهادتك نعتز فيها ونتمنى لك تجربة ممتازة مع المنتج. إذا احتجت أي مساعدة مستقبلاً حنا بالخدمة دايماً 🌟"`

### Step C: Human Review & Edits (`التدقيق البشري والتعديلات`)
1. **Added `"بطل"` & `"فنان"` to Positive Gulf Slang Lexicon**: Ensured the sentiment classifier recognizes Saudi colloquial praise (`"التغليف بطل"`, `"الشغل فنان"`, `"خرافي"`) as 5-star positive sentiment rather than literal "hero / artist / mythical".
2. **Tested 50 Adversarial Transcripts**: Verified `50/50` pass rate across Saudi, Emirati, and Egyptian test messages.

### Step D: Final Reviewed Example Outcome (`النتيجة النهائية المعتمدة`)
- Deployed dialect-aware WhatsApp/DM system prompt with country-code routing (`+966/+971` vs `+20`) and zero false-complaint misfires on Gulf idioms.

## 4. What Can Go Wrong & How to Fix It (`الأخطاء الشائعة وخطة الإنقاذ`)

- **Failure Case (`المشكلة المحتملة`)**: A customer in Cairo writes sarcastically `'يا سلام على السرعة، الأوردر بقاله أسبوعين مجاش!'` ('Oh what amazing speed, the order hasn't arrived in two weeks!'); a naive sentiment router sees `'يا سلام'` and replies `'شكراً لإعجابك بسرعة التوصيل! ❤️'`.
- **Correction & Fallback (`الحل الإجرائي والبديل الآمن`)**: Add the **Contradiction & Temporal Delay Rule**: whenever a message combines praise words (`يا سلام`, `برافو`, `ما شاء الله`) with delay/failure tokens (`أسبوعين`, `مجاش`, `ما وصل`, `متأخر`, `فين الطلب`), classify strictly as `HIGH_PRIORITY_DELIVERY_COMPLAINT` and route to a human agent.

## 5. Model & Platform Capability Matrix (`مصفوفة قدرات النماذج والمنصات — 2026-10-25`)

| Platform / Model | Status | Official Documentation | MENA Operational Constraint | Fallback |
| :--- | :--- | :--- | :--- | :--- |
| **GPT-4o / Claude 3.7 Sonnet / Gemini 2.5 Flash Arabic Dialect & Idiom Understanding** | `supported` | [Official Docs](https://www.aisyncso.com/en/blog/gulf-arabic-dialects-enterprise-ai-agents) (`2026-10-25`) | Modern frontier LLMs accurately parse Gulf and Egyptian idioms when explicitly instructed via system prompt guardrails, whereas legacy keyword/MSA-only classifiers fail on negation-based praise ('ما قصرت') and sarcasm. | Route any message with sentiment confidence `< 0.80` or mixed positive/delay tokens directly to a human queue. |

## 6. How to Measure Success (`خطة القياس والضوابط`)

- **Primary Metric**: Chatbot False-Sentiment Rate on weekly 100-conversation human QA sample (`Target: < 2%`) and CSAT score.
- **Baseline**: Pre-guardrail audit of misclassified customer chats.
- **Observation Window**: 14 days post-deployment.
- **Interpretation Boundary**: Dialect guardrails prevent embarrassing linguistic misfires, but order-status API integration is required to resolve actual shipping questions.

## 7. Primary Sources & Evidence Boundaries (`المصادر الموثقة وحدود الأدلة`)

- [Gulf Arabic Dialects: Why Generic AI Agents Fail Khaleeji Customers](https://www.aisyncso.com/en/blog/gulf-arabic-dialects-enterprise-ai-agents) — *AISyncSo* (Published `2026-09-24`, Accessed `2026-10-25`): Shows why customer-facing AI agents trained on MSA fail to parse everyday Khaleeji phrasing, politeness formulas, and intent in Riyadh, Dubai, and Doha.
- [Your Chatbot Just Offended an Arabic Customer — Here's the Data Fix](https://aitaggers.com.au/blog/chatbot-offended-arabic-customer) — *AI Taggers* (Published `2026-10-08`, Accessed `2026-10-25`): Explains how dialectal false friends (words polite in one Arab country but rude or abrupt in Gulf/Egyptian dialect) cause AI chatbots to offend customers.
