# Native duplication audit progress

Date: October 27, 2026.
Owner: current Codex session, started from `C:\Users\TommySeery\source\repos\tj-agents\agent` at Tommy's handoff instruction.

- Plan: plans/native-duplicates/NATIVE_DUPLICATES_PLAN.md
- Roadmap: plans/native-duplicates/NATIVE_DUPLICATES_ROADMAP.md
- Roadmap item: native-duplicates/migration

Artifact checkout: `C:\Users\TommySeery\source\repos\tj-agents\docs.worktrees\Audit-NativeDuplicates-20261027`.
Branch: `Docs/NativeDuplicates`.
Base: `d3a4d8699877c5a84f42587e6a3d1a4a0860f48b` from fetched `origin/main`.
PR: not opened; the handoff requires inventory approval before implementation.

## Current state

All 20 repositories have fresh audit worktrees and frozen source evidence. Three read-only delegated source audits completed. The parent verified primary native documentation and installed CLI help. Tables cover every named handoff capability, additional shell/runtime duplicates, all 62 Core skills, all other publisher capability families and every discovered authored behavior-hook family. The CSV provides the individual authored-skill roster.

The handoff's Machine duplicate-hook claim is stale on current Core main. Core#512 is a tier-gate scan fix; the other protected PRs remain route/auth work. All seven were OPEN when read. No protected branch, source runtime, host settings, hooks, marketplace installation or session lifecycle was changed.

The assessment is complete for the proposed native-reuse strategy. D1-D11 are proposals. Conditional parity cases are not implementation-ready. No new runtime PR, installed acceptance result or test pass is claimed.

## Validation

Passed: installed Workflow host-coverage validator (`valid: true`, exactly one record); catalogue reconciliation (20 frozen repositories, 286 unique authored skills, all source paths and table IDs, exact full SHAs); unchanged status in all 19 source audit worktrees; paired AGENTS.md/CLAUDE.md checks in the docs artifact repository; balanced Markdown fences. The plan-graph check initially found missing ledger linkage/scope fields; those are corrected in this commit and the check passes with zero errors or warnings. The artifact is checkpointed by the commit carrying this ledger. Runtime suites are not applicable to this source-only inventory; future code changes must run their owning checks. No close script has been armed or run, and no peer/session has been closed.

## Reviews

Canonical work order: `C:\Users\TommySeery\source\repos\tj-agents\docs\.git\agent-workflow\reviews\87eaca807a90e8afb564837d5ddfcad080ad71aa919e45545249caccf12c9281\work-order.md`.

First pass at `d5164de53dd4c894db7ff85793904a7877b4af2d`: native reviewer found no defects; fresh accuracy review checked every catalog path and principal removal measurements. Parent retained ACC1 (ledger graph fields) and ACC2 (ambiguous source paths). Both are repaired in this commit. The canonical work order owns incremental verification and its exact watermark; source review is not runtime acceptance or implementation approval.

## Next Steps

Paused: Tommy - approve, reject or narrow D1-D11 in the canonical inventory; implementation resumes only for the agreed groups, after refreshing origin/main and reconciling the named protected PRs.
Scope: current slice only; full plan remains incomplete. The handoff requires Tommy's inventory approval before substantial deletion.
Current slice: verified inventory and concrete deletion proposal for approval.
Remaining scope: approved implementation repo by repo, caller and package migration, native acceptance, tests, review and one PR per affected repository.
Done when: approved duplicate implementations are removed, remaining custom behavior is justified and packaged only where needed, all delivery/acceptance evidence is complete, and sessions remain open as instructed.
