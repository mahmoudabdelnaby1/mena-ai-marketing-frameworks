# InstaPay Checkout & Payment Reconciliation Review
## <span dir="rtl">مراجعة تجربة الدفع عبر InstaPay وتسوية المدفوعات</span>

Design clear transfer instructions and a safe order-reconciliation process using verified payment evidence from authorized sources.

## Prepare
Confirm payment instructions, beneficiary details, fees, settlement behavior, and payment confirmation source with the merchant's bank or provider. Assign a finance owner and define pending, verified, exception, and refund states.

## Workflow
1. Show only verified beneficiary details and clear order-identification instructions.
2. Tell customers that an entered reference, message, or screenshot does not itself confirm payment.
3. Keep the order pending until a transaction is matched to an authorized bank/provider record.
4. Record the match and reviewer; route ambiguous, duplicate, partial, or unmatched amounts to a human queue.
5. Test delayed confirmation, refunds, duplicate transfers, and provider downtime.

## Boundary
Do not scrape or parse personal banking SMS/email without authorization, and do not mark an order paid based solely on customer-submitted evidence. Verify provider features and fees directly. This is general operational guidance, not financial advice.
