# FW-082 — Worked Example

**Illustrative scenario only.** A store lets customers pay by bank transfer and enter an order reference at checkout.

The checkout confirms that the order is pending, explains that the reference is not proof of payment, and provides a support route. A finance operator compares the order against an authorized bank/provider transaction record, records the match, and then updates the order status. Unmatched or duplicate transfers go to an exception queue.

No real reference number, account data, or client result is used in this example.
