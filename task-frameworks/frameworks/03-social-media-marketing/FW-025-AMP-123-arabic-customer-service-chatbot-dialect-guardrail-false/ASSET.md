# FW-025: Arabic Customer-Service Chatbot Dialect Guardrail & 'False-Friends' Lexicon Checklist
## قائمة فحص وضبط لهجات بوتات خدمة العملاء بالعربية (منع «الأصدقاء الكاذبين» بين اللهجات والردود الفظة)

- **Consolidated Contextual Child IDs (`MERGE_INTO_EXISTING`)**: `AMP-133`, `AMP-143`, `AMP-153`, `AMP-163`, `AMP-173`
- **Selected Artifact Type**: `CHECKLIST`
- **Intended Audience**: Social Media Manager, Community Manager, Brand Strategist, Account Director
- **Target Markets & Languages**: Egypt & GCC (`Saudi Arabia, UAE, Kuwait, Qatar, Bahrain, Oman`) — Bilingual Arabic (`Egyptian Ammiya`, `Saudi/Gulf Khaleeji`, `White MSA`) + English
- **Version**: `1.2` | **Last Reviewed**: `2026-10-25` | **Status**: `READY_FOR_REVIEW`

## 1. Plain-Language Promise & Why This Artifact Form Fits the Job

- **What You Can Make or Decide (EN)**: Prevent AI customer-service chatbots on WhatsApp, Instagram, and web chat from offending Arab shoppers through cross-dialectal 'false friends', misread Gulf polite idioms, or robotic MSA replies.
- **ما الذي يمكنك إنجازه أو حسمه بهذه الأداة (AR)**: منع بوتات خدمة العملاء بالذكاء الاصطناعي على واتساب وإنستغرام والموقع من إساءة فهم تعبيرات المجاملة الخليجية والمصرية أو استخدام مفردات تحمل معاني مسيئة في لهجة أخرى.
- **Why `CHECKLIST` Fits This User Job (EN)**: Enterprise Arabic NLP audits (AISync / AI Taggers 2026) document that LLMs trained on mixed Arabic corpora misinterpret Gulf politeness idioms (`'يعطيك العافية'`, `'ما قصرت'`, `'سم'`, `'أبشر'`) or emit cross-dialectal false friends that offend customers; a pre-deployment CHECKLIST and system-prompt lexicon lock prevent live PR incidents.
- **لماذا يناسب شكل `CHECKLIST` هذه المهمة (AR)**: توثق دراسات الذكاء الاصطناعي للمؤسسات العربية (2026) أن البوتات المدربة على نصوص مختلطة تسيء تفسير عبارات المجاملة الخليجية («ما قصرت»، «يعطيك العافية»، «عساك على القوة») أو تستخدم كلمات مقبولة في لهجة ولكنها مسيئة في لهجة أخرى؛ وتمنع قائمة الفحص هذه تلك الأخطاء قبل الإطلاق.

## 2. "Use It When" Trigger, Boundaries & Exact Inputs to Prepare

- **Use It When (EN)**: Use before deploying or updating any AI customer-support agent on WhatsApp Business, Instagram DM, Facebook Messenger, or website live chat in KSA, UAE, Kuwait, Qatar, or Egypt.
- **متى تستخدم هذه الأداة (AR)**: تُستخدم قبل إطلاق أو تحديث أي بوت خدمة عملاء بالذكاء الاصطناعي على واتساب أو إنستغرام أو ماسنجر أو دردشة الموقع في الخليج ومصر.
- **When NOT to Use It (EN)**: Do not let an AI chatbot handle angry refund disputes, medical adverse events, or legal threats without immediate human agent handoff (`AMP-128`).
- **متى لا تستخدم هذه الأداة (AR)**: لا تسمح للبوت بالتعامل الذاتي مع النزاعات المالية الحادة أو الشكاوى الطبية أو التهديدات القانونية دون تحويل فوري لموظف بشري (`AMP-128`).

### Exact Inputs to Prepare Before Starting (`المدخلات المطلوب تجهيزها`)
1. Target Customer Geography (`KSA/GCC` vs. `Egypt` vs. `Multi-Country`)
2. System Prompt & Knowledge Base of the WhatsApp / Social DM Agent
3. List of 50 real historical customer chat transcripts (including angry, sarcastic, and polite local phrasing)

### Privacy-Safe Data Handling (`ضوابط الخصوصية وحماية البيانات الشخصية PDPL`)
- **Strict PII Redaction Before Prompting**: Under Saudi PDPL (Art. 25), UAE Federal Decree-Law No. 45 of 2021, Qatar Law No. 13 of 2016, and Egypt Law No. 151 of 2020, **never paste raw customer names, unhashed mobile numbers (`+9665...` / `+201...`), email addresses, national IDs, or private WhatsApp transcripts into public/consumer LLM interfaces**. Use anonymized placeholders (`{first_name}`, `ORD_10045`) during prompt testing and restrict live customer data to zero-data-retention enterprise API endpoints or local deterministic scripts.

## 3. The Directly Usable Artifact (`الأداة التطبيقية الجاهزة للنسخ والتنفيذ`)

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

## 4. Model & Platform Capability Branches (`فروع قدرات النماذج والمنصات والبدائل الاحتياطية`)

| System / Platform | Capability Status | Official Documentation & Access Date | Operational Constraint in Egypt & GCC | Fallback When Feature/Modality Is Unavailable |
| :--- | :--- | :--- | :--- | :--- |
| **GPT-4o / Claude 3.7 Sonnet / Gemini 2.5 Flash Arabic Dialect & Idiom Understanding** | `supported` | [Official Reference](https://www.aisyncso.com/en/blog/gulf-arabic-dialects-enterprise-ai-agents) (`2026-10-25`) | Modern frontier LLMs accurately parse Gulf and Egyptian idioms when explicitly instructed via system prompt guardrails, whereas legacy keyword/MSA-only classifiers fail on negation-based praise ('ما قصرت') and sarcasm. | Route any message with sentiment confidence `< 0.80` or mixed positive/delay tokens directly to a human queue. |

## 5. Consolidated Regional & Vertical Adaptation Matrix (`دمج الأنماط السياقية الفرعية بدون حشو`)

Per Agent 2 v1.2's anti-padding rule, the following **5 cross-verified contextual synthesis patterns** and **1 screened duplicate variants** share this core mechanism and are consolidated directly into this source-of-truth framework:

| Child Pattern ID | Disposition | Regional / Sector Operating Context | Specific Adaptation & Guardrail Integrated in This Asset | Evidence Tier |
| :--- | :--- | :--- | :--- | :--- |
| **`AMP-133`** | `MERGE_INTO_EXISTING` | Egyptian E-Commerce & Social Commerce (Shopify / WooCommerce / Cairo & Alexandria) | Dialect-routed intent classifiers with human escalation triggers and approved regional greeting lexicons.; Specifically impacts Egyptian brands operating in EGP where merchant-specific payment mix from recent order records, Mobile Wallets (Vodafone Cash), InstaPay, and Fawry dominate. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-143`** | `MERGE_INTO_EXISTING` | UAE & Multi-Market GCC Enterprise / Retail (Dubai, Abu Dhabi, Doha, Kuwait) | Dialect-routed intent classifiers with human escalation triggers and approved regional greeting lexicons.; Specifically impacts bilingual Arabic/English campaigns in high-CPM, expat-dense Gulf markets under UAE PDPL / TDRA and Qatari regulations. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-153`** | `MERGE_INTO_EXISTING` | High-Trust & Regulated Verticals (Healthcare/SFDA/EDA, Fintech/SAMA/FRA, Real Estate) | Dialect-routed intent classifiers with human escalation triggers and approved regional greeting lexicons.; Specifically impacts regulated claims requiring SFDA, EDA, MOH, SAMA, FRA, or RERA compliance pre-clearance and strict hallucination guardrails. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-163`** | `MERGE_INTO_EXISTING` | Seasonal Peak Operations (Ramadan, Eid, White/Yellow Friday, Saudi Founding/National Day) | Dialect-routed intent classifiers with human escalation triggers and approved regional greeting lexicons.; Specifically impacts high-velocity seasonal surges where CPMs jump 40-70%, prices change rapidly, and Hijri calendar cultural sensitivity is paramount. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-173`** | `MERGE_INTO_EXISTING` | Multi-Client Agency & MarTech API Automation Pipelines (LLM APIs, Webhooks, GA4, CAPI) | Dialect-routed intent classifiers with human escalation triggers and approved regional greeting lexicons.; Specifically impacts automated multi-SKU or multi-client LLM/API pipelines where schema validation, token cost, and attribution governance are required. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-513`** | `REJECT_DUPLICATE` | Screened UI/Format Synonym (`Merged Variant: Minor UI/Format Synonym of AMP-133 (Social Media Marketing)`) | Consolidated into parent workflow without duplicate file inflation. | `SCREENED_DUPLICATE_VARIANT` |

### Context-Specific Execution Knobs Across the 5 MENA Operating Environments
1. **Saudi D2C E-Commerce (`Salla / Zid / Riyadh & Jeddah Retail`)**: Enforce `SAR` tax-inclusive pricing (`15% ZATCA VAT`), native `Mada / Apple Pay / Tabby / Tamara` visibility (`AMP-387`), `GAMR Mawthooq` creator verification (`AMP-281`), and White Saudi Khaleeji orthography (`AMP-002`, `AMP-177`).
2. **Egyptian E-Commerce & Social Commerce (`Shopify / WooCommerce / Cairo & Alexandria`)**: Use each merchant’s own order and payment data to assess Cash on Delivery (`COD`), mobile wallets, InstaPay, Fawry, `valU`, address fields, and pre-dispatch WhatsApp confirmation. Verify current provider terms and local requirements before implementation.
3. **UAE & Multi-Market GCC Enterprise / Retail (`Dubai, Abu Dhabi, Doha, Kuwait`)**: Separate high-CPM UAE/Qatar budgets from lower-CPM markets (`AMP-061`), enforce UAE `TDRA` `9 PM – 7 AM` SMS curfew + `AD-` prefix (`AMP-442`), UAE Media Council permits (`AMP-282`), and bilingual Arabic/English canonical & currency parity (`current applicable UAE VAT`, `current applicable Qatar/Kuwait tax rules`, 3-decimal `KWD` `AMP-239`).
4. **High-Trust & Regulated Verticals (`Healthcare SFDA/MOH/EDA, FinTech SAMA/FRA, Real Estate REGA/RERA`)**: Strip all therapeutic/cure verbs (`AMP-176`, `AMP-286`), display mandatory `MOH/SFDA/DHA/EDA/Fal/Trakheesi` permit numbers (`AMP-070`), and route budgets to high-credibility channels (`AMP-290`, `AMP-339`).
5. **Seasonal Peak Operations (`Ramadan, Eid, White/Yellow Friday, Saudi Founding/National Day`)**: Lock Hijri-Gregorian overlaps (`Feb 2027 Ramadan x Saudi Founding Day x Kuwait National Day` `AMP-125`), pre-schedule GMC `sale_price_effective_date` 48h ahead (`AMP-063`), verify 30-day baseline discount permits (`AMP-064`), and disable Meta Advantage+ auto-music (`AMP-065`).

## 6. Worked Example Summary & Failure Recovery (`ملخص المثال التطبيقي وخطة الإنقاذ`)

*(Full step-by-step worked example with annotated human edits is also provided in `EXAMPLE.md`)*

- **Sample Input Brief**: - **Deployment**: WhatsApp Customer Support Bot for a Riyadh & Cairo E-Commerce Electronics Store.
- **Failed Transcript Before Fix**:
  - Saudi Customer (`+96650...`): `"وصلت الطلبية اليوم، صراحة ما قصرتوا والتغليف بطل"`
  - Uncalibrated Bot: `"نعتذر بشدة عن أي تقصير في خدمتكم! يرجى تزويدنا برقم الطلب لرفع شكوى عاجلة لقسم الجودة."` *(Misread `"ما قصرتوا"` as `"تقصير"` and `"بطل"` as `"باطل/معطل"`!)*
- **Human Review & Key Edits Applied**: 1. **Added `"بطل"` & `"فنان"` to Positive Gulf Slang Lexicon**: Ensured the sentiment classifier recognizes Saudi colloquial praise (`"التغليف بطل"`, `"الشغل فنان"`, `"خرافي"`) as 5-star positive sentiment rather than literal "hero / artist / mythical".
2. **Tested 50 Adversarial Transcripts**: Verified `50/50` pass rate across Saudi, Emirati, and Egyptian test messages.
- **Final Usable Output**: - Deployed dialect-aware WhatsApp/DM system prompt with country-code routing (`+966/+971` vs `+20`) and zero false-complaint misfires on Gulf idioms.
- **What Can Go Wrong**: A customer in Cairo writes sarcastically `'يا سلام على السرعة، الأوردر بقاله أسبوعين مجاش!'` ('Oh what amazing speed, the order hasn't arrived in two weeks!'); a naive sentiment router sees `'يا سلام'` and replies `'شكراً لإعجابك بسرعة التوصيل! ❤️'`.
- **Correction & Fallback**: Add the **Contradiction & Temporal Delay Rule**: whenever a message combines praise words (`يا سلام`, `برافو`, `ما شاء الله`) with delay/failure tokens (`أسبوعين`, `مجاش`, `ما وصل`, `متأخر`, `فين الطلب`), classify strictly as `HIGH_PRIORITY_DELIVERY_COMPLAINT` and route to a human agent.

## 7. Measurement Plan & Hypothesis Framing (`خطة القياس والضوابط الإحصائية`)

- **Primary Metric to Track**: Chatbot False-Sentiment Rate on weekly 100-conversation human QA sample (`Target: < 2%`) and CSAT score.
- **Baseline Definition**: Pre-guardrail audit of misclassified customer chats.
- **Observation Window**: 14 days post-deployment. *(Must span full 7/14-day weekly cycles and account for 25th–30th monthly salary windows per `AMP-391`)*.
- **What Cannot Be Concluded (Boundary)**: Dialect guardrails prevent embarrassing linguistic misfires, but order-status API integration is required to resolve actual shipping questions.
