# End-to-End Worked Example & Failure Recovery — `FW-030` (`AMP-128`)

- **Framework**: MENA Social Crisis-Response & Anti-Hallucination Escalation Playbook (X, Facebook & TikTok)
- **العنوان بالعربية**: دليل التشغيل للرد على الأزمات والشكاوى العلنية على إكس وفيسبوك وتيك توك (منع اعتراف الذكاء الاصطناعي بالمسؤولية أو اختلاق التعويضات)
- **Selected Artifact Type**: `PLAYBOOK`
- **Disclaimer**: *All scenarios, brand names, SKU codes, and metrics below are original, realistic illustrative examples for MENA practitioner training and are never represented as verified client outcomes.*

## 1. Realistic Sample Brief / Input (`المدخلات وموجز الحالة العملية`)

- **Platform**: X (Twitter) in Saudi Arabia.
- **Public Tweet by Customer**: `"طلبت من متجركم قبل 4 أيام للرياض وللحين ما وصلت الشحنة ولا أحد يرد! أسوأ تجربة، تواصلت معكم وما في فايدة!"`
- **Unsafe Raw AI Reply (Before Playbook)**: `"نعتذر بشدة عن فشل نظام الشحن لدينا وضياع شحنتك! سنقوم فوراً بإرجاع كامل المبلغ لحسابك مع قسيمة تعويض بقيمة 200 ريال هدية منا!"` *(Hallucinated a lost shipment, admitted systemic failure, and invented an unauthorized 200 SAR gift voucher!)*

## 2. Initial Generated / Completed Output (`المخرج الأولي عند تطبيق الأداة`)

- **Playbook-Compliant Draft (Reviewed & Sent by Human Agent in 4 Minutes)**:
  `"أهلاً بك أخي الكريم، حقك علينا ويهمنا جداً وصول طلبك بأسرع وقت. تفضل بتزويدنا برقم الطلب عبر الرسائل الخاصة الآن، وسيتابع فريق العمليات شحنتك فوراً ويتواصل معك هاتفياً خلال دقائق. أبشر بالخير."`

## 3. Human Review & Localization/Technical Edits (`المراجعة البشرية والتعديلات الرقابية والتقنية`)

1. **Verified Operations Action First**: Human agent checked the order in the dashboard, saw it was out for delivery with SMSA in North Riyadh, called the customer within 6 minutes, and confirmed delivery that evening.
2. **Customer Follow-Up Tweet**: Customer voluntarily replied under the thread: `"تواصلوا معي وما قصروا، وصلت الطلبية نفس اليوم شكراً لكم"`.

## 4. Final Reviewed Example Outcome (`النتيجة النهائية الجاهزة للتنفيذ`)

- Public thread de-escalated in `<10` minutes with zero unauthorized financial promises, zero PDPL privacy leaks, and documented public resolution.

## 5. What Can Go Wrong & Specific Correction / Fallback (`حالة الفشل المحتملة وخطة الإنقاذ والبديل`)

- **Common Failure Mode (`ما الذي قد يسير بشكل خاطئ؟`)**:
  An automated comment responder replies to a customer complaining about an allergic skin reaction with `'منتجاتنا آمنة 100% ومستحيل تسبب حساسية، المشكلة من طريقة استخدامك!'`, igniting a viral backlash and SFDA scrutiny.
- **Specific Correction & Non-AI / Platform Fallback (`الإصلاح المحدد والبديل الآمن`)**:
  Hard-code a keyword kill-switch on all social auto-responders: any comment containing health/safety/regulatory tokens (`حساسية، تسمم، مستشفى، وزارة التجارة، بلاغ، نصب، احتيال، الغذاء والدواء، حماية المستهلك`) is routed silently to the Human Escalation Slack/WhatsApp channel with **zero automated public reply**.
