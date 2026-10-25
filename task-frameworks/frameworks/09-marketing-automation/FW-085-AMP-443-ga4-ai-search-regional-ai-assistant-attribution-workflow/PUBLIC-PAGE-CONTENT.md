# GA4 AI Search & Regional AI Assistant Attribution Workflow (Capturing the 96.9% in Organic Search + Custom Regex for Perplexity, Claude & HUMAIN Chat)
## <span dir="rtl">مسار عمل تتبع إحالات محركات الذكاء الاصطناعي في `GA4` (رصد الـ `96.9%` المسجلة داخل البحث العضوي + فصل `Perplexity` و`Claude` و`HUMAIN Chat` من الإحالات)</span>

> **Asset ID**: `FW-085` (`AMP-443`) | **Artifact Type**: `OPERATING_FRAMEWORK` | **Channel**: Marketing Automation | **Markets**: Egypt & GCC (`KSA, UAE, Kuwait, Qatar, Bahrain, Oman`) | **Version**: `1.2` (`Reviewed 2026-10-25`)

**What You Can Do With This (`ماذا يمكنك أن تنجز بهذه الأداة؟`)**:
- **EN**: Stop under-counting AI search traffic by 30x in GA4 by combining a Custom Channel Group regex (capturing `Perplexity`, `Claude`, `HUMAIN Chat`, `Poe`, `You.com` alongside `ChatGPT`/`Gemini`/`DeepSeek`/`Copilot`/`Grok`) with a Google Search Console AI-Overview landing-page join.
- **AR**: <span dir="rtl">إيقاف فقدان 96.9% من زيارات بحث الذكاء الاصطناعي في تقارير `GA4` عبر الجمع بين قاعدة Regex مخصصة (تلتقط `Perplexity` و`Claude` و`HUMAIN Chat` التي تسقط في `Referral`) وربط صفحات الهبوط مع تقارير `Search Console`.</span>

## 1. Use It When & Required Inputs (`متى تستخدمها وما المدخلات المطلوبة؟`)

- **Use It When (EN)**: Use whenever configuring Google Analytics 4 (`GA4`) or reporting on AI Search (`AEO / GEO`) traffic and conversions in KSA, UAE, or Egypt.
- **متى تستخدمها (AR)**: <span dir="rtl">تُستخدم عند إعداد تقارير `GA4` أو قياس زيارات وتحويلات محركات الذكاء الاصطناعي في السعودية والإمارات ومصر.</span>
- **When NOT to Use It (EN)**: Never show a client GA4's default `AI Assistant` channel row (`e.g., 45 sessions`) and tell them 'that is 100% of your AI search traffic'—that omits 96.9% of AI citations coming through Google `AI Overviews` / `AI Mode` + `Perplexity`/`Claude`/`HUMAIN`!
- **متى لا تستخدمها (AR)**: <span dir="rtl">لا تعرض للعميل صف قناة `AI Assistant` الافتراضي في GA4 وتخبره أن هذا هو إجمالي زيارات الذكاء الاصطناعي؛ لأن ذلك يغفل 96.9% من النقرات القادمة عبر `AI Overviews` في البحث العضوي بالإضافة إلى `Perplexity` و`Claude` و`HUMAIN Chat`!</span>

### Exact Inputs to Prepare (`المدخلات المطلوب تجهيزها قبل البدء`)
- GA4 Admin access (`Admin -> Data display -> Channel groups -> Create new channel group`)
- Google Search Console (`GSC`) linked to GA4 / BigQuery export
- List of informational/comparison landing pages optimized for AEO (`AMP-180`)

## 2. The Working `OPERATING_FRAMEWORK` (`الأداة الكاملة الجاهزة للنسخ والتطبيق الفوري`)

### 2-Layer GA4 MENA AI Search Attribution Architecture (Verified 2026-10-25)

#### Layer 1: Custom GA4 Channel Group (`Extended AI Assistants & Answer Engines`)
In `GA4 Admin -> Data display -> Channel groups`, copy the default channel group, create a custom channel named **`AI Assistants & Answer Engines (Extended MENA)`**, **move it ABOVE `Referral` and `Organic Search` in priority order**, and apply this exact **Source** regex:
```regex
(?i).*(chatgpt\.com|openai\.com|gemini\.google\.com|bard\.google\.com|deepseek\.com|copilot\.microsoft\.com|edgeservices\.bing\.com|grok\.com|x\.ai|perplexity\.ai|claude\.ai|anthropic\.com|humain\.ai|chat\.humain\.com|poe\.com|you\.com|phind\.com|mistral\.ai|lechat\.mistral\.ai|meta\.ai|qwenlm\.ai|kimi\.moonshot\.cn).*
```
- **Why Priority Order Matters**: In GA4 Channel Groups, rules evaluate top-to-bottom. Placing this rule **above `Referral`** rescues `perplexity.ai`, `claude.ai`, `humain.ai`, `poe.com`, and `you.com` from being swallowed by the generic `Referral` bucket!

#### Layer 2: Measuring the `96.9%` Google `AI Overviews` & `AI Mode` Traffic Inside `Organic Search`
Because Google Search Console and GA4 record clicks from **Google `AI Overviews` and `AI Mode`** under standard `google / organic` (`Organic Search`):
1. **In Google Search Console (`Performance -> Search results`)**:
   - Filter queries by **Informational & Comparison Question Stems (`كيف، افضل، الفرق بين، كم سعر، ما هو، مقارنة`)** (`AMP-001`, `AMP-180`) on Web Search where `AI Overviews` trigger.
2. **In GA4 / Looker Studio Executive Reporting**:
   - Present AI-driven discovery as a **2-Part Scorecard**:
     - **Part A (`Direct Chatbot Referrals`)**: Tracked via the Layer 1 Custom Channel Group (`ChatGPT`, `Gemini`, `Perplexity`, `Claude`, `DeepSeek`, `Copilot`, `Grok`, `HUMAIN Chat`).
     - **Part B (`Google AI Overviews / AI Mode Organic Citations — ~96.9% of Volume`)**: Tracked via `google / organic` sessions landing on your AEO comparison/guide pages (`AMP-180`) cross-referenced with GSC query data.
     - **Explicit Boundary Note (`AMP-543`)**: Note transparently in reports that links copied from AI apps and pasted into private WhatsApp chats open in WhatsApp's in-app browser without an HTTP referrer and land in `Direct` (an industry-wide `Unknown` that cannot be fabricated).

## 3. Complete End-to-End Worked Example (`مثال تطبيقي متكامل من المدخلات حتى المراجعة البشرية والنتيجة النهائية`)

*(Illustrative scenario — original example for training, never represented as a verified client outcome)*

### Step A: Sample Brief / Input (`موجز المدخلات`)
- **Property**: Saudi B2B & Consumer E-Commerce Platform (`180,000` monthly sessions in GA4).
- **Problem**: Default GA4 `AI Assistant` channel showed only `112` sessions (`ChatGPT` + `Gemini`), while `340` sessions from `perplexity.ai`, `claude.ai`, and `humain.ai` were hidden inside `Referral`, and `3,850` clicks from Google `AI Overviews` on comparison guides were lumped undifferentiated inside `Organic Search`.

### Step B: Initial Output (`المخرج الأولي`)
- **Deployed Layer 1 + Layer 2 Reporting**:
  1. Created Custom Channel Group `AI Assistants & Answer Engines (Extended MENA)` positioned above `Referral` (retroactively reclassifying all historical `perplexity.ai`, `claude.ai`, `humain.ai`, and `poe.com` sessions in GA4!).
  2. Built a Looker Studio 2-Part AI Discovery view separating **Standalone Chatbot Referrals (`452` sessions)** from **Google AI-Overview / Question-Query Organic Landing Sessions (`3,850` sessions)**.

### Step C: Human Review & Edits (`التدقيق البشري والتعديلات`)
1. **Added Known Caveats Box on Dashboard (`AMP-543`, `AMP-545`, `AMP-549`)**: Documented on the executive dashboard that (a) Google keeps its internal default AI hostname list unpublished (`AMP-549`), and (b) AI links shared via private WhatsApp arrive as `Direct` (`AMP-543`).
2. **Verified Retroactive Channel Group Application**: Confirmed in GA4 `Traffic Acquisition` that custom channel groups apply retroactively to historical property data.

### Step D: Final Reviewed Example Outcome (`النتيجة النهائية المعتمدة`)
- Complete, non-deceptive GA4 AI Search & Assistant measurement framework deployed with custom MENA regex (`including Perplexity, Claude & HUMAIN Chat`) and GSC AI-Overview organic reconciliation.

## 4. What Can Go Wrong & How to Fix It (`الأخطاء الشائعة وخطة الإنقاذ`)

- **Failure Case (`المشكلة المحتملة`)**: An analyst adds the custom AI regex channel at the **bottom** of the GA4 Channel Group list (below `Referral`); because GA4 stops at the first matching rule, `Referral` matches `perplexity.ai` and `claude.ai` first, and the new channel shows `0` sessions!
- **Correction & Fallback (`الحل الإجرائي والبديل الآمن`)**: In `GA4 Admin -> Channel groups -> Reorder`, always drag **`AI Assistants & Answer Engines (Extended MENA)`** to **Position #1 or #2 (strictly ABOVE `Referral` and `Organic Search`)** before saving!

## 5. Model & Platform Capability Matrix (`مصفوفة قدرات النماذج والمنصات — 2026-10-25`)

| Platform / Model | Status | Official Documentation | MENA Operational Constraint | Fallback |
| :--- | :--- | :--- | :--- | :--- |
| **Google Analytics 4 Default `AI Assistant` Channel (13 May 2026) vs. Custom Channel Groups** | `supported` | [Official Docs](https://voctos.net/ga4-ai-traffic-arab-markets/) (`2026-10-25`) | VOCTOS Oct 2026 audit proved that GA4's default AI Assistant channel misses Perplexity, Claude, and regional tools, while 96.9% of measured AI search clicks come via Google Organic Search (AI Overviews / AI Mode). | Use GA4 Custom Channel Groups (which evaluate retroactively!) placed above `Referral`. |

## 6. How to Measure Success (`خطة القياس والضوابط`)

- **Primary Metric**: Reclassified `Perplexity / Claude / HUMAIN / Poe` sessions rescued from `Referral`, plus Conversion Rate of `AI Assistants (Extended)` vs. site average.
- **Baseline**: Default GA4 `AI Assistant` channel session count.
- **Observation Window**: Immediate (retroactive in GA4 Custom Channel Groups) + ongoing 28-day tracking.
- **Interpretation Boundary**: Custom channel regex captures browser-referred chatbot clicks, but cannot measure dark-social WhatsApp pastes (`AMP-543`) or zero-click AI answers.

## 7. Primary Sources & Evidence Boundaries (`المصادر الموثقة وحدود الأدلة`)

- [How GA4 Classifies AI Traffic for Arab Websites: What Saudi, UAE and Egyptian Sites Lose (2026 Study)](https://voctos.net/ga4-ai-traffic-arab-markets/) — *VOCTOS* (Published `2026-10-18`, Accessed `2026-10-25`): GA4's AI Assistant channel (launched 13 May 2026) misses 96.9% of AI search citations (which come from Google AI Overviews and AI Mode and land in Organic Search), sends ChatGPT links with rel='noreferrer' or WhatsApp shares to Direct, and sends Perplexity, Claude, HUMAIN Chat (KSA), Fanar (Qatar), and Gulf marketplaces (amazon.sa, noon.com) to Referral.
