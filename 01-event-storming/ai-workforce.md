# AI Workforce

AI agents are workers with bounded authority, not an untraceable automation layer.

| Business events | AI decision and action events | Human decisions / overrides |
| --- | --- | --- |
| Agent Policy Published; Agent Authority Granted; Agent Authority Revoked; Escalation Created; Escalation Resolved; Agent Run Completed; Agent Run Failed | AI Reservation Agent Started Conversation; AI Reservation Agent Sent Quote; AI Concierge Suggested Experience; AI Concierge Created Service Request; AI Operations Agent Replanned Work; AI Kitchen Agent Generated Prep Plan; AI Revenue Agent Proposed Rate; AI Finance Agent Matched Payment; AI Safety Agent Escalated Incident | Manager Approved Agent Policy; Manager Rejected AI Action; Manager Took Over Conversation; Manager Suspended Agent |

## Minimum audit envelope

Every AI decision/action requires: `agent`, `policyVersion`, `inputReferences`, `decisionOrAction`, `confidence`, `authorityBasis`, `correlationId`, `timestamp` and, where applicable, `approver`.

The phrase “AI learned” is deliberately absent: model learning or prompt changes need a separate governed evaluation and release process, not an ambiguous production event.
