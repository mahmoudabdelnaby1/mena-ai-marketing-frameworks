# End-to-End Worked Example & Failure Recovery — `FW-057` (`AMP-285`)

- **Framework**: MENA Influencer Geo-Audience & Engagement-Pod Forensic Vetting Checklist
- **العنوان بالعربية**: قائمة الفحص الجنائي لجمهور المؤثرين في المنطقة (كشف المتابعين الوهميين، مجموعات التفاعل `Pods`، والجمهور خارج نطاق الشحن)
- **Selected Artifact Type**: `CHECKLIST`
- **Disclaimer**: *All scenarios, brand names, SKU codes, and metrics below are original, realistic illustrative examples for MENA practitioner training and are never represented as verified client outcomes.*

## 1. Realistic Sample Brief / Input (`المدخلات وموجز الحالة العملية`)

- **Store**: Saudi Specialty Dates & Gifting Brand shipping **only inside Saudi Arabia (`Riyadh, Jeddah, Dammam`)**.
- **AI Tool Recommendation**: Shortlisted Creator A (`420,000` IG followers, bio says `"📍 Riyadh"`, AI Engagement Score `5.8% — Excellent`, fee `SAR 12,000`) and Creator B (`68,000` IG/Snap followers, fee `SAR 3,500`).

## 2. Initial Generated / Completed Output (`المخرج الأولي عند تطبيق الأداة`)

- **Forensic Vetting Results**:
  - **Creator A (`REJECTED`)**: Native 28-day IG Insights revealed only **`14%` of followers were in Saudi Arabia** (86% were outside GCC from an old international giveaway), and 65% of comments on recent posts came from a 30-person creator engagement pod. Effective KSA reach cost was `10x` inflated!
  - **Creator B (`APPROVED`)**: **`84%` of viewers in Saudi Arabia** (`52%` in Riyadh alone), median Story views `9,400` (`13.8%` view ratio), and comments full of genuine Saudi buyer questions (`"وين موقعكم بالرياض؟"`, `"بكم بوكس الضيافة؟"`).

## 3. Human Review & Localization/Technical Edits (`المراجعة البشرية والتعديلات الرقابية والتقنية`)

1. **Requested Screen Recording of Native Insights**: Required a 10-second screen recording of the native `Instagram Insights -> Reached Audience -> Top Countries & Cities` tab (to prevent Photoshopped static screenshots).
2. **Calculated 'Cost per 1,000 Target-Country Views' (`Geo-Adjusted CPM`)**: Evaluated creators on `Fee / (Median_Views * Target_Country_Share_%)` instead of raw follower count.

## 4. Final Reviewed Example Outcome (`النتيجة النهائية الجاهزة للتنفيذ`)

- Saved `SAR 12,000` by rejecting the geo-mismatched pod account and booked 3 geo-verified Saudi micro-creators delivering `84%+` in-kingdom reach.

## 5. What Can Go Wrong & Specific Correction / Fallback (`حالة الفشل المحتملة وخطة الإنقاذ والبديل`)

- **Common Failure Mode (`ما الذي قد يسير بشكل خاطئ؟`)**:
  A Cairo local restaurant chain hires a food TikToker with 1.2M followers based in Cairo without checking city distribution; 78% of the creator's viewers are in Iraq, Algeria, and Jordan, resulting in high video views and hampir zero restaurant walk-ins.
- **Specific Correction & Non-AI / Platform Fallback (`الإصلاح المحدد والبديل الآمن`)**:
  Always calculate **`In-Zone Deliverable Views = Median_Organic_Views × (Target_City_or_Country_% / 100)`** from a live 28-day native analytics recording before signing any creator.
