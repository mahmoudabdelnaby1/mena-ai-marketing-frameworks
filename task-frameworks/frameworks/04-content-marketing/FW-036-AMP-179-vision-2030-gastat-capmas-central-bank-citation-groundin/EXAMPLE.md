# End-to-End Worked Example & Failure Recovery — `FW-036` (`AMP-179`)

- **Framework**: Vision 2030, GASTAT, CAPMAS & Central Bank Citation Grounding Workflow (Anti-Hallucination)
- **العنوان بالعربية**: مسار عمل توثيق إحصاءات رؤية 2030 والهيئة العامة للإحصاء (`GASTAT`) والجهاز المركزي (`CAPMAS`) ومنع هلوسة الأرقام
- **Selected Artifact Type**: `OPERATING_FRAMEWORK`
- **Disclaimer**: *All scenarios, brand names, SKU codes, and metrics below are original, realistic illustrative examples for MENA practitioner training and are never represented as verified client outcomes.*

## 1. Realistic Sample Brief / Input (`المدخلات وموجز الحالة العملية`)

- **Task**: Write an executive LinkedIn & Blog introduction on E-Commerce Payment & BNPL Adoption in Saudi Arabia, UAE, and Egypt.
- **Supplied Evidence Pack**:
  1. `SRC-083` (Digitology 2026 Egypt Payment Benchmark): Use the merchant’s recent order records to estimate payment mix.
  2. `SRC-082` (Huptech 2026 UAE/KSA BNPL Study): BNPL (Tabby/Tamara) accounts for `~14%` of UAE Shopify checkout volume.
  3. **Missing Data**: Exact Q3 2026 SAMA Mada transaction growth rate (not in supplied pack).

## 2. Initial Generated / Completed Output (`المخرج الأولي عند تطبيق الأداة`)

```xml
<verbatim_evidence_extractions>
1. Egypt Payment Split: "merchant-measured Cash on Delivery, merchant-measured mobile-wallet use, 10–20% Cards" — Source: Digitology (2026), https://digitology.co/payment-gateway-egypt/
2. UAE BNPL Share: "~14% of UAE checkout volume via Tabby and Tamara" — Source: Huptech (2026), https://www.huptechweb.com/blogs/tabby-vs-tamara-shopify-uae-bnpl-2026
3. SAMA Q3 2026 Mada Growth Rate: [ABSTAINED — Not present in <supplied_evidence_pack>; phrased qualitatively without inventing a percentage].
</verbatim_evidence_extractions>
```

## 3. Human Review & Localization/Technical Edits (`المراجعة البشرية والتعديلات الرقابية والتقنية`)

1. **Verified Abstention**: Confirmed the model did NOT fabricate a SAMA percentage and instead wrote `"مع الانتشار الواسع لبطاقات مدى والمدفوعات الرقمية في المملكة"` while citing the verified `~14%` BNPL figure and `merchant-measured payment mix from recent order records` Egypt COD figure with exact links.
2. **Checked Date Attribution**: Preserved the `2026` benchmark year and publisher attribution inline.

## 4. Final Reviewed Example Outcome (`النتيجة النهائية الجاهزة للتنفيذ`)

- Published bilingual industry brief with `100%` source-verified statistics and `0` fabricated Vision 2030 / GASTAT / CAPMAS citations.

## 5. What Can Go Wrong & Specific Correction / Fallback (`حالة الفشل المحتملة وخطة الإنقاذ والبديل`)

- **Common Failure Mode (`ما الذي قد يسير بشكل خاطئ؟`)**:
  A copywriter prompts ChatGPT `'Write an article about real estate growth in Riyadh with 5 statistics from GASTAT and Knight Frank'`; ChatGPT invents 5 realistic-looking percentages and fake report titles that embarrass the brokerage when a client asks for the link.
- **Specific Correction & Non-AI / Platform Fallback (`الإصلاح المحدد والبديل الآمن`)**:
  Never prompt an LLM to `'find or include X statistics'` without either (a) running live web search + browsing the primary page first, or (b) pasting the verified source excerpts into `<supplied_evidence_pack>`.
