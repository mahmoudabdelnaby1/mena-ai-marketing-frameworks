# Zid & MENA Storefront `robots.txt` Sitemap Directive & AI-Crawler Governance Checklist
## <span dir="rtl">قائمة فحص ملف `robots.txt` وإعلان `Sitemap:` وضبط زواحف الذكاء الاصطناعي في متاجر زد والمنطقة</span>

> **Asset ID**: `FW-006` (`AMP-006`) | **Artifact Type**: `CHECKLIST` | **Channel**: Search Engine Optimization (SEO) | **Markets**: Egypt & GCC (`KSA, UAE, Kuwait, Qatar, Bahrain, Oman`) | **Version**: `1.2` (`Reviewed 2026-10-25`)

**What You Can Do With This (`ماذا يمكنك أن تنجز بهذه الأداة؟`)**:
- **EN**: Verify `Sitemap:` directive presence and intentional AI-crawler rules (`GPTBot`, `ClaudeBot`, `Google-Extended`, `PerplexityBot`) in storefront `robots.txt` files.
- **AR**: <span dir="rtl">التحقق من وجود سطر `Sitemap:` في ملف `robots.txt` وضبط صلاحيات زواحف الذكاء الاصطناعي (`GPTBot`، `ClaudeBot`، `Google-Extended`) بوعي.</span>

## 1. Use It When & Required Inputs (`متى تستخدمها وما المدخلات المطلوبة؟`)

- **Use It When (EN)**: Use during technical SEO onboarding for any Zid, Salla, Shopify, or WooCommerce store in KSA, UAE, or Egypt.
- **متى تستخدمها (AR)**: <span dir="rtl">تُستخدم عند التهيئة التقنية للـ SEO لأي متجر على زد أو سلة أو شوبيفاي أو ووكومرس في السعودية أو الإمارات أو مصر.</span>
- **When NOT to Use It (EN)**: Do not assume blocking `Google-Extended` blocks Google Search indexing—`Googlebot` controls Search & AI Overviews indexing, while `Google-Extended` controls Gemini training/grounding.
- **متى لا تستخدمها (AR)**: <span dir="rtl">لا تفترض أن حظر `Google-Extended` يمنع أرشفة المتجر في بحث جوجل؛ فزاحف `Googlebot` هو المسؤول عن البحث وAI Overviews.</span>

### Exact Inputs to Prepare (`المدخلات المطلوب تجهيزها قبل البدء`)
- Live `https://store-domain.com/robots.txt` output
- Verified `sitemap.xml` URL (`200 OK`)
- Google Search Console & Bing Webmaster Tools property access

## 2. The Working `CHECKLIST` (`الأداة الكاملة الجاهزة للنسخ والتطبيق الفوري`)

### `robots.txt` & Sitemap Discovery Checklist

#### 1. Instant Terminal Diagnostic
```bash
curl -sL "https://your-store.sa/robots.txt" | grep -iE "^(Sitemap|User-agent|Disallow):" | tail -n 30
```

#### 2. Verification & Action Checklist
- [ ] **Check 1 — `Sitemap:` Directive Presence**:
  - Run `curl -sL https://your-store.sa/robots.txt | grep -i '^Sitemap:'`.
  - **If Missing (Observed on 9/10 Zid stores)**:
    1. Submit `https://your-store.sa/sitemap.xml` manually inside **Google Search Console -> Sitemaps** AND **Bing Webmaster Tools -> Sitemaps** (critical because ChatGPT Search relies heavily on Bing's index alongside `OAI-SearchBot`).
    2. If `robots.txt` is editable (or routed via Cloudflare Worker on custom domain), append `Sitemap: https://your-store.sa/sitemap.xml` at the bottom of `robots.txt`.
- [ ] **Check 2 — Verify Actual AI Crawler Rules (Do Not Guess)**:
  - Check explicit rules for:
    - `Googlebot` (Google Search + AI Overviews)
    - `OAI-SearchBot` & `ChatGPT-User` (ChatGPT Search citations)
    - `GPTBot` (OpenAI model training)
    - `ClaudeBot` / `Claude-SearchBot` (Anthropic)
    - `PerplexityBot` (Perplexity AI)
  - *Empirical Note*: Zid's 1,268-line default `robots.txt` (observed on 8/10 Zid stores in Oct 2026) blocks 627 scrapers and `PetalBot`, but **allows** `GPTBot`, `ClaudeBot`, and `Google-Extended`. Always inspect the live file rather than assuming a platform blocks AI bots.
- [ ] **Check 3 — Verify Cart/Checkout Disallows Do Not Block JS/CSS Assets**:
  - Confirm `/cart`, `/checkout`, and internal unnormalized search result URLs (`/?q=*` or `/search*`) are disallowed to save crawl budget, while `/assets/`, `/*.js`, and `/*.css` remain allowed for Googlebot mobile rendering.

## 3. Complete End-to-End Worked Example (`مثال تطبيقي متكامل من المدخلات حتى المراجعة البشرية والنتيجة النهائية`)

*(Illustrative scenario — original example for training, never represented as a verified client outcome)*

### Step A: Sample Brief / Input (`موجز المدخلات`)
- **Store**: Saudi Electronics & Accessories Store on Zid (`https://tech-example.sa`).
- **Diagnostic Output**: `robots.txt` is 1,268 lines long, contains `0` `Sitemap:` lines, blocks `PetalBot`, and allows `Googlebot`, `GPTBot`, and `ClaudeBot`.

### Step B: Initial Output (`المخرج الأولي`)
- `grep -i '^Sitemap:' robots.txt` -> **(Empty / 0 matches)**
- Bing Webmaster Tools status -> **No Sitemap Submitted (340 new SKUs undiscovered by Bing / ChatGPT Search)**

### Step C: Human Review & Edits (`التدقيق البشري والتعديلات`)
1. **Manual Sitemap Registration**: Submitted `https://tech-example.sa/sitemap.xml` directly in both Google Search Console and Bing Webmaster Tools.
2. **Cloudflare Edge Append**: Added a lightweight Cloudflare Worker rule on `/robots.txt` appending `\nSitemap: https://tech-example.sa/sitemap.xml\n` so all compliant crawlers discover the sitemap automatically.

### Step D: Final Reviewed Example Outcome (`النتيجة النهائية المعتمدة`)
```text
# Appended to https://tech-example.sa/robots.txt via Edge / Platform Settings
Sitemap: https://tech-example.sa/sitemap.xml
```
- Verified `200 OK` and `Sitemap:` line readable by `Googlebot`, `Bingbot`, and `OAI-SearchBot`.

## 4. What Can Go Wrong & How to Fix It (`الأخطاء الشائعة وخطة الإنقاذ`)

- **Failure Case (`المشكلة المحتملة`)**: An agency tells a Zid merchant 'your store is invisible in ChatGPT because Zid blocks GPTBot in robots.txt' without reading the file, wasting engineering hours on a falsified assumption (`AMP-565`).
- **Correction & Fallback (`الحل الإجرائي والبديل الآمن`)**: Always run `curl -s https://domain/robots.txt | grep -i -A 3 'GPTBot'` first; in 8 of 10 Zid stores audited by VOCTOS (Oct 2026), `GPTBot` is allowed and the actual gap was missing `Sitemap:` registration in Bing/GSC.

## 5. Model & Platform Capability Matrix (`مصفوفة قدرات النماذج والمنصات — 2026-10-25`)

| Platform / Model | Status | Official Documentation | MENA Operational Constraint | Fallback |
| :--- | :--- | :--- | :--- | :--- |
| **Zid Default `robots.txt` Template** | `supported` | [Official Docs](https://voctos.net/salla-zid-store-seo-audit/) (`2026-10-25`) | 9 of 10 audited Zid stores omitted the `Sitemap:` directive in `robots.txt`, while 10 of 10 Salla stores included it. | Submit `sitemap.xml` directly in GSC and Bing Webmaster Tools, or append `Sitemap:` via Cloudflare on custom domains. |

## 6. How to Measure Success (`خطة القياس والضوابط`)

- **Primary Metric**: Time-to-discovery of newly published product URLs in Google Search Console & Bing Webmaster Tools.
- **Baseline**: Pre-fix crawl discovery latency for new SKUs.
- **Observation Window**: 14 days after sitemap submission.
- **Interpretation Boundary**: Adding `Sitemap:` ensures crawlers find URLs, but does not override `noindex` tags or poor content quality.

## 7. Primary Sources & Evidence Boundaries (`المصادر الموثقة وحدود الأدلة`)

- [تحسين محركات البحث للمتاجر الإلكترونية | زد المدونة](https://zid.sa/ar/blog/%D8%AA%D8%AD%D8%B3%D9%8A%D9%86-%D9%85%D8%AD%D8%B1%D9%83%D8%A7%D8%AA_%D8%A7%D9%84%D8%A8%D8%AD%D8%AB/) — *Zid* (Published `2023-03-26`, Accessed `2026-10-25`): Outlines Zid's e-commerce SEO structure for product titles, meta descriptions, and category taxonomy.
- [We Audited 20 Salla and Zid Stores: The SEO Defaults Saudi Merchants Inherit (2026)](https://voctos.net/salla-zid-store-seo-audit/) — *VOCTOS* (Published `2026-10-08`, Accessed `2026-10-25`): Audit of 20 Saudi stores (10 Salla, 10 Zid): 60% of sampled Salla sitemap URLs (88/146) redirected or returned 410; 6/6 Salla English pages canonicalized to Arabic; 9/10 Zid stores lacked Sitemap in robots.txt; 0/10 Salla stores had Brand in Product JSON-LD; 8/11 English pages kept Arabic-script titles.
