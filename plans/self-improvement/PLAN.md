# Automatic repair and improvement

Status: existing core self-repair owner selected for the priority/deferral follow-up after PR #206.
Updated: 2026-10-11.

## Existing source owner

Core [PR #199](https://github.com/tj-agents/core/pull/199), branch
`Fix/SessionGuidanceHandoffCompliance`, owns `self-repair`. Its recorded native session is
`01a12ad4-3f5b-7c72-ad11-ea65007cdd0c`; verify identity and liveness before resuming.
The directory called `Feature-SelfRepair` contains a stale unrelated goal and is not evidence of ownership.
PR #196 contains related native-handoff enforcement, but #199 explicitly excludes that cancelled
receipt/wording work. Preserve the exclusion and its artifacts. The coordinator selected this exact
#199 native context for the next priority/deferral slice; its existing canonical goal is updated.

## Desired behavior


When a mistake is observed, including by the agent itself:

1. Answer the user directly when a question was asked; identify evidence and the governing owner.
2. Record or deduplicate the problem immediately. A suspicion remains a triage item until supported.
3. Link to an existing live repair when one already owns the cause.
4. Repair a small inseparable in-scope defect within the current task when appropriate.
5. For an independent authorized repair, request scheduler admission for one native successor.
6. If capabilities, dependencies or capacity prevent launch, retain a queued/blocked record with a resolver
   and wake condition. Recording it is a valid current disposition; it is not declaring the repair done.

Update the current unconditional "launch in the same turn" rule and its host enforcement together.
The enforceable invariant should become "record, reconcile and assign a valid disposition before moving
on; dispatch immediately when eligible." Hooks must accept a verifiable queued dependency and retain
the repair obligation, rather than forcing a launch that cannot work.

Repeated symptoms of the same cause add evidence to its existing task. Distinct failures of the repair
machinery are recorded, but do not recursively open tabs without admission. This prevents the current
failure mode in which fixing the response to a mistake creates another handoff before the first one can run.

This is an improving engineering system: detect -> record -> prioritize -> repair -> test -> review ->
deliver -> verify adoption -> measure recurrence. It changes skills, tools and tests, not model weights.
It cannot promise that an LLM never makes another mistake. Its measurable promise is that errors are
contained, visible and recoverable, with less dependence on Tommy noticing and restarting work.

## Dependencies and next action

Use the [problem skills](../problem-management/PLAN.md) and
[handoff priority/deferral](../handoff-priority/PLAN.md) rather than a second record or dispatch system.
Resume the existing owner when this slice is selected. Preserve existing work and evidence; do not start
a replacement merely because its original terminal is closed.
