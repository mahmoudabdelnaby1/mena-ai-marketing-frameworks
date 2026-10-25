# End-to-End Worked Example & Failure Recovery — `FW-031` (`AMP-129`)

- **Framework**: Social Comment Moderation Whitelist & Dialectal Price-Inquiry Routing Checklist (`بكام` / `بكم`)
- **العنوان بالعربية**: قائمة فحص وضبط الفلترة الآلية للتعليقات لحماية استفسارات الشراء باللهجات (`بكام` / `بكم` / `تفاصيل`)
- **Selected Artifact Type**: `CHECKLIST`
- **Disclaimer**: *All scenarios, brand names, SKU codes, and metrics below are original, realistic illustrative examples for MENA practitioner training and are never represented as verified client outcomes.*

## 1. Realistic Sample Brief / Input (`المدخلات وموجز الحالة العملية`)

- **Store**: Cairo Women's Footwear & Handbags Brand running Instagram & Facebook Reels ads.
- **Problem Discovered**: An AI sentiment/spam plugin was set to `'Hide repetitive 1-word comments and negative slang'`. Over 30 days, it auto-hid `1,420` comments asking `"بكام"` and `"تفاصيل"`, cutting comment-driven orders in half.

## 2. Initial Generated / Completed Output (`المخرج الأولي عند تطبيق الأداة`)

- **Moderation & Automation Audit**:
  1. Whitelisted all 28 Egyptian & Gulf price/stock inquiry tokens (`بكام`, `بكم`, `سعره كام`, `تفاصيل`, `موجود`, `متوفر`).
  2. Configured ManyChat / Meta Automation to reply publicly with the transparent `EGP` price + COD/InstaPay availability AND send the direct product checkout card via DM within 10 seconds.

## 3. Human Review & Localization/Technical Edits (`المراجعة البشرية والتعديلات الرقابية والتقنية`)

1. **Orthographic Variant Expansion (`AMP-002`)**: Added elongated vowel variants (`بكاام`, `بكاآام`, `تفاااصيل`) and Franco-Arabic (`bkam`, `details`) to the trigger regex `ب+ك+ا+م+`.
2. **Real Spam Isolation**: Restricted auto-hide strictly to actual spam patterns (external `http`/`wa.me` links posted by third-party accounts, crypto scams, and explicit profanity).

## 4. Final Reviewed Example Outcome (`النتيجة النهائية الجاهزة للتنفيذ`)

- `0` legitimate `"بكام / بكم"` buyer inquiries hidden; 100% receive an instant transparent public price reply + private checkout DM link.

## 5. What Can Go Wrong & Specific Correction / Fallback (`حالة الفشل المحتملة وخطة الإنقاذ والبديل`)

- **Common Failure Mode (`ما الذي قد يسير بشكل خاطئ؟`)**:
  A brand uses ManyChat to reply `'تم الرد عالخاص شيك رسايلك 🌸'` to 300 comments without stating the price publicly; frustrated shoppers reply in the comments `'ما تقولوا السعر هنا ليه الكهن ده!'`, tanking ad sentiment and CTR.
- **Specific Correction & Non-AI / Platform Fallback (`الإصلاح المحدد والبديل الآمن`)**:
  Always state the starting or exact price inside the **public comment reply** alongside the DM trigger—transparency in comments converts silent lurkers who never comment.
