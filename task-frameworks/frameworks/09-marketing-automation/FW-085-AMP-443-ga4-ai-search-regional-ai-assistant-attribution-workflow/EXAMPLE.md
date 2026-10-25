# End-to-End Worked Example & Failure Recovery — `FW-085` (`AMP-443`)

- **Framework**: GA4 AI Search & Regional AI Assistant Attribution Workflow (Capturing the 96.9% in Organic Search + Custom Regex for Perplexity, Claude & HUMAIN Chat)
- **العنوان بالعربية**: مسار عمل تتبع إحالات محركات الذكاء الاصطناعي في `GA4` (رصد الـ `96.9%` المسجلة داخل البحث العضوي + فصل `Perplexity` و`Claude` و`HUMAIN Chat` من الإحالات)
- **Selected Artifact Type**: `OPERATING_FRAMEWORK`
- **Disclaimer**: *All scenarios, brand names, SKU codes, and metrics below are original, realistic illustrative examples for MENA practitioner training and are never represented as verified client outcomes.*

## 1. Realistic Sample Brief / Input (`المدخلات وموجز الحالة العملية`)

- **Property**: Saudi B2B & Consumer E-Commerce Platform (`180,000` monthly sessions in GA4).
- **Problem**: Default GA4 `AI Assistant` channel showed only `112` sessions (`ChatGPT` + `Gemini`), while `340` sessions from `perplexity.ai`, `claude.ai`, and `humain.ai` were hidden inside `Referral`, and `3,850` clicks from Google `AI Overviews` on comparison guides were lumped undifferentiated inside `Organic Search`.

## 2. Initial Generated / Completed Output (`المخرج الأولي عند تطبيق الأداة`)

- **Deployed Layer 1 + Layer 2 Reporting**:
  1. Created Custom Channel Group `AI Assistants & Answer Engines (Extended MENA)` positioned above `Referral` (retroactively reclassifying all historical `perplexity.ai`, `claude.ai`, `humain.ai`, and `poe.com` sessions in GA4!).
  2. Built a Looker Studio 2-Part AI Discovery view separating **Standalone Chatbot Referrals (`452` sessions)** from **Google AI-Overview / Question-Query Organic Landing Sessions (`3,850` sessions)**.

## 3. Human Review & Localization/Technical Edits (`المراجعة البشرية والتعديلات الرقابية والتقنية`)

1. **Added Known Caveats Box on Dashboard (`AMP-543`, `AMP-545`, `AMP-549`)**: Documented on the executive dashboard that (a) Google keeps its internal default AI hostname list unpublished (`AMP-549`), and (b) AI links shared via private WhatsApp arrive as `Direct` (`AMP-543`).
2. **Verified Retroactive Channel Group Application**: Confirmed in GA4 `Traffic Acquisition` that custom channel groups apply retroactively to historical property data.

## 4. Final Reviewed Example Outcome (`النتيجة النهائية الجاهزة للتنفيذ`)

- Complete, non-deceptive GA4 AI Search & Assistant measurement framework deployed with custom MENA regex (`including Perplexity, Claude & HUMAIN Chat`) and GSC AI-Overview organic reconciliation.

## 5. What Can Go Wrong & Specific Correction / Fallback (`حالة الفشل المحتملة وخطة الإنقاذ والبديل`)

- **Common Failure Mode (`ما الذي قد يسير بشكل خاطئ؟`)**:
  An analyst adds the custom AI regex channel at the **bottom** of the GA4 Channel Group list (below `Referral`); because GA4 stops at the first matching rule, `Referral` matches `perplexity.ai` and `claude.ai` first, and the new channel shows `0` sessions!
- **Specific Correction & Non-AI / Platform Fallback (`الإصلاح المحدد والبديل الآمن`)**:
  In `GA4 Admin -> Channel groups -> Reorder`, always drag **`AI Assistants & Answer Engines (Extended MENA)`** to **Position #1 or #2 (strictly ABOVE `Referral` and `Organic Search`)** before saving!
