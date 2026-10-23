# Workflow and Agent Store boundaries

## Decision status

This is the standing architecture decision approved under the 21 October 2026 dispatch. Responsibility
boundaries and acceptance gates remain distinct from implementation evidence.

As of 23 October 2026, Core's [lifecycle source](https://github.com/tj-agents/core/pull/355) and
[selection and review cleanup repair](https://github.com/tj-agents/core/pull/356) are merged and their
causal package publication passed. [Marketplace selection](https://github.com/tj-agents/marketplace/pull/24)
and [Personal caller guidance](https://github.com/tj-agents/personal/pull/17) are also merged with passing
publication and native loading evidence. These deliveries do not complete the coordinated caller rollout.
The remaining repository declarations and caller acceptance stay with
[Core's Workflow and Agent Store GOAL](https://github.com/tj-agents/core/blob/Fix/WorkflowSelectionClosure/plans/workflow-agent-store/GOAL.md).
[Core's continuation incident](https://github.com/tj-agents/core/issues/364) remains open: scheduler
registration alone does not prove progress through a delayed decision and terminal reporting.

## Responsibilities

| Owner | Responsibility | Boundary |
| --- | --- | --- |
| Base | Universal entry routing | Routes substantive work to selected Workflow; it does not run a lifecycle. |
| Agent Store | Recorded execution, session, ownership and reference state | Owns SQLite schema, transactions, identities and atomic claims; an unended row is not process-liveness proof. |
| Machine | Native observation and host operations | Observes processes, attaches sessions, launches, reopens and operates terminals; it does not reinterpret recorded state as a lifecycle decision. |
| Workflow | Generic lifecycle | Owns the single whole-goal owner and the public plan, run, resume, status and handoff subjects. |
| Engineering | Technical operations | Supplies bounded software design, implementation, diagnosis, testing, review and delivery evidence to Workflow. |
| Personal | GitHub profile operations | Retains Personal's GitHub records, identity checks, factual updates and closure policy. |
| Infonetica | Azure profile operations | Retains Infonetica's Azure records, native-type policy, identity checks and company delivery gates. |

Workflow has one generic lifecycle owner. `workflow:run` can execute with or without a plan, retains the
whole goal across phases and delegates bounded technical work where appropriate. Engineering operations
do not establish a competing whole-goal lifecycle when Workflow has accepted the goal.

The public Workflow surface is `workflow:plan`, `workflow:run`, `workflow:resume`, `workflow:status`
and `workflow:handoff`. There is no `workflow:review`: plan and run own readiness and completion
responsibilities, while `engineering:review` remains the code-review operation. Review-only authority
does not grant repair, execution or publication authority.

## Capability graph

Arrows mean a declared capability requirement. The graph is acyclic.

```text
Agent Store -> no lifecycle or host package
Base        -> no lifecycle package; route substantive work to selected Workflow
Machine     -> Base, Agent Store
Workflow    -> Base, Agent Store, Machine
Engineering -> Base, Workflow, Agent Store, Machine
```

Base alone can handle ordinary questions. Generic sustained work selects Workflow and its closure.
Software work selects Engineering and that same closure. A missing selected capability must be reported;
entry routing must not imply that tracking or execution occurred when its required package is absent.

## State, runtime and profiles

Agent Store records durable state. Machine makes explicit native observations. Workflow status may combine
recorded state with selected tracker reads and a stated Machine observation, but no layer may treat a
stored row as proof that a native process is live. Existing atomic ownership rules remain in force: a
live or ambiguous owner is reconciled, never silently taken over.

The canonical runtime is authored once at `.agents/agent-store/runtime/` and embedded unchanged at the
same package-relative path in each consuming payload. A consuming package loads its own packaged bytes,
never a sibling plugin cache or author checkout. This keeps payloads self-contained while Agent Store
remains the API and runtime source owner; it does not introduce a resolver service or a second registry.

Personal and Infonetica are distinct profiles, not lifecycle owners. Personal retains GitHub-specific
record operations. Infonetica retains Azure-specific native type handling and company delivery controls.
Profile producer dependencies and repository ownership never establish profile adoption. A reconciled
profile item enters Workflow with the same canonical identity and its existing mapped Engineering technical
operation; Workflow reuses or acquires the sole goal owner, and Engineering returns technical evidence.

## Gates and caller acceptance

Three gates remain separate:

| Gate | What it proves | What it does not prove |
| --- | --- | --- |
| Source | Canonical sources, generated mirrors, manifests and tests agree | Selected packages are installed or active on a host. |
| Declaration | Catalog and project selection express the required closure | A host has accepted, installed or activated that selection. |
| Native activation | A fresh supported host resolves selected installed entry points | Source or declaration work was sufficient on another host. |

Known callers must be accepted together: Core lifecycle callers and adapters, Marketplace catalog and
project declarations, Personal GitHub guidance, Infonetica Azure guidance, and affected already-bound
readers. Source generation, a passing test suite, a catalog entry, or a selection declaration alone is
not that acceptance. Each caller needs its applicable source, declaration and native gate evidence.

Publication follows the coordinated order recorded by Core: source stack, generated-package publication,
then marketplace exposure. Installed Windows and Linux host acceptance remain explicit evidence gates.
No decision here authorizes a launch, package installation, profile adoption, tracker operation or native
host activation.

## Sources

- [Canonical Core implementation plan](https://github.com/tj-agents/core/blob/Fix/WorkflowSelectionClosure/plans/workflow-agent-store/GOAL.md)
- [S1 source evidence: `5e815d06`](https://github.com/tj-agents/core/commit/5e815d0658597f031c332e9d2a3e3bb35d886e8a)
- [S2 source evidence: `7c77e7d5`](https://github.com/tj-agents/core/commit/7c77e7d5b1dc6c419b5096431018079e7c530026)
- [Status source evidence: `995f5e45`](https://github.com/tj-agents/core/commit/995f5e45caf269ca71ffd7235b4b1e520b9cc940)

- [Lifecycle source snapshot: `a6123ed9`](https://github.com/tj-agents/core/commit/a6123ed93061b9c8d816691ac69f71f711ca2c8a)

These commits identify source snapshots. The linked Core PR and goal own current implementation, review
and acceptance evidence; a source reference does not establish publication or activation.
