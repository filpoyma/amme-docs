# Finance Model

## Folio aggregate

`Folio` is the mutable financial workspace for a stay, group or commercial relationship. It owns billable `Charge` and `Credit` entries, their source reference, current balance and links to invoices. A charge records quantity, price, service/tax treatment, fulfilment status and author.

Accommodation, wellness, transfers and restaurant operations may request charges through Finance's public command. They never write folio entries directly.

## Invoice aggregate

`Invoice` is the immutable tax/financial document created from selected folio entries at checkout, or earlier when law or contract requires it. It owns numbered invoice lines, tax/service-charge amounts, issue date, currency and immutable `BillToSnapshot`. It is editable only while draft. Once issued it is immutable; a mistake is corrected by voiding the invoice and issuing a new one in the MVP.

An invoice may cover multiple rooms, guests, services and retreat components for one payer. Before payment, Finance issues a non-tax `Proforma` or `PaymentRequest`; after money is received it creates a `Receipt`. A booking may have several payment requests and receipts; the refundable deposit is a liability, not an invoice charge.

## Payment aggregate

`Payment` records money received through Cash, Bank Transfer, Card or QRIS. It owns one or more `PaymentAllocation` entries to invoices. This supports one payment paying several invoices and one invoice being paid by several payments. Allocations may not exceed the valid outstanding balance without an explicit credit policy.

Payment obligation status, including `Overdue`, is derived by Finance from issued amount, allocation, due date and approved grace period. It never changes Booking state directly.

## Refundable Deposit aggregate

`RefundableDeposit` tracks money held for a booking/stay separately from charges and revenue. It is visible on the Folio as a liability line, but is not a `Charge`. It records receipt, held balance, authorised deductions and return. Manager approval is required for deductions due to damage, minibar, unpaid charges or late checkout. The physical money may sit in the hotel's account, but it remains a refundable guest balance in the model.

## Finance rules

All money is IDR in the MVP. Taxes and service charge are separate amounts; only a Manager may change their rates. Supported discounts are percentage, fixed amount, package price and manual discount. A single daily cash balance is sufficient; daily close freezes ordinary edits and uses auditable correction operations.
