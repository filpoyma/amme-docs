# Finance and Settlement

## Folio, requests, receipts and invoices

The Folio is the live ledger of charges, credits, package inclusions and refundable-deposit liability. Before payment, Finance may issue a `Proforma` or `PaymentRequest`. Receiving money creates a `Receipt` and Payment record. Finance creates the immutable Invoice at checkout or earlier if legally/contractually needed.

An invoice correction uses void-plus-replacement; it never edits an issued document. Tax and service charge are separate, versioned monetary components and only a Manager may change their rates.

A closed day is reopened only by a Manager, Finance Admin or Owner through an audited exception command.

## Deposit, credit and payments

- A refundable security deposit is collected at check-in: base amount **1,000,000 IDR per room**.
- A Manager may increase it for full-villa buyout, long stay, an approved risk flag or special event; the reason and amount are recorded before collection.
- The deposit appears on Folio as a refundable liability, is held separately from revenue and returns after checkout unless approved deductions apply.
- Manager approval is required for deductions for damage, minibar, unpaid charges or late checkout.
- Overpayment becomes `Guest Credit`, not revenue. It may pay accommodation, restaurant, wellness, activities and — where policy allows — a future booking. Returning credit follows the refund workflow.
- Payment dispute/chargeback creates `Payment Disputed` and `Financial Risk`. It does not automatically block the guest or checkout; checkout is blocked only by a real outstanding balance.

## External and restaurant services

An external-provider service can be created as `Pending External Service`, but no confirmed Folio charge exists until the provider confirms. 

Restaurant complimentary actions require a reason: kitchen error, wrong dish, material delay, Manager hospitality or service recovery. Staff meals are a separate transaction type. Every complimentary charge retains its reason code and approver.
