# FW-008: Arabic URL Slug Architecture & Percent-Encoding Length Decision Aid
## أداة القرار المعماري لروابط صفحات الويب العربية (`URL Slugs`) ومنع انفجار الترميز المئوي (`%D8%`)

- **Consolidated Contextual Child IDs (`MERGE_INTO_EXISTING`)**: `AMP-020`, `AMP-032`, `AMP-044`, `AMP-056`
- **Selected Artifact Type**: `DECISION_AID`
- **Intended Audience**: SEO Specialist, E-Commerce Manager, Content Strategist, Technical SEO Lead
- **Target Markets & Languages**: Egypt & GCC (`Saudi Arabia, UAE, Kuwait, Qatar, Bahrain, Oman`) — Bilingual Arabic (`Egyptian Ammiya`, `Saudi/Gulf Khaleeji`, `White MSA`) + English
- **Version**: `1.2` | **Last Reviewed**: `2026-10-25` | **Status**: `READY_FOR_REVIEW`

## 1. Plain-Language Promise & Why This Artifact Form Fits the Job

- **What You Can Make or Decide (EN)**: Choose and enforce a URL slug convention that prevents 6x UTF-8 percent-encoding expansion from breaking WordPress's 200-char database limit and GA4's 420-char `page_location` cap.
- **ما الذي يمكنك إنجازه أو حسمه بهذه الأداة (AR)**: اختيار وتطبيق معمارية روابط (`URL Slugs`) تمنع تضخم الحروف العربية بالترميز المئوي (6 أضعاف) من كسر حد ووردبريس (200 حرف) وحد GA4 البالغ 420 حرفاً.
- **Why `DECISION_AID` Fits This User Job (EN)**: Choosing between ASCII English slugs under `/ar/`, transliterated slugs, or ultra-short 3-word Arabic slugs is an architectural decision with hard byte thresholds (200 chars in WordPress `post_name`, 420 chars in GA4 `page_location`); a quantitative DECISION_AID makes the threshold math unmistakable.
- **لماذا يناسب شكل `DECISION_AID` هذه المهمة (AR)**: المفاضلة بين الروابط الإنجليزية النظيفة تحت `/ar/` أو الروابط العربية القصيرة جداً هي قرار معماري تحكمه حدود تقنية صارمة (200 حرف في قاعدة بيانات ووردبريس و420 حرفاً في GA4)؛ لذا فإن أداة القرار الرقمية تحسم الاختيار بدقة.

## 2. "Use It When" Trigger, Boundaries & Exact Inputs to Prepare

- **Use It When (EN)**: Use when launching a new Arabic/bilingual website, migrating a store, or configuring AI blog/product publishing pipelines in WordPress, Shopify, Salla, Zid, or Next.js.
- **متى تستخدم هذه الأداة (AR)**: تُستخدم عند إطلاق موقع عربي أو ثنائي اللغة، أو ترحيل متجر، أو ضبط أنابيب النشر الآلي بالذكاء الاصطناعي على ووردبريس أو شوبيفاي أو سلة أو زد.
- **When NOT to Use It (EN)**: Do not bulk-change URL slugs on existing high-ranking Arabic pages without a 1:1 `301` redirect map and canonical update—only rewrite existing slugs if they are actively truncated or broken.
- **متى لا تستخدم هذه الأداة (AR)**: لا تقم بتغيير روابط الصفحات العربية المتصدرة حالياً بشكل جماعي دون خريطة تحويل `301` دقيقة؛ طبّق القاعدة فوراً على الصفحات الجديدة أو الروابط المعطوبة فقط.

### Exact Inputs to Prepare Before Starting (`المدخلات المطلوب تجهيزها`)
1. CMS / E-Commerce platform (`WordPress/WooCommerce`, `Salla`, `Zid`, `Shopify`, `Custom Next.js`)
2. Average query parameter length appended by paid ads (`?utm_source=...&fbclid=...&gclid=...`, typically 120–180 ASCII chars)
3. Target page title in Arabic and English

### Privacy-Safe Data Handling (`ضوابط الخصوصية وحماية البيانات الشخصية PDPL`)
- **Strict PII Redaction Before Prompting**: Under Saudi PDPL (Art. 25), UAE Federal Decree-Law No. 45 of 2021, Qatar Law No. 13 of 2016, and Egypt Law No. 151 of 2020, **never paste raw customer names, unhashed mobile numbers (`+9665...` / `+201...`), email addresses, national IDs, or private WhatsApp transcripts into public/consumer LLM interfaces**. Use anonymized placeholders (`{first_name}`, `ORD_10045`) during prompt testing and restrict live customer data to zero-data-retention enterprise API endpoints or local deterministic scripts.

## 3. The Directly Usable Artifact (`الأداة التطبيقية الجاهزة للنسخ والتنفيذ`)

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

## 4. Model & Platform Capability Branches (`فروع قدرات النماذج والمنصات والبدائل الاحتياطية`)

| System / Platform | Capability Status | Official Documentation & Access Date | Operational Constraint in Egypt & GCC | Fallback When Feature/Modality Is Unavailable |
| :--- | :--- | :--- | :--- | :--- |
| **WordPress `post_name` (200 chars) & GA4 `page_location` (420 chars)** | `supported` | [Official Reference](https://voctos.net/arabic-url-slugs-seo/) (`2026-10-25`) | VOCTOS 2026 audit of 24 Arab websites found 72% exceeded 300 encoded chars and 13/16 bilingual brands use clean English slugs under `/ar/`. | Enforce `validate_mena_slug()` before publishing any URL. |

## 5. Consolidated Regional & Vertical Adaptation Matrix (`دمج الأنماط السياقية الفرعية بدون حشو`)

Per Agent 2 v1.2's anti-padding rule, the following **4 cross-verified contextual synthesis patterns** and **1 screened duplicate variants** share this core mechanism and are consolidated directly into this source-of-truth framework:

| Child Pattern ID | Disposition | Regional / Sector Operating Context | Specific Adaptation & Guardrail Integrated in This Asset | Evidence Tier |
| :--- | :--- | :--- | :--- | :--- |
| **`AMP-020`** | `MERGE_INTO_EXISTING` | Egyptian E-Commerce & Social Commerce (Shopify / WooCommerce / Cairo & Alexandria) | Short 3-to-4 word hand-crafted Arabic slugs or clean English slugs under /ar/ folders stay well below truncation limits.; Specifically impacts Egyptian brands operating in EGP where merchant-specific payment mix from recent order records, Mobile Wallets (Vodafone Cash), InstaPay, and Fawry dominate. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-032`** | `MERGE_INTO_EXISTING` | UAE & Multi-Market GCC Enterprise / Retail (Dubai, Abu Dhabi, Doha, Kuwait) | Short 3-to-4 word hand-crafted Arabic slugs or clean English slugs under /ar/ folders stay well below truncation limits.; Specifically impacts bilingual Arabic/English campaigns in high-CPM, expat-dense Gulf markets under UAE PDPL / TDRA and Qatari regulations. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-044`** | `MERGE_INTO_EXISTING` | High-Trust & Regulated Verticals (Healthcare/SFDA/EDA, Fintech/SAMA/FRA, Real Estate) | Short 3-to-4 word hand-crafted Arabic slugs or clean English slugs under /ar/ folders stay well below truncation limits.; Specifically impacts regulated claims requiring SFDA, EDA, MOH, SAMA, FRA, or RERA compliance pre-clearance and strict hallucination guardrails. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-056`** | `MERGE_INTO_EXISTING` | Seasonal Peak Operations (Ramadan, Eid, White/Yellow Friday, Saudi Founding/National Day) | Short 3-to-4 word hand-crafted Arabic slugs or clean English slugs under /ar/ folders stay well below truncation limits.; Specifically impacts high-velocity seasonal surges where CPMs jump 40-70%, prices change rapidly, and Hijri calendar cultural sensitivity is paramount. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-506`** | `REJECT_DUPLICATE` | Screened UI/Format Synonym (`Merged Variant: Minor UI/Format Synonym of AMP-056 (Search Engine Optimization (SEO))`) | Consolidated into parent workflow without duplicate file inflation. | `SCREENED_DUPLICATE_VARIANT` |

### Context-Specific Execution Knobs Across the 5 MENA Operating Environments
1. **Saudi D2C E-Commerce (`Salla / Zid / Riyadh & Jeddah Retail`)**: Enforce `SAR` tax-inclusive pricing (`15% ZATCA VAT`), native `Mada / Apple Pay / Tabby / Tamara` visibility (`AMP-387`), `GAMR Mawthooq` creator verification (`AMP-281`), and White Saudi Khaleeji orthography (`AMP-002`, `AMP-177`).
2. **Egyptian E-Commerce & Social Commerce (`Shopify / WooCommerce / Cairo & Alexandria`)**: Use each merchant’s own order and payment data to assess Cash on Delivery (`COD`), mobile wallets, InstaPay, Fawry, `valU`, address fields, and pre-dispatch WhatsApp confirmation. Verify current provider terms and local requirements before implementation.
3. **UAE & Multi-Market GCC Enterprise / Retail (`Dubai, Abu Dhabi, Doha, Kuwait`)**: Separate high-CPM UAE/Qatar budgets from lower-CPM markets (`AMP-061`), enforce UAE `TDRA` `9 PM – 7 AM` SMS curfew + `AD-` prefix (`AMP-442`), UAE Media Council permits (`AMP-282`), and bilingual Arabic/English canonical & currency parity (`current applicable UAE VAT`, `current applicable Qatar/Kuwait tax rules`, 3-decimal `KWD` `AMP-239`).
4. **High-Trust & Regulated Verticals (`Healthcare SFDA/MOH/EDA, FinTech SAMA/FRA, Real Estate REGA/RERA`)**: Strip all therapeutic/cure verbs (`AMP-176`, `AMP-286`), display mandatory `MOH/SFDA/DHA/EDA/Fal/Trakheesi` permit numbers (`AMP-070`), and route budgets to high-credibility channels (`AMP-290`, `AMP-339`).
5. **Seasonal Peak Operations (`Ramadan, Eid, White/Yellow Friday, Saudi Founding/National Day`)**: Lock Hijri-Gregorian overlaps (`Feb 2027 Ramadan x Saudi Founding Day x Kuwait National Day` `AMP-125`), pre-schedule GMC `sale_price_effective_date` 48h ahead (`AMP-063`), verify 30-day baseline discount permits (`AMP-064`), and disable Meta Advantage+ auto-music (`AMP-065`).

## 6. Worked Example Summary & Failure Recovery (`ملخص المثال التطبيقي وخطة الإنقاذ`)

*(Full step-by-step worked example with annotated human edits is also provided in `EXAMPLE.md`)*

- **Sample Input Brief**: - **CMS**: WordPress + WooCommerce (Cairo & Riyadh E-Commerce blog).
- **AI-Generated Draft Slug**: `أفضل-فرشاة-حرارية-لاسلكية-لفرد-الشعر-في-السعودية-ومصر-بالتقسيط` (`62` visible chars).
- **Human Review & Key Edits Applied**: 1. **Selected Scenario A (Clean ASCII under `/ar/`)**: Changed the slug to `/ar/cordless-hair-straightener-brush` (`32` ASCII chars) while keeping the Arabic `<title>` and `<h1>` 100% localized.
2. **Provided Scenario B Alternative**: For teams requiring Arabic script in the URL, shortened to 3 words: `/ar/فرشاة-شعر-لاسلكية` (`17` visible chars = `92` encoded chars, passing both WordPress and GA4 gates).
- **Final Usable Output**: - **Production URL**: `https://example.sa/ar/cordless-hair-straightener-brush`
- `encoded_slug_len`: `32` chars (`PASS <= 190`)
- `ga4_projected_len_with_utms`: `215` chars (`PASS <= 420`)
- **What Can Go Wrong**: An AI auto-blogger plugin sets the WordPress slug directly from the full 12-word Arabic article title; WordPress truncates `post_name` at byte 200, producing a malformed trailing `%D8` byte that causes `400 Bad Request` or infinite redirect loops on Nginx/Apache.
- **Correction & Fallback**: Configure the publishing script to generate a dedicated 3–5 word English ASCII slug (`slug_ascii`) or a max-3-word Arabic root slug (`<= 25` chars) instead of copying `post_title`.

## 7. Measurement Plan & Hypothesis Framing (`خطة القياس والضوابط الإحصائية`)

- **Primary Metric to Track**: Percentage of site URLs under 250 encoded characters (allowing 170 chars for UTMs/click IDs within GA4's 420-char limit) and zero truncated `utm_campaign` values in GA4.
- **Baseline Definition**: Current count of truncated `page_location` strings in GA4 exploration reports.
- **Observation Window**: 7–14 days post-implementation on new pages. *(Must span full 7/14-day weekly cycles and account for 25th–30th monthly salary windows per `AMP-391`)*.
- **What Cannot Be Concluded (Boundary)**: URL slug cleanliness prevents analytics truncation and WordPress DB clipping, but on-page relevance still comes from `<title>`, `<h1>`, and body copy.
