# Auto-merge rollout progress

- Plan: `plans/tj-agents-auto-merge/PLAN.md`
- Roadmap: `plans/tj-agents-auto-merge/ROADMAP.md`
- Roadmap item: `tj-agents-auto-merge/reviewed-policy-rollout`
- Worktree: isolated candidate checkout in `tj-agents/docs`
- Branch: `Chore/AgentAutoMerge`
- Last reconciled: 2026-10-10

## Current state

Tommy authorized standing agent merging in his `tj-agents` repositories after reviews and required checks pass, for Claude and Codex. Repository `allow_auto_merge` is enabled and verified on the nine public targets. GitHub's Free organization plan keeps it disabled on private `work`, `infonetica` and `docs`; GitHub returned `false` after the authorized update, and no billing, visibility or branch-protection changes were made.

The twelve policy candidates are committed at their recorded heads. Eleven non-docs candidates are clean and have canonical immutable review descriptors. The canonical cross-repository plan, progress and roadmap are committed in the docs candidate. The docs candidate is frozen by its Git-private immutable descriptor before review; any later content change requires a replacement descriptor. The parent owns every review work order, finding, delivery decision and exact-head check result.

## Next action

Review the twelve frozen policy candidates, deliver only after required reviews and checks pass, and retain each exact candidate identity with its recovery evidence. Stop for actual review, check, or platform gates.
