# Bug, mistake and debt skills

Status: foundation merged in PR #206 and generated publication verified on 2026-10-11.
Shared design owner: tj-agents/docs. Implementation owner: tj-agents/core.

## Outcome

Agents record problems they discover without waiting for Tommy to request documentation. Recording and
addressing remain separate, independently callable skills, following the merged debt naming convention.
Each underlying problem has one canonical record; related goals and affected repositories link to it.
A bug is faulty behavior, a mistake is an observed agent/process error, and debt is a deliberately deferred
improvement or compromise. A mistake may expose a bug or debt; link the causal repair instead of creating
duplicate repair jobs. Recording a suspicion does not establish its cause.

## Current evidence and existing owners

- Core PR #173 merged on 2026-10-11: `write-debt` records in the owning area's `TECH_DEBT.md`;
  `address-debt` resolves a selected item. Resolved debt entries are removed, with Git retaining history.
- Core PR #205 merged on 2026-10-11: root `MISTAKES.md` holds seven incidents, M001 through M007,
  with evidence and correction criteria. It preserves addressed incidents and verification evidence.
- Existing `bugfix` owns defect diagnosis and repair. PR #199 owns the proposed `self-repair` workflow;
  PR #196 owns related handoff enforcement. Reconcile those branches before editing overlapping policy.
- PR #168 covers recording noticed problems and direction changes; it remains open at this checkpoint.
  Consume what already reached main through #173; do not restart that work or assume an open PR is merged.

## Scope of the next slice

Provide bug and mistake recording and addressing entry points matching the debt pair: provisionally
`write-bug`, `address-bug`, `write-mistake`, and `address-mistake`. The addressing skills select a record
and invoke its existing owning lifecycle; they must not copy `bugfix` or the pending `self-repair` engine.
Keep shared record semantics under one owner. Names are subject to the existing skill taxonomy check.

Recording must deduplicate by cause/owner, preserve evidence, distinguish symptom from confirmed cause,
and capture the observed problem, impact, priority, owner, state, linked repair and resolution evidence.
It must support `blocked_by`, conflicting work/owned paths, a deferral reason, the resolver, an observable
resume condition and the next action. Unknown ownership stays visible and is investigated; it never grants
permission to create another writer. A blocked record is an outstanding obligation, not completion.

The user's latest requirement makes these skills a prerequisite for handoff priority/deferral. This slice
provides the durable recording vocabulary and standalone record/address behavior. The dependent slice
changes dispatch and enforcement together; it must not be hidden inside a recording skill.

## Storage and migration decision

Tommy previously preferred one place to document problems. A clarification offered a shared typed register
or separate BUGS.md, MISTAKES.md and TECH_DEBT.md files; no answer had arrived when this checkpoint was
written. The long-term consolidation choice remains unresolved. The compatible first-slice default preserves
existing MISTAKES.md and area TECH_DEBT.md owners, adds BUGS.md where no bug owner is declared, and respects
a repository-declared shared register. This is a reversible implementation choice, not a user decision
to abandon consolidation. Whichever is selected, preserve one canonical
record per repair and the existing M001-M007 facts, stable identities and history. Reconcile the different
retention rules deliberately; debt removal must not accidentally erase the mistake learning record.
Do not silently migrate every consumer repository or conflate 'one record' with mandatory duplication
in multiple files. Existing repository configuration and the merged convention are the compatibility base.

## Acceptance

- A newly noticed bug and a process mistake are recorded without a separate user instruction.
- Repeating the observation adds evidence to the same record; existing owner/session/PR links survive.
- An address request selects an actionable record, follows the owning repair workflow, verifies the
  resolution and applies that record kind's retention rule. A blocked item remains recorded.
- The foundation can represent a blocked skill-read repair, conflicting source-policy edits and full
  capacity without asserting that a scheduler or automatic wake exists.
- Codex and Claude entry points resolve to one canonical definition; package harness manifests,
  catalogs and required source companion artifacts ship in the same change.
- Focused source checks plus a disposable consumer demonstrate the convention. Installed-host acceptance
  is reported separately from source tests and merge status.

## Delivered outcome and next action

PR #206 merged at 2026-10-11T19:55:02Z with landing commit
`d3fc4d49ca412d9e9811faa3b07aed4d43ff0f70`. Required Windows/Linux CI, generated-path guard and independent
review passed. The causal publication run `38170019843` succeeded; publication commit
`73f1fbcc24efdda8ed1c0b0ccf07dc4064e7782c` contains all eight host entries and the shared problem contract.
The completed source goal is `core/.worktrees/Feature-ProblemSkills/plans/problem-skills/GOAL.md`;
its owner recorded completion. Existing M001-M007 remain intact. No consumer profile installation is claimed.

The four named skills and the shared record contract are delivered. The compatible storage defaults are
now source behavior; long-term physical consolidation remains a separate preference, not unfinished
foundation scope. Proceed to [handoff priority/deferral](../handoff-priority/PLAN.md) using those fields.
