# End-to-End Worked Example & Failure Recovery — `FW-025` (`AMP-123`)

- **Framework**: Arabic Customer-Service Chatbot Dialect Guardrail & 'False-Friends' Lexicon Checklist
- **العنوان بالعربية**: قائمة فحص وضبط لهجات بوتات خدمة العملاء بالعربية (منع «الأصدقاء الكاذبين» بين اللهجات والردود الفظة)
- **Selected Artifact Type**: `CHECKLIST`
- **Disclaimer**: *All scenarios, brand names, SKU codes, and metrics below are original, realistic illustrative examples for MENA practitioner training and are never represented as verified client outcomes.*

## 1. Realistic Sample Brief / Input (`المدخلات وموجز الحالة العملية`)

- **Deployment**: WhatsApp Customer Support Bot for a Riyadh & Cairo E-Commerce Electronics Store.
- **Failed Transcript Before Fix**:
  - Saudi Customer (`+96650...`): `"وصلت الطلبية اليوم، صراحة ما قصرتوا والتغليف بطل"`
  - Uncalibrated Bot: `"نعتذر بشدة عن أي تقصير في خدمتكم! يرجى تزويدنا برقم الطلب لرفع شكوى عاجلة لقسم الجودة."` *(Misread `"ما قصرتوا"` as `"تقصير"` and `"بطل"` as `"باطل/معطل"`!)*

## 2. Initial Generated / Completed Output (`المخرج الأولي عند تطبيق الأداة`)

- **Corrected Bot Response with `<arabic_cultural_and_dialect_guardrails>`**:
  - Intent Classified: `POSITIVE_FEEDBACK_PRAISE` (`Confidence: 0.99`)
  - Bot Reply: `"حياك الله! الله يعافيك ويسعدك، شهادتك نعتز فيها ونتمنى لك تجربة ممتازة مع المنتج. إذا احتجت أي مساعدة مستقبلاً حنا بالخدمة دايماً 🌟"`

## 3. Human Review & Localization/Technical Edits (`المراجعة البشرية والتعديلات الرقابية والتقنية`)

1. **Added `"بطل"` & `"فنان"` to Positive Gulf Slang Lexicon**: Ensured the sentiment classifier recognizes Saudi colloquial praise (`"التغليف بطل"`, `"الشغل فنان"`, `"خرافي"`) as 5-star positive sentiment rather than literal "hero / artist / mythical".
2. **Tested 50 Adversarial Transcripts**: Verified `50/50` pass rate across Saudi, Emirati, and Egyptian test messages.

## 4. Final Reviewed Example Outcome (`النتيجة النهائية الجاهزة للتنفيذ`)

- Deployed dialect-aware WhatsApp/DM system prompt with country-code routing (`+966/+971` vs `+20`) and zero false-complaint misfires on Gulf idioms.

## 5. What Can Go Wrong & Specific Correction / Fallback (`حالة الفشل المحتملة وخطة الإنقاذ والبديل`)

- **Common Failure Mode (`ما الذي قد يسير بشكل خاطئ؟`)**:
  A customer in Cairo writes sarcastically `'يا سلام على السرعة، الأوردر بقاله أسبوعين مجاش!'` ('Oh what amazing speed, the order hasn't arrived in two weeks!'); a naive sentiment router sees `'يا سلام'` and replies `'شكراً لإعجابك بسرعة التوصيل! ❤️'`.
- **Specific Correction & Non-AI / Platform Fallback (`الإصلاح المحدد والبديل الآمن`)**:
  Add the **Contradiction & Temporal Delay Rule**: whenever a message combines praise words (`يا سلام`, `برافو`, `ما شاء الله`) with delay/failure tokens (`أسبوعين`, `مجاش`, `ما وصل`, `متأخر`, `فين الطلب`), classify strictly as `HIGH_PRIORITY_DELIVERY_COMPLAINT` and route to a human agent.
