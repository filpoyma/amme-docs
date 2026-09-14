# State Machines

This stage makes the approved lifecycle rules executable in principle: every state has allowed incoming/outgoing transitions, a responsible actor and terminal conditions. Commands, APIs and database constraints follow later.

## Reading order

1. [Reservation and room allocation](reservation-and-allocation.md)
2. [Room operations](room-operations.md)
3. [Finance](finance.md)
4. [Services and operational work](services-and-work.md)

## Conventions

- Arrows are allowed transitions; all unlisted transitions are forbidden.
- Terminal states have no ordinary outgoing transition. Exceptional correction uses a separately authorised command and audit record.
- `Overdue` is a collection condition, independent of an invoice's payment status.
- Room operational state and sellability overlay are independent so that a room can be both `Dirty` and `Blocked`.
