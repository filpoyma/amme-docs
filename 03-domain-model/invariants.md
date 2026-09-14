# Cross-Aggregate Invariants

These rules must hold across commands and later database transactions. They are not mere UI validation.

1. A confirmed Room Reservation has one active allocation to a specific Room for its whole sellable period.
2. Two active allocations for the same Room cannot overlap in time.
3. An active Hold consumes only category capacity and expires at its recorded deadline. Its holder cannot exceed the configured hold limit.
4. A Room Allocation cannot be created or extended across an active blocking condition, except a documented minor-defect decision by a Manager.
5. Confirmation is a human-authorised Booking action. AI, events and payment receipt alone cannot perform it.
6. A master booking may contain mixed reservation states; individual reservation commands do not overwrite sibling states.
7. `Overdue` is a Finance obligation condition. Cancelling an unpaid reservation is an explicit Booking command with a recorded reason.
8. An issued invoice's payer snapshot, lines, monetary totals and invoice number cannot change. Correction creates a void plus replacement invoice.
9. A payment allocation is positive, idempotent and cannot allocate more than the invoice's remaining valid amount without an approved credit policy.
10. A refundable deposit is never recognised as revenue. Its deductions require Manager approval and its return cannot exceed its held balance.
11. A room charge for restaurant service requires an active stay and recorded guest authorisation.
12. A service appointment requires resource capacity. A waitlist request never consumes a confirmed service slot.
13. A package's internal allocations reconcile to its sold package price.
14. Medical data is not copied into general booking, invoice or kitchen records; each consumer gets only its least-privileged view.
