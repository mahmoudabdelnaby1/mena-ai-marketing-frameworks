# End-to-End Worked Example & Failure Recovery — `FW-038` (`AMP-181`)

- **Framework**: XML-Indexed Brand Voice & Context-Window Hygiene Workflow for Long Arabic Drafts
- **العنوان بالعربية**: مسار عمل فهرسة أدلة الهوية اللغوية بهيكلة `XML` لمنع انحراف التعليمات (`Instruction Drift`) في النصوص العربية الطويلة
- **Selected Artifact Type**: `OPERATING_FRAMEWORK`
- **Disclaimer**: *All scenarios, brand names, SKU codes, and metrics below are original, realistic illustrative examples for MENA practitioner training and are never represented as verified client outcomes.*

## 1. Realistic Sample Brief / Input (`المدخلات وموجز الحالة العملية`)

- **Task**: Write a 2,000-word Saudi B2B FinTech Guide on Corporate Expense Management (`إدارة مصروفات الشركات والبطاقات المؤسسية في السعودية`).
- **Previous Failure**: Team uploaded a 42-page PDF brand book + 15 old English blog posts into the prompt. By Section 4, the model drifted from Saudi executive terminology (`الفوترة الإلكترونية ZATCA المرحلة الثانية - ربط`) into generic translated US tax terms (`خصومات مصلحة الضرائب الفيدرالية IRS`).

## 2. Initial Generated / Completed Output (`المخرج الأولي عند تطبيق الأداة`)

- **Distilled `<brand_constitution>` (`380` tokens)**:
  - Locked Saudi financial lexicon: `هيئة الزكاة والضريبة والجمارك (ZATCA)`, `الفوترة الإلكترونية (فاتورة - مرحلة الربط والتكامل)`, `نظام مدى`, `سريع (SARIE)`, `ضريبة القيمة المضافة 15%`.
  - Explicitly banned US/EU regulatory terms (`IRS`, `401k`, `VAT 20%`, `HMRC`).
- **Modular 4-Part Generation**: Generated Sections 1–4 with 100% lexical consistency from opening paragraph to final conclusion.

## 3. Human Review & Localization/Technical Edits (`المراجعة البشرية والتعديلات الرقابية والتقنية`)

1. **Verified ZATCA Phase 2 Terminology**: Confirmed accurate reference to ZATCA Phase 2 integration (`المرحلة الثانية: مرحلة الربط والتكامل`) and XML/UUID invoice requirements.
2. **Checked Zero Cliché Drift**: Confirmed zero occurrences of `"في عالمنا الرقمي المتسارع"` across all 4 sections.

## 4. Final Reviewed Example Outcome (`النتيجة النهائية الجاهزة للتنفيذ`)

- 2,000-word Saudi B2B FinTech whitepaper completed with zero foreign regulatory drift and 82% reduction in input prompt token cost.

## 5. What Can Go Wrong & Specific Correction / Fallback (`حالة الفشل المحتملة وخطة الإنقاذ والبديل`)

- **Common Failure Mode (`ما الذي قد يسير بشكل خاطئ؟`)**:
  A writer pastes 10 old blog posts into the prompt as 'style examples', unaware that 4 of them were written by a previous freelancer in Levantine/Egyptian idioms; the LLM imitates the noisy examples and ignores the system prompt.
- **Specific Correction & Non-AI / Platform Fallback (`الإصلاح المحدد والبديل الآمن`)**:
  Audit every few-shot `<sample>` before adding it to `<brand_constitution>`: **1 clean 100-word golden paragraph beats 10 noisy historical posts**.
