# FW-057: MENA Influencer Geo-Audience & Engagement-Pod Forensic Vetting Checklist
## قائمة الفحص الجنائي لجمهور المؤثرين في المنطقة (كشف المتابعين الوهميين، مجموعات التفاعل `Pods`، والجمهور خارج نطاق الشحن)

- **Consolidated Contextual Child IDs (`MERGE_INTO_EXISTING`)**: `AMP-295`, `AMP-305`, `AMP-315`, `AMP-325`
- **Selected Artifact Type**: `CHECKLIST`
- **Intended Audience**: Influencer Marketing Manager, PR & Communications Lead, Talent Coordinator, Legal & Compliance Lead
- **Target Markets & Languages**: Egypt & GCC (`Saudi Arabia, UAE, Kuwait, Qatar, Bahrain, Oman`) — Bilingual Arabic (`Egyptian Ammiya`, `Saudi/Gulf Khaleeji`, `White MSA`) + English
- **Version**: `1.2` | **Last Reviewed**: `2026-10-25` | **Status**: `READY_FOR_REVIEW`

## 1. Plain-Language Promise & Why This Artifact Form Fits the Job

- **What You Can Make or Decide (EN)**: Vet influencer accounts beyond surface AI engagement scores by verifying target-country follower share (`>= 65%` in KSA/UAE/Egypt delivery zone), comment-pod patterns, and historical story view-to-follower ratios.
- **ما الذي يمكنك إنجازه أو حسمه بهذه الأداة (AR)**: تدقيق حسابات المؤثرين بما يتجاوز «نسبة التفاعل السطحية» في أدوات الذكاء الاصطناعي عبر التحقق من نسبة المتابعين الفعليين داخل دولة الشحن المستهدفة (`65% فأكثر`) وكشف مجموعات التبادل (`Comment Pods`) ونسبة مشاهدات القصص الحقيقية.
- **Why `CHECKLIST` Fits This User Job (EN)**: A creator living in Dubai or Riyadh frequently has 70%+ of their followers located in other countries where a local merchant does not ship, or inflates their AI engagement score (`ER = 6.5%`) using WhatsApp/Telegram comment pods of the same 40 accounts posting `'ما شاء الله 🔥'`; a forensic CHECKLIST catches geo-mismatch and pod inflation before money is spent.
- **لماذا يناسب شكل `CHECKLIST` هذه المهمة (AR)**: كثيراً ما يقيم المؤثر في دبي أو الرياض بينما يتواجد 70%+ من متابعيه خارج الدولة التي يشحن إليها المتجر، أو يرفع «نسبة التفاعل» أمام أدوات الذكاء الاصطناعي عبر مجموعات تبادل التعليقات (`Pods`)؛ وتكشف قائمة الفحص الجنائي هذه التضخم قبل التعاقد.

## 2. "Use It When" Trigger, Boundaries & Exact Inputs to Prepare

- **Use It When (EN)**: Use before approving any influencer or creator budget in Saudi Arabia, UAE, Kuwait, Qatar, or Egypt.
- **متى تستخدم هذه الأداة (AR)**: تُستخدم قبل اعتماد التعاقد المالي مع أي مؤثر أو صانع محتوى في السعودية أو الإمارات أو الكويت أو قطر أو مصر.
- **When NOT to Use It (EN)**: Never approve a creator based solely on total follower count + an AI discovery tool's aggregate `Engagement Rate %` badge.
- **متى لا تستخدم هذه الأداة (AR)**: لا تعتمد التعاقد مع أي مؤثر بناءً على «إجمالي المتابعين + نسبة التفاعل العامة» في أداة الذكاء الاصطناعي دون فحص التوزيع الجغرافي الفعلي.

### Exact Inputs to Prepare Before Starting (`المدخلات المطلوب تجهيزها`)
1. Creator's live native platform analytics screenshot/screen-recording from the **last 28 days** (`Instagram Professional Dashboard / TikTok Studio / Snapchat Public Profile Insights` showing **Top Countries & Cities** and **Age/Gender**)
2. Last 10 Organic Posts + Last 3 Sponsored Posts comment threads
3. Target Store Delivery Geography (e.g., `Riyadh Only`, `All KSA`, `UAE`, or `Egypt`)

### Privacy-Safe Data Handling (`ضوابط الخصوصية وحماية البيانات الشخصية PDPL`)
- **Strict PII Redaction Before Prompting**: Under Saudi PDPL (Art. 25), UAE Federal Decree-Law No. 45 of 2021, Qatar Law No. 13 of 2016, and Egypt Law No. 151 of 2020, **never paste raw customer names, unhashed mobile numbers (`+9665...` / `+201...`), email addresses, national IDs, or private WhatsApp transcripts into public/consumer LLM interfaces**. Use anonymized placeholders (`{first_name}`, `ORD_10045`) during prompt testing and restrict live customer data to zero-data-retention enterprise API endpoints or local deterministic scripts.

## 3. The Directly Usable Artifact (`الأداة التطبيقية الجاهزة للنسخ والتنفيذ`)

### 5-Point Forensic Influencer Vetting Checklist (MENA Geo & Pod Audit)

#### 1. Mandatory Vetting Gates (Require Native Insights Screenshot from Last 28 Days)
| Vetting Gate | Pass Threshold (`APPROVE`) | Red Flag / Disqualification (`REJECT`) | Why AI Discovery Scores Miss It |
| :--- | :--- | :--- | :--- |
| **Gate 1: Target Country Follower & Viewer Share** | **`>= 65%` of reached audience** (and `>= 50%` for expat hubs like UAE) is physically located in your exact shipping country (`KSA` / `UAE` / `Egypt`). | Creator lives in Riyadh/Dubai, but `72%` of followers are in countries you cannot ship to! | Third-party AI scrapers often classify a creator's location by the creator's bio (`"📍 Dubai / Riyadh"`) rather than where their *viewers* actually live. |
| **Gate 2: Story / Reel View-to-Follower Ratio** | Average 24h Story Reach `>= 5% – 15%` of followers; median Reel/TikTok views stable across last 15 posts. | `500,000` followers, but average Story views are `< 1,200` (`0.2%`) or 1 viral giveaway post has `2M` views while the other 14 posts have `900` views. | Mean (average) views are skewed by 1 viral meme or paid boost; always check the **Median of the last 12 non-boosted posts**. |
| **Gate 3: Comment Pod & Bot Linguistic Audit** | Comments ask specific product/topic questions (`"بكم؟"`, `"من وين العباية؟"`, `"جربتوه؟"`). | `80%+` of comments arrive in the first 15 minutes from other micro-influencers posting generic 2-word emojis (`"مبدعة 🔥"`, `"استمري حبيبتي 🌸"`, `"بالتوفيق"`). | Generic engagement calculators count a pod comment (`"روعة"`) equal to a real buyer comment (`"فرعكم في التجمع ولا زايد؟"`). |
| **Gate 4: Ad Saturation Ratio (Last 14 Days)** | `<= 25%` of recent stories/posts are paid ads; high organic content trust. | `80%+` of daily Snapchat/IG stories are back-to-back paid ads (`#إعلان` for 10 different stores in one day). | Followers develop severe ad blindness on accounts that post only consecutive paid shoutouts. |
| **Gate 5: License & Category Compliance (`AMP-281`/`AMP-286`)** | Active `Mawthooq` (KSA) / `UAE Media Council` permit + zero illegal medical/fake-discount claims. | Unlicensed or promotes counterfeit/illegal giveaways. | Protects brand from regulatory liability. |

## 4. Model & Platform Capability Branches (`فروع قدرات النماذج والمنصات والبدائل الاحتياطية`)

| System / Platform | Capability Status | Official Documentation & Access Date | Operational Constraint in Egypt & GCC | Fallback When Feature/Modality Is Unavailable |
| :--- | :--- | :--- | :--- | :--- |
| **Instagram Professional Dashboard, TikTok Studio & Snapchat Public Profile Native Geo Insights** | `supported` | [Official Reference](https://23hublab.com/digital-advertising-landscape-in-egypt/) (`2026-10-25`) | Third-party influencer databases estimate follower geography via sampling and frequently misclassify MENA diaspora/regional audiences; native creator dashboard insights provide verified 28-day viewer geo splits. | Require a 28-day native Audience Country/City screenshot or screen recording as a mandatory pre-contract attachment. |

## 5. Consolidated Regional & Vertical Adaptation Matrix (`دمج الأنماط السياقية الفرعية بدون حشو`)

Per Agent 2 v1.2's anti-padding rule, the following **4 cross-verified contextual synthesis patterns** and **0 screened duplicate variants** share this core mechanism and are consolidated directly into this source-of-truth framework:

| Child Pattern ID | Disposition | Regional / Sector Operating Context | Specific Adaptation & Guardrail Integrated in This Asset | Evidence Tier |
| :--- | :--- | :--- | :--- | :--- |
| **`AMP-295`** | `MERGE_INTO_EXISTING` | Egyptian E-Commerce & Social Commerce (Shopify / WooCommerce / Cairo & Alexandria) | Requiring native platform audience-geography screenshots (>60% in target shipping country) and unique promo/link tracking.; Specifically impacts Egyptian brands operating in EGP where merchant-specific payment mix from recent order records, Mobile Wallets (Vodafone Cash), InstaPay, and Fawry dominate. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-305`** | `MERGE_INTO_EXISTING` | UAE & Multi-Market GCC Enterprise / Retail (Dubai, Abu Dhabi, Doha, Kuwait) | Requiring native platform audience-geography screenshots (>60% in target shipping country) and unique promo/link tracking.; Specifically impacts bilingual Arabic/English campaigns in high-CPM, expat-dense Gulf markets under UAE PDPL / TDRA and Qatari regulations. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-315`** | `MERGE_INTO_EXISTING` | High-Trust & Regulated Verticals (Healthcare/SFDA/EDA, Fintech/SAMA/FRA, Real Estate) | Requiring native platform audience-geography screenshots (>60% in target shipping country) and unique promo/link tracking.; Specifically impacts regulated claims requiring SFDA, EDA, MOH, SAMA, FRA, or RERA compliance pre-clearance and strict hallucination guardrails. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-325`** | `MERGE_INTO_EXISTING` | Seasonal Peak Operations (Ramadan, Eid, White/Yellow Friday, Saudi Founding/National Day) | Requiring native platform audience-geography screenshots (>60% in target shipping country) and unique promo/link tracking.; Specifically impacts high-velocity seasonal surges where CPMs jump 40-70%, prices change rapidly, and Hijri calendar cultural sensitivity is paramount. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |

### Context-Specific Execution Knobs Across the 5 MENA Operating Environments
1. **Saudi D2C E-Commerce (`Salla / Zid / Riyadh & Jeddah Retail`)**: Enforce `SAR` tax-inclusive pricing (`15% ZATCA VAT`), native `Mada / Apple Pay / Tabby / Tamara` visibility (`AMP-387`), `GAMR Mawthooq` creator verification (`AMP-281`), and White Saudi Khaleeji orthography (`AMP-002`, `AMP-177`).
2. **Egyptian E-Commerce & Social Commerce (`Shopify / WooCommerce / Cairo & Alexandria`)**: Use each merchant’s own order and payment data to assess Cash on Delivery (`COD`), mobile wallets, InstaPay, Fawry, `valU`, address fields, and pre-dispatch WhatsApp confirmation. Verify current provider terms and local requirements before implementation.
3. **UAE & Multi-Market GCC Enterprise / Retail (`Dubai, Abu Dhabi, Doha, Kuwait`)**: Separate high-CPM UAE/Qatar budgets from lower-CPM markets (`AMP-061`), enforce UAE `TDRA` `9 PM – 7 AM` SMS curfew + `AD-` prefix (`AMP-442`), UAE Media Council permits (`AMP-282`), and bilingual Arabic/English canonical & currency parity (`current applicable UAE VAT`, `current applicable Qatar/Kuwait tax rules`, 3-decimal `KWD` `AMP-239`).
4. **High-Trust & Regulated Verticals (`Healthcare SFDA/MOH/EDA, FinTech SAMA/FRA, Real Estate REGA/RERA`)**: Strip all therapeutic/cure verbs (`AMP-176`, `AMP-286`), display mandatory `MOH/SFDA/DHA/EDA/Fal/Trakheesi` permit numbers (`AMP-070`), and route budgets to high-credibility channels (`AMP-290`, `AMP-339`).
5. **Seasonal Peak Operations (`Ramadan, Eid, White/Yellow Friday, Saudi Founding/National Day`)**: Lock Hijri-Gregorian overlaps (`Feb 2027 Ramadan x Saudi Founding Day x Kuwait National Day` `AMP-125`), pre-schedule GMC `sale_price_effective_date` 48h ahead (`AMP-063`), verify 30-day baseline discount permits (`AMP-064`), and disable Meta Advantage+ auto-music (`AMP-065`).

## 6. Worked Example Summary & Failure Recovery (`ملخص المثال التطبيقي وخطة الإنقاذ`)

*(Full step-by-step worked example with annotated human edits is also provided in `EXAMPLE.md`)*

- **Sample Input Brief**: - **Store**: Saudi Specialty Dates & Gifting Brand shipping **only inside Saudi Arabia (`Riyadh, Jeddah, Dammam`)**.
- **AI Tool Recommendation**: Shortlisted Creator A (`420,000` IG followers, bio says `"📍 Riyadh"`, AI Engagement Score `5.8% — Excellent`, fee `SAR 12,000`) and Creator B (`68,000` IG/Snap followers, fee `SAR 3,500`).
- **Human Review & Key Edits Applied**: 1. **Requested Screen Recording of Native Insights**: Required a 10-second screen recording of the native `Instagram Insights -> Reached Audience -> Top Countries & Cities` tab (to prevent Photoshopped static screenshots).
2. **Calculated 'Cost per 1,000 Target-Country Views' (`Geo-Adjusted CPM`)**: Evaluated creators on `Fee / (Median_Views * Target_Country_Share_%)` instead of raw follower count.
- **Final Usable Output**: - Saved `SAR 12,000` by rejecting the geo-mismatched pod account and booked 3 geo-verified Saudi micro-creators delivering `84%+` in-kingdom reach.
- **What Can Go Wrong**: A Cairo local restaurant chain hires a food TikToker with 1.2M followers based in Cairo without checking city distribution; 78% of the creator's viewers are in Iraq, Algeria, and Jordan, resulting in high video views and hampir zero restaurant walk-ins.
- **Correction & Fallback**: Always calculate **`In-Zone Deliverable Views = Median_Organic_Views × (Target_City_or_Country_% / 100)`** from a live 28-day native analytics recording before signing any creator.

## 7. Measurement Plan & Hypothesis Framing (`خطة القياس والضوابط الإحصائية`)

- **Primary Metric to Track**: Geo-Adjusted Cost per 1,000 Views (`Target Country Views CPM`) and Cost per Incremental New Customer (`AMP-288`).
- **Baseline Definition**: Prior unvetted influencer campaign CAC.
- **Observation Window**: 7–14 days post-creator post. *(Must span full 7/14-day weekly cycles and account for 25th–30th monthly salary windows per `AMP-391`)*.
- **What Cannot Be Concluded (Boundary)**: Forensic geo and pod vetting guarantees real target-market eyeballs, while offer strength and creator brief authenticity (`AMP-283`) drive purchases.
