# Handoff priority and deferral

Status: requested follow-up, explicitly dependent on bug/mistake recording skills.
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
The existing self-repair and handoff-enforcement owners (#199 and #196 at this checkpoint) must be
reconciled before changing their files. Replace unconditional same-turn dispatch and its host guards
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

## Next Steps

Complete the foundation and reconcile existing source owners, then implement one bounded priority and
deferral slice. Full machine-wide admission and monitoring remain in
[the orchestration plan](../agent-orchestration/GAMEPLAN.md).
