# Native duplication audit progress

Date: October 27, 2026.
Owner: current Codex session, started from `C:\Users\TommySeery\source\repos\tj-agents\agent` at Tommy's handoff instruction.

- Plan: plans/native-duplicates/NATIVE_DUPLICATES_PLAN.md
- Roadmap: plans/native-duplicates/NATIVE_DUPLICATES_ROADMAP.md
- Roadmap item: native-duplicates/migration

Artifact checkout: `C:\Users\TommySeery\source\repos\tj-agents\docs.worktrees\Audit-NativeDuplicates-20261027`.
Branch: `Docs/NativeDuplicates`.
Base: `d3a4d8699877c5a84f42587e6a3d1a4a0860f48b` from fetched `origin/main`.
PR: no new migration PR yet; inventory approval is now satisfied. Agent #24 already landed D2 during the audit.

## Current state

All 20 repositories have fresh audit worktrees and frozen source evidence. Three read-only delegated source audits completed. The parent verified primary native documentation and installed CLI help. Tables cover every named handoff capability, additional shell/runtime duplicates, all 62 Core skills, all other publisher capability families and every discovered authored behavior-hook family. The CSV provides the individual authored-skill roster.

At the initial inventory checkpoint, the handoff's Machine duplicate-hook claim was stale and Core #512 had a tier-gate-scan scope. Protected PRs were open; their source remained untouched. The later reconciliation below supersedes that historical Core head/scope.

Tommy confirmed the native-first single-wrapper model and approved D1-D11 within their conditions. His latest steering requires independent native checks on both hosts and separate host runtime/adapter implementation. Conditional parity cases remain design/acceptance gates.

Active Agent slice: `C:\Users\TommySeery\source\repos\tj-agents\agent.worktrees\Refactor-NativeWrappers`, branch `Refactor/NativeWrappers`, fresh base `438783a2ba1049f2afbecc16d62677cb4b8fd1ac`. Agent PR #24 already landed D2. Core #512 now owns full routing removal at `1268140a639b649632593f75b2c9ff0b26a4a5fe`; preserve it. Agent #22 remains protected. Read-only investigators own bounded Core, Personal/Infonetica and native-message parity evidence; parent owns all design and writes. No new runtime PR or installed acceptance result is claimed.

## Validation

Passed: installed Workflow host-coverage validator (`valid: true`, exactly one record); catalogue reconciliation (20 frozen repositories, 286 unique authored skills, all source paths and table IDs, exact full SHAs); unchanged status in all 19 source audit worktrees; paired AGENTS.md/CLAUDE.md checks in the docs artifact repository; balanced Markdown fences. The plan-graph check initially found missing ledger linkage/scope fields; those are corrected in this commit and the check passes with zero errors or warnings. The artifact is checkpointed by the commit carrying this ledger. Runtime suites are not applicable to this source-only inventory; future code changes must run their owning checks. No close script has been armed or run, and no peer/session has been closed.

## Reviews

Canonical work order: `C:\Users\TommySeery\source\repos\tj-agents\docs\.git\agent-workflow\reviews\87eaca807a90e8afb564837d5ddfcad080ad71aa919e45545249caccf12c9281\work-order.md`.

First pass at `d5164de53dd4c894db7ff85793904a7877b4af2d`: native reviewer found no defects; fresh accuracy review checked every catalog path and principal removal measurements. Parent retained ACC1 (ledger graph fields) and ACC2 (ambiguous source paths). Both are repaired in this commit. The canonical work order owns incremental verification and its exact watermark; source review is not runtime acceptance or implementation approval.

## Next Steps

Scope: whole plan through all approved D1-D11 owner slices and requested per-repository PR delivery; conditional parity and protected-work gates remain.
Current slice: finish precise Agent/CLI native-wrapper design, then implement from fresh Agent base while preserving other owners.
Remaining scope: Agent/CLI, Core, Personal, Infonetica and any proved Template/context cutovers; caller/package migration, native acceptance, tests, review and one PR per affected repository. D2 is already landed through Agent #24.
Done when: approved duplicate implementations are removed, remaining custom behavior is justified and packaged only where needed, all delivery/acceptance evidence is complete, and sessions remain open as instructed.

## Agent implementation checkpoint

The Agent owner slice is maintained at `C:/Users/TommySeery/source/repos/tj-agents/agent.worktrees/Refactor-NativeWrappers/plans/native-wrappers/NATIVE_WRAPPERS_PLAN.md`. Native message/peer/memory adapters are implemented, the verified message helper is isolated in Codex runtime, the incorrect memory writer and retired close/reaper path are removed. Targeted tests (42) and generation/check passed; full Agent suite and frozen review are pending. D4 terminal extraction must preserve live startup/recovery callers and exact identity guarantees before deleting OS adapters. Agent #22 now reads `03aa0472bf38959960d6787cb3d424d6544a7e8d`. No session has been closed.
