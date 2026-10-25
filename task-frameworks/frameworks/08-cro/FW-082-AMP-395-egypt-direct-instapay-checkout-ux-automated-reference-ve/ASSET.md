# FW-082 — InstaPay Checkout & Payment Reconciliation Review
## مراجعة تجربة الدفع عبر InstaPay وتسوية المدفوعات

### Purpose
Help a commerce team make bank-transfer instructions understandable while keeping order status tied to authorized payment evidence.

### Before implementation
- Confirm the payment method, receiving account, beneficiary details, transfer instructions, fees, and settlement behavior directly with the merchant's bank or payment provider.
- Identify the authorized source of payment confirmation and the finance owner responsible for reconciliation.
- Define a pending state, order-hold policy, customer support route, and refund/duplicate-payment handling.

### Workflow
1. Show only verified beneficiary details and clear payment instructions. Do not collect unnecessary banking or personal data.
2. Tell the customer how to identify the order and what status to expect while payment is pending.
3. Treat customer-submitted references, images, or messages as unverified input.
4. Match payment using an authorized provider/bank record and the merchant's reconciliation controls; record reviewer, timestamp, amount, and order reference.
5. Change order status only after verification. Route ambiguous, duplicate, partial, or unmatched transfers to a human queue.
6. Reconcile pending orders and payments on a defined operating schedule; notify customers accurately when verification is delayed.
7. Test failure, refund, duplicate, and unavailable-provider scenarios before launch.

### Output
A reviewed checkout instruction, pending/verified status model, reconciliation checklist, exception path, and named owner.

### Boundary
Do not scrape personal SMS or email, parse unapproved bank alerts, or rely on customer-provided screenshots as proof of payment. Verify current bank/provider terms, supported integrations, and fees. This is not financial or legal advice.
