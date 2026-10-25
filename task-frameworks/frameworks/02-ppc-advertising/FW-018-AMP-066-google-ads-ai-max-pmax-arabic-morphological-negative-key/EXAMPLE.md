# End-to-End Worked Example & Failure Recovery — `FW-018` (`AMP-066`)

- **Framework**: Google Ads AI Max & PMax Arabic Morphological Negative Keyword Generator Prompt
- **العنوان بالعربية**: قالب توليد قوائم الكلمات السلبية الصرفية واللهجية لحملات Google Ads AI Max وPerformance Max بالعربية
- **Selected Artifact Type**: `PROMPT_TEMPLATE`
- **Disclaimer**: *All scenarios, brand names, SKU codes, and metrics below are original, realistic illustrative examples for MENA practitioner training and are never represented as verified client outcomes.*

## 1. Realistic Sample Brief / Input (`المدخلات وموجز الحالة العملية`)

- **Advertiser**: Riyadh & Cairo B2B ERP Accounting Software Provider (`SAR 12,000/year` subscription).
- **Problem**: Enabled Google Ads `AI Max for Search` on `"برنامج محاسبة للشركات"`. Search Terms report revealed `38%` of budget was spent on queries like `"تحميل برنامج محاسبة مجاني بالكراك"`, `"برنامج محاسبه ببلاش اكسيل"`, and `"وظائف محاسب في الرياض"`.

## 2. Initial Generated / Completed Output (`المخرج الأولي عند تطبيق الأداة`)

- Generated `148` morphological Arabic negative keywords across 4 buckets (`Free/Excel/Crack`, `Jobs/Accountant Vacancies`, `University Homework/PDF`, `Used Hardware`) including all `ة/ه` and `أ/ا` variants and `بـ/الـ` prefixes.

## 3. Human Review & Localization/Technical Edits (`المراجعة البشرية والتعديلات الرقابية والتقنية`)

1. **Protected High-Intent Trial Queries**: Made sure `"تجربة مجانية"` (Free Trial) was **NOT** blocked while blocking `"تحميل مجاني بالكراك"` and `"ببلاش مدى الحياة"`.
2. **Account-Level PMax Attachment**: Applied the shared list at the Campaign level for Search and Account-level Negative Keywords for Performance Max.

## 4. Final Reviewed Example Outcome (`النتيجة النهائية الجاهزة للتنفيذ`)

- `148`-term Arabic Morphological Negative List attached to Search and PMax; wasted spend on free/crack/job queries dropped from `38%` to `<2%` in the subsequent 14-day Search Terms audit.

## 5. What Can Go Wrong & Specific Correction / Fallback (`حالة الفشل المحتملة وخطة الإنقاذ والبديل`)

- **Common Failure Mode (`ما الذي قد يسير بشكل خاطئ؟`)**:
  A media buyer adds only the single word `-مجاني` (with Yaa) as a negative keyword; Google Ads still serves ads on `"تحميل برنامج محاسبة مجانا"` (with Alef), `"بالمجان"`, and `"ببلاش"` because negative match does not stem Arabic morphological variants.
- **Specific Correction & Non-AI / Platform Fallback (`الإصلاح المحدد والبديل الآمن`)**:
  Always generate the full orthographic and prefix inflection family (`مجاني، مجانية، مجانيه، مجانا، مجاناً، بالمجان، المجاني، ببلاش، بلاش`) for every excluded Arabic root.
