# End-to-End Worked Example & Failure Recovery — `FW-004` (`AMP-004`)

- **Framework**: Bilingual Storefront Canonical & Hreflang Conflict Resolution Checklist (Salla, Zid & Custom MENA Stores)
- **العنوان بالعربية**: قائمة فحص وإصلاح تضارب `canonical` و`hreflang` في المتاجر ثنائية اللغة (العربية والإنجليزية)
- **Selected Artifact Type**: `CHECKLIST`
- **Disclaimer**: *All scenarios, brand names, SKU codes, and metrics below are original, realistic illustrative examples for MENA practitioner training and are never represented as verified client outcomes.*

## 1. Realistic Sample Brief / Input (`المدخلات وموجز الحالة العملية`)

- **Store**: Bilingual Saudi Specialty Coffee Store on Salla with custom domain `roaster-example.sa`.
- **Symptom**: Google Search Console reports `"Duplicate, Google chose different canonical than user"` for 100% of `/en/` product pages, so expat shoppers in Riyadh and Dubai searching in English cannot find the `/en/` pages.

## 2. Initial Generated / Completed Output (`المخرج الأولي عند تطبيق الأداة`)

```html
<!-- Raw <head> output on https://roaster-example.sa/en/ethiopian-coffee-250g -->
<link rel="canonical" href="https://roaster-example.sa/ethiopian-coffee-250g" />
<link rel="alternate" hreflang="ar" href="https://roaster-example.sa/ethiopian-coffee-250g" />
<link rel="alternate" hreflang="en" href="https://roaster-example.sa/en/ethiopian-coffee-250g" />
```
*(Contradiction: `canonical` tells Google not to index `/en/`, while `hreflang="en"` tells Google to serve `/en/` to English users.)*

## 3. Human Review & Localization/Technical Edits (`المراجعة البشرية والتعديلات الرقابية والتقنية`)

1. **Verified Translation Completeness First (`AMP-005`)**: Confirmed that the 45 products had English titles and descriptions populated before fixing canonicals.
2. **Deployed Self-Referencing Canonical Rule**: Applied the Cloudflare `HTMLRewriter` canonical fix on `/en/*` paths and stripped `?utm_*` parameters from the canonical output.

## 4. Final Reviewed Example Outcome (`النتيجة النهائية الجاهزة للتنفيذ`)

```html
<!-- Corrected <head> output on https://roaster-example.sa/en/ethiopian-coffee-250g -->
<link rel="canonical" href="https://roaster-example.sa/en/ethiopian-coffee-250g" />
<link rel="alternate" hreflang="ar-SA" href="https://roaster-example.sa/ethiopian-coffee-250g" />
<link rel="alternate" hreflang="en-SA" href="https://roaster-example.sa/en/ethiopian-coffee-250g" />
<link rel="alternate" hreflang="x-default" href="https://roaster-example.sa/ethiopian-coffee-250g" />
```

## 5. What Can Go Wrong & Specific Correction / Fallback (`حالة الفشل المحتملة وخطة الإنقاذ والبديل`)

- **Common Failure Mode (`ما الذي قد يسير بشكل خاطئ؟`)**:
  A team rewrites `<link rel="canonical">` using client-side JavaScript (`document.querySelector`) via Google Tag Manager; Googlebot reads the initial server HTML canonical before JS execution or treats conflicting signals as untrusted.
- **Specific Correction & Non-AI / Platform Fallback (`الإصلاح المحدد والبديل الآمن`)**:
  Always apply canonical tag fixes in server-side templates or at the CDN edge (`Cloudflare HTMLRewriter`), never via client-side GTM JavaScript injection.
