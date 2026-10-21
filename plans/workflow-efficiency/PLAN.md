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
