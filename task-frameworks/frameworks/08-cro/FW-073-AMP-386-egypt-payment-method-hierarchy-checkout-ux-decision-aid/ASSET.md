# FW-073 — Egypt Payment-Method & Checkout UX Decision Aid
## أداة قرار لترتيب وسائل الدفع وتجربة إتمام الطلب في المتجر المصري

### Inputs
- Merchant, platform, market, products, average order value, and delivery footprint.
- Payment methods actually enabled and supported by the merchant's provider.
- Current provider fees, settlement timing, refund process, and reconciliation requirements.
- Merchant-specific checkout sessions, completion, payment status, cancellation, delivery, refund, and support data.
- Mobile experience, customer language, trust needs, and operational capacity.

### Decision workflow
1. **Map current behavior.** Establish a dated baseline from the store's own sessions and settled orders; define how each metric is calculated.
2. **Verify available options.** Confirm provider support, fees, settlement, refund, and operational terms from current official/provider sources.
3. **Identify friction.** Review failed or abandoned sessions, payment-related support contacts, and mismatches between payment and order state.
4. **Design clear choices.** Use familiar labels, accurate fees, concise instructions, and a consistent mobile experience. Do not promise instant settlement unless verified.
5. **Protect order status.** Distinguish pending, authorized, settled, failed, and refunded states according to the actual provider integration.
6. **Test one change at a time.** Use a documented comparison and track both checkout completion and operational outcomes such as failed payments, cancellations, refunds, and delivered contribution.
7. **Decide from evidence.** Keep, revise, or remove an option using the merchant's data and provider constraints.

### Output
A merchant-specific payment-method matrix, transparent checkout copy, verified fee/settlement notes, and a measured test plan.

### Boundary
Payment availability and fees vary by merchant, provider, account, and time. This aid makes no claim about a national payment mix or a universal minimum number of methods. It is not financial advice.
