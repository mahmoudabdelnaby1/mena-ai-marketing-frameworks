# Arabic Email Typography, Web-Safe Font Stack & Line-Height Checklist (Preventing Tiny Times New Roman Fallback in Outlook)
## <span dir="rtl">قائمة فحص خطوط البريد الإلكتروني العربية (`Font Stack`) وتباعد الأسطر لمنع الارتداد لخط `Times New Roman` غير المقروء في Outlook</span>

> **Asset ID**: `FW-050` (`AMP-238`) | **Artifact Type**: `CHECKLIST` | **Channel**: Email Marketing | **Markets**: Egypt & GCC (`KSA, UAE, Kuwait, Qatar, Bahrain, Oman`) | **Version**: `1.2` (`Reviewed 2026-10-25`)

**What You Can Do With This (`ماذا يمكنك أن تنجز بهذه الأداة؟`)**:
- **EN**: Configure Arabic HTML email font stacks, minimum pixel sizes (`>= 16px` body), and line-heights (`1.7–1.8`) so Windows Outlook, Gmail, and iOS Mail never fall back to cramped 12px Times New Roman.
- **AR**: <span dir="rtl">ضبط سلسلة الخطوط البديلة (`Font Stack`) وحجم الخط (`16px` كحد أدنى) وتباعد الأسطر (`1.75`) في رسائل البريد العربية لمنع تحول النص في برنامج Outlook إلى خط `Times New Roman` الصغير غير المقروء.</span>

## 1. Use It When & Required Inputs (`متى تستخدمها وما المدخلات المطلوبة؟`)

- **Use It When (EN)**: Use on every Arabic or bilingual HTML email template in Klaviyo, HubSpot, Mailchimp, Braze, or custom ESPs.
- **متى تستخدمها (AR)**: <span dir="rtl">تُستخدم في جميع قوالب البريد الإلكتروني العربية أو ثنائية اللغة على كافة منصات الإرسال.</span>
- **When NOT to Use It (EN)**: Never set Arabic email body text smaller than `16px` or `line-height` smaller than `1.65`, and never use `letter-spacing` (`tracking > 0`) on Arabic text (positive `letter-spacing` breaks connected Arabic cursive ligatures!).
- **متى لا تستخدمها (AR)**: <span dir="rtl">لا تجعل حجم خط المتن العربي في البريد أقل من `16px` ولا تباعد الأسطر أقل من `1.65`، ويُحظر تماماً وضع تباعد بين الحروف (`letter-spacing > 0`) لأنه يقطع اتصال الحروف العربية!</span>

### Exact Inputs to Prepare (`المدخلات المطلوب تجهيزها قبل البدء`)
- HTML Email Template CSS styles (`font-family`, `font-size`, `line-height`, `letter-spacing`)
- Brand Primary Arabic Web Font (e.g., `Tajawal`, `Cairo`, `IBM Plex Sans Arabic`, `Almarai`)

## 2. The Working `CHECKLIST` (`الأداة الكاملة الجاهزة للنسخ والتطبيق الفوري`)

### Arabic Email Typography & Outlook Fallback Checklist

#### 1. The Mandatory Arabic Email Font Stack & MSO Conditional Fix
- **For Clients Supporting Web Fonts (Apple Mail, iOS Mail, Android Mail)**: Load `Tajawal`, `Cairo`, or `IBM Plex Sans Arabic` via `<link>`.
- **For Gmail & Windows Desktop Outlook (Which Strip Web Fonts)**: Place **`'Segoe UI'`, `Tahoma`, and `Arial`** immediately after the web font (NEVER leave `serif` or `Times New Roman` as the fallback!), and include the `<!--[if mso]>` block below so Windows Outlook forces clean `Segoe UI` / `Tahoma`:

```html
<!--[if mso]>
<style type="text/css">
  body, table, td, p, a, h1, h2, h3, span, li {
    font-family: 'Segoe UI', Tahoma, Arial, sans-serif !important;
  }
</style>
<![endif]-->
```

#### 2. Hard Arabic Email Typography Rules (Inline on Every `<td>`, `<p>`, `<h1>`, `<a>`)
| CSS Property | Broken Western Default in AI Templates | Mandatory Arabic Email Standard (`PASS`) | Why It Matters in Arabic Script |
| :--- | :--- | :--- | :--- |
| **`font-family`** | `'Inter', Helvetica, sans-serif` (Falls back to `Times New Roman` in Outlook!) | `'Tajawal', 'Cairo', 'Segoe UI', Tahoma, Arial, sans-serif` | `'Segoe UI'` and `Tahoma` are pre-installed on 100% of Windows/macOS machines with crisp, legible Arabic UI glyphs. |
| **`font-size` (Body)** | `13px` or `14px` | **`16px` – `18px`** (`Minimum 16px`) | Arabic x-height and ascenders/dots require at least `16px` to remain scannable on mobile and desktop. |
| **`line-height`** | `1.2` – `1.4` | **`1.70` – `1.85`** (`28px–30px` for `16px` body) | Prevents upper hamzas/dots (`أ، إ، ت، ث`) from colliding with lower descenders (`ج، ح، ي، ر`) on the line above. |
| **`letter-spacing`** | `0.5px` or `0.05em` (Common on English headings/buttons!) | **`0px` / `normal` (`STRICTLY 0!`)** | Any positive `letter-spacing` tears connected Arabic cursive letters apart (`ت س و ق` instead of `تسوق`). |
| **`font-style`** | `italic` (For emphasis/quotes) | **`normal` + `font-weight: 700` or color highlight** | Arabic script does not use Western slanted italics; synthetic browser/Outlook `italic` distorts Arabic glyphs. |

## 3. Complete End-to-End Worked Example (`مثال تطبيقي متكامل من المدخلات حتى المراجعة البشرية والنتيجة النهائية`)

*(Illustrative scenario — original example for training, never represented as a verified client outcome)*

### Step A: Sample Brief / Input (`موجز المدخلات`)
- **Template**: AI-generated HubSpot Newsletter for a Riyadh & Cairo FinTech platform.
- **Defects Found**:
  1. CTA button had `letter-spacing: 1.5px; text-transform: uppercase;`, tearing the button text `"افتح حسابك الآن"` into disconnected letters on Gmail.
  2. Body text used `font-family: 'Montserrat', sans-serif; font-size: 13px;`, rendering in tiny `13px Times New Roman` on Windows Outlook across corporate banking clients.

### Step B: Initial Output (`المخرج الأولي`)
- **Applied Typographic Fix**:
  - Updated inline style on all `<td>`, `<p>`, and `<a>` elements to:
    `font-family: 'IBM Plex Sans Arabic', 'Segoe UI', Tahoma, Arial, sans-serif; font-size: 16px; line-height: 1.75; letter-spacing: 0px; font-style: normal;`
  - Added `<!--[if mso]>` conditional block forcing `'Segoe UI', Tahoma, Arial, sans-serif !important` on Windows Outlook.

### Step C: Human Review & Edits (`التدقيق البشري والتعديلات`)
1. **Scannability Check**: Audited all subheadings (`<h2>`) and CTA buttons to ensure `letter-spacing: 0` and removed all `<i>`/`<em>` tags around Arabic text, replacing them with `<strong>` (`font-weight: 700`).
2. **Verified Outlook 365 Desktop Rendering**: Confirmed clean `16px Segoe UI` rendering with generous `1.75` line spacing.

### Step D: Final Reviewed Example Outcome (`النتيجة النهائية المعتمدة`)
- Master HubSpot/Klaviyo Arabic typography CSS snippet deployed across all templates with zero `Times New Roman` fallbacks and zero broken cursive ligatures.

## 4. What Can Go Wrong & How to Fix It (`الأخطاء الشائعة وخطة الإنقاذ`)

- **Failure Case (`المشكلة المحتملة`)**: A designer uses an English luxury template where all `<h2>` headings and buttons inherit `letter-spacing: 2px` from the global stylesheet; every Arabic heading renders with ugly gaps between connected letters (`م ج م و ع ة`).
- **Correction & Fallback (`الحل الإجرائي والبديل الآمن`)**: Add `letter-spacing: 0px !important; font-style: normal !important;` to your global `[dir="rtl"]` and inline Arabic style rules.

## 5. Model & Platform Capability Matrix (`مصفوفة قدرات النماذج والمنصات — 2026-10-25`)

| Platform / Model | Status | Official Documentation | MENA Operational Constraint | Fallback |
| :--- | :--- | :--- | :--- | :--- |
| **Windows Outlook (Word Rendering Engine) & Gmail Web Font Support** | `plan/region dependent` | [Official Docs](https://mailtester.com/blog/right-to-left-email-rendering-problems-gmail-outlook/) (`2026-10-25`) | Windows Outlook ignores external `@font-face` web fonts and falls back to `Times New Roman` unless `<!--[if mso]>` specifies a system-installed Arabic sans-serif font (`Segoe UI` / `Tahoma`). | Always include `'Segoe UI', Tahoma, Arial, sans-serif` in inline `font-family` and `<!--[if mso]>` blocks. |

## 6. How to Measure Success (`خطة القياس والضوابط`)

- **Primary Metric**: 100% pass rate on Outlook/Gmail typography visual check (`0` `Times New Roman` fallbacks, `0` broken ligatures) and Email Read-Time / Click-Through Rate.
- **Baseline**: Pre-fix visual inspection and CTOR.
- **Observation Window**: 14 days post-template update.
- **Interpretation Boundary**: Clean Arabic typography removes eye strain and credibility loss, while content relevance drives click conversion.

## 7. Primary Sources & Evidence Boundaries (`المصادر الموثقة وحدود الأدلة`)

- [Top Arabic Content Writing Mistakes Hurting Your SEO Rankings](https://www.aiqalam.com/en/blog/top-arabic-content-writing-mistakes-hurting-your-seo-rankings) — *AI Qalam* (Published `2026-10-24`, Accessed `2026-10-25`): Documents poor RTL text alignment, unnatural AI phrasing, and morphological keyword stuffing in Arabic content.
- [Solving Right-to-Left Email Rendering Problems in Gmail and Outlook](https://mailtester.com/blog/right-to-left-email-rendering-problems-gmail-outlook/) — *MailTester* (Published `2026-09-24`, Accessed `2026-10-25`): Documents how missing dir='rtl' attributes, inline CSS overrides, and mixed bidirectional strings cause broken Arabic email rendering in Outlook and Gmail across Klaviyo, HubSpot, and Mailchimp.
