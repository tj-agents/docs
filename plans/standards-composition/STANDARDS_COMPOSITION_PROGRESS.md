# Standards composition progress

<!-- BEGIN plan-tracker-migration -->
Current work is tracked through the selected Personal GitHub provider. This document retains design, decisions and historical evidence. Recording does not change implementation authority or existing delivery ownership.

- [Reconcile scoped standards composition](https://github.com/tj-agents/docs/issues/16)
<!-- END plan-tracker-migration -->

- Plan: `plans/standards-composition/STANDARDS_COMPOSITION_PLAN.md`
- Roadmap: `plans/standards-composition/STANDARDS_COMPOSITION_ROADMAP.md`
- Roadmap item: `standards-composition/scoped-selection`
- Repository: https://github.com/tj-agents/docs
- Worktree: C:/Users/TommySeery/source/repos/tj-agents/docs
- Branch: Docs/SharedDesignPlans
- PR: not opened
- Last reconciled: 2026-10-09, shared documentation ownership

## Current state

Tommy requested a shared docs repository for global design and cross-repository plans, following
Concertable's documentation ownership model. This migration moves the plan, roadmap and progress record
together into tj-agents/docs. The core copies are retired after this repository's planning artifacts land;
core retains a link to the shared documentation owner. Existing implementation plans stay in their source repositories.

The proposal was published through core PR169, merge `8ea3baae61621668729e12333aaf66b17a31ea6b`,
reviewed head `9ead6c5a185ba0405e0eaaf7830efaffec9cd385`. Earlier discovery landed through core PR167.
Those PRs retain the original design history. Moving these artifacts does not authorize runtime work.

The proposal uses homogeneous contract skills, an additive package standards manifest, scoped context
v2 adoption, explicit house choices, one immutable resolution and full-body delivery proof. Its source
inventory, .NET/React examples, kit changes, migration/rollback, owner slices and acceptance cases remain
unchanged. No runtime, application or hook-setting changes are part of this migration.

## Verification

Original design baseline: core finite-profile reader 11, .NET source/profile 3, React core-profile 5,
kit generator 42 and employer 14 tests passed. Three JSON examples parse; nine Python excerpts syntax-check
in their stated contexts. These establish neither the proposed runtime nor host acceptance.

Core PR169 passed frozen documentation reachability and diff checks. Its plan graph had zero errors and
one pre-existing size warning in an unrelated ledger. Its guard passed; Windows/Linux CI was still running
at the docs merge. Main regeneration subsequently reported generated output already current.
Migration checks passed: plan graph (zero errors/warnings), relative links, instruction-file pairing and
preservation of the design body outside ownership/provenance notes. Record review and publication identities
when this relocation completes.

## Reviews

Core PR169's native and parent reviews resolved four gaps: resource addressing, target-relevant choices,
the unspecified concern API and legacy-release compatibility. Incremental review approved `9ead6c5`.
The configured fresh lens was unsupported on this account and supplied no evidence. That completed
review remains provenance for the design; this move receives its own documentation review.

## Decisions, discoveries, blockers, and deviations

Reuse .NET PR24/32/35, core PR140/116, kit inventories and the employer package. The dated inventory in
the plan records unfinished source-ownership, catalog, conditional-route, naming, auto-merge and host work;
reconcile those owners against current source before implementation. Preserve other writers and the
originating cris-authz application's unpublished work.

The shared plan owns cross-repository dependencies and acceptance. Source repositories own runtime
implementation plans and reviews. The docs migration is authorized; the proposed runtime design still
requires Tommy's decision. No live hook change, implementation executor or takeover of another owner is authorized.

## Execution readiness

The design proposal is published; whole-refactor implementation readiness is not claimed. C0/K1 and
existing-body splits need owner implementation-design review after approval. Source ownership,
new Dapper/raw guidance and fresh-host qualification retain the explicit gates in the plan.

## Next Steps

1. Finish the authorized docs migration: validate and review this repository, publish its artifacts to main,
   then remove the core copies and land core's documentation pointer. Record both publication identities here.
2. Await Tommy's decision on the existing proposal. If revision is requested, revise this same plan in docs.
3. After explicit runtime approval, record its scope here, reconcile existing source owners and start the
   authorized C0 slice in a core checkout from current origin/main. Keep implementation progress with that
   owner and cross-repository dependencies here. The docs checkout is not a runtime implementation target.

Scope: current slice only; full plan remains incomplete.
Current slice: publish the shared docs owner and retire the duplicate core artifacts.
Remaining scope: design approval, owner implementation slices, producer/consumer migration and host qualification.
Done when: the shared plan is published in docs, core links to it without duplicate artifacts, and the
runtime decision boundary remains explicit.
