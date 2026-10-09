# Durable plan persistence

## Status

Draft: requirements persisted; cleanup choice and implementation mechanisms awaiting design.

## Scope

This cross-repository plan defines how canonical plans, progress records, and roadmaps are persisted and retired. The selected central plans repository for this scope is [tj-agents/docs](https://github.com/tj-agents/docs). It covers the lifecycle contract and its eventual implementation, enforcement, and host qualification. It does not authorize or change runtime behavior, policy bindings, or installations.

The current ownership model is split: core policy is presently repository-local, while the docs repository README assigns global plans to the central plans repository. Phase 1 must reconcile those owners and state the branch and publication contract. The later phases below are provisional planning phases; mechanisms and implementation readiness remain unresolved.

## Persisted requirements

- Store all future canonical plans and their progress records in the selected central plans repository.
- Keep one canonical remote path for each plan. Source repositories and execution branches may keep references to that canonical path.
- Author and update the initial plan in the ordinary main checkout. Do not create a planning branch or worktree for it.
- Commit and push the initial plan to origin/main, then verify the exact remote tip before implementation, handoff, or declaring the plan persisted.
- Commit and push material planning updates promptly, and verify the remote state so progress is not left only in a local checkout.
- A failed push must preserve the local record and block dependent execution. Never force-push or discard another person's changes.
- This rule for initial planning does not prohibit normal product implementation branches.
- Retain an unfinished or multi-PR plan until its whole outcome and delivery gates are complete.
- Retire the finished plan and progress record with the PR that delivers the work; preserve their history in Git.
- Cleanup spans two repositories: the source delivery PR cannot delete a file in the central plans repository. The retirement mechanism is unresolved pending user choice between a linked cleanup PR after delivery and direct removal from main after delivery.

## Provisional phases

1. Reconcile the existing core policy owner with the docs repository's global-plan ownership and define the ordinary-main publication contract.
2. Design persistence helpers, read receipts and recovery behavior, plus the policy for promptly publishing material planning updates.
3. Design PR-linked closeout for delivered work, including the cross-repository cleanup choice.
4. Define meaningful failure, concurrency, multi-PR and host acceptance tests.

These phases describe planning work only. No implementation is ready until the mechanisms have been designed and reviewed.

## Current readiness

Requirements are recorded. Cleanup semantics and implementation mechanisms remain open. This document is not an implementation-ready specification.
