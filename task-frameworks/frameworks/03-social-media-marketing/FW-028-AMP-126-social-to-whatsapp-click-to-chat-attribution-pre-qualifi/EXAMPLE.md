# End-to-End Worked Example & Failure Recovery — `FW-028` (`AMP-126`)

- **Framework**: Social-to-WhatsApp Click-to-Chat Attribution & Pre-Qualification Triage Workflow
- **العنوان بالعربية**: مسار عمل تتبع إحالات روابط «انقر للدردشة في واتساب» (`Click-to-WhatsApp`) وفرز العملاء قبل التحويل للمبيعات
- **Selected Artifact Type**: `OPERATING_FRAMEWORK`
- **Disclaimer**: *All scenarios, brand names, SKU codes, and metrics below are original, realistic illustrative examples for MENA practitioner training and are never represented as verified client outcomes.*

## 1. Realistic Sample Brief / Input (`المدخلات وموجز الحالة العملية`)

- **Business**: Cairo & Riyadh Custom Kitchens & Dressing Rooms Showroom (`Average Deal: 45,000 EGP / 14,000 SAR`).
- **Problem**: Instagram Reels ads drove `420` daily WhatsApp clicks. Sales reps spent 6 hours/day replying to `"بكام المتر؟"` from users outside their delivery governorates, and GA4 attributed `0` orders to Instagram because links sent from inside WhatsApp opened as `Direct`.

## 2. Initial Generated / Completed Output (`المخرج الأولي عند تطبيق الأداة`)

- **Deployed WhatsApp Triage & Attribution Flow**:
  1. Extracted `ctwa_clid` and `[كود المرجع: IGREEL-KITCH-02]`.
  2. Instant Bot Reply delivered the transparent starting price table per meter + material guide PDF, then asked:
     - **السؤال 1**: `"في أي مدينة/محافظة يقع المشروع؟"` (`[القاهرة الكبرى / الإسكندرية]` vs `[خارج نطاق التركيب]`)
     - **السؤال 2**: `"متى ترغب في رفع المقاسات؟"` (`[خلال هذا الأسبوع]` vs `[أستكشف الأسعار فقط]`)

## 3. Human Review & Localization/Technical Edits (`المراجعة البشرية والتعديلات الرقابية والتقنية`)

1. **Polite Out-of-Zone Handling**: For users selecting governorates outside the installation zone, the bot politely informs them of current coverage boundaries instead of consuming a sales engineer's phone slot.
2. **UTM Tagging on Outbound Links**: Appended `?utm_source=whatsapp_business&utm_medium=chat_concierge&utm_campaign=igreel_kitch_02` to every link sent by the bot or sales rep so GA4 never buckets WhatsApp return visits into `Direct`.

## 4. Final Reviewed Example Outcome (`النتيجة النهائية الجاهزة للتنفيذ`)

- Human sales engineers now receive `65` pre-qualified, in-zone measurement requests/day (with full `ctwa_clid` + campaign attribution) instead of `420` unfiltered raw chats.

## 5. What Can Go Wrong & Specific Correction / Fallback (`حالة الفشل المحتملة وخطة الإنقاذ والبديل`)

- **Common Failure Mode (`ما الذي قد يسير بشكل خاطئ؟`)**:
  A botWithholds the product price and forces the shopper to answer 6 mandatory personal questions (Name, Email, Budget, Company, Role, Address) before revealing the price; 85% of Arab shoppers abandon the chat immediately.
- **Specific Correction & Non-AI / Platform Fallback (`الإصلاح المحدد والبديل الآمن`)**:
  Follow the **'Give Value First, Qualify Second' Rule**: always state the transparent price range / starting price in the very first automated reply, then ask at most 2 quick-reply button questions before routing to checkout or a human rep.
