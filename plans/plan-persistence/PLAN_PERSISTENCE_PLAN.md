# Durable plan persistence

## Status

Draft: source findings and lifecycle constraints recorded; cleanup choice and exact implementation mechanisms await design and review.

## Scope

This cross-repository plan defines a durable lifecycle for canonical plans, progress records and roadmaps. The selected central plans repository for this scope is [tj-agents/docs](https://github.com/tj-agents/docs). It does not authorize runtime, policy-binding or installation changes.

## Persisted requirements

- All future canonical plans and their progress records belong in the selected central plans repository, in one canonical remote location. Source repositories and execution branches retain references only.
- Create the initial record in the existing ordinary main checkout, publish it directly to origin/main, and verify the remote publication before implementation, handoff or declaring it persisted. Do not create a planning branch or worktree.
- Publish each material plan update immediately, before dependent work or handoff continues. Verify the remote state and preserve local commits if transport fails.
- Ordinary implementation branches remain source-owned and follow their repository's normal rules. The no-planning-branch rule does not prohibit implementation branches.
- Existing plans retain their current owners until explicit migration or completion. This direction applies to all future plans and does not authorize moving or deleting existing owner plans.
- Retain unfinished plans, including multi-PR outcomes, until all authorized outcome and delivery gates are terminal.
- Never force-push, discard concurrent work or overwrite a same-plan edit. Failed, offline or non-fast-forward publication blocks dependent execution and handoff until publication succeeds.

## Source evidence

As of 2026-10-09, the existing planning guidance assigns conflicting responsibilities that must be reconciled together:

- Base plan-artifacts assigns plans to source repositories or standalone task directories.
- Engineering plans assigns active delivery branches to source ownership and publication to a docs PR.
- Plan-checkpoint correlates plans with source checkouts and disallows separate transport-only updates.
- These storage and publication clauses must change together while retaining whole-plan retention, meaningful checkpoints and code-review gates.
- The workflow runtime currently anchors repository state and checkpoint validation to a source repository. In [workflow_runtime.py](https://github.com/tj-agents/core/blob/main/.agents/workflows/workflow_runtime.py), RepositoryStateProvider.resolve and validate_checkpoint reject external artifact paths, and _repository_path_key enforces containment.
- [workflow_ops.py](https://github.com/tj-agents/core/blob/main/.agents/workflows/workflow_ops.py) inspect_repository discovers source plans/*_PROGRESS.md; delivery_owner resolves ownership through the provider.
- [plan_graph.py](https://github.com/tj-agents/core/blob/main/.agents/hooks/plan_graph.py) validates a selected --root and assumes the plan, ledger and roadmap share that repository. owner_ledger_path must resolve the canonical ledger rather than substitute a source-worktree copy.
- [plan_handoff_stop.py](https://github.com/tj-agents/core/blob/main/.agents/hooks/plan_handoff_stop.py) uses branch_ledgers, logical_ledger_key and owner_copy_score with source-local assumptions.
- The v2 [state schema](https://github.com/tj-agents/core/blob/main/.agents/workflows/contract/v2/state.schema.json) has no artifact-repository identity field and rejects unknown fields.
- The continuation runtime already preserves an explicit absolute external goal through initialize and check_identity; its test is test_absolute_external_goal_survives_claim_yield_repair_and_wake. Reuse that behavior and the [external-goal continuation plan](https://github.com/tj-agents/core/blob/main/plans/external-goal-continuation/EXTERNAL_GOAL_CONTINUATION.md), which owns cross-worktree continuation transitions.
- Planning and auto-merge publication ownership is already tracked in the sibling [standards-composition proposal](https://github.com/tj-agents/docs/blob/main/plans/standards-composition/STANDARDS_COMPOSITION_PLAN.md). Link that proposal; do not introduce a second auto-merge authority or scheduler.

## Mechanism constraints

The design must distinguish canonical artifact identity from execution ownership:

- Canonical artifact identity consists of an approved remote repository and repo-relative goal directory, resolved in that repository's existing main checkout.
- Execution identity remains the source repository, worktree, branch and PR.
- Source dispatch containment and writer leases stay rooted in the source repository. Do not disable _repository_path_key globally to permit external plans.
- Extend the declared workflow state schema and provider fields together. Do not repurpose current path strings. Exact field shape, validation rules and code examples require implementation design and review before the plan can claim execution readiness.
- Verify the approved origin and main branch in the ordinary checkout. Serialize publishers sharing that checkout; preserve unrelated working-tree and index contents; stage only the owned plan, progress and roadmap changes; commit; perform an ordinary non-force push to origin/main; fetch and verify that the candidate commit is reachable from main and that artifact identity and contents still match.
- Exact-tip equality proves uncontended transport. A later harmless main commit is acceptable only when ancestry and artifact contents are verified. Same-plan concurrent edits require explicit reconciliation.
- Failed, offline or non-fast-forward pushes preserve the local commit and block dependent execution or handoff until publication succeeds.
- Store transport receipts outside tracked plan content to avoid receipt-only commit loops. Each substantive amendment is a deliverable and is published immediately; source-code commits continue under normal source-repository rules.

## Delivery and retirement

Closeout requires a fresh result from completion_check in .agents/workflows/completion.py for every declared (repository, PR, exact head), together with pending-task and acceptance-gate checks. Before cleanup, re-read the current central plan revision. Refuse cleanup if new remaining work exists or the plan revision or delivered source heads changed.

A plan survives intermediate PRs and blocked or abandoned PRs. Retire the plan and progress only after the entire authorized outcome is terminal; retain the roadmap tick and Git history. A source delivery PR cannot delete a central-repository file.

The cleanup choice remains pending: either a linked central cleanup PR after source delivery or direct removal from central main after source delivery. Do not choose or execute either path until the user decides.

## Acceptance

Add focused acceptance cases covering:

- New-repository and standalone-task plans both use central main; no planning branch or worktree is created.
- Initial publication is verified before implementation or handoff; each material update is published immediately.
- Source trees retain references only, while unrelated dirty and staged files remain untouched.
- A harmless concurrent main advance is accepted only after ancestry and content checks; same-plan conflicts, offline failures and non-fast-forward failures retain local work and block dependent steps.
- External-plan resolution preserves source-root escape checks and source-rooted writer leases.
- Incomplete multi-PR outcomes remain open; stale cleanup revisions or source heads are refused; whole-plan terminal cleanup works after the selected cleanup route is approved.
- Both-host packaged and fresh-host enforcement evidence are reported separately from source generation.

Test owners are test_workflow_contracts.py, test_plan_graph.py, test_plan_handoff_stop.py and ownership tests, test_plan_workflows.py, test_continuation_runtime.py, test_completion.py, plus persistence-transport tests under their declared source owner.

## Ordered owner slices

1. Policy and dual-repository contract design. Goal: reconcile plan ownership, immediate central-main publication and source implementation-branch rules. Validation: the three planning guidance clauses agree, with retention, checkpoints and code-review gates preserved.
2. Main persistence and gate helper. Goal: design serialized, narrow staging and verified publication, recovery and receipts. Validation: acceptance cases prove safe publication, preservation of unrelated state and blocking on failure.
3. Provider, discovery and handoff integration. Goal: resolve central artifacts while preserving source-root containment and leases. Validation: provider, graph and handoff cases accept canonical artifacts and reject source-root escapes.
4. PR-bound retirement after the cleanup choice. Goal: require fresh completion evidence and revision/head checks before retirement. Validation: intermediate, stale and terminal multi-PR cases produce the required keep/refuse/retire outcomes.
5. Focused tests and fresh-host acceptance. Goal: verify both host packages and fresh installations with evidence distinct from generation. Validation: the named workflow tests and host acceptance records pass.

These are design slices, not implementation-ready instructions. Exact mechanisms, including artifact identity fields and code examples, remain pending design and review. Documentation does not authorize runtime or installation changes.

## Readiness

The requirements and source constraints are recorded. The cleanup route is unresolved, and the state schema and implementation mechanisms require design and review. This plan remains a draft.
