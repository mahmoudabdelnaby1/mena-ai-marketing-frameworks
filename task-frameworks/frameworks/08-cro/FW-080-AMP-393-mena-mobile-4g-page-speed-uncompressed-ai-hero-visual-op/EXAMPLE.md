# End-to-End Worked Example & Failure Recovery — `FW-080` (`AMP-393`)

- **Framework**: MENA Mobile 4G Page-Speed & Uncompressed AI Hero Visual Optimization Checklist (`LCP < 2.5s`)
- **العنوان بالعربية**: قائمة فحص سرعة تحميل صفحات الجوال على شبكات `4G` وضغط الصور والفيديوهات المولدة بالذكاء الاصطناعي (`LCP < 2.5s`)
- **Selected Artifact Type**: `CHECKLIST`
- **Disclaimer**: *All scenarios, brand names, SKU codes, and metrics below are original, realistic illustrative examples for MENA practitioner training and are never represented as verified client outcomes.*

## 1. Realistic Sample Brief / Input (`المدخلات وموجز الحالة العملية`)

- **Landing Page**: Cairo & Riyadh White Friday Promotional Landing Page receiving `12,000` daily mobile clicks from Meta and TikTok ads.
- **Problem**: Designer uploaded 4 raw Midjourney `.png` banners (`5.2 MB` each = `20.8 MB` page weight!) and placed `loading="lazy"` on the main hero banner. Mobile 4G Largest Contentful Paint (`LCP`) was **`9.4 seconds`**, and **`44%` of paid ad clicks bounced before the page finished loading** (`GA4 Engaged Sessions / Ad Clicks = 56%`).

## 2. Initial Generated / Completed Output (`المخرج الأولي عند تطبيق الأداة`)

- **Executed Compression & Markup Fix**:
  1. Converted the 4 raw `.png` files (`20.8 MB` total) to responsive `800w` mobile `.webp` files totaling **`310 KB` (`98.5%` weight reduction!)**.
  2. Removed `loading="lazy"` from the Hero image and added `fetchpriority="high" width="800" height="1000"`.
  3. Dropped 4 unused weights of the `Cairo` font, keeping only `400` and `700` `.woff2` with `font-display: swap`.

## 3. Human Review & Localization/Technical Edits (`المراجعة البشرية والتعديلات الرقابية والتقنية`)

1. **Deferred Third-Party Tracking Pixels**: Moved non-essential heatmaps and chat widgets (`AMP-389`) to load after `window.onload` or `3.5s` interaction delay so they don't block the main thread during initial mobile paint.
2. **Verified Mobile 4G Throttled Test**: Tested on Chrome DevTools `Fast 4G / Slow 4G` throttling from Cairo and Riyadh test nodes.

## 4. Final Reviewed Example Outcome (`النتيجة النهائية الجاهزة للتنفيذ`)

- Mobile 4G `LCP` dropped from `9.4s` to **`1.8s`**, total page weight fell from `22.1 MB` to `640 KB`, and Ad-Click-to-Landing-Page View rate jumped from `56%` to **`89%`**.

## 5. What Can Go Wrong & Specific Correction / Fallback (`حالة الفشل المحتملة وخطة الإنقاذ والبديل`)

- **Common Failure Mode (`ما الذي قد يسير بشكل خاطئ؟`)**:
  An optimization plugin blindly adds `loading="lazy"` to **every** `<img>` tag on the page, including the #1 Hero Banner at the top of the screen; the browser delays fetching the hero image until layout completes, adding `1.2 seconds` of unnecessary penalty to `LCP`.
- **Specific Correction & Non-AI / Platform Fallback (`الإصلاح المحدد والبديل الآمن`)**:
  Enforce the **LCP Priority Rule**: the **first visible image above the fold** MUST have `fetchpriority="high"` and **NO `loading="lazy"`**, while all images below the fold (`Image #2 onwards`) get `loading="lazy"`.
