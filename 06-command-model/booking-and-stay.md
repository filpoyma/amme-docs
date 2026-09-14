# Booking and Stay Commands

## Sales and reservation

| Command | Initiator | Preconditions | Success / principal event | Exception outcome |
| --- | --- | --- | --- | --- |
| `CreateInquiry` | Reception, Manager, Owner | Name and phone present | `Inquiry Created` | — |
| `CreateInquiryDraft` | AI | Approved source and policy | Draft inquiry for staff review | AI never confirms it |
| `CreateHold` | Reception, Manager, Owner | Category capacity; actor hold limit | `Hold Created` | `CONFLICT` / `REJECTED` |
| `CreateShortHold` | AI | One active AI hold; 15-minute limit | `Short Hold Created` | `REJECTED` |
| `CreateQuoteDraft` | Reception, Manager, Owner, AI | Offer data available | Quote draft | AI cannot issue a commercial exception |
| `IssueQuote` | Reception, Manager, Owner | Valid price snapshot | `Quote Issued` | Approval if override exceeds limit |
| `RecordQuoteAcceptance` | Reception, Manager, Owner | Payment, written acceptance or signed terms evidence | `Quote Accepted` | — |
| `CreatePaymentRequest` | Reception, Manager, Owner | Payer and amount defined | `Payment Request Created` | — |
| `ConfirmReservation` | Reception, Manager, Owner | Accepted quote; payment condition; concrete allocation; required guest data | `Reservation Confirmed` | `APPROVAL_REQUIRED` for full-villa confirmation or group/retreat exception; `CONFLICT` if room lost |
| `CancelReservation` | Reception, Manager, Owner | Reservation is cancellable | `Reservation Cancelled` with policy result | Maker-checker for cancellation exception |
| `RequestReservationChange` | Reception, Manager, Owner, AI | Target exists | Change request/draft | — |
| `AmendReservation` | Reception | Non-commercial change only: typo/contact; guest count within policy | `Reservation Amended` | `APPROVAL_REQUIRED` for commercial change |
| `ApproveReservationChange` | Manager, Owner | Guest approval; availability rechecked; policy passes | `Reservation Amended` | `CONFLICT` / `REJECTED` |
| `RestoreCancelledReservation` | Manager, Owner | Availability revalidated | `Reservation Restored` | `CONFLICT` |
| `MarkNoShow` | Reception, Manager, Owner | Arrival deadline and contact attempt recorded | `No Show Recorded` | — |
| `RestoreNoShow` | Manager, Owner | Availability and arrival evidence | `No Show Restored` | `CONFLICT` |

Reception may cancel a confirmed reservation under standard policy. Cancellation exception, group/retreat exception and full-villa exception require maker-checker approval.

## Arrival, departure and occupancy

| Command | Initiator | Preconditions | Success |
| --- | --- | --- | --- |
| `CheckIn` | Reception, Manager, Owner | Confirmed reservation; identity, house rules and financial check-in conditions pass | `Guest Checked In`; allocation becomes active |
| `RequestTemporaryIdentityException` | Reception | Technical/document issue with evidence | Approval request for up to two hours |
| `ApproveTemporaryIdentityException` | Manager, Owner | Deadline and reason recorded | Exception granted |
| `CheckOut` | Reception, Manager, Owner | Folio settled or approved balance exception | `Guest Checked Out`; room becomes dirty |
| `ForceCheckout` | Manager, Owner | Mandatory reason and maker-checker approval | `Guest Force Checked Out` |
| `RequestStayExtension` | Reception, Manager, Owner, AI | Desired new period | Extension request |
| `ApproveStayExtension` | Manager, Owner | Availability atomically rechecked; price/guest approval conditions pass | `Stay Extended` |
| `AssignRoom` / `ReassignRoom` | Reception, Manager, Owner | Valid allocation and no conflict | `Room Assigned` / `Room Reassigned` |

Reception may assign or reassign before check-in if availability remains valid. A commercial room-category change follows `RequestReservationChange` and Manager approval.
