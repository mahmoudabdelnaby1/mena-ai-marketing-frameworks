# Arabic URL Slug Architecture & Percent-Encoding Length Decision Aid
## <span dir="rtl">أداة القرار المعماري لروابط صفحات الويب العربية (`URL Slugs`) ومنع انفجار الترميز المئوي (`%D8%`)</span>

> **Asset ID**: `FW-008` (`AMP-008`) | **Artifact Type**: `DECISION_AID` | **Channel**: Search Engine Optimization (SEO) | **Markets**: Egypt & GCC (`KSA, UAE, Kuwait, Qatar, Bahrain, Oman`) | **Version**: `1.2` (`Reviewed 2026-10-25`)

**What You Can Do With This (`ماذا يمكنك أن تنجز بهذه الأداة؟`)**:
- **EN**: Choose and enforce a URL slug convention that prevents 6x UTF-8 percent-encoding expansion from breaking WordPress's 200-char database limit and GA4's 420-char `page_location` cap.
- **AR**: <span dir="rtl">اختيار وتطبيق معمارية روابط (`URL Slugs`) تمنع تضخم الحروف العربية بالترميز المئوي (6 أضعاف) من كسر حد ووردبريس (200 حرف) وحد GA4 البالغ 420 حرفاً.</span>

## 1. Use It When & Required Inputs (`متى تستخدمها وما المدخلات المطلوبة؟`)

- **Use It When (EN)**: Use when launching a new Arabic/bilingual website, migrating a store, or configuring AI blog/product publishing pipelines in WordPress, Shopify, Salla, Zid, or Next.js.
- **متى تستخدمها (AR)**: <span dir="rtl">تُستخدم عند إطلاق موقع عربي أو ثنائي اللغة، أو ترحيل متجر، أو ضبط أنابيب النشر الآلي بالذكاء الاصطناعي على ووردبريس أو شوبيفاي أو سلة أو زد.</span>
- **When NOT to Use It (EN)**: Do not bulk-change URL slugs on existing high-ranking Arabic pages without a 1:1 `301` redirect map and canonical update—only rewrite existing slugs if they are actively truncated or broken.
- **متى لا تستخدمها (AR)**: <span dir="rtl">لا تقم بتغيير روابط الصفحات العربية المتصدرة حالياً بشكل جماعي دون خريطة تحويل `301` دقيقة؛ طبّق القاعدة فوراً على الصفحات الجديدة أو الروابط المعطوبة فقط.</span>

### Exact Inputs to Prepare (`المدخلات المطلوب تجهيزها قبل البدء`)
- CMS / E-Commerce platform (`WordPress/WooCommerce`, `Salla`, `Zid`, `Shopify`, `Custom Next.js`)
- Average query parameter length appended by paid ads (`?utm_source=...&fbclid=...&gclid=...`, typically 120–180 ASCII chars)
- Target page title in Arabic and English

## 2. The Working `DECISION_AID` (`الأداة الكاملة الجاهزة للنسخ والتطبيق الفوري`)

### URL Slug Percent-Encoding Math & Architecture Decision Matrix

#### 1. Why AI-Generated Arabic Slugs Break Analytics & Databases
Each Arabic letter takes **2 bytes in UTF-8** and expands to **6 ASCII characters** when percent-encoded (`ش` → `%D8%B4`):
- A 10-word AI-generated Arabic headline slug (`57` visible characters) expands to **`280–330+` encoded characters**.
- **WordPress / WooCommerce Hard Limit**: `wp_posts.post_name` is `VARCHAR(200)`. Any encoded Arabic slug >200 characters is **silently truncated mid-byte**, corrupting the URL and breaking links!
- **GA4 Hard Limit**: GA4 truncates `page_location` at **420 characters** (VOCTOS Oct 2026 audit: **72% of audited Arabic sites exceeded 300 characters** once UTM + `fbclid`/`gclid` parameters were added, cutting off attribution data!).

#### 2. Architectural Decision Matrix
| Store / Site Scenario | Recommended Slug Architecture | Max Slug Length Rule | Example URL | Why (Empirical Evidence) |
| :--- | :--- | :--- | :--- | :--- |
| **Scenario A: New Bilingual or Arabic Brand / Enterprise Site (`/ar/` + `/en/`)** | **Clean ASCII English Slug under `/ar/` subfolder** (`RECOMMENDED DEFAULT`) | `<= 50` ASCII chars (`3–6` English words) | `https://brand.sa/ar/cordless-hair-brush` | Adopted by **13 of 16 leading bilingual Arab brands** in VOCTOS's 2026 audit; `0` percent-encoding expansion, never clips in WhatsApp/X shares or GA4 `page_location`, and causes zero Google ranking penalty (`AMP-558`). |
| **Scenario B: Single-Language Arabic Site Requiring Arabic-Script Slugs** | **Ultra-Short 3-Word Root Arabic Slug** | **`<= 25` visible Arabic chars** (`3–4` words max; `<= 140` encoded chars) | `https://brand.sa/p/فرشاة-شعر-لاسلكية` | Keeps encoded slug under `150` chars, safely below WordPress's `200`-char `VARCHAR` cap and leaving `270` chars of headroom for UTM/`gclid` inside GA4's `420`-char limit. |
| **Scenario C: Legacy Site with Existing Ranking Long Arabic Slugs** | **Keep Indexed `200 OK` URLs + Enforce Rule A/B on All New Pages** | Do not break live rankings; fix only `404`/truncated WordPress slugs via `301` | Keep live `200 OK`; apply `<=25` chars or ASCII to new posts | Avoids unnecessary redirect chains while stopping new bloat. |

#### 3. Copy-Ready Python Slug Length Gate (Add to CMS / AI Publishing Script)
```python
import urllib.parse

def validate_mena_slug(base_domain: str, locale_prefix: str, raw_slug: str, utm_buffer: int = 160):
    encoded_slug = urllib.parse.quote(raw_slug.strip("/"), safe="-_")
    full_encoded_url = f"https://{base_domain.strip('/')}/{locale_prefix.strip('/')}/{encoded_slug}"
    wp_post_name_len = len(encoded_slug)
    ga4_projected_len = len(full_encoded_url) + utm_buffer
    return {
        "raw_slug": raw_slug,
        "encoded_slug_len": wp_post_name_len,
        "wordpress_200_limit_pass": wp_post_name_len <= 190,
        "ga4_420_limit_pass": ga4_projected_len <= 420,
        "ga4_projected_len_with_utms": ga4_projected_len,
        "recommendation": "PASS" if (wp_post_name_len <= 190 and ga4_projected_len <= 420) else "REJECT_TOO_LONG_USE_ASCII_OR_3_WORDS"
    }
```

## 3. Complete End-to-End Worked Example (`مثال تطبيقي متكامل من المدخلات حتى المراجعة البشرية والنتيجة النهائية`)

*(Illustrative scenario — original example for training, never represented as a verified client outcome)*

### Step A: Sample Brief / Input (`موجز المدخلات`)
- **CMS**: WordPress + WooCommerce (Cairo & Riyadh E-Commerce blog).
- **AI-Generated Draft Slug**: `أفضل-فرشاة-حرارية-لاسلكية-لفرد-الشعر-في-السعودية-ومصر-بالتقسيط` (`62` visible chars).

### Step B: Initial Output (`المخرج الأولي`)
- `validate_mena_slug("example.sa", "ar", "أفضل-فرشاة-حرارية-لاسلكية-لفرد-الشعر-في-السعودية-ومصر-بالتقسيط")`:
  - `encoded_slug_len`: **`328` chars** (`FAIL` — exceeds WordPress 200-char `post_name` limit by 128 chars; WordPress cuts it off mid-character!).
  - `ga4_projected_len_with_utms`: **`511` chars** (`FAIL` — exceeds GA4 420-char `page_location` limit, stripping `gclid` and `utm_campaign`!).

### Step C: Human Review & Edits (`التدقيق البشري والتعديلات`)
1. **Selected Scenario A (Clean ASCII under `/ar/`)**: Changed the slug to `/ar/cordless-hair-straightener-brush` (`32` ASCII chars) while keeping the Arabic `<title>` and `<h1>` 100% localized.
2. **Provided Scenario B Alternative**: For teams requiring Arabic script in the URL, shortened to 3 words: `/ar/فرشاة-شعر-لاسلكية` (`17` visible chars = `92` encoded chars, passing both WordPress and GA4 gates).

### Step D: Final Reviewed Example Outcome (`النتيجة النهائية المعتمدة`)
- **Production URL**: `https://example.sa/ar/cordless-hair-straightener-brush`
- `encoded_slug_len`: `32` chars (`PASS <= 190`)
- `ga4_projected_len_with_utms`: `215` chars (`PASS <= 420`)

## 4. What Can Go Wrong & How to Fix It (`الأخطاء الشائعة وخطة الإنقاذ`)

- **Failure Case (`المشكلة المحتملة`)**: An AI auto-blogger plugin sets the WordPress slug directly from the full 12-word Arabic article title; WordPress truncates `post_name` at byte 200, producing a malformed trailing `%D8` byte that causes `400 Bad Request` or infinite redirect loops on Nginx/Apache.
- **Correction & Fallback (`الحل الإجرائي والبديل الآمن`)**: Configure the publishing script to generate a dedicated 3–5 word English ASCII slug (`slug_ascii`) or a max-3-word Arabic root slug (`<= 25` chars) instead of copying `post_title`.

## 5. Model & Platform Capability Matrix (`مصفوفة قدرات النماذج والمنصات — 2026-10-25`)

| Platform / Model | Status | Official Documentation | MENA Operational Constraint | Fallback |
| :--- | :--- | :--- | :--- | :--- |
| **WordPress `post_name` (200 chars) & GA4 `page_location` (420 chars)** | `supported` | [Official Docs](https://voctos.net/arabic-url-slugs-seo/) (`2026-10-25`) | VOCTOS 2026 audit of 24 Arab websites found 72% exceeded 300 encoded chars and 13/16 bilingual brands use clean English slugs under `/ar/`. | Enforce `validate_mena_slug()` before publishing any URL. |

## 6. How to Measure Success (`خطة القياس والضوابط`)

- **Primary Metric**: Percentage of site URLs under 250 encoded characters (allowing 170 chars for UTMs/click IDs within GA4's 420-char limit) and zero truncated `utm_campaign` values in GA4.
- **Baseline**: Current count of truncated `page_location` strings in GA4 exploration reports.
- **Observation Window**: 7–14 days post-implementation on new pages.
- **Interpretation Boundary**: URL slug cleanliness prevents analytics truncation and WordPress DB clipping, but on-page relevance still comes from `<title>`, `<h1>`, and body copy.

## 7. Primary Sources & Evidence Boundaries (`المصادر الموثقة وحدود الأدلة`)

- [Arabic URL Slugs: What 24 Arab Websites Use](https://voctos.net/arabic-url-slugs-seo/) — *VOCTOS* (Published `2026-10-11`, Accessed `2026-10-25`): Each UTF-8 Arabic letter percent-encodes to 6 characters (%D8%..), expanding 82-char Arabic slugs to 235 chars on average; 72% exceed WordPress's 200-char post_name limit (truncating after ~6 words) and risk exceeding GA4's 420-char page_referrer limit.
- [We Audited 20 Salla and Zid Stores: The SEO Defaults Saudi Merchants Inherit (2026)](https://voctos.net/salla-zid-store-seo-audit/) — *VOCTOS* (Published `2026-10-08`, Accessed `2026-10-25`): Audit of 20 Saudi stores (10 Salla, 10 Zid): 60% of sampled Salla sitemap URLs (88/146) redirected or returned 410; 6/6 Salla English pages canonicalized to Arabic; 9/10 Zid stores lacked Sitemap in robots.txt; 0/10 Salla stores had Brand in Product JSON-LD; 8/11 English pages kept Arabic-script titles.
