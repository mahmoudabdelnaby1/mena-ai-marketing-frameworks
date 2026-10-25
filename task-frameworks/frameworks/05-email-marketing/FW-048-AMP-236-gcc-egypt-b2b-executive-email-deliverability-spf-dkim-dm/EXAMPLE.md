# End-to-End Worked Example & Failure Recovery — `FW-048` (`AMP-236`)

- **Framework**: GCC & Egypt B2B Executive Email Deliverability (SPF/DKIM/DMARC) & Bilingual Conciseness Checklist
- **العنوان بالعربية**: قائمة فحص موثوقية نطاق البريد (`SPF/DKIM/DMARC`) وهيكلة رسائل الشركات (`B2B`) ثنائية اللغة في الخليج ومصر
- **Selected Artifact Type**: `CHECKLIST`
- **Disclaimer**: *All scenarios, brand names, SKU codes, and metrics below are original, realistic illustrative examples for MENA practitioner training and are never represented as verified client outcomes.*

## 1. Realistic Sample Brief / Input (`المدخلات وموجز الحالة العملية`)

- **Sender**: Riyadh & Dubai Enterprise Cybersecurity & Cloud Compliance Provider sending follow-ups to 450 opted-in LEAP / GITEX booth visitors.
- **Problem**: Previous AI sequence sent a 420-word English-only essay with 6 links and 2 PDF attachments from a domain missing `_dmarc`; Microsoft Defender 365 routed `71%` of emails to Quarantine/Junk at Saudi & Emirati enterprise banks.

## 2. Initial Generated / Completed Output (`المخرج الأولي عند تطبيق الأداة`)

- **DNS Audit & Fix**: Published 2048-bit DKIM + `_dmarc` (`p=quarantine`) on dedicated sending subdomain `updates.cyber-example.sa`, removed PDF attachments (replaced with 1 tracked first-party link), and compressed the message into a `68-word` Arabic + `54-word` English executive note.

## 3. Human Review & Localization/Technical Edits (`المراجعة البشرية والتعديلات الرقابية والتقنية`)

1. **Workweek Timing Check (`AMP-391`)**: Scheduled sends for **Monday–Wednesday at `10:00 AM` local Riyadh/Dubai time** (avoiding Friday/Saturday weekend and Sunday morning inbox backlog).
2. **RTL Alignment on Bilingual Block**: Wrapped the top Arabic paragraph in `<div dir="rtl" style="direction:rtl; text-align:right;">` and the bottom English summary in `<div dir="ltr" style="direction:ltr; text-align:left;">` (`AMP-231`).

## 4. Final Reviewed Example Outcome (`النتيجة النهائية الجاهزة للتنفيذ`)

- Enterprise inbox placement rose from `29%` to `96.4%`, with positive executive reply rate increasing across both Arabic-first (KSA government/enterprise) and English-first (UAE multinational) recipients.

## 5. What Can Go Wrong & Specific Correction / Fallback (`حالة الفشل المحتملة وخطة الإنقاذ والبديل`)

- **Common Failure Mode (`ما الذي قد يسير بشكل خاطئ؟`)**:
  An AI outreach tool inserts 4 different tracking links, a Calendly iframe, and an external image signature into a B2B follow-up email; corporate Barracuda/Mimecast gateways at Saudi and Emirati enterprises block the email for high link-to-text ratio.
- **Specific Correction & Non-AI / Platform Fallback (`الإصلاح المحدد والبديل الآمن`)**:
  Keep executive B2B follow-up emails to **plain-text-style minimal HTML (`<= 1` link total, `0` heavy image banners, `< 90` words per language)** and ask for a direct calendar reply (`'هل يناسبكم يوم الثلاثاء الساعة 11 صباحاً؟'`).
