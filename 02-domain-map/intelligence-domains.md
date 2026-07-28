# Intelligence Domains

Intelligence modules improve decisions and coordination; they do not become a second transactional system.

## Automation

Rules react to domain events, delays and schedules. An execution records trigger, rule version, inputs, attempted commands, results and failures. High-risk actions require an approval step.

## AI workforce

Specialised agents (Sales, Concierge, Operations, Finance, Marketing, Analytics and Manager) form proposals or invoke authorised low-risk public commands. They may answer approved routine questions, collect data, draft requests, send reminders, add a guest to a waitlist and create one short-lived hold. They never confirm, cancel or amend a booking or appointment; change a room or staff schedule; issue discounts or refunds; alter money; or access health data without human approval. Every material action stores agent identity, policy version, evidence, confidence, tool calls and human intervention when applicable.

## Notifications

Messages may be triggered by people, automation or AI. Channel delivery is independently observable (`Notification Sent`, `Notification Failed`); it must not be confused with the business event it communicates.

## Analytics

Dashboards, reports and forecasts use denormalised read models and events. They may identify anomalies or recommendations but cannot write operational records directly.

## Guardrails

- Payment, refunds, safety, sensitive documents and irreversible guest-impacting actions have explicit permission/approval rules.
- AI uncertainty produces escalation, not invented certainty.
- An insight is not a decision; a proposal is not an action; a sent notification is not proof that a guest acted.
