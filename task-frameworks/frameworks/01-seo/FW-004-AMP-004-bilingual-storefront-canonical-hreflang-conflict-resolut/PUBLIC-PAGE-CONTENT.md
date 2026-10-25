# Bilingual Storefront Canonical & Hreflang Conflict Resolution Checklist (Salla, Zid & Custom MENA Stores)
## <span dir="rtl">قائمة فحص وإصلاح تضارب `canonical` و`hreflang` في المتاجر ثنائية اللغة (العربية والإنجليزية)</span>

> **Asset ID**: `FW-004` (`AMP-004`) | **Artifact Type**: `CHECKLIST` | **Channel**: Search Engine Optimization (SEO) | **Markets**: Egypt & GCC (`KSA, UAE, Kuwait, Qatar, Bahrain, Oman`) | **Version**: `1.2` (`Reviewed 2026-10-25`)

**What You Can Do With This (`ماذا يمكنك أن تنجز بهذه الأداة؟`)**:
- **EN**: Detect and resolve cross-language canonical conflicts where `/en/` product pages canonicalize back to `/ar/` URLs while `hreflang` claims they are indexable alternates.
- **AR**: <span dir="rtl">كشف وإصلاح التضارب التقني حين تشير علامة `canonical` في الصفحات الإنجليزية (`/en/`) إلى الرابط العربي (`/ar/`) بينما تطلب علامات `hreflang` فهرستها.</span>

## 1. Use It When & Required Inputs (`متى تستخدمها وما المدخلات المطلوبة؟`)

- **Use It When (EN)**: Use whenever enabling English (`/en/`) alongside Arabic (`/ar/`) on Salla, Zid, Shopify Markets, or WooCommerce WPML/Polylang in KSA, UAE, or Egypt.
- **متى تستخدمها (AR)**: <span dir="rtl">تُستخدم عند تفعيل اللغة الإنجليزية (`/en/`) بجانب العربية (`/ar/`) على منصات سلة أو زد أو شوبيفاي أو ووكومرس في السعودية أو الإمارات أو مصر.</span>
- **When NOT to Use It (EN)**: Do not enable `/en/` storefront routes if English titles and descriptions are not actually translated (`AMP-005`)—keep the store single-language Arabic until English copy is ready.
- **متى لا تستخدمها (AR)**: <span dir="rtl">لا تقم بتفعيل مسار اللغة الإنجليزية (`/en/`) إذا لم تكن عناوين وأوصاف المنتجات مترجمة فعلياً (`AMP-005`)؛ أبقِ المتجر أحادي اللغة حتى تكتمل الترجمة.</span>

### Exact Inputs to Prepare (`المدخلات المطلوب تجهيزها قبل البدء`)
- Sample pair of live Arabic and English product URLs (e.g., `https://store.sa/ar/p1` and `https://store.sa/en/p1`)
- Raw HTML `<head>` source (fetched via `curl -s` or View Source, not rendered DOM alone)
- Cloudflare DNS/Proxy access (if running a managed SaaS storefront that requires HTML edge rewriting)

## 2. The Working `CHECKLIST` (`الأداة الكاملة الجاهزة للنسخ والتطبيق الفوري`)

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

## 3. Complete End-to-End Worked Example (`مثال تطبيقي متكامل من المدخلات حتى المراجعة البشرية والنتيجة النهائية`)

*(Illustrative scenario — original example for training, never represented as a verified client outcome)*

### Step A: Sample Brief / Input (`موجز المدخلات`)
- **Store**: Bilingual Saudi Specialty Coffee Store on Salla with custom domain `roaster-example.sa`.
- **Symptom**: Google Search Console reports `"Duplicate, Google chose different canonical than user"` for 100% of `/en/` product pages, so expat shoppers in Riyadh and Dubai searching in English cannot find the `/en/` pages.

### Step B: Initial Output (`المخرج الأولي`)
```html
<!-- Raw <head> output on https://roaster-example.sa/en/ethiopian-coffee-250g -->
<link rel="canonical" href="https://roaster-example.sa/ethiopian-coffee-250g" />
<link rel="alternate" hreflang="ar" href="https://roaster-example.sa/ethiopian-coffee-250g" />
<link rel="alternate" hreflang="en" href="https://roaster-example.sa/en/ethiopian-coffee-250g" />
```
*(Contradiction: `canonical` tells Google not to index `/en/`, while `hreflang="en"` tells Google to serve `/en/` to English users.)*

### Step C: Human Review & Edits (`التدقيق البشري والتعديلات`)
1. **Verified Translation Completeness First (`AMP-005`)**: Confirmed that the 45 products had English titles and descriptions populated before fixing canonicals.
2. **Deployed Self-Referencing Canonical Rule**: Applied the Cloudflare `HTMLRewriter` canonical fix on `/en/*` paths and stripped `?utm_*` parameters from the canonical output.

### Step D: Final Reviewed Example Outcome (`النتيجة النهائية المعتمدة`)
```html
<!-- Corrected <head> output on https://roaster-example.sa/en/ethiopian-coffee-250g -->
<link rel="canonical" href="https://roaster-example.sa/en/ethiopian-coffee-250g" />
<link rel="alternate" hreflang="ar-SA" href="https://roaster-example.sa/ethiopian-coffee-250g" />
<link rel="alternate" hreflang="en-SA" href="https://roaster-example.sa/en/ethiopian-coffee-250g" />
<link rel="alternate" hreflang="x-default" href="https://roaster-example.sa/ethiopian-coffee-250g" />
```

## 4. What Can Go Wrong & How to Fix It (`الأخطاء الشائعة وخطة الإنقاذ`)

- **Failure Case (`المشكلة المحتملة`)**: A team rewrites `<link rel="canonical">` using client-side JavaScript (`document.querySelector`) via Google Tag Manager; Googlebot reads the initial server HTML canonical before JS execution or treats conflicting signals as untrusted.
- **Correction & Fallback (`الحل الإجرائي والبديل الآمن`)**: Always apply canonical tag fixes in server-side templates or at the CDN edge (`Cloudflare HTMLRewriter`), never via client-side GTM JavaScript injection.

## 5. Model & Platform Capability Matrix (`مصفوفة قدرات النماذج والمنصات — 2026-10-25`)

| Platform / Model | Status | Official Documentation | MENA Operational Constraint | Fallback |
| :--- | :--- | :--- | :--- | :--- |
| **Salla Bilingual `/en/` Canonical Output** | `plan/region dependent` | [Official Docs](https://voctos.net/salla-zid-store-seo-audit/) (`2026-10-25`) | VOCTOS Oct 2026 audit documented that 6 of 6 English-enabled Salla stores pointed the English page canonical back to the Arabic URL. | Use Cloudflare `HTMLRewriter` at the DNS edge to rewrite `/en/*` canonicals, or disable `/en/` if English SEO is not actively maintained. |

## 6. How to Measure Success (`خطة القياس والضوابط`)

- **Primary Metric**: Count of `/en/` URLs indexed in Google Search Console (`Valid / Indexed` vs `Duplicate, Google chose different canonical`).
- **Baseline**: Number of indexed `/en/` URLs prior to canonical fix.
- **Observation Window**: 21–28 days after requesting validation in GSC.
- **Interpretation Boundary**: Fixing canonicals enables `/en/` indexing, but pages still require English `<title>` tags (`AMP-005`) and English body copy to rank for English queries.

## 7. Primary Sources & Evidence Boundaries (`المصادر الموثقة وحدود الأدلة`)

- [We Audited 20 Salla and Zid Stores: The SEO Defaults Saudi Merchants Inherit (2026)](https://voctos.net/salla-zid-store-seo-audit/) — *VOCTOS* (Published `2026-10-08`, Accessed `2026-10-25`): Audit of 20 Saudi stores (10 Salla, 10 Zid): 60% of sampled Salla sitemap URLs (88/146) redirected or returned 410; 6/6 Salla English pages canonicalized to Arabic; 9/10 Zid stores lacked Sitemap in robots.txt; 0/10 Salla stores had Brand in Product JSON-LD; 8/11 English pages kept Arabic-script titles.
- [The Arabic SEO in Saudi Arabia Mistakes Costing Riyadh Brands Rankings](https://digistreetmedia.com/blog/the-arabic-seo-in-saudi-arabia-mistakes-costing-riyadh-brands-rankings/) — *DigiStreet Media* (Published `2026-09-29`, Accessed `2026-10-25`): Identifies 5 recurring KSA SEO failures: treating Arabic as translation, running one strategy across Arabic/English, broken hreflang/RTL mobile UX, ignoring Vision 2030 sector context, and chasing non-local backlinks while treating Riyadh, Jeddah, and Dammam as homogeneous.
