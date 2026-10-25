# End-to-End Worked Example & Failure Recovery — `FW-068` (`AMP-336`)

- **Framework**: MENA Cultural Visual Guardrail & Authentic Gulf/Egyptian Wardrobe, Architecture & Etiquette Prompt Pack (Extending `video-prompt-architect`)
- **العنوان بالعربية**: حزمة الضوابط البصرية والثقافية لمشاهد الفيديو بالذكاء الاصطناعي (ضبط الزي السعودي والخليجي، العمارة، وآداب الضيافة — امتداد `video-prompt-architect`)
- **Selected Artifact Type**: `EXTEND_EXISTING`
- **Disclaimer**: *All scenarios, brand names, SKU codes, and metrics below are original, realistic illustrative examples for MENA practitioner training and are never represented as verified client outcomes.*

## 1. Realistic Sample Brief / Input (`المدخلات وموجز الحالة العملية`)

- **Campaign**: Saudi National Day / Founding Day & Ramadan Bank Commercial generated in `Veo 3.1 / Kling 3.0`.
- **Previous Failed Prompt**: `"An Arab man serving traditional coffee to a guest in a luxury Middle Eastern living room."`
- **Model Hallucination**: Rendered a man in a South Asian tunic and turban holding a Turkish mug with a handle in his **left hand**, with wine glasses on a Moroccan tile table in the background!

## 2. Initial Generated / Completed Output (`المخرج الأولي عند تطبيق الأداة`)

- **Corrected `video-prompt-architect` Master Prompt with Cultural Guardrail Pack**:
  `Medium cinematic 9:16 shot inside a contemporary Riyadh Salmani-style majlis with warm limestone walls and soft daylight. A welcoming Saudi host in a crisp tailored white collared thobe, neatly draped red-and-white shimagh, and black double-coiled iqal holds a traditional brass Najdi Dallah in his left hand and offers a small handleless porcelain finjan cup with his RIGHT hand to an honoured guest who receives it with his RIGHT hand. Fresh Khalas dates in a minimalist wooden bowl on the low table. Warm 3500K lighting, 50mm lens, f/2.0. Negative prompt: left-handed serving, cup with handle, wine glasses, alcohol, turban, South Asian kurta, Moroccan tiles, text, watermarks. --ar 9:16`

## 3. Human Review & Localization/Technical Edits (`المراجعة البشرية والتعديلات الرقابية والتقنية`)

1. **Reference Keyframe Lock (`Image-to-Video`)**: Uploaded a real reference photo of an authentic Saudi thobe, shimagh/iqal fold, and Najdi Dallah as the `Ingredient / Start Frame` reference (`Phase 4 Rule 4` in `video-prompt-architect`) so the video model locked 100% onto authentic Saudi tailoring.
2. **Etiquette Frame Inspection**: Verified frame-by-frame that the guest receives the finjan with the **right hand** and zero prohibited props appear on side tables.

## 4. Final Reviewed Example Outcome (`النتيجة النهائية الجاهزة للتنفيذ`)

- Culturally authentic 9:16 Saudi hospitality scene passing 100% wardrobe, architectural, and right-hand coffee etiquette QA.

## 5. What Can Go Wrong & Specific Correction / Fallback (`حالة الفشل المحتملة وخطة الإنقاذ والبديل`)

- **Common Failure Mode (`ما الذي قد يسير بشكل خاطئ؟`)**:
  A prompt for a family Iftar scene in Riyadh or Cairo asks for `'A festive dinner table with sparkling drinks in tall glasses'`; the video model renders champagne flutes and wine bottles on the Ramadan Iftar table!
- **Specific Correction & Non-AI / Platform Fallback (`الإصلاح المحدد والبديل الآمن`)**:
  In **every** MENA dining, hospitality, hotel, or Ramadan/Eid prompt, explicitly include in the **Negative Prompt**: `wine bottles, champagne flutes, wine glasses, alcohol, beer, pork, left-handed eating/drinking` and specify the exact local beverages (`Vimto in glass pitcher, Arabic coffee finjan, laban cups, water tumblrs, qamar al-din`).
