# Handoff priority and deferral

<!-- BEGIN plan-tracker-migration -->
Current work is tracked through the selected Personal GitHub provider. This document retains design, decisions and historical evidence. Recording does not change implementation authority or existing delivery ownership.

- [Reconcile handoff priority and deferral](https://github.com/tj-agents/docs/issues/12)
<!-- END plan-tracker-migration -->

Status: selected for execution; prerequisite PR #206 is merged and published. Existing native owner successfully resumed.
Decision recorded: 2026-10-11. Source owner: tj-agents/core.

## Required behavior

Before creating or resuming work, reconcile its existing goal and exact native context. Reuse the current
owner or reopen its verified resumable CLI. A genuinely independent work item may receive a new context.

Decide whether the handoff can execute now before comparing priority:

1. Confirm authority and find any existing owner, launch attempt or repair already covering the cause.
2. Check required capabilities and explicit dependency results. A merge alone is not installed recovery.
3. Check conflicting writers, overlapping owned files and shared resources, then available capacity.
4. Launch or resume eligible work through the existing supported skills; order runnable work by impact,
   urgency, blocker fan-out and age. P1 severity does not stop unrelated work.
5. Otherwise use the problem-recording skills to record or update why it is deferred, the responsible
   owner/resolver, `blocked_by` or conflict reference, resume evidence and the exact next action.

A bug, mistake or debt record remains the canonical home for its repair. An ordinary feature handoff
waits in its existing feature/work-item goal and links the blocking problem; it must not be mislabelled
as a bug just to put it in a backlog. Repeated reports and retries do not create additional records or CLIs.

## Dependencies and implementation boundary

The [bug/mistake/debt foundation](../problem-management/PLAN.md) must provide the record contract first.
Owner reconciliation selected existing PR #199 and native session
`01a12ad4-3f5b-7c72-ad11-ea65007cdd0c` for this slice. Its original goal excluded the cancelled #196
receipt/wording work; preserve that exclusion and artifacts rather than restarting that PR. Replace unconditional same-turn dispatch and its host guards
together: a verified deferred disposition retains the obligation and is accepted when launch cannot run.

A saved blocker is only the foundation. Automatic resumption additionally needs a verified monitor or
supported continuation wake. The orchestration runtime owns that mechanism; do not claim documentation
alone resumes anything or install a competing polling loop. Use existing continuation where supported.

## Acceptance

- A broken skill/goal read capability blocks dependent workers and points to one repair; independent
  work remains eligible.
- Two tasks touching the same policy owner serialize or coordinate through its existing owner.
- Exhausted capacity queues work with a visible reason rather than spawning more terminals.
- Existing in-flight repair is reused; ambiguous launch outcome is reconciled before any retry.
- A verified dependency completion makes its dependent eligible exactly once; enabling actual automatic
  launch requires the supported wake and ownership mechanism to be active.
- Repeating an unchanged blocked condition does not produce an apology loop, duplicate records or
  recursive handoffs.

## Execution owner and next action

Tommy requested the next handoff after foundation completion on 2026-10-11. Reuse the existing
self-repair context `01a12ad4-3f5b-7c72-ad11-ea65007cdd0c`, observed non-live, and its checkout
`core/.worktrees/Fix-SessionGuidanceHandoffCompliance` / PR #199. The updated canonical implementation goal
is `plans/session-guidance-handoff-compliance/GOAL.md` within that checkout. It owns current scope,
source-policy reconciliation, focused validation and delivery; the shared docs remain coordinator-owned.

`machine:open-codex` reopened this exact native context with exit 0. Its native transcript records
the new priority handoff at 20:41:31 UTC, an assistant response at 20:41:34, and successful handoff/goal
reads by 20:41:55 on 2026-10-11. Resume and initial execution are observed; implementation and delivery
remain outstanding. The coordinator has released source-path writes to that same existing owner. PR #199's old guard/Linux CI failures are part of that owner's reconciliation, not a reason to
spawn another repair. Full machine-wide admission and monitoring remain in
[the orchestration plan](../agent-orchestration/GAMEPLAN.md).
