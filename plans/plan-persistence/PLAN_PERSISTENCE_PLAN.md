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

Core currently has no CI path classifier: [.github/workflows/ci.yml](https://github.com/tj-agents/core/blob/main/.github/workflows/ci.yml) runs Windows and Linux verification for pushes and PRs without path filters, regenerates on every main push, and its PR guard only rejects generated paths. tj-agents/docs currently has zero Actions workflows. The current [merge skill](https://github.com/tj-agents/core/blob/main/.agents/engineering/workflow/merge/SKILL.md) places goal deletion in a later docs closeout after a fresh completion check; that instruction must be reconciled with source-local deletion in the final implementation PR. [completion.py](https://github.com/tj-agents/core/blob/main/.agents/workflows/completion.py) reads the goal file and requires every declared delivery PR to be MERGED. [continuation_runtime.py](https://github.com/tj-agents/core/blob/main/.agents/workflows/continuation_runtime.py) requires the canonical goal file to remain available. [finish.ps1](https://github.com/tj-agents/core/blob/main/.agents/machine/utility/peer-cli/scripts/finish.ps1) consumes a cleanup_proof.py removable-worktree receipt and removes host/worktree state; it does not own plan deletion.

## Mechanism constraints

- Keep source-plan identity rooted in its owning source repository. A global plan directly consumed by a source workflow may need an approved docs-repository identity and repo-relative goal directory, distinct from execution identity (source repo, worktree, branch and PR). Design that integration only if needed; exact schema/provider fields and code examples remain open.
- Initial publication uses the owning repository's existing ordinary main checkout. Substantive source plan-only amendments publish immediately to the current canonical branch: source main before execution, then the active delivery branch during execution. When code accompanies the amendment, plan, progress and code share the same substantive commit. Global docs amendments publish immediately to docs main; no parallel live source-main plan copy is maintained during delivery.
- Serialize publishers and stage only owned plan, progress and roadmap files. Verify origin, branch, ancestry and artifact contents after a normal non-force push. Accept a harmless later remote commit only when ancestry and content still prove publication. Reconcile same-plan conflicts explicitly; failed/offline/non-fast-forward publication retains local work and blocks dependent work.
- Design a narrow, tested docs-only classifier allowlist for plans/** and qualifying prose docs/**, based on the full changed-file diff, not branch names. Evaluate the entire pushed range or PR merge-base and both paths of renames. Skip expensive jobs through conditional jobs while preserving cheap checks behind a required gate, so required checks do not remain pending. Mixed or behavior-affecting paths, and missing change evidence, run the required full validation. Exclude .agents/skills Markdown from any blanket docs exemption.
- Preserve code checks for mixed runtime, skills, schema, hooks and CI changes. Do not claim CI optimization is implemented.

## Delivery and retirement

For a source plan, pre-merge retirement eligibility checks implementation, E2E, CI, review, pending work, acceptance gates and other non-merge prerequisites. Re-read the plan and delivered heads; changed revisions or new work block preparing deletion. Do not require completion_check, which requires MERGED delivery PRs, as a pre-merge prerequisite. Include plan and progress deletion in the final implementation PR only after pre-merge checks pass; the plan remains on main until that verified PR merges. If pre-merge E2E or CI fails, the main plan remains intact and restoring plan/progress on the delivery branch before resumed work must be automatic. After merge, validate authenticated Git/receipt evidence for the merged delivery and goal state, with the continuation consumer updated for that state. If post-merge validation fails, restore canonical plan/progress in an authorized follow-up correction; deletion alone is never completion. Keep this lifecycle evidence distinct from cleanup_proof.py removable-worktree receipts. finish.ps1 remains responsible for post-merge host/worktree removal, not plan deletion; do not rewrite its default flow unless its receipt interface changes. Intermediate PRs retain the plan; failed or abandoned delivery leaves it on main. Keep and tick the roadmap.

A global docs plan is retired by its owning repository after final source delivery is verified. Link the docs deletion to that delivery because the source PR cannot delete a file in docs. This separate owner action applies only to global plans.

## Acceptance

Cover repository-owned source plans in owner main and global plans in docs main; retain the existing task-directory contract for non-repository standalone tasks; no planning branch/worktree; verified initial publication; immediate source plan-only publication on the current canonical branch; same-commit plan/progress/code updates when code accompanies them; unrelated dirty/staged file preservation; concurrent remote advance, same-plan conflict and failed transport; source-root containment and lease protection; pre-merge E2E/CI failure with automatic branch-plan restoration; post-merge authenticated goal-state validation and authorized plan/progress restoration on failure; deletion alone not completing work; intermediate/failed/abandoned PR retention and completed multi-PR closeout; linked global-plan retirement; diff-based docs-only CI with conditional jobs plus cheap required gate; and ordinary review/merge gates.

The CI classifier must test plan add/update/delete, prose-doc updates, mixed behavior paths, renames using both old and new paths, and missing-base/change evidence. Keep packaged and fresh-host evidence distinct from generation.

Test owners include test_workflow_contracts.py, test_plan_graph.py, test_plan_handoff_stop.py and ownership tests, test_plan_workflows.py, test_continuation_runtime.py, test_completion.py, plus persistence and CI-classifier tests under their declared owners.

## Ordered owner slices

1. Policy and ownership contract. Goal: align plan-artifacts, engineering plans and plan-checkpoint with owner-local plans, global designs, initial main publication and stable source-branch checkpoints. Validation: retention, checkpoint and review rules remain intact.
2. Owner-aware publication and closeout. Goal: design safe publication, pre-merge retirement eligibility, recovery on pre-merge and post-merge validation failures, and authenticated post-merge goal evidence. Validation: final-PR deletion cannot lose the main plan on failed checks, resumed work restores the branch copy automatically, and post-merge failures restore the canonical plan through authorized correction.
3. Bounded global-plan support. Goal: determine whether workflows need direct global artifact resolution and define its identity/provider contract without changing local-plan requirements. Validation: local containment and leases hold; canonical global artifacts cannot be replaced by source copies.
4. Docs-aware CI classification. Goal: classify the full changed-file diff and skip expensive jobs with conditional jobs plus a cheap required gate. Validation: full-range/merge-base and rename cases select checks correctly, including missing evidence and mixed changes; ordinary review and merge gates remain.
5. Focused tests and host acceptance. Goal: qualify workflow behavior, host packages and fresh-host enforcement. Validation: named tests pass and enforcement evidence is distinct from generation.

The merge skill closeout wording, completion goal evidence, continuation consumer and CI job wiring still require coordinated design. Do not invent a receipt or consumer mechanism here. These are design slices only; this plan does not authorize runtime, workflow, host-removal or CI implementation.

## Readiness

Source-local and global-doc ownership are distinguished. The retirement recovery lifecycle must coordinate the merge skill, completion goal, continuation consumer and host/worktree cleanup boundary; docs-only CI still needs a diff-based conditional-job design. This remains a draft.
