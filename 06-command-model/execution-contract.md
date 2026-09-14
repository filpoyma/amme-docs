# Execution Contract

## Approval requests

| Request type | Default TTL | Approver | Maker-checker required |
| --- | ---: | --- | --- |
| Price override, discount, reservation change, refund | 24 hours | Manager / Owner by policy | Yes for critical commercial or financial action |
| Deposit deduction | 48 hours | Manager ≤1,000,000 IDR; Owner above | Yes |
| Full-villa confirmation | 12 hours | Manager / Owner | Yes |
| Force checkout | 1 hour | Manager / Owner | Yes |
| Critical maintenance | 30 minutes | Manager / assigned emergency authority | No when immediate safety action is needed |
| Specialist review | Until appointment time | Qualified wellness specialist | Specialist cannot be replaced by Reception |

Expired requests move to `Expired`; no financial or critical action executes automatically. The creator cannot approve their own request. An Owner may be the sole maker/approver only when explicitly operating alone; this exception is audited.

## Concurrency contract

Availability-changing commands validate and reserve their target atomically. If two employees confirm the same room/date range, the first successful transaction wins; the other receives `ROOM_NO_LONGER_AVAILABLE` and can call `SuggestAlternativeRoom` or inspect availability. Frontend availability checks are advisory and never sufficient.

The same rule applies to hold creation, allocation, extension, reassignment, service-resource confirmation and release of a sellability block.

## Error outcome vocabulary

| Outcome | Meaning |
| --- | --- |
| `NOT_AUTHORIZED` | Actor lacks permission. |
| `REJECTED` | Current state or non-overridable policy forbids the action. |
| `APPROVAL_REQUIRED` | An approval request was created; no business change occurred. |
| `PENDING_EXTERNAL` | Provider, payment verification or evidence is still required. |
| `CONFLICT` | The target changed concurrently. |
| `ACCEPTED` | Command executed and emitted its domain event(s). |
