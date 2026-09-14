# Services and Operational Work

## Wellness Appointment

```mermaid
stateDiagram-v2
  [*] --> Requested
  Requested --> Waitlisted: no capacity
  Requested --> NeedsSpecialistReview: reported contraindication
  Requested --> Confirmed: capacity and payment condition pass
  Waitlisted --> Confirmed: guest consents; capacity and payment pass
  NeedsSpecialistReview --> Confirmed: specialist approves
  NeedsSpecialistReview --> Cancelled: specialist declines or guest withdraws
  Confirmed --> CheckedIn
  Confirmed --> Cancelled
  Confirmed --> NoShow
  CheckedIn --> InProgress
  InProgress --> Completed
  Cancelled --> [*]
  NoShow --> [*]
  Completed --> [*]
```

`No Show` is allowed only from `Confirmed`. A specialist-review case can be confirmed only after a qualified specialist authorises it. Cancellation/no-show releases the resource slot but does not perform an automatic refund.

## Transfer

```mermaid
stateDiagram-v2
  [*] --> Requested
  Requested --> PendingProvider
  PendingProvider --> Confirmed: provider accepts
  PendingProvider --> Cancelled
  Confirmed --> DriverAssigned
  Confirmed --> Cancelled
  Confirmed --> NoShow
  DriverAssigned --> GuestPickedUp
  DriverAssigned --> Cancelled
  DriverAssigned --> NoShow
  GuestPickedUp --> Completed
  Cancelled --> [*]
  NoShow --> [*]
  Completed --> [*]
```

## Retreat Registration

```mermaid
stateDiagram-v2
  [*] --> Inquiry
  Inquiry --> Reserved
  Inquiry --> Waitlisted
  Inquiry --> Cancelled
  Reserved --> Confirmed
  Reserved --> Cancelled
  Waitlisted --> Reserved: capacity released and guest accepts
  Waitlisted --> Cancelled
  Confirmed --> CheckedIn
  Confirmed --> Cancelled
  Confirmed --> NoShow
  CheckedIn --> Completed
  Cancelled --> [*]
  NoShow --> [*]
  Completed --> [*]
```

## Maintenance

```mermaid
stateDiagram-v2
  [*] --> Reported
  Reported --> Triaged
  Triaged --> Assigned
  Triaged --> Cancelled
  Assigned --> InProgress
  Assigned --> Cancelled
  InProgress --> AwaitingInspection
  AwaitingInspection --> Resolved: inspection accepted
  AwaitingInspection --> Assigned: rework reassigned
  AwaitingInspection --> InProgress: rework begins immediately
  Resolved --> Closed
  Cancelled --> [*]
  Closed --> [*]
```

## Housekeeping Task

```mermaid
stateDiagram-v2
  [*] --> Requested
  Requested --> Assigned
  Requested --> Cancelled
  Assigned --> InProgress
  Assigned --> Cancelled
  InProgress --> AwaitingInspection
  AwaitingInspection --> Completed: inspection accepted
  AwaitingInspection --> Rework: inspection rejected
  Rework --> Assigned
  Rework --> InProgress
  Cancelled --> [*]
  Completed --> [*]
```

`Cancelled` is allowed only before `Completed`. Photo evidence is mandatory when the applicable business rule requires it; acceptance/rejection is an authorised inspection action.
