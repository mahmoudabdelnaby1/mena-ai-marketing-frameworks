# End-to-End Worked Example & Failure Recovery — `FW-006` (`AMP-006`)

- **Framework**: Zid & MENA Storefront `robots.txt` Sitemap Directive & AI-Crawler Governance Checklist
- **العنوان بالعربية**: قائمة فحص ملف `robots.txt` وإعلان `Sitemap:` وضبط زواحف الذكاء الاصطناعي في متاجر زد والمنطقة
- **Selected Artifact Type**: `CHECKLIST`
- **Disclaimer**: *All scenarios, brand names, SKU codes, and metrics below are original, realistic illustrative examples for MENA practitioner training and are never represented as verified client outcomes.*

## 1. Realistic Sample Brief / Input (`المدخلات وموجز الحالة العملية`)

- **Store**: Saudi Electronics & Accessories Store on Zid (`https://tech-example.sa`).
- **Diagnostic Output**: `robots.txt` is 1,268 lines long, contains `0` `Sitemap:` lines, blocks `PetalBot`, and allows `Googlebot`, `GPTBot`, and `ClaudeBot`.

## 2. Initial Generated / Completed Output (`المخرج الأولي عند تطبيق الأداة`)

- `grep -i '^Sitemap:' robots.txt` -> **(Empty / 0 matches)**
- Bing Webmaster Tools status -> **No Sitemap Submitted (340 new SKUs undiscovered by Bing / ChatGPT Search)**

## 3. Human Review & Localization/Technical Edits (`المراجعة البشرية والتعديلات الرقابية والتقنية`)

1. **Manual Sitemap Registration**: Submitted `https://tech-example.sa/sitemap.xml` directly in both Google Search Console and Bing Webmaster Tools.
2. **Cloudflare Edge Append**: Added a lightweight Cloudflare Worker rule on `/robots.txt` appending `\nSitemap: https://tech-example.sa/sitemap.xml\n` so all compliant crawlers discover the sitemap automatically.

## 4. Final Reviewed Example Outcome (`النتيجة النهائية الجاهزة للتنفيذ`)

```text
# Appended to https://tech-example.sa/robots.txt via Edge / Platform Settings
Sitemap: https://tech-example.sa/sitemap.xml
```
- Verified `200 OK` and `Sitemap:` line readable by `Googlebot`, `Bingbot`, and `OAI-SearchBot`.

## 5. What Can Go Wrong & Specific Correction / Fallback (`حالة الفشل المحتملة وخطة الإنقاذ والبديل`)

- **Common Failure Mode (`ما الذي قد يسير بشكل خاطئ؟`)**:
  An agency tells a Zid merchant 'your store is invisible in ChatGPT because Zid blocks GPTBot in robots.txt' without reading the file, wasting engineering hours on a falsified assumption (`AMP-565`).
- **Specific Correction & Non-AI / Platform Fallback (`الإصلاح المحدد والبديل الآمن`)**:
  Always run `curl -s https://domain/robots.txt | grep -i -A 3 'GPTBot'` first; in 8 of 10 Zid stores audited by VOCTOS (Oct 2026), `GPTBot` is allowed and the actual gap was missing `Sitemap:` registration in Bing/GSC.
