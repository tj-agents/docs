# Auto-merge rollout progress

- Plan: `plans/tj-agents-auto-merge/PLAN.md`
- Roadmap: `plans/tj-agents-auto-merge/ROADMAP.md`
- Roadmap item: `tj-agents-auto-merge/reviewed-policy-rollout`
- Worktree: isolated candidate checkout in `tj-agents/docs`
- Branch: `Chore/AgentAutoMerge`
- Last reconciled: 2026-10-10

## Current state

Tommy authorized standing agent merging in his `tj-agents` repositories after reviews and required checks pass, for Claude and Codex. Repository `allow_auto_merge` is enabled and verified on the nine public targets. GitHub's Free organization plan keeps it disabled on private `work`, `infonetica` and `docs`; GitHub returned `false` after the authorized update, and no billing, visibility or branch-protection changes were made.

The twelve policy candidates are committed at their recorded heads. Eleven non-docs candidates are clean and have canonical immutable review descriptors. This docs candidate is receiving the canonical cross-repository plan, progress and roadmap; its descriptor must be prepared after this commit. The parent owns every review work order, finding, delivery decision and exact-head check result.

## Next action

Finish and verify the docs plan promotion, prepare its immutable review descriptor, then continue independent review and delivery across the twelve candidates. Stop for actual review, check, or platform gates and retain each exact candidate identity with its recovery evidence.
