# Native duplication audit progress

Date: October 27, 2026.
Owner: current Codex session, started from the Agent checkout at Tommy's handoff instruction.

- Plan: plans/native-duplicates/NATIVE_DUPLICATES_PLAN.md
- Roadmap: plans/native-duplicates/NATIVE_DUPLICATES_ROADMAP.md
- Roadmap item: native-duplicates/migration

- Worktree: C:/Users/TommySeery/source/repos/tj-agents/docs.worktrees/Audit-NativeDuplicates-20261027
- Branch: Docs/NativeDuplicates
- PR: https://github.com/tj-agents/docs/pull/29
Initial base: `d3a4d8699877c5a84f42587e6a3d1a4a0860f48b`.

## Current state

Tommy approved D1-D11 within the inventory's conditions. Both hosts were assessed independently. Tommy subsequently clarified that a common skill name alone is not useful: sufficient native controls are used directly, and retained skills require concrete added workflow, policy or missing-host behavior. The frozen inventory covers all 20 repositories and 286 authored skills. Its historical sizes and SHAs remain an audit snapshot rather than a claim about the changed branches.

Four source cutovers are published as open PRs. Agent and Core are ready after fresh review and exact-head CI. This Docs checkpoint is completing its final review; Personal and Infonetica remain ready at their unchanged heads. All implementation writer leases are released; parent owns acceptance and the remaining validation. Protected routing and permission work remains untouched. Agent #24 landed D2's 1,246-line duplicate shell removal during the audit, before this task's Agent source commit.

| Owner | PR and frozen head | Source change | Current evidence |
| --- | --- | --- | --- |
| Agent | https://github.com/tj-agents/agent/pull/26; `446230fdfa37014d846da2f08eb3c749025643b0` | Native message/peer entries with additional requirements; verified-delivery helper in Codex runtime; wrong memory writer, redundant memory wrapper and retired close/reaper removed | Ready correction; generator Check (277), absence scan and native-boundary test pass; native/independent incremental reviews and exact-head CI `40557806980` pass, including genuine Windows/Linux repository tests and host admission |
| Core | https://github.com/tj-agents/core/pull/517; `c631774393aebead04de6998d3c0e02445ab0e1e` | Codex-only durable continuation runtime; Claude native continuation; five selectors removed; security guidance corrected; authoring rule requires real wrapper value | Ready correction; generator Check (446), guidance examples, generated-path guard and native/independent reviews pass; full exact-head CI `40557817874` passes Windows/Linux native startup, source/package and shared runtime tests, Windows compatibility/scheduler tests and the required aggregate |
| Personal | https://github.com/tj-agents/personal/pull/41; `9505b84ea0ed8108b09d219a4642fac775a307d8` | Remove duplicate SessionStart policy emitter; preserve native instruction projection and PreToolUse clean-cut | Ready; native and independent reviews passed; CI `40547934870` genuinely passed Windows/Linux tests and host admission |
| Infonetica | https://github.com/tj-agents/infonetica/pull/31; `4c9cb97d02df5f360b7bdb8e58c661bd17d13219` | Replace 189-line shell engine with 44-line company policy wrapper around selected worktree owner | Ready; native direct and independent reviews passed; 56 local tests passed with one relative-Core-path skip; absolute Core payload check passed; hosted CI manual under repository policy |

## Owner plans and validation

Agent slice: `plans/native-wrappers/NATIVE_WRAPPERS_PLAN.md` in Agent #26 above. At the pre-correction checkpoint, all 42 focused tests, generator Check (282 outputs), guidance, plan graph, instruction pairing and diff checks passed. The current memory-removal checkpoint passes generator Check with 277 outputs, as recorded above. Main synchronization added PR #25's Claude refresh fix; its nine retirement tests and native-boundary test passed. The exact-head remote suites now supersede the local environment limitation for source validation. Live messaging and memory setting changes were not exercised.

Core slice: `plans/native-wrappers/GOAL.md` in Core #517 above. The 46-test adapter suite (six platform skips), all 42 supervisor tests, 23 layout tests, 19 process-standard tests and 11 review-adapter tests passed. Complete source/package fixtures, strict-root failures, host rejection, owner limits and completion evidence passed. Generator Check (446 outputs), digests, harness, tier, guidance and CRLF-aware diff checks passed. Core's generated digest fields remain uncommitted under its explicit publication policy; committed guard passes. Routine CI skipped platform suites, so the parent explicitly enabled the existing full-validation label. Exact-head full run `40549311958` passed both platform suites, native startup/discovery, generated-output guard and required aggregate; Windows also passed corpus references, PowerShell compatibility and continuation scheduler tests.

Personal: native adoption write/check, generator Check (129 outputs), guidance, exact AGENTS/CLAUDE pairing, unchanged PreToolUse assertions, emitter caller scan and focused modules passed. No new runtime remains in this instruction delivery path. Infonetica has no generator; its shared native manifests and work-scope instructions remain unchanged. No personal profile was injected into employer source.

Local full-suite limits were observed and retained: Agent 949 tests (22 failures, one error, 25 skips); Core repository 431 (four failures, 61 errors, 14 skips) and hooks 620 (three failures, 170 errors, seven skips); Personal 123 (27 errors, three skips). A deterministic Windows `mock.patch.dict` probe loses an empty inherited Git configuration value and turns Git success into Git128. The Agent Store failures reproduce on unchanged source. Core's stale skill-count assertion was corrected; all ten unchanged pre-tool tests and the unchanged timeout test passed in isolation. No credential controls, hook gates or test isolation behavior were changed to manufacture a pass. Exact-head remote platform evidence is recorded separately above.

## Wrapper value audit after Tommy's correction

`engineering:skill-authoring` in Core #517 owns the general existence rule. Agent #26 removes both `agent:memory` and the old `codex:memory`, including adapters, generated entries and aliases. Memory controls are native; no new memory implementation or setting change is introduced.

| Retained skill | Concrete requirement beyond native command spelling |
| --- | --- |
| Message | Authorized exact recipient/profile/responsibility, uncertain-send reconciliation and optional Codex recipient-history proof |
| Peer | Registered cross-host inventory and exact physical-terminal/process identity |
| Listen | One existing watcher and callback identity, compact completion delivery, resume the owning workflow without repeated model polling |
| Plugins / refresh | House dependency/selection policy, publisher-head and trust/readiness checks, same-session convergence |
| Search / recent | Offline selected-profile history, tool-call worktree attribution, activity ordering and exact resume command enrichment |
| Open / recover | Cross-host resolution, live-tab focus, interrupted execution ownership and duplicate-writer prevention |
| Review | Frozen candidate, independent assessment and delivery evidence around native reviewers |
| Persistent workflow | Exact delivery/acceptance authority and observed wakes; Codex-only durable CLI transport where required |
| Infonetica worktree | Employer checkout layout, branch policy and exact cleanup evidence around the shared lifecycle |

The separate `recent` entry has a narrower requirement than search and native pickers; its custom history attribution remains used by Engineering recents. It is not retained merely for the name. Personal's removed instruction emitter and Core's five deleted selectors remain deleted.

## Retained requirements and boundaries

- D1: Codex native queue admission returns queued status and lacks recipient-history correlation. Keep the unchanged 355-line history-proof/active-correction helper only for those explicitly required outcomes, in Codex runtime. Claude uses native messaging only.
- D6: Codex CLI/IDE lack Scheduled management. Keep the durable CLI adapter and scheduler only under Codex. Native scheduling and actual installed wakes remain separate acceptance. Existing Claude external registrations must be reconciled by exact owner before deployment can claim a completed native migration; updating source does not transfer them.
- D4: retain terminal OS helpers until the shared CLI inventory/focus contract preserves live startup/recovery identity and caller requirements. The current CLI verified-close API is not a drop-in replacement for Agent's focus/inventory paths. Do not weaken exact identity proof or conflict with protected Agent #22 to claim a deletion.
- D8 and conditional role/context/loader cases: native plugin transport does not replace house roster, publisher-head/trust/convergence policy, lane grants, dynamic profile detection or whole-tree integrity. Keep those demonstrated additional requirements. Protected Core #512 and cpp #56 remain with their owners; no new Template/context cutover was proved.

These retained cases are explicit conditional outcomes, not claims that a native equivalent was exercised or that all custom code was removed. No new CLI, Template or cpp implementation PR is created without the required proof.

## Reviews and safety

The tracked plan, progress and roadmap own the canonical execution state. The linked source PRs and CI runs above provide durable source and validation evidence. First inventory review retained ACC1/ACC2, fixed at `2d95b2380b36a895f38cd7a50aa37ee55f65d12f`. The approval checkpoint's stale execution text and protected Agent head are corrected in this update. Final publication review clarified open PR status and removed machine-private evidence dependencies and unrelated diagnostic detail.

All sessions remain open. No close was armed or executed. Authentication/trust controls were not bypassed.

## Next Steps

Scope: whole plan, including approved source PR delivery and all conditional parity/protected-work/installed acceptance gates. The full plan remains incomplete while those required gates remain unresolved.
Current slice: Agent #26 and Core #517 are ready after fresh reviews and exact-head validation of the memory-wrapper removal and authoring-rule correction; finish this Docs checkpoint review and publish Docs #29 ready. PR delivery is the requested source milestone; deployment conditions below remain explicit.
Remaining scope: reconcile exact existing Claude external registrations before deployment; fresh installed native behavior on supported surfaces; D4 only after its caller/API and protected-owner condition is satisfied; conditional role/context/loader removals only after equivalent proof.
Done when: source cutovers and requested PRs are delivered, every retained custom requirement has its explicit rationale, and any claimed installed migration has its actual acceptance evidence. Sessions remain open.

Verify the linked PR heads and report the reviewed source-delivery checkpoint with its retained deployment conditions.
