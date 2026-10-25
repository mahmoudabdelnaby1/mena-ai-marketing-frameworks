# Master Flagship Worked Examples Across All 9 Channels (`EXAMPLE.md`)
## نماذج تطبيقية شاملة عبر القنوات التسويقية التسع (من المدخلات والمراجعة البشرية حتى النتيجة النهائية)

> Every individual framework folder (`frameworks/01-seo/FW-001...` through `frameworks/09-marketing-automation/FW-092...`) contains its own dedicated `EXAMPLE.md`. Below are 9 flagship end-to-end worked examples (1 per marketing channel) demonstrating the full input → output → human review → final result + failure recovery loop.

## FW-001 (`AMP-001` — Search Engine Optimization (SEO)): MENA Native Search Root & Dialect Keyword Matrix Prompt
### قالب هندسة الكلمات المفتاحية العربية حسب الجذر اللغوي واللهجة المحلية (مصر والخليج)

- **Artifact Type**: `PROMPT_TEMPLATE` | **Disposition**: `CREATE_FRAMEWORK`
- **Sample Input Brief**:
- **Target Market**: Saudi Arabia (Riyadh & Jeddah) + Egypt (Cairo & Alexandria)
- **Platform**: Salla (KSA store) & WooCommerce (Egypt store)
- **Product Concept**: "Cordless Hair Straightener Brush" (فرشاة فرد الشعر اللاسلكية)
- **Price & Payment**: KSA: 299 SAR (incl. 15% VAT, Tabby/Tamara 4 payments); Egypt: 2,450 EGP (COD + InstaPay + valU)
- **Verified Seeds**: فرشاه شعر لاسلكيه، مشط حراري لاسلكي، سيراميك شعر بدون سلك
- **Initial Generated / Completed Output**:
| Cluster ID | Native Arabic Query | Market & Register | Intent Stage | Orthographic Variants | Literal Translation Rejected | Target Page Element |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| KW-01 | مشط حراري لاسلكي للشعر | KSA (Khaleeji/MSA) | Commercial / Transactional | مشط حرارى لاسلكى، فرشاه حراريه | فرشاة تقويم الشعر بدون حبل | H1 & Meta Title (KSA) |
| KW-02 | افضل فرشاة شعر لاسلكية بالتقسيط تابي | KSA (Riyadh/Jeddah) | High-Intent Transactional | افضل فرشاه شعر لاسلكيه تابى | شراء مملس شعر لاسلكي رخيص | Product Subtitle & FAQ |
| KW-03 | سعر فرشاة فرد الشعر اللاسلكية في مصر | Egypt (Ammiya/MSA) | Transactional Price Check | سعر فرشاه فرد الشعر اللاسلكيه | تكلفة فرشاة تنعيم الشعر | H1 & Meta Title (Egypt) |
| KW-04 | مكواة شعر فرشاه بدون سلك الدفع عند الاستلام | Egypt (Ammiya) | Transactional COD | مكواه شعر فرشاه، فرشة شعر حرارية | أداة تصفيف الشعر الخالية من الأسلاك | Collection Filter & Meta Description |
- **Human Review & Edits**:
1. **Lexical Validation (KSA)**: Verified in Saudi Google Autocomplete that shoppers search `"استشوار مشط لاسلكي"` and `"فرشاة سيراميك لاسلكية"` more frequently than `"فرشاة فرد"`. Added `"استشوار مشط لاسلكي"` as secondary H2 keyword for the Salla KSA storefront.
2. **Regulatory Guardrail (SFDA/EDA)**: Removed an AI-suggested FAQ phrase `"يعالج تقصف الشعر نهائياً"` (therapeutic claim risk under SFDA cosmetic rules) and replaced it with `"تصفيف سريع مع التحكم في درجات الحرارة"`.
3. **Slug Hygiene**: Kept the URL slug in clean ASCII (`/ar/cordless-hair-straightener-brush`) per `AMP-008` to avoid UTF-8 percent-encoding bloat while keeping `<title>` and `<h1>` in native Arabic.
- **Final Reviewed Example Outcome**:
- **KSA Salla `<title>` (58 chars)**: `مشط حراري وفرشاة شعر لاسلكية | تقسيط تابي وتمارا - متجرنا`
- **KSA Salla `<h1>`**: `فرشاة فرد الشعر الحرارية اللاسلكية (شحن USB-C)`
- **Egypt WooCommerce `<title>` (61 chars)**: `فرشاة فرد الشعر الحرارية اللاسلكية | شحن لجميع محافظات مصر`
- **Egypt WooCommerce `<h1>`**: `مكواة وفرشاة فرد الشعر اللاسلكية - الدفع عند الاستلام أو إنستاباي`
- **Failure Case & Recovery**:
  - *What Can Go Wrong*: An SEO specialist runs the prompt without supplying `VERIFIED_SEEDS` from Google Search Console or Autocomplete, causing the LLM to invent plausible-sounding Gulf slang that has zero actual monthly search volume.
  - *Correction / Fallback*: Enforce the Pre-Flight Rule: never accept an AI keyword table into production until at least 3 top terms per cluster are cross-checked against Google Search Console Performance queries, Google Autocomplete (set to KSA/Egypt locale), or Salla/Amazon.sa search bar suggestions.

## FW-013 (`AMP-061` — Pay-Per-Click (PPC) Advertising): MENA Cross-Market Budget Isolation Decision Aid (Preventing the 4–5x Egypt vs. GCC CPM Arbitrage Trap)
### أداة قرار فصل الميزانيات الإعلانية بين مصر والخليج (منع فخ التهام الميزانية بسبب فارق الـ CPM البالغ 4–5 أضعاف)

- **Artifact Type**: `DECISION_AID` | **Disposition**: `CREATE_FRAMEWORK`
- **Sample Input Brief**:
- **Advertiser**: Regional D2C Modest Fashion Brand shipping to UAE, Saudi Arabia, and Egypt.
- **Total Monthly Budget**: `$30,000/month` (`$1,000/day`).
- **Previous Mistake**: Ran 1 global Meta Advantage+ Shopping Campaign (`Maximize Conversions`) targeting `UAE + KSA + Egypt` together. Result: `88%` of budget (`$26,400`) was spent in Egypt (where AOV was `$28` with `32%` COD returns), while UAE (`$145` AOV) received only `3%` of spend.
- **Initial Generated / Completed Output**:
- **Isolated Campaign Architecture (`$1,000/day` Total)**:
  - **Campaign 1 (`KSA_ASC_SAR`)**: `$500/day` (50% budget) | Currency: `SAR` (incl. 15% VAT) | Creative: Saudi Khaleeji + Tamara/Tabby badge.
  - **Campaign 2 (`UAE_ASC_AED`)**: `$300/day` (30% budget) | Currency: `AED` (incl. 5% VAT) | Creative: Bilingual English/Gulf + Tabby/Apple Pay.
  - **Campaign 3 (`EGY_ASC_EGP`)**: `$200/day` (20% budget) | Currency: `EGP` | Bidding: Value-adjusted for Net Delivered COD orders (`AMP-062`).
- **Human Review & Edits**:
1. **Catalog Feed Separation**: Linked each of the 3 campaigns to its country-specific catalog feed (`SAR`, `AED`, `EGP`) so dynamic product overlays never display `EGP` prices to Dubai shoppers or `AED` prices to Cairo shoppers.
2. **Ad Set Minimums Check**: Confirmed each isolated campaign generates `>65` conversions/week, clearing Meta's learning-phase threshold without cross-country cannibalization.
- **Final Reviewed Example Outcome**:
- 3 Country-Isolated Campaigns live with locked daily caps (`KSA: $500/d`, `UAE: $300/d`, `EGY: $200/d`), localized currencies, and zero cross-border CPM arbitrage leakage.
- **Failure Case & Recovery**:
  - *What Can Go Wrong*: A media buyer separates Egypt and UAE into two Ad Sets inside the SAME Meta Campaign with Advantage+ Campaign Budget (`CBO`) turned ON; CBO still shifts 85% of the campaign budget into the Egypt Ad Set.
  - *Correction / Fallback*: Enforce isolation at the **Campaign level** (or disable Campaign Budget Optimization and lock Ad Set daily budgets explicitly)—never rely on CBO across countries with >30% CPM divergence.

## FW-023 (`AMP-121` — Social Media Marketing): MENA Country-by-Country Social Platform Reach & Channel Mix Calibration Aid (KSA vs. UAE vs. Egypt)
### أداة معايرة مزيج منصات التواصل الاجتماعي حسب الدولة (السعودية مقابل الإمارات مقابل مصر — تجنب نسخ خطط سناب شات عشوائياً)

- **Artifact Type**: `DECISION_AID` | **Disposition**: `CREATE_FRAMEWORK`
- **Sample Input Brief**:
- **Brand**: Riyadh-based D2C Specialty Perfumes expanding into Cairo (Egypt) and Dubai (UAE).
- **KSA Baseline**: Brand spends `65%` on Snapchat Ads + Saudi Snap Creators, `25%` on TikTok, `10%` on Instagram.
- **Draft AI Expansion Plan**: Prompted ChatGPT to 'adapt our KSA social plan for Egypt and UAE', and it kept the exact `65% Snapchat / 25% TikTok / 10% Instagram` split for Cairo.
- **Initial Generated / Completed Output**:
- **Calibrated 3-Market Channel Allocation**:
  - **KSA (Keep Proven Core)**: `55%` Snapchat, `25%` TikTok, `15%` Instagram, `5%` X.
  - **Egypt (Re-weighted for Mass & Affluent Reach)**: `45%` Meta (Instagram Reels + Facebook Video/Catalog), `30%` TikTok, `15%` YouTube TrueView (`AMP-339`), `10%` Snapchat (strictly geo/interest-targeted to New Cairo, Sheikh Zayed & Alexandria affluent segments).
  - **UAE (Bilingual Split)**: `40%` Instagram Reels/Stories (EN + AR), `30%` TikTok, `20%` Snapchat (targeted to Arabic/Emirati segment), `10%` YouTube/LinkedIn.
- **Human Review & Edits**:
1. **Egypt Checkout Alignment**: Paired the Egypt Meta/TikTok social mix with InstaPay/Fawry/COD checkout messaging (`AMP-386`) instead of KSA's Tamara/Mada badges.
2. **UAE Language Split**: Created two separate ad sets in UAE (`UAE_AR_Khaleeji` including Snapchat + IG, and `UAE_EN_Expat` on IG + TikTok).
- **Final Reviewed Example Outcome**:
- Approved 3-country channel allocation sheet with distinct platform weights, dialect tracks, and payment-rail hooks per country.
- **Failure Case & Recovery**:
  - *What Can Go Wrong*: A Saudi brand launches in Egypt allocating 70% of its paid social budget to Snapchat Broad targeting; frequency spikes above 8.0 within 5 days while missing 80%+ of Egyptian online shoppers on Instagram, Facebook, and TikTok.
  - *Correction / Fallback*: Cap Snapchat in Egypt at `<= 10–15%` of social spend (focused on specific Gen-Z/affluent segments) and anchor Egyptian acquisition on Meta (FB/IG) and TikTok.

## FW-033 (`AMP-176` — Content Marketing): SFDA & Egyptian EDA Cosmetic, Supplement & Wellness Copy Compliance Checklist (Preventing market-specific legal consequences Therapeutic Claim Penalties)
### قائمة فحص امتثال محتوى التجميل والمكملات للوائح هيئة الغذاء والدواء (`SFDA`) وهيئة الدواء المصرية (`EDA`)

- **Artifact Type**: `CHECKLIST` | **Disposition**: `CREATE_FRAMEWORK`
- **Sample Input Brief**:
- **Product**: Rosemary & Caffeine Hair Serum (`Cosmetic Notification in SFDA eCosma & Egypt EDA`).
- **Draft AI Copy**: `"سيروم الروزماري الطبي المعجزة! يعالج الصلع الوراثي وينبت الشعر من جديد خلال 14 يوماً، ويقضي نهائياً على التهابات وثعلبة فروة الرأس. معتمد طبياً من هيئة الغذاء والدواء!"`
- **Initial Generated / Completed Output**:
- **`scan_sfda_eda_claims()` Result**:
  - `compliant`: `False` (`BLOCK`)
  - `flagged_therapeutic_terms`: `['يعالج', 'الصلع', 'ينبت الشعر', 'يقضي نهائياً', 'معتمد طبياً']`
- **Human Review & Edits**:
1. **Replaced All 5 Therapeutic Claims**: Rewrote using surface cosmetic conditioning and appearance verbs permitted for notified cosmetics.
2. **Corrected SFDA Terminology**: Removed `"معتمد طبياً"` and kept accurate notification reference in the product specification table.
- **Final Reviewed Example Outcome**:
- **Compliant SFDA / EDA Product Copy**:
  `"سيروم العناية بالشعر بخلاصة إكليل الجبل (الروزماري) والكافيين. تركيبة خفيفة تغذي فروة الرأس وترطب خصلات الشعر الجافة لتمنحكِ مظهراً أكثر كثافة ولمعاناً وحيوية مع الاستخدام المنتظم."`
- **Failure Case & Recovery**:
  - *What Can Go Wrong*: An e-commerce store uses an AI review-summary widget that highlights a customer review saying `'هذا الكريم عالج الأكزيما عندي نهائياً'` inside a paid Meta/Snapchat ad headline; SFDA treats promotional use of third-party therapeutic claims in ads as an advertiser violation.
  - *Correction / Fallback*: Apply the `FORBIDDEN_THERAPEUTIC_RE` filter to both brand-authored copy AND any user-generated review or creator script (`AMP-286`) used in marketing.

## FW-043 (`AMP-231` — Email Marketing): Arabic HTML Email `dir='rtl'` & Unicode `<bdi>` Isolation Rendering Checklist (Gmail, Outlook & Apple Mail)
### قائمة فحص وقالب برمجة رسائل البريد العربية (`dir='rtl'` وعزل `<bdi>`) لمنع تشوه المحاذاة وانعكاس الأرقام في Gmail وOutlook

- **Artifact Type**: `CHECKLIST` | **Disposition**: `CREATE_FRAMEWORK`
- **Sample Input Brief**:
- **ESP**: Klaviyo Abandoned Cart Flow for a Saudi & UAE Perfume Store.
- **Broken AI HTML Output**: Used a standard LTR Klaviyo drag-and-drop block without `dir="rtl"` or `<bdi>`. In Gmail and Outlook, the line `"استخدم كود خصم VIP25 للحصول على خصم 25% والاتصال على +966 50 000 0000"` rendered flushed left as `"0000 000 50 966+ %25 VIP25..."` with the `+` sign and `%` sign detached and reversed.
- **Initial Generated / Completed Output**:
- **Applied Master RTL Wrapper + `<bdi>` Isolation**:
  - Wrapped `VIP25`, `25%`, `299.00 SAR`, and `+966 50 000 0000` in `<bdi style="direction:ltr; unicode-bidi:isolate;">` inside `<td dir="rtl" align="right">`.
- **Human Review & Edits**:
1. **Outlook Desktop VML Button Check**: Added `direction:rtl;` inside the CTA button table cell so the left-pointing arrow (`← أكملي طلبك الآن`) points in the natural RTL reading direction (`AMP-389`).
2. **Tested Across 4 Clients**: Verified rendering on Gmail iOS, Gmail Web, Apple Mail, and Outlook 365 Desktop (Windows).
- **Final Reviewed Example Outcome**:
- Production Klaviyo HTML template passing 100% RTL alignment and BiDi number/code isolation across Gmail, Outlook, and Apple Mail.
- **Failure Case & Recovery**:
  - *What Can Go Wrong*: A customer registers their first name in English (`"Sarah"`) on an Arabic store; in the welcome email `'مرحباً Sarah، شكراً لتسجيلك!'`, the Arabic comma `،` jumps to the right of `Sarah` because an unisolated Latin token at the start of an RTL line flips adjacent neutral punctuation.
  - *Correction / Fallback*: Always wrap `{{ first_name }}` in `<bdi>{{ first_name }}</bdi>&rlm;` (followed by the Right-to-Left Mark entity `&rlm;`) whenever a merge tag can contain either Arabic or Latin script.

## FW-053 (`AMP-281` — Influencer Marketing): Saudi GAMR 'Mawthooq' (موثوق) Influencer License Verification & Contracting Checklist
### قائمة فحص التحقق الإلزامي من رخصة «موثوق» (`Mawthooq` - الهيئة العامة لتنظيم الإعلام `GAMR`) قبل التعاقد مع المؤثرين في السعودية

- **Artifact Type**: `CHECKLIST` | **Disposition**: `CREATE_FRAMEWORK`
- **Sample Input Brief**:
- **Campaign**: Riyadh Coffee & Roastery Chain launching a new winter menu with 12 Saudi lifestyle & food creators shortlisted by an AI influencer tool (`SAR 180,000` total creator budget).
- **Pre-Flight Audit Result**:
  - `8` creators supplied active verified `Mawthooq` license numbers.
  - `2` micro-influencers had **no `Mawthooq` license** (`"نعلن بدون ترخيص لأن حسابنا صغير"` — illegal under GAMR rules, which apply to any paid/barter ad regardless of follower size).
  - `1` creator supplied a `Mawthooq` license that had **expired 4 months ago**.
  - `1` creator was a tourist on a visit visa filming in Riyadh with no Saudi agency/commercial permit.
- **Initial Generated / Completed Output**:
- **Compliance Triage**:
  - **Approved Immediately (`8` Creators)**: Contracted with `Mawthooq` number logged in campaign ledger.
  - **On Hold (`1` Expired Creator)**: Paused PO until creator renewed via `gmedia.gov.sa` (renewed in 48 hours -> moved to Approved).
  - **Replaced (`3` Unlicensed Creators)**: Replaced with 3 pre-vetted `Mawthooq`-licensed micro-creators in Riyadh.
- **Human Review & Edits**:
1. **Added License Column to Master Campaign Tracker**: Made `mawthooq_license_number` and `mawthooq_expiry_date` mandatory blocking fields in the agency's procurement sheet before finance can issue any 50% advance payment.
2. **Paired with `#إعلان` Disclosure (`AMP-287`)**: Added mandatory `#إعلان` overlay check on all story frames.
- **Final Reviewed Example Outcome**:
- `12 / 12` contracted Saudi creators verified with active `GAMR Mawthooq` licenses and documented compliance clauses prior to campaign launch.
- **Failure Case & Recovery**:
  - *What Can Go Wrong*: A brand sends 30 'free PR gift boxes' with a written WhatsApp message saying `'الهدية مقابل تصوير 3 سنابات مع رابط المتجر وكود الخصم'`; GAMR treats barter/gifted posts with a posting or promo-code obligation as commercial advertising requiring `Mawthooq` and `#إعلان` disclosure.
  - *Correction / Fallback*: Apply the exact same `Mawthooq` verification checklist to **barter, affiliate-code, and PR-gifting campaigns** whenever there is an agreement or expectation to post.

## FW-063 (`AMP-331` — Video Advertising): Diffusion Clean-Plate Generation & Post-Production RTL Arabic Typography Workflow (Extending `video-prompt-architect`)
### مسار عمل توليد المشاهد النظيفة (`Clean-Plate`) وإضافة النصوص العربية المتجهية في المونتاج (امتداد لمهارة `video-prompt-architect`)

- **Artifact Type**: `EXTEND_EXISTING` | **Disposition**: `EXTEND_EXISTING`
- **Sample Input Brief**:
- **Scenario**: Riyadh Luxury Perfume Launch (`15s` vertical ad on Kling 3.0 / Veo 3.1).
- **Previous Failure**: Prompt asked the video model for `'A golden neon sign in a Riyadh desert camp reading عطر الفخامة الملكي'`. The model rendered disconnected, reversed LTR letters (`ي ك ل م ل ا ة م ا خ ف ل ا`).
- **Initial Generated / Completed Output**:
- **Stage 1 Clean-Plate Prompt**:
  `Cinematic 9:16 vertical commercial shot in a luxury Riyadh desert camp at twilight. A minimalist matte-black glass perfume flacon rests on a warm sandstone plinth in the lower-center frame, leaving clean, moody amber-lit negative space in the upper-middle third of the frame. Volumetric desert breeze, warm tungsten lanterns (2800K) in soft bokeh background. Zero text, zero signage, blank glass surface ready for post-production composite. --ar 9:16`
- **Stage 2 Vector Overlay Spec**: Exported clean `.srt` / CapCut text layer with `"عطر الفخامة الملكي — إصدار الرياض الخاص"` in `IBM Plex Sans Arabic Bold` positioned at `Y: 360px`.
- **Human Review & Edits**:
1. **Verified Adobe Premiere / CapCut RTL Setting**: Added reminder to enable **`World-Ready Layout / Middle Eastern & South Asian Text Engine (تفعيل محرك النصوص العربية من اليمين لليسار)`** in Premiere/After Effects before pasting the overlay table.
2. **Product Label Composite**: Composited the real vector `.png` bottle label onto the Start Frame keyframe before running Image-to-Video so the bottle label stayed 100% sharp.
- **Final Reviewed Example Outcome**:
- Delivered cinema-grade 9:16 video ad with zero hallucinated Arabic glyphs and razor-sharp vector Arabic headlines and bottle branding.
- **Failure Case & Recovery**:
  - *What Can Go Wrong*: An editor pastes the clean Arabic text from Stage 2 into Adobe Premiere/After Effects on a machine where 'Default Composer' is set to Latin instead of 'Middle Eastern Composer'—causing Premiere itself to render the Arabic letters disconnected from left to right!
  - *Correction / Fallback*: In Adobe Premiere Pro / After Effects: open `Preferences -> Type (أو Graphics)` -> Switch Text Engine to **`Middle Eastern and South Asian`** and set paragraph direction to `Right-to-Left` before creating the text layer.

## FW-073 (`AMP-386` — CRO - Conversion Rate Optimization): Egypt Payment-Method Hierarchy & Checkout UX Decision Aid (merchant-measured payment mix, mobile wallets, InstaPay, Fawry & valU)
### أداة قرار ترتيب وسائل الدفع وتجربة إتمام الطلب في السوق المصري وفق بيانات التاجر، بما فيها المحافظ وإنستاباي وفوري وفاليو

- **Artifact Type**: `DECISION_AID` | **Disposition**: `CREATE_FRAMEWORK`
- **Sample Input Brief**:
- **Store**: Global Athletic Footwear Brand launching its localized Egypt Shopify/WooCommerce site (`AOV: 3,400 EGP`).
- **Previous Mistake**: Copied their European checkout template offering only Credit/Debit Cards (`Visa/Mastercard`). Checkout abandonment rate in Cairo and Alexandria hit **`89%`**.
- **Initial Generated / Completed Output**:
- **Re-Architected Egypt Checkout Stack (via Paymob + Direct InstaPay)**:
  1. Enabled **Mobile Wallets** (`Vodafone Cash`, `Orange Cash`, `Etisalat Cash`, `WE Pay`) with 1-field mobile number (`010/011/012/015` normalized per `AMP-388`).
  2. Enabled **valU & Sympl** BNPL badges on product and checkout pages.
  3. Enabled **InstaPay** (`AMP-395`) with `"شحن مجاني عند الدفع بإنستاباي أو البطاقة"`.
  4. Enabled **Cash on Delivery (`الدفع عند الاستلام`)** paired with automated WhatsApp order confirmation (`AMP-448`).
- **Human Review & Edits**:
1. **Added Local Trust Icons**: Displayed official Egyptian logos (`ميزة Meeza`, `إنستاباي InstaPay`, `فودافون كاش`, `فاليو valU`, `فوري Fawry`) above the fold on the cart drawer instead of generic US `Discover / Amex / PayPal` icons (which Egyptians don't use).
2. **Configured COD Fee Transparency**: Clearly stated `"رسوم خدمة الدفع عند الاستلام: 25 ج.م (أو مجاناً عند الدفع عبر إنستاباي/المحفظة/البطاقة)"` to nudge prepaid adoption without blocking COD buyers.
- **Final Reviewed Example Outcome**:
- Checkout completion rate rose from `11%` to `34.6%`, with `46%` of orders paid upfront via InstaPay, Mobile Wallets, valU, and Meeza/Cards and `54%` via WhatsApp-verified COD.
- **Failure Case & Recovery**:
  - *What Can Go Wrong*: A store enables 'Mobile Wallets' inside a nested submenu labeled in English `'Alternative Digital Gateways'` with no Vodafone Cash logo; Egyptian shoppers don't realize Vodafone Cash is supported and abandon or default to COD.
  - *Correction / Fallback*: Display **`فودافون كاش والمحافظ الإلكترونية`** and **`إنستاباي (InstaPay)`** as **top-level radio buttons with their recognizable color logos** directly on the main checkout screen.

## FW-083 (`AMP-441` — Marketing Automation): WhatsApp Business API Template Pre-Approval & Category Classification Checklist (`MARKETING` vs. `UTILITY`)
### قائمة فحص اعتماد قوالب `WhatsApp Business API` ومنع الرفض الآلي (تصنيف `Marketing` مقابل `Utility` وأمثلة المتغيرات `{{1}}`)

- **Artifact Type**: `CHECKLIST` | **Disposition**: `CREATE_FRAMEWORK`
- **Sample Input Brief**:
- **Submission**: Saudi E-Commerce Store submitting an Order Confirmation template under `UTILITY`.
- **Rejected Draft**:
  `"{{1}}، تم تأكيد طلبك {{2}} {{3}}! استخدم كود VIP10 لخصم 10% على طلبك القادم من هنا: https://bit.ly/3xyz — {{4}}"` (Submitted with empty variable sample fields).
- **Initial Generated / Completed Output**:
- **`lint_whatsapp_template()` Output (`4 Fatal Rejection Reasons Found`)**:
  1. `FAIL`: Starts with `{{1}}` and ends with `{{4}}` (bare variables at start and end).
  2. `FAIL`: Adjacent variables `{{2}} {{3}}` with no separating words.
  3. `FAIL`: Promotional text (`"استخدم كود VIP10 لخصم 10%"`) and `bit.ly` shortener inside a `UTILITY` template.
  4. `FAIL`: Missing sample values for `{{1}}..{{4}}`.
- **Human Review & Edits**:
1. **Rewrote into Pure `UTILITY` Template with Fixed Wrapping Words**:
   `"أهلاً بك يا {{1}}، تم تأكيد طلبك رقم {{2}} بقيمة {{3}} ريال سعودي بنجاح. يمكنك متابعة حالة الشحنة عبر الرابط الرسمي للمتجر بالأسفل. شكراً لثقتك بنا."`
2. **Attached Realistic Arabic Sample Values**: `{{1}}: "أحمد"`, `{{2}}: "#ORD-99412"`, `{{3}}: "349.00"`, and replaced `bit.ly` with a dynamic button pointing to `https://store.sa/orders/{{1}}`.
- **Final Reviewed Example Outcome**:
- Template approved by Meta WhatsApp Manager in `< 2 minutes` under `UTILITY` pricing with `0` rejections.
- **Failure Case & Recovery**:
  - *What Can Go Wrong*: A marketer submits a template with `{{1}}` and `{{3}}` (skipping `{{2}}` after editing a sentence); Meta's API rejects the payload with `Invalid parameter: variable parameters must be sequential`.
  - *Correction / Fallback*: Always run `lint_whatsapp_template()` before clicking Submit in WhatsApp Manager or Wati/Respond.io.
