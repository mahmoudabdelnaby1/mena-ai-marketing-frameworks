# Short-Form Gulf Snapchat Creative Hypothesis & Storyboard Template
## <span dir="rtl">قالب فرضية إبداعية ولوحة مشاهد قصيرة لإعلانات سناب شات في الخليج</span>

> **Asset ID**: `FW-065` (`AMP-333`) | **Artifact Type**: `EXTEND_EXISTING` | **Channel**: Video Advertising | **Markets**: Egypt & GCC (`KSA, UAE, Kuwait, Qatar, Bahrain, Oman`) | **Version**: `1.2` (`Reviewed 2026-10-25`)

**What You Can Do With This (`ماذا يمكنك أن تنجز بهذه الأداة؟`)**:
- **EN**: Structure Gulf Snapchat video ads and AI video prompts to hit Snapchat's proven 5–6 second vertical cadence—delivering the core message in Second 1 and the concrete SAR/AED offer in Seconds 2–3 with zero static logo openings.
- **AR**: <span dir="rtl">هيكلة إعلانات سناب شات الموجهة للخليج وبرومبتات توليد الفيديو وفق الإيقاع القياسي لسناب شات (قصير: الرسالة الأساسية في الثانية 1، والعرض والسعر في الثانية 2–3، مع حظر البدء بشعار ثابت).</span>

## 1. Use It When & Required Inputs (`متى تستخدمها وما المدخلات المطلوبة؟`)

- **Use It When (EN)**: Use whenever scripting or generating Snapchat Single Image/Video Ads, Story Ads, or 6-second non-skippable Commercials for Saudi Arabia, UAE, Kuwait, or Qatar.
- **متى تستخدمها (AR)**: <span dir="rtl">تُستخدم عند كتابة أو توليد إعلانات سناب شات الممولة في السعودية والإمارات والكويت وقطر.</span>
- **When NOT to Use It (EN)**: Never open a Snapchat ad with a fade-in from black, a 2-second animated brand logo card, or a slow establishing drone shot with no human/product action.
- **متى لا تستخدمها (AR)**: <span dir="rtl">لا تبدأ إعلان سناب شات أبداً بشاشة سوداء تدريجية (`Fade-in`) أو بطاقة شعار ثابت لمدة ثانيتين أو لقطة جوية بطيئة خالية من الحركة المباشرة للمنتج.</span>

### Exact Inputs to Prepare (`المدخلات المطلوب تجهيزها قبل البدء`)
- Hero Product Visual Action (what moves in Frame 1 at `0.0s`)
- Exact Offer String (`Price in SAR/AED + Discount % + Tabby/Tamara`)
- Spoken Saudi/Gulf Hook (`<= 14 words total` for a 5.5-second ad at 2.5 words/sec!)

## 2. The Working `EXTEND_EXISTING` (`الأداة الكاملة الجاهزة للنسخ والتطبيق الفوري`)

### Gulf Snapchat short-form Micro-Commercial Blueprint (`video-prompt-architect` Extension)

#### 1. Second-by-Second Timeline Contract (`Total: 5.5 to 6.0 Seconds — Max 14 Spoken Arabic Words`)
| Second Window | Visual Camera & Subject Action | Audio / Spoken Khaleeji VO (`AMP-332` Vocalized) | On-Screen Safe-Zone Overlay (`AMP-338`) |
| :--- | :--- | :--- | :--- |
| **`0.0s – 1.2s` (`Second 1: Immediate Hero Message — NO LOGO CARD`)** | **Start mid-action (`In Media Res`)**: Hands unboxing, pouring, spraying, or demonstrating the product result in close-up `9:16`. | **4–5 words max**:<br>`"قهوتك المختصة صارت معك بالبر!"` | High-contrast hook pill at `Y: 360px` + small corner `#إعلان` badge (`AMP-287`). |
| **`1.2s – 3.5s` (`Seconds 2–3: Establish Offer, Price & BNPL`)** | Smooth camera whip/pull-back showing full product in hand + clear physical scale. | **5–6 words max**:<br>`"بـ ثلاث مية وتسعة وأربعين ريال ومقسمة على تابي."` | Large Price & Offer Badge at `Y: 1150px`: **`349 ر.س (شامل الضريبة) | 4 دفعات تابي`**. |
| **`3.5s – 5.8s` (`Seconds 4–6: Direct Swipe/Tap CTA`)** | Satisfying final product hero lock + hand pointing or directional visual cue toward the bottom CTA button. | **3–4 words max**:<br>`"ارفع الشاشة واطلبها الحين!"` | Directional arrow pointing to Snapchat's native bottom CTA bar (`اطلب الآن`). |

#### 2. Copy-Ready `video-prompt-architect` Prompt Block for 6s Single-Shot Snapchat Ad (`Veo 3.1 / Kling 3.0 / Sora 2`)
```text
Vertical 9:16 high-energy Gulf commercial single-take shot (6 seconds, 24fps).
[0.0s-1.5s]: Starts immediately in mid-action—no fade-in, no static logo card. Extreme close-up of a sleek matte-black portable espresso maker held in a young Saudi man's right hand (wearing crisp white thobe cuff) pouring rich golden crema espresso into a glass cup inside a sunlit Riyadh desert camp.
[1.5s-4.0s]: Rapid smooth handheld camera pull-back revealing the compact device size and warm desert morning atmosphere, upper-middle frame kept clean with soft bokeh for post-production Arabic offer overlay.
[4.0s-6.0s]: Subject lifts the cup toward camera with a confident warm smile. Natural morning sunlight (4500K), crisp commercial contrast, zero embedded text, zero watermarks. --ar 9:16 --duration 6s
```

## 3. Complete End-to-End Worked Example (`مثال تطبيقي متكامل من المدخلات حتى المراجعة البشرية والنتيجة النهائية`)

*(Illustrative scenario — original example for training, never represented as a verified client outcome)*

### Step A: Sample Brief / Input (`موجز المدخلات`)
- **Brand**: Saudi Home Fragrance & Diffuser Store on Salla (`Smart Waterless Car & Majlis Diffuser`, `179 SAR` incl. VAT).
- **Previous 25-Second Ad**: Opened with 3 seconds of a spinning gold logo, followed by 10 seconds of slow B-roll before mentioning the product at Second 14. Result: `89%` of Snapchat viewers swiped away before Second 3 (`Average Watch Time: 1.4s`).

### Step B: Initial Output (`المخرج الأولي`)
- **Re-Engineered 5.5-Second Gulf Snapchat Ad**:
  - **`[0.0s–1.2s]`**: Instant dense aromatic mist burst from the anodized diffuser placed in a luxury car cupholder (`VO: "فواحة ذكية بدون موية تغير جو سيارتك ومجلسك!"`).
  - **`[1.2s–3.5s]`**: Hand taps the digital intensity button (`VO: "بـ مية وتسعة وسبعين ريال بس ومع تابي وتمارا."` | Overlay: `179 ر.س شامل الضريبة | 4 دفعات تابي`).
  - **`[3.5s–5.5s]`**: Clean hero hold (`VO: "ارفع الشاشة واطلبها الحين!"`).

### Step C: Human Review & Edits (`التدقيق البشري والتعديلات`)
1. **Word Count Trim**: Confirmed spoken script is exactly `16` short Arabic words (`5.2 seconds` spoken at energetic Gulf cadence).
2. **Right-Hand Etiquette Check (`AMP-336`)**: Confirmed the hand holding/tapping the diffuser in the prompt is explicitly the **right hand**.

### Step D: Final Reviewed Example Outcome (`النتيجة النهائية المعتمدة`)
- 5.5-second Snapchat Gulf Commercial & Story Ad pack delivered with Sec 1 action hook, Sec 2–3 SAR/Tabby offer, and 3x improvement in Offer-View Rate.

## 4. What Can Go Wrong & How to Fix It (`الأخطاء الشائعة وخطة الإنقاذ`)

- **Failure Case (`المشكلة المحتملة`)**: An editor exports a 6-second Snapchat video where the first `0.5` seconds is a black frame (`Fade from Black`); Snapchat uses Frame 0 as the preload thumbnail, causing viewers to see a black screen as the story loads and immediately tap past it.
- **Correction & Fallback (`الحل الإجرائي والبديل الآمن`)**: Enforce the **Frame-Zero Rule**: Frame `00:00:00` (the very first frame of the video file) MUST be a bright, fully lit action frame showing the product in motion—zero black frames, zero fade-ins!

## 5. Model & Platform Capability Matrix (`مصفوفة قدرات النماذج والمنصات — 2026-10-25`)

| Platform / Model | Status | Official Documentation | MENA Operational Constraint | Fallback |
| :--- | :--- | :--- | :--- | :--- |
| **Snapchat Commercials & Snap Ads short-form Gulf Best Practices** | `supported` | [Official Docs](https://esafqa.com/en/blog/snapchat-ads-guide-saudi-gulf/) (`2026-10-25`) | Snapchat official ad guidance and Esafqa's Oct 2026 Gulf guide specify 5–6 second vertical ads with the key message in Second 1, the offer in Seconds 2–3, and no static logo opening. | Even when running a longer 15s UGC story, cut a dedicated 6-second version from the strongest product demo moment as a parallel ad variation. |

## 6. How to Measure Success (`خطة القياس والضوابط`)

- **Primary Metric**: 2-Second Hold Rate (`Target: >= 35%`), Offer-Frame View Rate (`% reaching Second 3`), and Swipe-Up / eCPSU.
- **Baseline**: Prior 15–30s slow-intro Snapchat ad performance.
- **Observation Window**: 7 days post-launch.
- **Interpretation Boundary**: Hitting the 5–6s Gulf structure ensures viewers actually see your offer, while landing page speed (`AMP-393`) and checkout UX (`AMP-387`) convert the swipe.

## 7. Primary Sources & Evidence Boundaries (`المصادر الموثقة وحدود الأدلة`)

- [Snap Advertising Policies - Snap Inc.](https://www.snap.com/ad-policies) — *Snap Inc.* (Published `2026-06-01`, Accessed `2026-10-25`): Enforces country-specific creative, cultural sensitivity, financial, and health/cosmetic claim rules across Saudi Arabia, UAE, and Egypt.
- [Snapchat vs TikTok Ads in Saudi Arabia (2026)](https://thegrower.ai/blog/snapchat-vs-tiktok-ads-saudi-arabia) — *Grower AI* (Published `2026-02-10`, Accessed `2026-10-25`): Compares Snapchat vs TikTok ad formats, SAR test budget splits, Khaleeji creative norms, and conversion attribution in Saudi Arabia.
- [Snapchat Ads Guide for Online Stores in Saudi Arabia and the Gulf](https://esafqa.com/en/blog/snapchat-ads-guide-saudi-gulf/) — *Esafqa* (Published `2026-10-09`, Accessed `2026-10-25`): Details Snapchat's official creative rules for Gulf stores: 9:16 native shoot, hero message in second 1, brand before second 2 (no static logo opening), 5-6s duration with offer in seconds 2-3, natural Saudi/Gulf dialect + captions, and zero recycled TikTok/Reels watermarks.
