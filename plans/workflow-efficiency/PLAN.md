# Reduce time to useful progress

<!-- BEGIN plan-tracker-migration -->
Current work is tracked through the selected Personal GitHub provider. This document retains design, decisions and historical evidence. Recording does not change implementation authority or existing delivery ownership.

- [Reconcile reduce time to useful progress](https://github.com/tj-agents/docs/issues/18)
<!-- END plan-tracker-migration -->

Status: improvement proposal; preserve the existing review and delivery gates.
Updated: 2026-10-11.

## Proposed changes

- Reuse a live owner and its evidence; avoid repeating completed diagnosis and broad context reads.
- Keep handoff goals concise: outcome, authority, causal evidence, scope, required companions, acceptance
  and next action. Link detail instead of copying a transcript or the skill corpus.
- Include mandatory catalog/manifest/generated-validation companion work in the proposed change boundary.
  Genuine explicit exclusions still apply and must be resolved before accepting that work package.
- Run focused local tests against the changed behavior; let required CI own the full platform matrix.
  Broaden locally only for a failure or unresolved concern. Re-run checks when their relevant inputs change.
- Freeze a review candidate; update/rebase when correctness, conflict or repository policy requires it,
  rather than chasing every unrelated new main commit and invalidating evidence repeatedly.

## Evidence and acceptance

The [orchestration evidence](../agent-orchestration/GAMEPLAN.md#what-the-evidence-establishes) records
repeated validation, changing base revisions, contradictory handoff scope and missing capability
checks. Measure time to first causal evidence, redundant context reads/test runs, and stalled progress.
Faster token generation alone cannot fix a blocked launch or conflicting instructions.

## Next Steps

Select one measured cause for a bounded improvement after reconciling its existing owner; do not launch
a generic rewrite of all process skills.

## Recorded naming debt (2026-10-11)

Tommy called out terminal titles and worktree/branch names that do not explain the current task.
Canonical debt records are `core/.agents/machine/TECH_DEBT.md` (D-MACHINE-TASK-TITLES) and
`core/.agents/engineering/policy/git-branching/TECH_DEBT.md` (D-ENGINEERING-WORKTREE-NAMES).
The latter records this coordinator's scope change under the old SessionGuidanceHandoffCompliance name.
The intended user-facing description is **Launch, reuse or defer repair handoffs**. Those source-owned
records contain the evidence and resolution conditions; this plan links them rather than copying a
second backlog. Naming changes must preserve the existing native context and active work ownership.

On 2026-10-12, Tommy clarified that visible names literally say `Read handoff...`. The native Codex index
confirms that failure for both recent handoffs despite descriptive launcher/registry titles. The concrete
repair is now recorded as `core/BUGS.md` B006; the existing terminal naming debt links it. Acceptance must
check the native session list and visible terminal labels after startup/resume, not only launcher metadata.
