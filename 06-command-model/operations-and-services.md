# Rooms, Services and Work Commands

## Rooms and operational blocks

| Command | Initiator | Preconditions / result |
| --- | --- | --- |
| `CreateCleaningBlock` | Reception, Manager, Owner | Creates a cleaning-specific sellability block. |
| `ReleaseCleaningBlock` | Reception, Manager, Owner | Reason and current room state recorded. |
| `CreateMaintenanceBlock` | Manager, Owner | Maintenance evidence / scope present. |
| `CreateManualBlock` | Manager, Owner | Reason and period present; long block cannot be created by Reception. |
| `CreateOwnerBlock` / `ReleaseOwnerBlock` | Owner | Owner use period recorded. |
| `SuggestOperationalBlock` | AI | Creates suggestion only; no room state change. |
| `MarkRoomReady` | Housekeeping staff, Reception, Manager | Cleaning completed, key areas checked, no open maintenance issue. |
| `RequestRoomInspection` | Reception, Housekeeping staff, Manager | Inspection-required condition recorded. |
| `AcceptRoomInspection` | Manager, assigned inspector | Evidence and applicable photo requirements pass. |
| `RejectRoomInspection` | Manager, assigned inspector | Creates rework with reason and assignee. |

## Wellness, transfer and retreat

| Command | Initiator | Preconditions / result |
| --- | --- | --- |
| `CreateWellnessAppointmentRequest` | Reception, Manager, Owner, AI | Creates `Requested`; AI cannot confirm. |
| `AddToWaitlist` | Reception, Manager, Owner, AI | No capacity or guest preference; creates waitlist record. |
| `RequestSpecialistReview` | Reception, wellness staff | Contraindication reported; moves to review. |
| `ApproveSpecialistReview` | Qualified wellness specialist | Specialist assessment; moves request toward confirmation. |
| `ConfirmWellnessAppointment` | Reception, Manager, Owner | Capacity and payment/guarantee policy pass; specialist review accepted when required. |
| `CreateTransferRequest` | Reception, Manager, Owner, AI | Creates `Requested`; provider confirmation remains pending. |
| `ConfirmTransfer` | Reception, Manager, Owner | Provider accepts and policy conditions pass. |
| `CreateRetreatRegistration` | Reception, Manager, Owner | Creates Inquiry/Reserved according to capacity. |
| `ConfirmRetreatRegistration` | Reception, Manager, Owner | Capacity and payment/guarantee policy pass. |

Manager cannot override a wellness specialist's medical/safety decision unless a separately approved clinical policy exists; no such policy is defined for the MVP.

## Tasks, maintenance and housekeeping

| Command | Initiator | Preconditions / result |
| --- | --- | --- |
| `CreateTask` / `AssignTask` / `ReassignTask` | Reception, Manager, Owner | Reception can only assign ordinary work. |
| `StartTask` / `UpdateTask` | Assigned worker | Worker owns progress updates. |
| `ResolveMaintenance` / `SubmitHousekeepingForInspection` | Assigned worker | Moves work to inspection state with required evidence. |
| `AcceptMaintenanceInspection` / `AcceptHousekeepingInspection` | Manager, assigned inspector | Closes ordinary approved work. |
| `CloseMaintenance` | Assigned responsible staff | Ordinary ticket only; critical ticket requires Manager/inspector. |
| `CreateHousekeepingTask` / `CreateMaintenanceTask` | Reception, Manager, Owner, AI | AI creates a task request within policy, never closes it. |
