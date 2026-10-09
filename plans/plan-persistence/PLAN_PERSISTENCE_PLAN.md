# Durable plan persistence

## Status

Draft: owner-local and global plan lifecycles reconciled; publication, closeout and CI mechanisms still need design and review.

## Scope

Source repositories own implementation plans and operational documentation. tj-agents/docs owns global designs and cross-repository plans. Non-repository standalone tasks remain under their existing task-directory contract and are outside this repository-publication proposal; they do not need an invented repository owner. This plan proposes lifecycle rules only; it does not authorize runtime, policy, workflow or CI changes.

## Requirements

- Create every future plan and progress record, plus any associated roadmap changes, in its owning repository's existing ordinary main checkout. Commit, push and verify initial publication before implementation or handoff. Do not mandate a roadmap where the selected lifecycle does not require one; do not create a planning branch or worktree.
- Keep source implementation plans and roadmaps in their source repository. Implementation branches inherit the tracked local plan and progress; source repositories link to global designs in tj-agents/docs.
- Publish global docs plan amendments immediately to docs main. Publish substantive source-plan-only amendments immediately to the current canonical owner branch: source main before execution begins, then the active delivery branch during execution. When code accompanies a plan/progress update, include all of it in the same substantive commit. Do not maintain a parallel live copy on source main during delivery.
- Retain plans through intermediate PRs and until the entire outcome is implemented and verified. A failed or abandoned PR leaves its plan on main.
- In the final source implementation PR, remove the source-local plan and progress after verifying the whole outcome. Keep and tick the roadmap. The deletion reaches main when the final PR merges; do not require an impossible MERGED state before preparing that PR.
- Link global-plan retirement to the final implementation delivery, then delete the plan and progress in the owning docs repository. Keep and tick its roadmap.
- Serialize publishers, preserve unrelated working-tree and index contents, and stage only owned files. Use ordinary non-force pushes and verify remote ancestry and content. Failed publication preserves local commits and blocks dependent work or handoff. Keep transport receipts outside tracked plan content.

## Source evidence

As of 2026-10-09, base plan-artifacts assigns plans to source repositories or standalone task directories; engineering plans assigns active delivery branches to source ownership and docs-PR publication; plan-checkpoint correlates plans with source checkouts and forbids transport-only updates. Reconcile repository-owned plan publication while preserving the existing non-repository standalone task-directory contract, whole-plan retention, meaningful checkpoints and code-review gates.

The existing source-rooted RepositoryStateProvider, validate_checkpoint and _repository_path_key in [workflow_runtime.py](https://github.com/tj-agents/core/blob/main/.agents/workflows/workflow_runtime.py), source plan discovery in [workflow_ops.py](https://github.com/tj-agents/core/blob/main/.agents/workflows/workflow_ops.py), same-repository --root behavior in [plan_graph.py](https://github.com/tj-agents/core/blob/main/.agents/hooks/plan_graph.py), and source-local ledger selection in [plan_handoff_stop.py](https://github.com/tj-agents/core/blob/main/.agents/hooks/plan_handoff_stop.py) are valid defaults for source-owned plans. They are not defects in local-plan support. Any global-doc artifact resolution is a bounded separate concern; never weaken source containment or leases to implement it.

The v2 [state schema](https://github.com/tj-agents/core/blob/main/.agents/workflows/contract/v2/state.schema.json) rejects unknown fields and has no artifact-repository field. Do not repurpose existing path strings or require an external provider/schema change for local plans. Reuse the existing absolute-goal behavior in continuation_runtime.initialize/check_identity and its test test_absolute_external_goal_survives_claim_yield_repair_and_wake; see the [external-goal continuation plan](https://github.com/tj-agents/core/blob/main/plans/external-goal-continuation/EXTERNAL_GOAL_CONTINUATION.md). Link the sibling [standards-composition proposal](https://github.com/tj-agents/docs/blob/main/plans/standards-composition/STANDARDS_COMPOSITION_PLAN.md) for its existing planning and auto-merge ownership; do not create a second scheduler.

Core currently has no CI path classifier: [.github/workflows/ci.yml](https://github.com/tj-agents/core/blob/main/.github/workflows/ci.yml) runs Windows and Linux verification for pushes and PRs without path filters, regenerates on every main push, and its PR guard only rejects generated paths. tj-agents/docs currently has zero Actions workflows.

## Mechanism constraints

- Keep source-plan identity rooted in its owning source repository. A global plan directly consumed by a source workflow may need an approved docs-repository identity and repo-relative goal directory, distinct from execution identity (source repo, worktree, branch and PR). Design that integration only if needed; exact schema/provider fields and code examples remain open.
- Initial publication uses the owning repository's existing ordinary main checkout. Substantive source plan-only amendments publish immediately to the current canonical branch: source main before execution, then the active delivery branch during execution. When code accompanies the amendment, plan, progress and code share the same substantive commit. Global docs amendments publish immediately to docs main; no parallel live source-main plan copy is maintained during delivery.
- Serialize publishers and stage only owned plan, progress and roadmap files. Verify origin, branch, ancestry and artifact contents after a normal non-force push. Accept a harmless later remote commit only when ancestry and content still prove publication. Reconcile same-plan conflicts explicitly; failed/offline/non-fast-forward publication retains local work and blocks dependent work.
- Design a narrow, tested docs-only classifier allowlist for plans/** and qualifying prose docs/**, evaluated over the entire pushed range or PR merge-base and both paths of renames. Plan-only changes may skip expensive code suites and package regeneration while retaining cheap checks. Mixed or behavior-affecting paths, and missing change evidence, run the required full validation. Exclude .agents/skills Markdown from any blanket docs exemption.
- Preserve code checks for mixed runtime, skills, schema, hooks and CI changes. Do not claim CI optimization is implemented.

## Delivery and retirement

For a source plan, pre-merge checks cover implementation, tests, review, pending work, acceptance gates and other non-merge prerequisites. Re-read the plan and delivered heads; changed revisions or new work block preparing deletion. Do not require a MERGED completion_check before the final PR can be prepared. Include plan and progress deletion in the final implementation PR only after the pre-merge checks pass; the plan stays on main until that verified PR merges. Run the terminal merge completion_check after the final source PR merges. Intermediate PRs retain the plan; failed or abandoned delivery leaves it on main. Keep and tick the roadmap.

A global docs plan is retired by its owning repository after final source delivery is verified. Link the docs deletion to that delivery because the source PR cannot delete a file in docs. This separate owner action applies only to global plans.

## Acceptance

Cover repository-owned source plans in owner main and global plans in docs main; retain the existing task-directory contract for non-repository standalone tasks; no planning branch/worktree; verified initial publication; immediate source plan-only publication on the current canonical branch; same-commit plan/progress/code updates when code accompanies them; unrelated dirty/staged file preservation; concurrent remote advance, same-plan conflict and failed transport; source-root containment and lease protection; pre-merge gates, post-merge terminal completion_check, intermediate/failed/abandoned PR retention and completed multi-PR closeout; linked global-plan retirement; and docs-only versus mixed CI behavior.

The CI classifier must test plan add/update/delete, prose-doc updates, mixed behavior paths, renames using both old and new paths, and missing-base/change evidence. Keep packaged and fresh-host evidence distinct from generation.

Test owners include test_workflow_contracts.py, test_plan_graph.py, test_plan_handoff_stop.py and ownership tests, test_plan_workflows.py, test_continuation_runtime.py, test_completion.py, plus persistence and CI-classifier tests under their declared owners.

## Ordered owner slices

1. Policy and ownership contract. Goal: align plan-artifacts, engineering plans and plan-checkpoint with owner-local plans, global designs, initial main publication and stable source-branch checkpoints. Validation: retention, checkpoint and review rules remain intact.
2. Owner-aware publication and closeout. Goal: design safe initial publication, same-commit source checkpoints and final-PR local retirement. Validation: failure, unrelated-file, multi-PR and terminal-delivery cases behave as required.
3. Bounded global-plan support. Goal: determine whether workflows need direct global artifact resolution and define its identity/provider contract without changing local-plan requirements. Validation: local containment and leases hold; canonical global artifacts cannot be replaced by source copies.
4. Docs-aware CI classification. Goal: design an allowlist classifier for plan and qualifying prose-only changes. Validation: full-range/merge-base and rename cases select cheap or full checks correctly, including missing evidence and mixed changes.
5. Focused tests and host acceptance. Goal: qualify workflow behavior, host packages and fresh-host enforcement. Validation: named tests pass and enforcement evidence is distinct from generation.

These are design slices only. Exact publication, provider, retirement and classifier mechanisms remain subject to design and review; this plan does not authorize their implementation.

## Readiness

Source-local and global-doc ownership, checkpoint publication and retirement are distinguished. Safe publication, any bounded global artifact support, and docs-aware CI classification need design. This remains a draft.
