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

The twelve policy candidates are committed at their recorded heads. Core #174, cpp #38, marketplace #5, cli #2 and work #4 are recorded merged at their exact landing heads in `tj-agents-auto-merge-landings.json`. Core #175 remote head `cd938` had green CI; its owner integrated candidate `bd94fe2`, which is under fresh review. The earlier CI does not establish acceptance of that newer candidate. Docs #2 remains a draft at `7fff64c2c45e80e39954959410f73e2563343eb9`; this canonical plan/progress update requires fresh incremental review before publication. The parent owns every review work order, finding, delivery decision and exact-head check result.

## Verification blocker and recovery

Exact-head CI verification failed in the dotnet, rust, react, nvim and kit policy PRs. The common checker failure is in kit 1.2.0: `.agents/kit/utility/check/standard.json` excludes `.agents/delivery-authorization.json` from its exact `.agents` allowlist. Kit recovery at `a81d9b3b7c7969be7e66cc7b58ff8f68f8b1e379` changes 14 paths; its fresh review remains pending parent synthesis. Kit 1.2.1 is not published, and pinned consumers remain on 1.2.0. Failed jobs are not retried or bypassed. Infonetica #9 verification was not started because GitHub reported recent account payments failed or the spending limit needs to be increased; preserve this external hold without retry.

The docs checkout retains its foreground continuation owner and verified scheduler registration. Actions exclude billing, visibility, branch-protection changes, unrelated PRs and normal-profile installation. The approved sensitive second slice is not implemented.
## Reviews

The eleven initial policy candidates completed parent native-general fallback and independent L2
security/workflow review with no findings at their recorded full heads. Their current review watermarks
and identities are in `C:/Users/TommySeery/source/repos/tj-agents/rust/.worktrees/Fix-RustStandardDiscovery/.agents/continuation/tj-agents-auto-merge-review-results.json`.
The docs candidate's first pass found missing recovery fields in this ledger; this update resolves that
finding and requires an incremental review before publication. Required generated checks passed, as
did marketplace validation and CLI formatting, clippy and all 17 tests. GitHub owns exact-head CI.

## Source approval gate

Automatic approval review rejected the original configurable-exemption patch before application; its verbatim rejection remains in the scoped source goal. On 2026-10-10 Tommy explicitly approved a separate second slice for exactly `ci-workflow`, `migration`, `auth`, `money`, and `published-contract` across the twelve tj-agents repositories, after reviews and required checks. Holds and authorization-policy self-changes remain stops; other defaults are unchanged. This approval is not implementation authorization for the first source slice, and no sensitive-class implementation has started. The first source slice preserves all six current fixed stop classes.

The universal namespaced `.agents/configuration.json` placement is a separate read-only design investigation, not an accepted implementation or Concertable enablement.
## Next Steps

Scope: whole plan through all remaining phases and terminal delivery.
Current slice: twelve reviewed repository-policy deliveries and independent core host-coverage repairs. Core #175 remote head `cd938` had green CI; its owner integrated candidate `bd94fe2`, which is under fresh review. The earlier CI does not establish acceptance of that newer candidate.
Remaining scope: the separately approved sensitive-class second slice is unimplemented; private native auto-merge remains unavailable on GitHub Free. Universal namespaced repository configuration is a placement proposal under read-only design investigation, not an accepted implementation or Concertable enablement.
Done when: all twelve policies are delivered or have concrete external gates, authorized core repairs are delivered and verified for both hosts, and any separately approved follow-on is implemented and reviewed without bypassing required gates.

Review the twelve frozen policy candidates, deliver only after required reviews and checks pass, and retain each exact candidate identity with its recovery evidence. Stop for actual review, check, or platform gates.