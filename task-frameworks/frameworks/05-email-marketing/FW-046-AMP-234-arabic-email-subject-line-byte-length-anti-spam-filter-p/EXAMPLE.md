# End-to-End Worked Example & Failure Recovery — `FW-046` (`AMP-234`)

- **Framework**: Arabic Email Subject-Line Byte-Length & Anti-Spam Filter Prompt Template
- **العنوان بالعربية**: قالب صياغة عناوين رسائل البريد الإلكتروني العربية (ضبط طول البايتات `UTF-8` وتجنب فلاتر السبام والوعود المضللة)
- **Selected Artifact Type**: `PROMPT_TEMPLATE`
- **Disclaimer**: *All scenarios, brand names, SKU codes, and metrics below are original, realistic illustrative examples for MENA practitioner training and are never represented as verified client outcomes.*

## 1. Realistic Sample Brief / Input (`المدخلات وموجز الحالة العملية`)

- **Campaign**: Restock notification for a sold-out Ethiopian Specialty Coffee (`250g`, `79 SAR`) in Saudi Arabia.
- **Bad AI Draft (`74` chars + Spam Triggers)**: `"🔥🚨 عاجل جداً!! قهوتك الإثيوبية المفضلة عادت للمخزون الآن بخصم مجاني وشحن مجاني 100% لا تفوت الفرصة!!!"`

## 2. Initial Generated / Completed Output (`المخرج الأولي عند تطبيق الأداة`)

| Angle | `subject_ar` (<= 38 chars) | Char Count | UTF-8 Bytes | `preheader_ar` (45-70 chars) | Spam Risk Check |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **1. Direct Restock** | `رجعت محمصة إثيوبيا قوجي من جديد ☕` | `33` | `61 B` | `الحمصة الجديدة وصلت اليوم بكمية محدودة — متاح التقسيط عبر تابي` | `PASS (0 spam tokens)` |
| **2. VIP Personal** | `حجزنا لك كيسك من محصول إثيوبيا` | `30` | `55 B` | `محصول قوجي المجفف متوفر الحين بـ 79 ر.س مع توصيل سريع للرياض وجدة` | `PASS (0 spam tokens)` |
| **3. Sensory / Curiosity** | `حمصة هذا الأسبوع وصلت للتو` | `26` | `48 B` | `إيحاءات التوت والشوكولاتة في محصول قوجي الجديد — اطلبه قبل النفاد` | `PASS (0 spam tokens)` |

## 3. Human Review & Localization/Technical Edits (`المراجعة البشرية والتعديلات الرقابية والتقنية`)

1. **BiDi Emoji Placement Check**: Confirmed the coffee emoji `☕` is placed at the **end** of the Arabic string (left side in RTL) rather than the beginning, because leading emojis next to English merge tags can flip alignment on older Android clients.
2. **Verified Mobile Preview**: Confirmed all 3 subject lines render completely without `...` truncation on a 375px iPhone screen.

## 4. Final Reviewed Example Outcome (`النتيجة النهائية الجاهزة للتنفيذ`)

- Selected Subject Line #2 (`"حجزنا لك كيسك من محصول إثيوبيا"` — `30` chars, `55` UTF-8 bytes) paired with the 65-char preheader.

## 5. What Can Go Wrong & Specific Correction / Fallback (`حالة الفشل المحتملة وخطة الإنقاذ والبديل`)

- **Common Failure Mode (`ما الذي قد يسير بشكل خاطئ؟`)**:
  A marketer puts a Latin brand name or number at the very beginning of an Arabic subject line (`'50% خصم على عطور الشتاء'`); on Gmail iOS, the subject line aligns left-to-right and pushes the Arabic words off-screen.
- **Specific Correction & Non-AI / Platform Fallback (`الإصلاح المحدد والبديل الآمن`)**:
  Always **start an Arabic subject line with an Arabic word** (e.g., `'خصم 50% على عطور الشتاء'` instead of `'50% خصم...'`) so the inbox client detects the first strong directional character as Right-to-Left (`RTL`)!
