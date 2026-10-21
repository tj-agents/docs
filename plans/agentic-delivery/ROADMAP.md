# Agentic delivery roadmap

<!-- BEGIN plan-tracker-migration -->
Current work is tracked through the selected Personal GitHub provider. This document retains design, decisions and historical evidence. Recording does not change implementation authority or existing delivery ownership.

- [Reconcile agentic delivery roadmap](https://github.com/tj-agents/docs/issues/10)
<!-- END plan-tracker-migration -->

Status: shared coordination record, not blanket implementation approval.
Updated: 2026-10-11. Owner: tj-agents/docs; source repositories retain their implementation goals.

## Selected next work

The normal-launch recovery evidence is merged in core PR #205; that PR records the approved machine
repair and successful fresh-launch probes, rather than shipping the upstream runtime change itself.
Existing loaded sessions can still use their old runtime. Do not restart the completed diagnosis or
interfere with its surviving CLI owners. The debt split is merged in PR #173.

The bug and mistake foundation merged in PR #206 and generated publication passed. Tommy then requested
the next handoff: handoff priority and deferral, using the delivered record contract. A request for useful
parallelism is not a request to open a tab for every idea or restart existing owners.

| Workstream | Canonical design | Dependency / present disposition |
| --- | --- | --- |
| Bug, mistake and debt recording/addressing | [Problem skills](../problem-management/PLAN.md) | Delivered in #206; generated publication verified. |
| Handoff priority, conflicts and blocked dispositions | [Priority and deferral](../handoff-priority/PLAN.md) | Selected now; resume the existing #199 owner with the delivered record contract. |
| Automatic source repair and recurrence reduction | [Self-improvement](../self-improvement/PLAN.md) | Reuse #199 for priority/deferral; preserve its explicit exclusion of cancelled #196 work. |
| Multi-goal orchestration and monitoring | [Orchestration](../agent-orchestration/GAMEPLAN.md) | Compose independent skills; runtime ownership and capacity need detailed design. |
| Model-only lanes, independent effort and fast | [Execution profiles](../execution-profiles/PLAN.md) | Independent investigation/discussion; no approved migration. |
| Handoff/core workflow overhead | [Workflow efficiency](../workflow-efficiency/PLAN.md) | Select measured bottlenecks and reuse existing fixes. |
| Work items linked to native agent contexts | Existing Termboard plans | User-owned Rust learning project; see boundary below. |

## Termboard boundary

Tommy's existing Termboard design already associates features/work items with native agent contexts.
Opening or resuming through the work item supplies the context lookup that failed in this conversation.
Integrate orchestration/open skills with that intended association when Termboard is available; do not
invent extra Termboard requirements as a prerequisite or duplicate its context registry in another UI.

The existing canonical plans are `termboard/plans/ROADMAP.md` and the referenced
`agent-workboard/plans/agent-workflow-state-authority/MANAGED_WORK_ITEM_LAUNCH.md` in Tommy's local repos.
Termboard implementation remains with Tommy in learning mode and is not authorized by this roadmap.
Until then, peer-cli and exact native resume identity provide the supported lookup path.

## Mistakes and lessons retained from this conversation

The coordinator launched a fresh sandbox-repair context before using the existing session-recovery path.
The prior work and commits were still present; a new context did not mean that work was lost. The durable
correction is owner/session lookup before dispatch, preserving existing work and reopening when appropriate.
The coordinator also overstated missing Termboard requirements despite the existing work-item/context
design. Inspect the named plan and identify only evidenced gaps before proposing additional scope.
These observations should be reconciled into the selected mistake convention without duplicating M001-M007.

## Next Steps

The foundation is delivered. The exact existing self-repair native session was reopened for the
priority/deferral slice. Its native transcript confirms the new handoff and successful initial reads
at 20:41 UTC. Its canonical goal in `Fix-SessionGuidanceHandoffCompliance` owns implementation and
delivery; the coordinator no longer writes that checkout. Follow the [priority plan](../handoff-priority/PLAN.md) for the
source owner and actual launch outcome. No new unattended orchestration monitor has been installed here.
