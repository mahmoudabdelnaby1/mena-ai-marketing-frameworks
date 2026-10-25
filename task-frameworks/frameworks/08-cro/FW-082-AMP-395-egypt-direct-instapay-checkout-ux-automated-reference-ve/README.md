# `FW-082` — InstaPay Checkout & Payment Reconciliation Review
## مراجعة تجربة الدفع عبر InstaPay وتسوية المدفوعات

- **One-Sentence Promise (EN)**: Design clear transfer instructions and a safe order-reconciliation process using verified payment evidence from authorized sources.
- **الوعد التطبيقي في جملة واحدة (AR)**: صمّم تعليمات تحويل واضحة وآلية آمنة لمطابقة الطلبات بالاستناد إلى أدلة دفع موثوقة من مصادر مخولة.
- **Selected Artifact Type**: `DECISION_AID`
- **Intended Audience**: E-commerce, finance, and customer-operations teams.

## Use It When
Reviewing a manual bank-transfer checkout, payment reference workflow, or order-status reconciliation process.

## Key boundary
Never mark an order paid based only on a customer-entered reference or screenshot. Verify against an authorized bank/provider record and document reconciliation ownership. Confirm current provider fees and features.
