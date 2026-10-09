# Plan persistence progress

- Plan: plans/plan-persistence/PLAN_PERSISTENCE_PLAN.md
- Roadmap: plans/plan-persistence/PLAN_PERSISTENCE_ROADMAP.md
- Roadmap item: plan-persistence/durable-lifecycle
- Worktree: none (ordinary checkout in tj-agents/docs)
- Branch: main
- PR: not applicable; initial direct-to-main publication
- Last reconciled: 2026-10-09

## Current state

Initial global-plan requirements were published directly to docs main at 10a43945bcd9128a2e981d03d486281f442bd110; that exact main tip was verified before implementation or handoff. This update reconciles repository-owned plans with the existing standalone task-directory contract: source repositories own implementation plans and delivery branches; tj-agents/docs owns global designs; non-repository standalone tasks remain outside this publication proposal. Source plan-only amendments publish immediately to the current canonical branch; plan/progress updates accompany code in the same substantive commit when code is changing. Global amendments publish immediately to docs main. Runtime, policy and CI remain unchanged.

## Next Steps

Scope: current slice only; full plan remains incomplete.
Current slice: publish a reviewed, owner-aware lifecycle proposal.
Remaining scope: implementation, enforcement, any bounded global artifact support and docs-aware CI design after approved specifications.
Done when: the concrete proposal is published on main and the next authorized action is resolved.

Next action: design immediate current-branch publication and pre-merge local closeout gates, with terminal merged-state verification after delivery; scope any needed global artifact support and docs-only CI classifier separately.

## Verification

Initial plan graph check: 0 errors, 0 warnings. Initial exact docs main tip verified: 10a43945bcd9128a2e981d03d486281f442bd110. This update's plan graph check: 0 errors, 0 warnings. Whitespace check: passed. No implementation tests run; no update push is claimed.

## Reviews

Ownership correction requires a bounded documentation review before publication. Detailed publication, provider, retirement and CI mechanisms remain draft and have no implementation-readiness approval.
