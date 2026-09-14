# Finance and Approval Commands

## Folio, payment and documents

| Command | Initiator | Preconditions / result |
| --- | --- | --- |
| `CreateFolio` | Reception, Manager, Owner | Opens financial workspace for permitted relationship. |
| `AddStandardCharge` | Reception, Manager, Owner | Approved service / standard price; source retained. |
| `RequestChargeAdjustment` | Reception | Creates approval request when adjustment exceeds permitted scope. |
| `ApproveChargeAdjustment` | Manager, Owner | Approval and immutable audit data. |
| `AddGuestCredit` | Reception within limit; Manager, Owner | Creates non-revenue credit with source. |
| `CloseFolio` | Reception, Manager, Owner | Reception only when balance is zero and no outstanding issue; Manager can close approved exception. |
| `ReopenFolio` | Manager, Owner | Audited adjustment need. |
| `CreateProforma` / `CreatePaymentRequest` | Reception, Manager, Owner | Payer and amount defined. |
| `RecordCashPayment` / `RecordCardPayment` | Reception, Manager, Owner | Actual receipt through approved channel. |
| `RecordBankTransferPendingVerification` | Reception, Manager, Owner | Creates pending payment with structured reference. |
| `VerifyBankTransferReceived` | Manager, Finance-authorised user | Transaction ID/reference, amount, received time, verifier and evidence required. |
| `AllocatePayment` | Reception, Manager, Owner | Received payment; allocation does not exceed valid balance. |
| `CreateReceipt` | Reception, Manager, Owner | Actual money received. |
| `GenerateInvoice` | System at normal checkout; Manager for manual case | Finalised folio or legal/contractual trigger. |
| `ApproveManualInvoice` / `VoidInvoice` | Manager, Owner | Maker-checker for void; replacement invoice follows correction. |

## Refunds, deposits and close

| Command | Initiator | Approver / condition |
| --- | --- | --- |
| `RequestRefund` | Reception, Manager, Owner | Refund ≤1,000,000 IDR: Manager; above: Owner. Creator cannot approve. |
| `ApproveRefund` | Manager, Owner | Executes only within role limit and after evidence review. |
| `ReceiveSecurityDeposit` | Reception, Manager, Owner | Creates refundable liability, not revenue. |
| `RequestDepositDeduction` | Reception, Manager, Owner | Evidence, reason code and amount required. |
| `ApproveDepositDeduction` | Manager ≤1,000,000 IDR; Owner above | Maker-checker required. |
| `ReturnSecurityDeposit` | Reception, Manager, Owner | Held balance and approved deductions reconciled. |
| `CloseDailyCash` | Reception, Manager, Owner | Reconciliation passes; a Reception-initiated close requires Manager/Owner approval. |
| `ReopenDailyClose` | Manager, Finance Admin, Owner | Audited exception with reason and maker-checker when applicable. |

## AI command boundary

AI may submit `CreateInquiryDraft`, `CreateQuoteDraft`, `CreatePaymentRequest` draft, `CreateShortHold`, `AddToWaitlist`, `SendApprovedReminder`, `RequestReservationChange`, task creation, room suggestions, alternative-room suggestions, transfer requests, wellness appointment requests and approved routine guest messages. Complaint and safety communication remains human-approved.

AI cannot execute `ConfirmReservation`, `CancelConfirmedReservation`, `Refund`, `DeductDeposit`, `VoidInvoice`, `ForceCheckout`, `PriceOverride`, `ApproveSpecialistReview` or owner/permanent/manual room blocks. It prepares a draft, suggestion or approval request instead.
