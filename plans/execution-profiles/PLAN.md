# Model, effort and fast mode

<!-- BEGIN plan-tracker-migration -->
Current work is tracked through the selected Personal GitHub provider. This document retains design, decisions and historical evidence. Recording does not change implementation authority or existing delivery ownership.

- [Reconcile model, effort and fast mode](https://github.com/tj-agents/docs/issues/11)
<!-- END plan-tracker-migration -->

Status: investigation and discussion requested; migration is not yet approved.
Updated: 2026-10-11. Source owners: core engineering lanes and machine host adapters.

## Proposal

Tommy's subsequent proposal is three independent controls: lane selects the model only, effort selects
reasoning effort, and fast is on or off. Investigate and discuss this after the read blocker is recovered.
Do not silently migrate the existing ladder, whose rungs currently bind both model and effort. Determine
whether L1/L2/L3 are examples or the intended number of model categories; do not assume seven existing
rungs must become three. Resolve defaults, supported combinations, compatibility for existing consumers,
workflow-stage pins, host differences and pricing before implementation.

Tommy prefers fast mode for the repair when supported, and explicitly said not to delay it if the handoff
cannot handle that yet. The inspected installed launcher exposes lane, model and reasoning-effort options
but no fast option. No fast mode is claimed enabled. Confirm actual CLI/service support through the host
adapter before selecting it; use the existing supported launch path now. Urgency does not itself change
the model or reduce required judgment.

## Next Steps

Investigate the supported combinations and propose defaults and migration before implementation. This
design can be investigated independently of problem recording, but is not a blocker for those skills.

## Observed resume control gap (2026-10-11)

The supported open-codex helper accepts an explicit model but exposes no reasoning-effort argument.
Reopening self-repair session `01a12ad4-3f5b-7c72-ad11-ea65007cdd0c` with the L3 table's model
produced native turn context `effort: xhigh`, despite the previous recorded session effort being high.
The dispatch selected the L3 model; it did not establish the intended L3 effort. Do not restart a live
owner just to change this. Include exact native resume effort/fast controls in the separate profile
investigation and verify the actual resumed context instead of assuming the stored setting survived.
