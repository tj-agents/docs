# Controlled agent orchestration

Status: orchestration design proposal; problem skills delivered, handoff priority/deferral selected now.
Coordination: [shared roadmap](../agentic-delivery/ROADMAP.md). Updated: 2026-10-11.
Owner: tj-agents/docs for the cross-repository design. Core owns implementation of common behavior,
engineering workflows and machine runtime. Consumer repositories own adoption and their product defects.
Evidence reviewed: 2026-10-11. All times below are UTC. The diagnostic table records the earlier
incident; recovery status is updated in the shared roadmap and readiness section.

## Outcome and authorization

Tommy wants authorized work to advance without repeatedly reminding agents to continue, repair mistakes,
monitor dependencies or finish delivery. Independent contexts should have visible native tabs. The system
must survive blocked tools, interrupted sessions and a machine restart without spawning duplicate owners
or exhausting the machine. Severity alone must not stop unrelated work.

The original request selected investigation and a gameplan. Tommy subsequently authorized addressing
the read failure first through a native handoff. The orchestration implementation remains a proposal;
the model/effort/fast redesign is explicitly for investigation and discussion. The recovery evidence is now merged in core PR #205. Tommy selected bug/mistake skills next and explicitly
made handoff priority/deferral dependent on them. Their separate plans own those slices; wider runtime
architecture and profile migration remain proposals. Existing workstreams retain ownership.

Planning applies engineering:plan-authoring's common maintained-plan path and the skill-authoring
convention. The investigation is L3 in shape. The design warrants L1 consideration because global launch
admission, per-goal writer ownership and recovery interact across repositories and hosts: an incorrect
boundary can create competing writers or a recursive launch storm. Recording these classifications does
not claim an in-session model switch. A detailed core implementation design remains a subsequent step.

## What the evidence establishes

The audit sampled eight directly relevant Codex conversations, recent session metadata on both hosts,
active repair goals, the installed handoff contract, core continuation and launcher sources, and related
GitHub PRs. It is not a complete audit of every session or proof of the PC crash's OS-level cause.
Core's normal checkout was behind its remote; active worktree goals and live PR metadata were used for
in-flight changes. None of those worktrees was modified.

| Observation | Evidence | Consequence |
| --- | --- | --- |
| Ordinary shell reads fail before PowerShell starts; a reviewed execution outside the sandbox can read the same filesystem. | Reproduced in this planning session: `helper_unknown_error: setup refresh had errors`. | File extensions are not the useful diagnostic boundary. Execution-host health must be tested before dependent work launches. |
| A separately installed fixed runtime successfully ran ordinary sandboxed reads. | Sandbox repair goal and successor transcript: first fresh-host acceptance around 11:08; both original paths passed around 12:28. | Recovery has been proved for a particular runtime/session, not automatically for every existing or future session. |
| The repair explicitly preserved global runtime selection and required affected sessions to reopen with a specified runtime. | Sandbox recovery goal, sections "Status and next use" and "Recovery boundary". | Its narrow acceptance could pass while Tommy's wider ability to work remained broken. Record both outcomes and an owned adoption dependency; do not silently expand installation authority. |
| Approved recovery encountered another launch prerequisite failure. | Sandbox transcript: plugin-cache backup failed, direct launch was rejected, normal refresh later succeeded and normal launch followed. | Dependency failures need bounded recovery and one existing owner, with clear authorization boundaries. |
| Parent repeatedly reported a collaboration worker or an unconfirmed launch as a native handoff. | Continuation-heartbeat conversation, 11:04–11:31. | A narrative claim is insufficient. Requested transport, submitted launch, acknowledgement and accepted result need distinct states. |
| Stop hooks repeatedly prompted with no useful state transition. | Controller-association and merge-cleanup conversations: enabled scheduler reported unavailable; `binding-repo-changed` repeated after reconciliation and source repair. | Hook output must distinguish failed work from a failed observer and deduplicate unchanged failures. |
| The controller goal excluded a catalog change required to validate its manifest edit. | Controller-association conversation, around 12:30. | Handoffs need a coherent change boundary, including required companion artifacts; agents cannot invent extra permission questions for routine in-scope work. |
| Validation and changing upstream revisions consumed repeated cycles. | Dependent-PR cleanup conversation; Tommy explicitly requested focused local checks and the full suite in CI around 12:39. | Keep local feedback focused; track evidence against a stable candidate and avoid redundant broad reruns. |
| Existing continuation owns one worktree and branch, with per-owner budgets and receipts. | `persistent-workflow`, `continuation_runtime.py`. | Useful machinery exists. It does not establish a machine-wide launch budget or a complete cross-goal dependency scheduler. |
| Automatic source-repair guidance pushes toward immediate side handoffs. | Installed session-guidance and pending self-repair workflow. | Without shared admission, deduplication and a durable queued disposition, every new finding can create more work than the system can service. |

The sandbox repair record attributes the original setup defect to the upstream Codex Windows helper.
That is the repair owner's recorded diagnosis, not a fresh upstream source audit performed here.
The overnight period included an explicit pending installation approval. Elapsed wall time is not all
implementation time: after approval at 10:58, first fresh-host acceptance took about ten minutes;
reopening the original paths was verified around ninety minutes after approval.

The central failure is incomplete coordination between instructions, runtime state, delivery and installed
behavior. Models also made execution and reporting errors. More prose alone cannot make these transitions
reliable, and a faster model alone cannot resolve blocked launch prerequisites or stale hooks.

## Recommended capability ownership

Add one public workflow, provisionally `engineering:orchestration`, for supervising multiple authorized
goals and their dependencies. Confirm the name against both host catalogs before implementation.
It inventories existing owners, records the dependency graph, chooses runnable work and reconciles results.

Tommy selected `orchestrator` or `orchestration` as the name, and explicitly requires composition through
separate independently useful skills. Use `orchestration` in this proposal. The workflow actively invokes
the skills below and reconciles their results; it does not merely watch sessions or absorb their jobs
into one monolithic skill. Inventory the preserved self-improvement/self-repair work before designing a
replacement. Core PR #199 owns the current self-repair workflow; PR #196 owns related handoff
enforcement. The similarly named Feature-SelfRepair checkout has a stale unrelated goal, so its
directory name is not ownership evidence.

Keep related responsibilities with their existing owners:

| Capability | Proposed owner |
| --- | --- |
| Record bugs, process mistakes, technical debt and capability failures | Separate recording skills under the [problem contract](../problem-management/PLAN.md); retain merged `write-debt`. |
| Select and deliver a recorded repair | Separate addressing entry points composing existing bugfix/self-repair lifecycles; retain `address-debt`. |
| Detect a standards-related mistake and choose its disposition | Existing/pending `engineering:self-repair` and session-guidance. |
| Inspect process/session/tab identity | `machine:peer-cli`. |
| Start, reopen or transfer a native session | Existing machine launchers and `engineering:handoff`. |
| Writer lease, durable continuation, delivery identity | Existing continuation runtime and delivery contracts. |
| Cross-goal admission, dependencies, result reconciliation | New orchestration workflow plus a small shared runtime extension. |
| Human-readable status | Extend `engineering:workboard` to render authoritative state. |

Monitoring is a runtime responsibility within orchestration: inexpensive event checks and scheduled
reconciliation, with an LLM invoked when judgment or repair is needed. A separate public monitor skill is
only justified if read-only monitoring becomes independently useful enough to load on its own. It must
read the same state and must not create another task owner or scheduler.

An additional ownership skill is not required initially. Ownership is a shared contract consumed by the
orchestrator, handoff and continuation. The useful distinction is between responsibility for the outcome
and the current writer, not between two competing owner systems.

## Problem records

The independent [problem-management plan](../problem-management/PLAN.md) owns bug, mistake and debt
recording/addressing. Tommy selected those skills next. Their contract is a dependency of
[handoff priority and deferral](../handoff-priority/PLAN.md). This orchestrator consumes those records;
it must not create another backlog or dictate a storage migration itself.

## Ownership and task transitions

The orchestrator remains accountable for the overall outcome, even when a native child owns a distinct
repair. The child alone writes its assigned checkout. The parent may inspect status and accept evidence,
but it does not concurrently edit that child's goal, switch its branch or merge its PR.

Use a subagent for bounded work inside the current goal when shared context and a short lifetime make
sense. Use a native tab for an independent goal with its own context, review/delivery or continuing
lifetime, matching Tommy's preference. The scheduler controls when that tab starts. A visible independent
task must not silently be substituted with a collaboration worker.

Proposed task lifecycle:

`recorded -> queued/blocked -> admitted -> launching -> acknowledged -> running -> verifying -> complete`

Also represent `waiting`, `failed`, `needs-decision`, `cancelled` and `unknown`. A dead CLI is not a
completed goal. A live CLI is not evidence of progress. A completed repair does not complete its parent.
Terminal completion requires the task's acceptance evidence, including delivery and adoption where those
are in scope. Cleanup is an explicit obligation; a failed close does not erase a successful repair or
justify launching an unlimited chain of cleanup agents.

Persist a unique launch attempt before submission. An ambiguous launch is reconciled against that same
attempt and verified process identity. It is never retried merely because acknowledgement is late.
Completion events carry task, attempt, owner, repository and artifact/version identities. Delivery can
be at least once, but applying an event and waking a dependent must be idempotent. A child writes a durable
receipt before exit; a missed notification is recovered by reconciliation.

Reuse the per-goal writer mechanism rather than introducing a second writer lock. Add machine-wide
admission around all supported launch paths, including scheduled continuations and descendant workers.
Admission reserves capacity; the existing goal lease grants writing. Failure between those steps needs
an explicit reconciliation transition. Lock ordering and crash handling require focused design before
implementation. Elapsed lease time alone cannot justify a competing writer while process identity is
unknown. Multi-machine execution is outside the first release and needs a distributed ownership design.

## Scheduling and capacity

Start with a conservative configurable limit of two active workers across the machine, plus the user's
foreground coordination session. Reviews and descendant agents count toward the same worker budget.
Already running unmanaged sessions count as observed load, but are not killed or adopted automatically.
Sleeping/waiting tasks consume no LLM turns, though retained processes still count toward memory limits.
Cap expensive builds separately; initially permit one broad local build/test process at a time.

Make admission atomic across simultaneous parents. Add memory headroom and bounded launch-rate checks,
in addition to the worker count. Unknown capacity stops new launches and leaves a visible queued reason.
Existing work is allowed to checkpoint; the mechanism must not kill an arbitrary busy process to make room.

Eligibility comes before priority:

1. Confirm authority, capabilities, dependency evidence, an available writer and capacity.
2. Prefer work that restores capabilities required by many authorized goals, while accounting for impact.
3. Use severity and urgency among eligible tasks; use age to prevent starvation.
4. Continue independent work while another task is blocked. A P1 is not a global pause switch.

Example: a broken ordinary command runner blocks workers that require it; an authorized coordinator can
still analyze existing evidence through a functioning read path. A close-tab defect can queue unless its
retained processes exhaust capacity. If so, it becomes a capacity blocker. A broken monitor can block
unattended execution while bounded foreground work remains possible.

## Progress, notification and recovery

Track separate clocks for last heartbeat, last material progress, time waiting for a known dependency,
and time waiting for a human decision. Material progress is a new reproduction, causal finding, validated
change, useful review disposition, or dependency transition; another status paragraph is not progress.

Proposed initial budgets, tunable with measured evidence:

- Five minutes to acknowledge a launch; then reconcile the existing attempt instead of spawning again.
- Ten minutes without material progress on a high-impact blocking repair triggers inspection by its owner.
- Two repetitions of the same failure without new evidence trigger a changed diagnostic step or a single
  owned infrastructure incident. Known long-running commands have explicit expected bounds.
- A third unchanged stop-hook result is coalesced into one monitor/capability incident. The action it
  guarded stays blocked; suppressing repetitive messages must not grant permission to bypass the guard.
- Use the existing per-goal attempt/deadline budgets, plus an aggregate repair-family budget. Nested repairs
  inherit the remaining budget rather than resetting it by acquiring a new task ID.

One lightweight monitor records outcomes and wakes eligible dependents. The user should see a compact
board: task, owner/tab, state, blocker, last material progress and next action. Display queued, submitted,
acknowledged, running, verified and merged precisely. Avoid repeated narration of unchanged internal errors.

On restart, reconcile retained goal and launch records with verified live processes and durable results
before launching anything. A supervisor restart must not restart every pending task. A stale loaded hook
or runtime is a versioned dependency: a source merge alone cannot establish that a live session uses it.

## Automatic repair

The independent [self-improvement plan](../self-improvement/PLAN.md) owns observed-mistake response
and recurrence reduction, preserving the existing self-repair owner. Orchestration supplies shared
admission and wake mechanisms to that workflow.

## Independent supporting work

[Execution profiles](../execution-profiles/PLAN.md) owns model-only lanes, separate effort and fast
on/off. [Workflow efficiency](../workflow-efficiency/PLAN.md) owns handoff and validation overhead.
Neither is folded into orchestration or a prerequisite for the selected recording-skills slice.

## Delivery sequence

Deliver in small independently verifiable slices. Existing repair owners retain their work; resolve
overlap before assigning a slice. Repository source changes, plugin release and consumer adoption are
distinct milestones with separate authority and evidence.

| Order | Deliverable | Dependency and acceptance |
| --- | --- | --- |
| 0 | Read-only inventory of current goals, owners, sessions, PRs and capability health; establish a launch budget. | Start with existing records. No duplicate repair or guessed completion. Record unknowns and the sandbox recovery/adoption gap. |
| 1 | Finish the existing foundational recovery path and its normal-launch acceptance. | Reconcile sandbox, preflight and scheduler-verification owners. Verify a normal admitted worker can read its goal, a skill and text, run a command and report a result. Machine selection/adoption remains within its recorded authority. |
| 2 | Implement the selected bug/mistake recording and addressing skills, then handoff priority/deferral. | #173 is merged. Follow the separate problem and priority plans, preserving existing owners and verifying the record contract before dependent dispatch changes. |
| 3 | Add atomic machine-wide launch admission and capacity accounting. | Integrate supported handoff/typed launchers and continuation wakes; concurrent launch tests prove limits and crash reconciliation. Native unmanaged sessions are reported honestly. |
| 4 | Add durable task results, dependency evaluation and one shared monitor. | Reuse continuation and writer ownership. Verify lost/duplicate events, ambiguous launches, restart recovery and version-specific acceptance. |
| 5 | Add the orchestration entry point composing separate skills, and queued self-repair semantics. | Reconcile the preserved self-improvement work first. Same-state host guards accept real queued records; ready tasks dispatch, blocked tasks wait, parent accountability remains. Both hosts demonstrate the flow. |
| 6 | Pilot two workers, measure intervention and failure rates, then expand conservatively. | Package manifests/catalogs/grants ship together; test installed payloads on Windows and Linux. Consumer adoption is explicit and verified. |

After recovery, investigate model-only lanes, independent effort and fast on/off as a separate design
decision. It is not a prerequisite for the blocker repair or permission to change the ladder immediately.

Slices 1 and 2 can proceed independently where their tooling is healthy. Capacity work can be developed
in a healthy context while recovery is owned elsewhere. The ordering is an acceptance/dependency sequence,
not a requirement to halt every task until every earlier bug is fixed.

Reuse existing runtime and host adapters for the initial orchestration slice. Termboard already owns
the intended work-item/context association; use it when available, as recorded in the shared roadmap.
A table can expose initial status without inventing additional Termboard scope.

## Acceptance scenarios and measurement

1. Ten independent handoff requests arrive together: only available worker slots launch; all other
   requests remain visible and owned. Descendants cannot bypass the limit.
2. Several tasks require broken capability A: they wait on one repair; an independent task B proceeds.
3. A second user or agent report repeats the same failure: one task receives evidence, no extra worker.
4. A native launch times out after possibly succeeding: reconcile its attempt; never launch a duplicate.
5. A worker returns "done" but acceptance evidence is missing: dependents stay blocked and the owner sees
   the exact unmet condition.
6. A fixed runtime passes an isolated probe while ordinary launches remain broken: report partial recovery,
   retain adoption ownership, and keep affected dependents blocked.
7. The monitor misses a child notification or restarts: persisted results wake dependents once; a late
   result from an obsolete attempt cannot overwrite the current attempt.
8. A scheduler probe fails or a stale hook loops: record one observer incident, bound retries, preserve
   the guarded action and continue independent authorized work.
9. A separate standards mistake is noticed while capacity is full: record and queue automatically, then
   start its native worker when dependencies and capacity permit without another user reminder.
10. A CLI fails to close: preserve the completed task result, track cleanup and memory load, and avoid
    recursively spawning cleanup workers.
11. Restart with live, dead and unverifiable processes: recover verified ownership and reconcile unknowns
    without overwriting another writer.
12. Run the installed flow in a disposable consumer repository on both hosts, including restart recovery.
    Source-only unit tests and merged PRs do not substitute for installed-host acceptance.

Measure time to first useful action, blocker detection and dependent resumption, material-progress gaps,
human reminders per goal, duplicate launches, peak active workers/memory, repeated hook prompts and
recurrence after repair. Initial pilot targets: zero duplicate writers, zero launches over the budget,
no unchanged hook loop beyond its bound, and automatic resumption of the tested dependency chain.
Resource thresholds and time budgets should be adjusted from these measurements, not guesswork.

## Existing owners and evidence pointers

- Sandbox recovery: core `.worktrees/Fix-SandboxSetupReadFailure/plans/sandbox-setup-read-failure/GOAL.md`;
  sessions `01a127ec-ae44-7353-95d7-436f4fccfd74` and `01a12aec-7f71-7c73-aeaf-5fca3d754103`.
- Launcher recovery: core `.worktrees/Fix-CodexPreflightRecovery/plans/codex-preflight-recovery/GOAL.md`;
  session `01a12aef-9dbc-7cb2-b5a6-b5ac56b71cf0`.
- Handoff enforcement: [PR #196](https://github.com/tj-agents/core/pull/196) and
  [PR #199](https://github.com/tj-agents/core/pull/199); the latter's workflow explicitly deduplicates a
  live source owner but does not provide the global admission mechanism proposed here.
- Parent continuation: [PR #194](https://github.com/tj-agents/core/pull/194).
- Cleanup: [PR #195](https://github.com/tj-agents/core/pull/195),
  [PR #198](https://github.com/tj-agents/core/pull/198) and follow-up
  [PR #202](https://github.com/tj-agents/core/pull/202). Recheck status before acting.
- Debt convention: [PR #173](https://github.com/tj-agents/core/pull/173), with alias routing
  [PR #197](https://github.com/tj-agents/core/pull/197) and noticed-problem recording
  [PR #168](https://github.com/tj-agents/core/pull/168).
- Continuation-heartbeat conversation: `01a12745-ab05-7d12-8a0c-0d6bfc04ee41`.
- Controller-association conversation: `01a12aa7-5b58-7312-9400-ef710762147f`.
- Dependent-cleanup conversation: `01a127b0-7047-7e30-af8c-c861898d7e5b`.
- Merge-cleanup conversation: `01a12aa8-8f88-7b91-865e-a6262d5b1a43`.
- Existing [plan-persistence proposal](../plan-persistence/PLAN_PERSISTENCE_PLAN.md) retains ownership of
  plan location/persistence. This proposal links to it and does not introduce a competing plan scheduler.

Private transcripts are not copied into this repository. Session IDs and summarized observations support
local audit; public PR links identify source repairs. PR status is time-sensitive and must be refreshed
before execution.

## Readiness and next action

This gameplan is ready for discussion, not a claim that the runtime design is implemented or fully
specified. Remaining implementation design: the atomic admission store/locking protocol and migration,
the exact supported host event transport and wake adapter, the fault-tolerant capability probe, machine
resource thresholds, and the host controls needed to account for descendant workers.

The key proposed decisions are one orchestration workflow composing separate skills, one problem record
per repair, two active workers initially, dependency-based admission, queued automatic repairs, and
installed-behavior acceptance. Orchestration implementation approval is still required.

The [problem-skills foundation](../problem-management/PLAN.md) merged and published in PR #206.
Immediate selected action: [handoff priority/deferral](../handoff-priority/PLAN.md), reusing the existing
self-repair owner rather than opening a duplicate context. Recovery acceptance and incident evidence merged
in core PR #205 on 2026-10-11. That records the approved machine repair; it does not update this already
running session's runtime. Existing repair and self-repair contexts retain ownership.

No new unattended monitor has been established by this planning session.
