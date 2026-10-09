# Auto-merge rollout progress

- Plan: `plans/tj-agents-auto-merge/PLAN.md`
- Roadmap: `plans/tj-agents-auto-merge/ROADMAP.md`
- Roadmap item: `tj-agents-auto-merge/reviewed-policy-rollout`
- Worktree: `C:/Users/TommySeery/source/repos/tj-agents/rust/.worktrees/Fix-RustStandardDiscovery/.agents/continuation/auto-merge-checkouts/docs`
- Branch: `Chore/AgentAutoMerge`
- PR: not opened
- Last reconciled: 2026-10-10

## Current state

Tommy authorized standing agent merging in his `tj-agents` repositories after reviews and required checks pass, for Claude and Codex. Repository `allow_auto_merge` is enabled and verified on the nine public targets. GitHub's Free organization plan keeps it disabled on private `work`, `infonetica` and `docs`; GitHub returned `false` after the authorized update, and no billing, visibility or branch-protection changes were made.

The twelve policy candidates are committed at their recorded heads. Eleven non-docs candidates are clean and have canonical immutable review descriptors. The canonical cross-repository plan, progress and roadmap are committed in the docs candidate. The docs candidate is frozen by its Git-private immutable descriptor before review; any later content change requires a replacement descriptor. The parent owns every review work order, finding, delivery decision and exact-head check result.

## Reviews

The eleven initial policy candidates completed parent native-general fallback and independent L2
security/workflow review with no findings at their recorded full heads. Their current review watermarks
and identities are in `C:/Users/TommySeery/source/repos/tj-agents/rust/.worktrees/Fix-RustStandardDiscovery/.agents/continuation/tj-agents-auto-merge-review-results.json`.
The docs candidate's first pass found missing recovery fields in this ledger; this update resolves that
finding and requires an incremental review before publication. Required generated checks passed, as
did marketplace validation and CLI formatting, clippy and all 17 tests. GitHub owns exact-head CI.

## Source approval gate

Automatic approval review rejected the proposed configurable exceptions for CI, auth/permission,
migration, money and published-contract changes because it requires explicit approval of that sensitive
scope. The rejected enforcement patch was not applied. Tommy has a pending approval question; the inert
proposal and verbatim rejection are linked from the existing scoped-agent-delivery source goal.
That source owner may implement the independent, stronger native merge-gate coverage while preserving
all six fixed stop classes. The general both-host planning repair remains with its verified native owner.

## Next Steps

Scope: whole plan through all remaining phases and terminal delivery.
Current slice: twelve reviewed repository-policy deliveries and the independent core host-coverage repairs.
Remaining scope: sensitive-class exceptions await Tommy's explicit decision; private native auto-merge remains unavailable on GitHub Free.
Done when: all twelve policies are delivered or have concrete external gates, the authorized core repairs are delivered and verified for both hosts, and the remaining sensitive-class decision is resolved without bypassing reviews or checks.

Review the twelve frozen policy candidates, deliver only after required reviews and checks pass, and retain each exact candidate identity with its recovery evidence. Stop for actual review, check, or platform gates.
