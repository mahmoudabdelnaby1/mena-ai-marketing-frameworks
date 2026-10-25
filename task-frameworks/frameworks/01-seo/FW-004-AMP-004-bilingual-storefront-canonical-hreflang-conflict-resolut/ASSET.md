# FW-004: Bilingual Storefront Canonical & Hreflang Conflict Resolution Checklist (Salla, Zid & Custom MENA Stores)
## قائمة فحص وإصلاح تضارب `canonical` و`hreflang` في المتاجر ثنائية اللغة (العربية والإنجليزية)

- **Consolidated Contextual Child IDs (`MERGE_INTO_EXISTING`)**: `AMP-016`, `AMP-028`, `AMP-040`, `AMP-052`
- **Selected Artifact Type**: `CHECKLIST`
- **Intended Audience**: SEO Specialist, E-Commerce Manager, Content Strategist, Technical SEO Lead
- **Target Markets & Languages**: Egypt & GCC (`Saudi Arabia, UAE, Kuwait, Qatar, Bahrain, Oman`) — Bilingual Arabic (`Egyptian Ammiya`, `Saudi/Gulf Khaleeji`, `White MSA`) + English
- **Version**: `1.2` | **Last Reviewed**: `2026-10-25` | **Status**: `READY_FOR_REVIEW`

## 1. Plain-Language Promise & Why This Artifact Form Fits the Job

- **What You Can Make or Decide (EN)**: Detect and resolve cross-language canonical conflicts where `/en/` product pages canonicalize back to `/ar/` URLs while `hreflang` claims they are indexable alternates.
- **ما الذي يمكنك إنجازه أو حسمه بهذه الأداة (AR)**: كشف وإصلاح التضارب التقني حين تشير علامة `canonical` في الصفحات الإنجليزية (`/en/`) إلى الرابط العربي (`/ar/`) بينما تطلب علامات `hreflang` فهرستها.
- **Why `CHECKLIST` Fits This User Job (EN)**: Cross-language canonical contradiction is a binary HTML `<head>` defect (found on 6 out of 6 English-enabled Salla stores in VOCTOS's Oct 2026 audit); a technical CHECKLIST with exact HTML inspection and Cloudflare Worker/theme override patterns fixes it cleanly.
- **لماذا يناسب شكل `CHECKLIST` هذه المهمة (AR)**: تضارب الـ `canonical` بين اللغتين هو خلل برمجي محدد في ترويسة `<head>` (رُصد في 6 من أصل 6 متاجر سلة مفعلة للإنجليزية في فحص VOCTOS أكتوبر 2026)؛ وقائمة الفحص التقنية تتيح كشفه ومعالجته بدقة.

## 2. "Use It When" Trigger, Boundaries & Exact Inputs to Prepare

- **Use It When (EN)**: Use whenever enabling English (`/en/`) alongside Arabic (`/ar/`) on Salla, Zid, Shopify Markets, or WooCommerce WPML/Polylang in KSA, UAE, or Egypt.
- **متى تستخدم هذه الأداة (AR)**: تُستخدم عند تفعيل اللغة الإنجليزية (`/en/`) بجانب العربية (`/ar/`) على منصات سلة أو زد أو شوبيفاي أو ووكومرس في السعودية أو الإمارات أو مصر.
- **When NOT to Use It (EN)**: Do not enable `/en/` storefront routes if English titles and descriptions are not actually translated (`AMP-005`)—keep the store single-language Arabic until English copy is ready.
- **متى لا تستخدم هذه الأداة (AR)**: لا تقم بتفعيل مسار اللغة الإنجليزية (`/en/`) إذا لم تكن عناوين وأوصاف المنتجات مترجمة فعلياً (`AMP-005`)؛ أبقِ المتجر أحادي اللغة حتى تكتمل الترجمة.

### Exact Inputs to Prepare Before Starting (`المدخلات المطلوب تجهيزها`)
1. Sample pair of live Arabic and English product URLs (e.g., `https://store.sa/ar/p1` and `https://store.sa/en/p1`)
2. Raw HTML `<head>` source (fetched via `curl -s` or View Source, not rendered DOM alone)
3. Cloudflare DNS/Proxy access (if running a managed SaaS storefront that requires HTML edge rewriting)

### Privacy-Safe Data Handling (`ضوابط الخصوصية وحماية البيانات الشخصية PDPL`)
- **Strict PII Redaction Before Prompting**: Under Saudi PDPL (Art. 25), UAE Federal Decree-Law No. 45 of 2021, Qatar Law No. 13 of 2016, and Egypt Law No. 151 of 2020, **never paste raw customer names, unhashed mobile numbers (`+9665...` / `+201...`), email addresses, national IDs, or private WhatsApp transcripts into public/consumer LLM interfaces**. Use anonymized placeholders (`{first_name}`, `ORD_10045`) during prompt testing and restrict live customer data to zero-data-retention enterprise API endpoints or local deterministic scripts.

## 3. The Directly Usable Artifact (`الأداة التطبيقية الجاهزة للنسخ والتنفيذ`)

### Cross-Language Canonical & Hreflang Verification Checklist

#### 1. HTML `<head>` Diagnostic Commands
Run in terminal against any bilingual product pair:
```bash
curl -sL "https://example.sa/en/product-slug" | grep -iE 'rel="(canonical|alternate)"'
```

#### 2. Pass / Fail Rules Matrix
| HTML Element on `/en/product-slug` | Broken Pattern (Observed on 6/6 Salla `/en/` Stores) | Required Valid Pattern (`PASS`) |
| :--- | :--- | :--- |
| `<link rel="canonical">` | `href="https://example.sa/ar/product-slug"` (Points to Arabic!) | `href="https://example.sa/en/product-slug"` (Self-referencing `/en/` URL) |
| `<link rel="alternate" hreflang="ar-SA">` | `href="https://example.sa/ar/product-slug"` | `href="https://example.sa/ar/product-slug"` |
| `<link rel="alternate" hreflang="en-SA">` | `href="https://example.sa/en/product-slug"` | `href="https://example.sa/en/product-slug"` |
| `<link rel="alternate" hreflang="x-default">` | Missing or conflicting | `href="https://example.sa/ar/product-slug"` (or language selector root) |

#### 3. Remediation Workflow by Platform
- [ ] **Custom / Shopify / WooCommerce**: Configure WPML / Polylang / Shopify Markets so every translated locale outputs a **self-referencing canonical** matching its own `hreflang` URL.
- [ ] **Salla Managed Storefront (Edge Fix via Cloudflare HTMLRewriter)**:
  If your Salla store's `/en/` route outputs a canonical pointing to the Arabic URL and your domain is proxied through Cloudflare, deploy this `HTMLRewriter` Worker rule on `/en/*` routes:
```javascript
class CanonicalFixer {
  constructor(requestUrl) { this.requestUrl = requestUrl; }
  element(el) {
    if (el.getAttribute('rel') === 'canonical') {
      const cleanUrl = new URL(this.requestUrl);
      cleanUrl.search = ''; // Strip tracking query params
      el.setAttribute('href', cleanUrl.toString());
    }
  }
}
```
- [ ] **Fallback if Cloudflare Worker is Not Used**: If `/en/` pages are untranslated or you do not target English search traffic in KSA, disable the secondary language toggle so Google does not crawl contradictory `/en/` duplicates.

## 4. Model & Platform Capability Branches (`فروع قدرات النماذج والمنصات والبدائل الاحتياطية`)

| System / Platform | Capability Status | Official Documentation & Access Date | Operational Constraint in Egypt & GCC | Fallback When Feature/Modality Is Unavailable |
| :--- | :--- | :--- | :--- | :--- |
| **Salla Bilingual `/en/` Canonical Output** | `plan/region dependent` | [Official Reference](https://voctos.net/salla-zid-store-seo-audit/) (`2026-10-25`) | VOCTOS Oct 2026 audit documented that 6 of 6 English-enabled Salla stores pointed the English page canonical back to the Arabic URL. | Use Cloudflare `HTMLRewriter` at the DNS edge to rewrite `/en/*` canonicals, or disable `/en/` if English SEO is not actively maintained. |

## 5. Consolidated Regional & Vertical Adaptation Matrix (`دمج الأنماط السياقية الفرعية بدون حشو`)

Per Agent 2 v1.2's anti-padding rule, the following **4 cross-verified contextual synthesis patterns** and **0 screened duplicate variants** share this core mechanism and are consolidated directly into this source-of-truth framework:

| Child Pattern ID | Disposition | Regional / Sector Operating Context | Specific Adaptation & Guardrail Integrated in This Asset | Evidence Tier |
| :--- | :--- | :--- | :--- | :--- |
| **`AMP-016`** | `MERGE_INTO_EXISTING` | Egyptian E-Commerce & Social Commerce (Shopify / WooCommerce / Cairo & Alexandria) | Applies specifically to multi-language storefront configurations where canonicals default to the primary language URL.; Specifically impacts Egyptian brands operating in EGP where merchant-specific payment mix from recent order records, Mobile Wallets (Vodafone Cash), InstaPay, and Fawry dominate. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-028`** | `MERGE_INTO_EXISTING` | UAE & Multi-Market GCC Enterprise / Retail (Dubai, Abu Dhabi, Doha, Kuwait) | Applies specifically to multi-language storefront configurations where canonicals default to the primary language URL.; Specifically impacts bilingual Arabic/English campaigns in high-CPM, expat-dense Gulf markets under UAE PDPL / TDRA and Qatari regulations. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-040`** | `MERGE_INTO_EXISTING` | High-Trust & Regulated Verticals (Healthcare/SFDA/EDA, Fintech/SAMA/FRA, Real Estate) | Applies specifically to multi-language storefront configurations where canonicals default to the primary language URL.; Specifically impacts regulated claims requiring SFDA, EDA, MOH, SAMA, FRA, or RERA compliance pre-clearance and strict hallucination guardrails. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-052`** | `MERGE_INTO_EXISTING` | Seasonal Peak Operations (Ramadan, Eid, White/Yellow Friday, Saudi Founding/National Day) | Applies specifically to multi-language storefront configurations where canonicals default to the primary language URL.; Specifically impacts high-velocity seasonal surges where CPMs jump 40-70%, prices change rapidly, and Hijri calendar cultural sensitivity is paramount. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |

### Context-Specific Execution Knobs Across the 5 MENA Operating Environments
1. **Saudi D2C E-Commerce (`Salla / Zid / Riyadh & Jeddah Retail`)**: Enforce `SAR` tax-inclusive pricing (`15% ZATCA VAT`), native `Mada / Apple Pay / Tabby / Tamara` visibility (`AMP-387`), `GAMR Mawthooq` creator verification (`AMP-281`), and White Saudi Khaleeji orthography (`AMP-002`, `AMP-177`).
2. **Egyptian E-Commerce & Social Commerce (`Shopify / WooCommerce / Cairo & Alexandria`)**: Use each merchant’s own order and payment data to assess Cash on Delivery (`COD`), mobile wallets, InstaPay, Fawry, `valU`, address fields, and pre-dispatch WhatsApp confirmation. Verify current provider terms and local requirements before implementation.
3. **UAE & Multi-Market GCC Enterprise / Retail (`Dubai, Abu Dhabi, Doha, Kuwait`)**: Separate high-CPM UAE/Qatar budgets from lower-CPM markets (`AMP-061`), enforce UAE `TDRA` `9 PM – 7 AM` SMS curfew + `AD-` prefix (`AMP-442`), UAE Media Council permits (`AMP-282`), and bilingual Arabic/English canonical & currency parity (`current applicable UAE VAT`, `current applicable Qatar/Kuwait tax rules`, 3-decimal `KWD` `AMP-239`).
4. **High-Trust & Regulated Verticals (`Healthcare SFDA/MOH/EDA, FinTech SAMA/FRA, Real Estate REGA/RERA`)**: Strip all therapeutic/cure verbs (`AMP-176`, `AMP-286`), display mandatory `MOH/SFDA/DHA/EDA/Fal/Trakheesi` permit numbers (`AMP-070`), and route budgets to high-credibility channels (`AMP-290`, `AMP-339`).
5. **Seasonal Peak Operations (`Ramadan, Eid, White/Yellow Friday, Saudi Founding/National Day`)**: Lock Hijri-Gregorian overlaps (`Feb 2027 Ramadan x Saudi Founding Day x Kuwait National Day` `AMP-125`), pre-schedule GMC `sale_price_effective_date` 48h ahead (`AMP-063`), verify 30-day baseline discount permits (`AMP-064`), and disable Meta Advantage+ auto-music (`AMP-065`).

## 6. Worked Example Summary & Failure Recovery (`ملخص المثال التطبيقي وخطة الإنقاذ`)

*(Full step-by-step worked example with annotated human edits is also provided in `EXAMPLE.md`)*

- **Sample Input Brief**: - **Store**: Bilingual Saudi Specialty Coffee Store on Salla with custom domain `roaster-example.sa`.
- **Symptom**: Google Search Console reports `"Duplicate, Google chose different canonical than user"` for 100% of `/en/` product pages, so expat shoppers in Riyadh and Dubai searching in English cannot find the `/en/` pages.
- **Human Review & Key Edits Applied**: 1. **Verified Translation Completeness First (`AMP-005`)**: Confirmed that the 45 products had English titles and descriptions populated before fixing canonicals.
2. **Deployed Self-Referencing Canonical Rule**: Applied the Cloudflare `HTMLRewriter` canonical fix on `/en/*` paths and stripped `?utm_*` parameters from the canonical output.
- **Final Usable Output**: ```html
<!-- Corrected <head> output on https://roaster-example.sa/en/ethiopian-coffee-250g -->
<link rel="canonical" href="https://roaster-example.sa/en/ethiopian-coffee-250g" />
<link rel="alternate" hreflang="ar-SA" href="https://roaster-example.sa/ethiopian-coffee-250g" />
<link rel="alternate" hreflang="en-SA" href="https://roaster-example.sa/en/ethiopian-coffee-250g" />
<link rel="alternate" hreflang="x-default" href="https://roaster-example.sa/ethiopian-coffee-250g" />
```
- **What Can Go Wrong**: A team rewrites `<link rel="canonical">` using client-side JavaScript (`document.querySelector`) via Google Tag Manager; Googlebot reads the initial server HTML canonical before JS execution or treats conflicting signals as untrusted.
- **Correction & Fallback**: Always apply canonical tag fixes in server-side templates or at the CDN edge (`Cloudflare HTMLRewriter`), never via client-side GTM JavaScript injection.

## 7. Measurement Plan & Hypothesis Framing (`خطة القياس والضوابط الإحصائية`)

- **Primary Metric to Track**: Count of `/en/` URLs indexed in Google Search Console (`Valid / Indexed` vs `Duplicate, Google chose different canonical`).
- **Baseline Definition**: Number of indexed `/en/` URLs prior to canonical fix.
- **Observation Window**: 21–28 days after requesting validation in GSC. *(Must span full 7/14-day weekly cycles and account for 25th–30th monthly salary windows per `AMP-391`)*.
- **What Cannot Be Concluded (Boundary)**: Fixing canonicals enables `/en/` indexing, but pages still require English `<title>` tags (`AMP-005`) and English body copy to rank for English queries.
