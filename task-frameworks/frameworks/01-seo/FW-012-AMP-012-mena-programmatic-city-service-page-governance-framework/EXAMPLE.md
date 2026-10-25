# End-to-End Worked Example & Failure Recovery — `FW-012` (`AMP-012`)

- **Framework**: MENA Programmatic City/Service Page Governance Framework (Anti-Scaled Content Abuse)
- **العنوان بالعربية**: الإطار التشغيلي لحوكمة صفحات المدن والخدمات المولدة برمجياً (تجنب عقوبة `Scaled Content Abuse` في جوجل)
- **Selected Artifact Type**: `OPERATING_FRAMEWORK`
- **Disclaimer**: *All scenarios, brand names, SKU codes, and metrics below are original, realistic illustrative examples for MENA practitioner training and are never represented as verified client outcomes.*

## 1. Realistic Sample Brief / Input (`المدخلات وموجز الحالة العملية`)

- **Business**: B2B Commercial HVAC Maintenance & Smart Cooling Provider in Saudi Arabia.
- **Proposed AI Plan**: An agency proposed generating 60 city pages (`شركة صيانة تكييف في [المدينة]`) using a single ChatGPT template with only the city name swapped.

## 2. Initial Generated / Completed Output (`المخرج الأولي عند تطبيق الأداة`)

- **Gate 1 Audit of the 60 Proposed Cities**:
  - **Approved for Standalone Pages (`3` Hubs)**: Riyadh (`/ar/hvac-maintenance-riyadh`), Jeddah (`/ar/hvac-maintenance-jeddah`), Dammam/Khobar (`/ar/hvac-maintenance-dammam`) — where the company has field engineers, distinct SLA tables (4-hour emergency response), and real client projects.
  - **Blocked / Consolidated (`57` Minor Towns)**: Consolidated into a single interactive coverage & dispatch SLA table on the main service page (`0` thin doorway pages created).

## 3. Human Review & Localization/Technical Edits (`المراجعة البشرية والتعديلات الرقابية والتقنية`)

1. **Persona Differentiation**: Rewrote the Riyadh page around commercial towers and server-room precision cooling (`تبريد غرف السيرفرات والأبراج الإدارية بالرياض`), Jeddah around high-humidity coastal corrosion protection (`حماية وحدات التكييف من الرطوبة والأملاح في جدة`), and Dammam around industrial warehouse chillers (`صيانة الشيلرات المركزية للمصانع والمستودعات بالدمام والجبيل`).
2. **Shingle Check**: Verified 5-gram overlap between Riyadh, Jeddah, and Dammam pages dropped from `94%` (agency draft) to **`14%`**.

## 4. Final Reviewed Example Outcome (`النتيجة النهائية الجاهزة للتنفيذ`)

- Published 3 deeply differentiated regional hub pages with verified local SLAs, engineering specs, and `LocalBusiness` JSON-LD instead of 60 thin doorway pages.

## 5. What Can Go Wrong & Specific Correction / Fallback (`حالة الفشل المحتملة وخطة الإنقاذ والبديل`)

- **Common Failure Mode (`ما الذي قد يسير بشكل خاطئ؟`)**:
  A site publishes 200 AI-spun neighborhood pages (`سباك في حي الملز`, `سباك في حي النرجس`...) with identical text; Google classifies the directory under Scaled Content Abuse and deindexes the entire `/services/` subfolder.
- **Specific Correction & Non-AI / Platform Fallback (`الإصلاح المحدد والبديل الآمن`)**:
  Immediately return `410 Gone` (or `301` redirect to the 1–3 genuine city hubs) for all thin swapped-keyword pages, consolidate neighborhood coverage into a structured table on the parent city page, and submit a reconsideration/recrawl request.
