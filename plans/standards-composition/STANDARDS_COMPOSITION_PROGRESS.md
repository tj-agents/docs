# Standards composition progress

- Plan: `plans/standards-composition/STANDARDS_COMPOSITION_PLAN.md`
- Roadmap: `plans/standards-composition/STANDARDS_COMPOSITION_ROADMAP.md`
- Roadmap item: `standards-composition/scoped-selection`
- Repository: https://github.com/tj-agents/docs
- Worktree: C:/Users/TommySeery/source/repos/tj-agents/docs
- Branch: main
- PR: https://github.com/tj-agents/docs/pull/1 (merged)
- Core retirement: https://github.com/tj-agents/core/pull/170 (merged)
- Last reconciled: 2026-10-09, shared documentation ownership

## Current state

Tommy requested a shared docs repository for global design and cross-repository plans, following
Concertable's documentation ownership model. The plan, roadmap and progress record
are published together in tj-agents/docs through PR1, merge `bbe987e6d4245d06d59412027864a6aa4d33f816`.
Core PR170 retired the duplicate artifacts and added ownership pointers, merge
`193c48144e4cde03a30aab8e68fa2b684d1f4cb6`. Existing implementation plans stay in their source repositories.
The docs repository is private. The saved continuation prompt now points to this checkout.

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
preservation of the design body outside ownership/provenance notes. Both frozen reachability checks and
diff checks passed. Core's graph has zero errors and the same unrelated size warning. Core PR170's guard
passed; full Windows/Linux CI was still running at the docs-only merge. No full CI pass is claimed.
Docs has no CI/publish workflow; core's main workflow regenerates packages but this move changes no package source.

## Reviews

Core PR169's native and parent reviews resolved four gaps: resource addressing, target-relevant choices,
the unspecified concern API and legacy-release compatibility. Incremental review approved `9ead6c5`.
The configured fresh lens was unsupported on this account and supplied no evidence. That completed
review remains provenance for the design. Native Codex and parent documentation reviews passed with no
findings for docs `e2f6441037fde2645487bece1856b7542feebcfe` and core
`49a174289cf46861fa6571dfb49aac3de65ae50c`. The configured lens remained unavailable, so its bounded
checks used the documented parent fallback. Both delivery bindings were released after merge.

## Decisions, discoveries, blockers, and deviations

Reuse .NET PR24/32/35, core PR140/116, kit inventories and the employer package. The dated inventory in
the plan records unfinished source-ownership, catalog, conditional-route, naming, auto-merge and host work;
reconcile those owners against current source before implementation. Preserve other writers and the

The shared plan owns cross-repository dependencies and acceptance. Source repositories own runtime
implementation plans and reviews. The authorized docs migration is complete; the proposed runtime design still
requires Tommy's decision. No live hook change, implementation executor or takeover of another owner is authorized.

## Execution readiness

The design proposal is published; whole-refactor implementation readiness is not claimed. C0/K1 and
existing-body splits need owner implementation-design review after approval. Source ownership,
new Dapper/raw guidance and fresh-host qualification retain the explicit gates in the plan.

## Next Steps

Paused: Tommy — approve or revise the published design and authorize runtime owner slices; the original handoff reserves that decision.

Scope: current slice only; full plan remains incomplete.
Current slice: obtain the runtime decision on the published proposal; shared documentation migration is complete.
Remaining scope: approved owner implementation slices, producer/consumer migration and both-host qualification.
Done when: Tommy's decision is recorded and the next authorized action is resolved; the wider refactor remains open.

1. Read the published proposal in this docs repository. If Tommy requests a revision, update this same plan.
2. After explicit runtime approval, record its scope here, reconcile existing source owners and start the
   authorized C0 slice in a core checkout from current origin/main. Keep implementation progress with that
   owner and cross-repository dependencies here. The docs checkout is not a runtime implementation target.

This post-publication checkpoint rides the next substantive plan change; no bookkeeping-only PR is needed.
