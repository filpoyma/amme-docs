# Reservations

| Business events | AI events | Human decisions / overrides |
| --- | --- | --- |
| Booking Created; Room Allocated; Booking Confirmed; Deposit Deadline Set; Booking Amended; Room Reallocated; Booking Cancelled; Cancellation Fee Applied; Booking Restored | AI Detected Availability Conflict; AI Proposed Room Assignment; AI Predicted Cancellation Risk; AI Proposed Upsell; AI Held Room Temporarily | Manager Approved Exception Rate; Receptionist Overrode Allocation; Manager Waived Cancellation Fee |

Core invariant: a room cannot have overlapping confirmed allocations for the same inventory interval.
