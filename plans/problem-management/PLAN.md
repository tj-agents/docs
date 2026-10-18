# Bug, mistake and debt skills

Status on 18 October 2026: GitHub work-items tooling and Core integration delivered; personal-repository adoption and existing-record migration remain unfinished. The former PR #269 dependency has merged.
Shared design owner: tj-agents/docs. Implementation owners: tj-agents/work-items (new optional tracker package), Core (generic workflow integration), marketplace/machine (selection), and personal consumer repositories (adoption).

## Full rollout transfer - 18 October 2026

Tommy's "GO THEN" explicitly requests the actual execution handoff for the remaining rollout. Transfer the whole existing `problem-management/personal-policy` goal to one native Codex successor in C:/Users/TommySeery/source/repos/tj-agents/docs, retaining the current main checkout and preserving all unrelated dirty documentation. Predecessor: codex:01a1415f-6448-7123-8b17-c7fb67aee637. Local writer budget: one rollout owner. Lane: L4, because the tracker/storage design and scripts are delivered and remaining work is specified adoption, careful record reconciliation and verification. Do not reopen the storage design or stop after another plan.

Before deliverable writes, the successor must claim `problem-management/personal-policy` through the supported session-store CLI with `--host codex --role owner --status active --predecessor codex:01a1415f-6448-7123-8b17-c7fb67aee637`, preserving the title and `--plan-path plans/problem-management/PLAN.md`. Record its exact native handle, acknowledgement and first adoption result here. The predecessor stops owned-path writes before invoking the launcher and retains only read-only pickup observation. Pickup acknowledged on 18 October 2026 by `codex:01a14ec8-5bdd-70a3-90c1-9d31a71289cf`; the session-store transfer removed the predecessor and retained this goal's title and plan path. First adoption result: the docs pilot now declares `work-items@work-items-agents`, and the merged tracker command adopted the verified `tj-agents/docs` origin with native Feature/Bug/Task types, writing `.work-items.json` and `.problem-records.json`; a subsequent feature listing returned an empty, readable tracker. The Codex installed-host refresh could not initialize its app server, so installed-host discovery and a remote record write remain unverified.

Existing continuation reference: C:/Users/TommySeery/source/repos/tj-agents/work-items/.agents/continuation/owner.json, owner 1ff3ef5566d6f3b7fc37ee0f. No scheduler was registered; its original lease and deadline are historical. The supported `yield` operation rejected the historical token with `foreground-token-invalid`; the same runtime's process-identity predicate verifies that the old foreground is no longer alive, and the owner has no child. No registered scheduler or active continuation writer is claimed. This inactive historical record is preserved; the docs session-store transfer supplies current ownership. Preserve the record; do not hand-edit, delete it or infer it grants an active unattended wake. Reconcile through the current continuation workflow before using it again. It does not replace the docs task's atomic session-store transfer.

Execution is authorized for the remaining optional tracker adoption and migration in eligible personal repositories, with their existing review/publication gates. No employer changes or general profile migration are authorized. The docs checkout has no `.agents/settings.json`: effective `auto_approve_design=false`; implementation follows the approved design. Re-read each consumer's settings/instructions. Canonical completion remains the whole rollout, not the first pilot, a PR, installed package, or this handoff.

### Pilot checkpoint — 18 October 2026

The docs pilot now selects `work-items@work-items-agents` from `tj-agents/work-items`, with generated Codex and Claude settings, a GitHub tracker declaration for `tj-agents/docs`, and the Core problem-record provider declaration. Its feature listing returned an empty readable tracker. The work-items pilot uses isolated `Chore/AdoptWorkItemsTracker` from fetched `origin/main` at `881eb5b0df7204ba53cf49a93f556f7d341910ea`; it migrated its legacy schema-3 lock to the versionless selection, adopted `tj-agents/work-items`, and read its tracker successfully.

The work-items legacy records now have canonical managed issues: B001 is closed as #14, M001 is closed as #15, and M002 remains open as #16. Each creation used a durable migration request ID; B001 and M001 were read back after closure with their legacy identity, source links, states, and verification evidence intact. The legacy untracked `BUGS.md` and `MISTAKES.md` in the historical primary checkout remain untouched until their retained records and links can be reconciled by that checkout's owner. Codex installed-host discovery is still unverified because the Codex app server stopped during initialization; the exact merged tracker artifact was used after its files were verified byte-identical to the #13 landing.

Native review completed without findings for docs commit `9e76f3f` against `0d74933ff0889251f6228c96d81b7553ed95a736` and for work-items commit `34aeadf` against `881eb5b0df7204ba53cf49a93f556f7d341910ea`. One initial work-items review invocation used the wrong checkout; it was recorded as new evidence on M002 and contributes no review result. The correct rerun from `Chore/AdoptWorkItemsTracker` is the retained review evidence.

Native review completed without findings for docs commit `9e76f3f` against `0d74933ff0889251f6228c96d81b7553ed95a736` and for work-items commit `34aeadf` against `881eb5b0df7204ba53cf49a93f556f7d341910ea`. One initial work-items review invocation used the wrong checkout; it was recorded as new evidence on M002 and contributes no review result. The correct rerun from `Chore/AdoptWorkItemsTracker` is the retained review evidence.

### Pilot checkpoint — 18 October 2026

The docs pilot now selects `work-items@work-items-agents` from `tj-agents/work-items`, with generated Codex and Claude settings, a GitHub tracker declaration for `tj-agents/docs`, and the Core problem-record provider declaration. Its feature listing returned an empty readable tracker. The work-items pilot uses isolated `Chore/AdoptWorkItemsTracker` from fetched `origin/main` at `881eb5b0df7204ba53cf49a93f556f7d341910ea`; it migrated its legacy schema-3 lock to the versionless selection, adopted `tj-agents/work-items`, and read its tracker successfully.

The work-items legacy records now have canonical managed issues: B001 is closed as #14, M001 is closed as #15, and M002 remains open as #16. Each creation used a durable migration request ID; B001 and M001 were read back after closure with their legacy identity, source links, states, and verification evidence intact. The legacy untracked `BUGS.md` and `MISTAKES.md` in the historical primary checkout remain untouched until their retained records and links can be reconciled by that checkout's owner. Codex installed-host discovery is still unverified because the Codex app server stopped during initialization; the exact merged tracker artifact was used after its files were verified byte-identical to the #13 landing.

## Current conclusion and rollout handoff — 18 October 2026

The approved destination is GitHub Issues in each personal project's existing repository, outside its code branches and main-checkout Markdown registers. Feature, task, bug, mistake and debt are distinct record kinds, generated and maintained through deterministic scripts/templates in the separate optional `tj-agents/work-items` plugin. Specifications, substantial plans and curated knowledge stay with source. Core supplies generic integration; selecting Core alone does not impose this personal tracker on Infonetica, which retains Azure DevOps. No Firebase or custom cloud database was selected.

The tooling shipped: work-items foundation #3, GitHub lifecycle #5 and Core adapter #7, together with Core #272/#273 and marketplace #11. Controlled installed-host checks passed on Codex and Claude. That proves the capability, not migration of every personal repository. Existing records have not been claimed migrated. Fresh local inspection found neither `.work-items.json` nor `.problem-records.json` in the docs and work-items primary checkouts, so these consumers still lack the shipped explicit tracker adoption declarations.

Fresh GitHub verification: Core #269 merged on 16 October 2026 at 17:47:07 UTC, landing `2ed865e13f071a573d505dacd59c1a482eb5f2bb`. Core main CI `39094033180` succeeded at `774e2cb8dccf1621f919bc6128b6cf8cb789b2a3` on 18 October. Work-items #13 merged the versionless-plugin update on 17 October at `881eb5b0df7204ba53cf49a93f556f7d341910ea`. The earlier checkpoint's instruction to wait for #269 is superseded; inspect the current published selection contract when resuming instead of reviving versioned adoption.

The original rollout handoff is [HANDOFF-PERSONAL-POLICY.md](HANDOFF-PERSONAL-POLICY.md), now corrected to point at the executable rollout steps below. It had still pointed at the completed research-only brief. The last chat handoff concerned only the separate validation-efficiency investigation; it did not hand off or complete this rollout. This distinction and stale pointer are corrected here. No new session was launched by this status reconciliation; the registry still identifies this original session as owner of `problem-management/personal-policy`.

Sections below preserve dated research, decisions and delivery evidence. Their older proposed commands, package versions and dependency states are historical where superseded by this current snapshot.

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


## Personal workflow separation research (15 October 2026)

The delivered foundation above is historical evidence. Tommy now requests a separate research handoff
to determine how personal problem recording and documentation policy should be owned and selected.
Core must remain useful in every repository, including Infonetica work repositories. His personal
repositories must additionally adopt his bug, mistake, technical-debt and documentation workflow;
work repositories must not inherit that personal policy merely by using Core.

The original storage brief proposed observations in the source repository's shared primary checkout,
outside feature worktrees, without committing, pushing or creating a docs PR for each observation.
On 15 October Tommy reopened that choice: compare other agent workflows for solo projects, multiple
computers and potentially multiple developers, without a tracker subscription. Primary-checkout notes
are therefore a candidate to assess, not the predetermined future backend. Existing research notes still
remain uncommitted. The batch trigger and delivery owner remain design questions.
Fix the relevant write-debt, write-bug, write-mistake and documentation behavior and its ownership;
merely moving Markdown files while leaving Core's mandatory policy unchanged is insufficient.

This is distinct from Core B013: the original agent guessed a skill directory and reused a renamed
goal path. That concrete failed-read bug is recorded in Core's primary BUGS.md, uncommitted. Do not
misrepresent it as a missing installed skill, or turn this personal-policy research into that runtime repair.

### Authorization and boundaries

Tommy requested: "something to think about maybe do a handoff and it can dig into a solution", then
clarified that all his personal repositories need it while work repositories such as Infonetica need
Core without his personal tech-debt policy. This authorizes investigation and a concrete proposal.
It does not authorize implementing a new package, changing Core's defaults, migrating consumer repos,
installing profiles, committing shared notes, pushing, merging or publishing this research.

Planning owner: one separate Codex research session in C:/Users/TommySeery/source/repos/tj-agents/docs.
Branch: main; retain the current branch and all other agents' dirty documentation. Own edits only to
this existing PLAN.md; read other sources without modifying them. This planning-only task needs no new
worktree. Parent session codex:01a13fa0-a1c6-7051-b3ce-a63fb26916da retains Rolling Plugin Sync in its
existing Core checkout. Never claim that work item, edit that worktree, close the parent, or transfer it.
Lane: L3, because package/policy ownership and adoption have unresolved bounded alternatives.

### Evidence to inspect

- This plan's delivered record foundation and the standards-composition plan in this docs repository.
- Core .agents/engineering/resources/problem-records.md and the write/debt/address/documentation owners,
  their session-guidance/harness dependencies, and work-specific overrides. Current installed guidance
  records in the primary checkout but still requires immediate scoped documentation publication;
  the new personal batching instruction supersedes that cadence for this user's current notes.
- Core, tj-agents/work and tj-agents/infonetica ownership and packaging conventions. Read only relevant
  policy; do not copy private employer/product content into public docs.
- Actual marketplace/plugin/repository selection mechanisms, including current authored sources and
  already-owned work. Do not infer personal scope from a machine-global setting that affects work repos.
- Core BUGS.md B013 as the concrete failed-read incident, separate from the policy design.

### Completion expectation

Produce a concise, evidence-backed proposal in this same plan. Identify which capabilities stay generic,
which policy moves to an opt-in personal owner, and what work repos select or override. Compare viable
ownership locations before recommending one. Explain how all personal repos receive it without manual
per-machine drift, how shared uncommitted records avoid lost updates/duplicate IDs, how batched delivery
is triggered, and how existing records and skill callers migrate. Preserve useful autonomy without new
per-record ceremony. Include a small acceptance matrix: personal root, personal worktree, concurrent
agents, work repo using Core, explicit personal opt-out, and no accidental commit/publication.
Clearly distinguish supported facts, proposals and decisions Tommy must make. Return the recommendation;
do not proceed into implementation or publication under this research authorization.

## Research assessment: storage and personal ownership

Status on 15 October 2026: investigation complete for the bounded comparison below; recommendation only.
Tommy's latest request adds the storage comparison to the existing research authority. No package,
tracker, consumer, installation or publication change has been approved or performed.

### What the evidence establishes

The inspected Core primary checkout is at `1bb1c130b2d1762bce07b599bb0fbb7e311c6749` and is behind the
locally available `origin/main`, `f2dd95cae5aef351017eea4d7ce3dc39a9fcae76`. Current-source observations
below use `git show` at that latter commit and the installed `base-agents` 2.1.16 definitions. This is a
dated local/source inspection, not a claim that a network fetch or installed-host acceptance passed.

| Inspected owner | Finding and consequence |
| --- | --- |
| Core `.agents/engineering/resources/problem-records.md`, `convention/write-{bug,mistake,debt}/SKILL.md`, `workflow/address-{bug,mistake,debt}/SKILL.md` | The common record shape, causal deduplication and repair routing already exist. The contract also mandates primary-checkout records and immediate separate docs delivery when authorized. Those policy choices need an actual source split; moving files alone changes neither trigger nor cadence. |
| Core `policy/session-guidance/SKILL.md`, `convention/docs/SKILL.md`, `contract/committing/SKILL.md` | Automatic problem recording and completed-work commitment intersect with documentation ownership. A personal note-capture operation needs an explicit treatment separate from completion of a code or documentation deliverable. Generic accuracy, one-owner guidance and repair verification remain useful. |
| Installed engineering `hooks/handoff_admission.py:canonical_problem_record` | Admission checks assume primary-root `BUGS.md`/`MISTAKES.md` and tracked area `TECH_DEBT.md`. An issue-backed record would currently fail that path check. Record resolution, admission and tests must move together; a policy-only redirect is insufficient. |
| Installed machine `plugin-lock`, its `adopt_plugins.py` and `plugin_roster.json`; Core source `utility/plugin-lock/SKILL.md` | The current interface uses `.agents/plugins.lock.json` schema 2 plus generated Claude/Codex project settings. Adoption preserves selections and rejects unknown roster entries. There is no personal package in the inspected roster. The older primary-checkout `bootstrap-capabilities` interface is not the current installed interface. |
| [Standards composition](../standards-composition/STANDARDS_COMPOSITION_PLAN.md) and its progress owner | Fine-grained profile resolution remains proposed. Reuse the current project-lock mechanism for a small, explicitly adopted workflow package; do not claim the broader resolver is shipped. Reconcile its source-ownership and catalog dependencies before implementation. |
| Work README/harness at `3b021cab6943a422870772de88266b9323d494d9`; employer README/tier at `9546906d5358317dd249db901a56e0c2ce9226fe` | Work tooling is selected for work repositories. Employer applicability uses positive remote evidence. A folder name, an installed cache or absence of employer detection does not establish personal adoption. No private employer/product evidence is copied here. |
| Marketplace README at `ee868f1966b6e53b4975d6ff88e1378578c78320` | Marketplace discovery is separate from installing/selecting a plugin. A personal source package must be published and added to the catalog/roster before consumers can select it reproducibly. |

Core primary `BUGS.md#B013` remains the separate guessed-path incident. Initial reads in this research
also used incorrect inferred layouts; advertised host entries and file inventory located the actual
`convention/write-*` owners and packaged `resources/machine/scripts/work_item_sessions.py`. This is
additional incident evidence for that existing owner, not a missing-skill diagnosis or a second repair.
The correct session-store `status` command could not open its SQLite database in this sandbox. Pickup
identity is evidenced by `CODEX_SESSION_ID` and the acknowledgement below; no registry claim is asserted.

### Is repository self-documentation a good default?

Recommendation: retain repository documentation for specifications, decisions, implementation plans and
curated lessons. Use a shared tracker for the live queue when multiple computers or people need to see
current work independently of code branches. These are different responsibilities: the issue owns current
status, priority and discussion; a linked plan owns design and acceptance detail, without duplicating the
backlog. Local process/session state owns machine liveness, not cross-machine task truth.

Uncommitted primary-checkout notes serve concurrent agents sharing that clone. They do not travel through
Git to another computer. Committed files can synchronize through push/pull, but then publication cadence,
offline changes and merge conflicts become part of the task system. A local lock cannot coordinate another
clone or computer. This is the main reason to reconsider the original storage assumption. [R1]

### Existing approaches and cost

These are documented examples, not a representative survey of what most agentic programmers use.
Prices and capabilities were checked on 15 October 2026. Product documentation and source inspection
establish the stated designs; no candidate was installed or exercised here.

| Approach | Evidence | Assessment for Tommy |
| --- | --- | --- |
| Current shared, uncommitted Markdown registers | Core's inspected contract; Git only shares recorded history. [R1] | Few dependencies and readable locally. Fails the multi-computer sync requirement until notes are committed and pushed. Keeping this would require deliberate batch delivery and coordinated writers. |
| Committed, file-per-task backlog | Backlog.md is an MIT-licensed Markdown task manager with a CLI, local board and optional MCP integration. Its source locks creation and re-reads task updates inside a task lock. [R2] | Best file-based candidate if offline ownership and ordinary Git portability are essential. Its local locking is useful, but does not establish cross-computer exclusion. Git delivery remains necessary. Prefer evaluating this existing tool to building another tracker. |
| GitHub Issues plus repository docs | GitHub Free includes Issues and Projects. Issues support dependencies; the CLI supports issue creation, reading and editing. GitHub's own cloud-agent workflow can start from an assigned issue. [R3-R6] | Recommended first option for an online solo/small-team workflow. One hosted queue is visible from different clones and computers without a code commit per update. Start with issues/labels; a Project board is optional. Existing local agents can use the CLI without adopting the paid cloud-agent service. |
| Beads | Current upstream documentation describes a Dolt-backed issue graph, JSON-oriented agent commands, task claiming and explicit database push/pull. Embedded mode is single-writer; server mode supports concurrent clients. Its current JSONL export is not the authoritative database. [R7] | A serious candidate for dependency-aware agent scheduling. Adds a database, version compatibility and a second sync workflow. Do not choose it on the outdated assumption that it is just a small JSONL file committed with code. Atomic claims against one backend do not establish exclusivity between disconnected replicas. |
| Azure Boards | Microsoft lists the first five Basic users free, including Boards. [R8] | Cost alone does not rule it out. It would add another service to these GitHub-hosted personal projects; there is no demonstrated need for that here. Employer work-item skills remain work-only. |

OpenSpec and GitHub Spec Kit provide further examples of agents working from explicit specifications,
plans and tasks. They support keeping useful design artifacts near the code; their existence does not
prove that every observation belongs in a permanent incident ledger, or require adopting another planning
framework alongside the existing one. [R9-R10]

Idea assessment is complete for this comparison: adopt the existing GitHub issue service and selectively
reuse the existing record/plan contracts; evaluate Backlog.md if offline tracking is essential. A fork of
Core, a custom distributed Markdown tracker or self-hosted task infrastructure has no demonstrated benefit
for this scope. Beads remains an alternative if concrete scheduling requirements justify its additional
machinery. This assessment is not installation authority.

### Scripted work items and deterministic templates (15 October clarification)

Tommy accepts the hosted-tracker direction in principle and requires scripts/templates for mistakes,
debt and bugs so agents supply facts without regenerating boilerplate. He also asks whether features
and work items belong outside Issues. This adds a design requirement; it does not authorize source
implementation, issue creation or installation under the existing research-only boundary.

GitHub uses ?issue? as its general work-item record. Its documented organization defaults include Task,
Bug and Feature; feature work is an intended use, not a misuse of a defect tracker. Projects provide
board/table/roadmap views over those records. Use domain language such as ?work item? in our command
interface and preserve distinct kinds in templates, native types where available, and labels. [R11-R12]

| Proposed kind | Required substantive fields beyond common title/summary and ownership |
| --- | --- |
| Feature | Intended outcome, scope and acceptance criteria; link a plan when substantial. |
| Task | Concrete action and observable completion condition. |
| Bug | Expected behavior, observed behavior, reproduction or other concrete evidence, impact and resolution condition. Cause can be explicitly unknown. |
| Mistake | Observed incident/evidence, causal decision or explicitly unknown cause, relevant governing rule, proposed prevention and verification condition. |
| Debt | Current compromise, reason for deferral, impact and objective condition for removing the debt. |

Proposed automation boundary: one small Python command with compact JSON input and JSON output.
For example, `work-item create --kind bug --input bug.json` and the corresponding `feature`, `task`,
`mistake` and `debt` kinds. These are proposed commands, not existing installed utilities. A `schema`
operation returns only the selected kind's input fields. The script validates the supplied facts,
renders the versioned template, adds verified repository/time metadata, maps kind to configured type/
labels, links the parent/plan when supplied, submits via GitHub CLI/API and returns the resulting identity
and URL. Reuse one implementation across kinds and hosts.

AI owns diagnosis, relevant evidence, scope, acceptance criteria and identifying an existing causal
record. Code owns mechanical validation, formatting, defaults explicitly defined by the policy, transport
and output. It must never infer a cause or claim verification merely to complete a template. Formatting
can be deterministic without making the underlying judgment deterministic or eliminating all input tokens.

The canonical schema/templates ship once with their source owner. Generate optional browser-facing
GitHub forms from the same definitions rather than maintaining a second authored template set. GitHub
supports issue templates/forms and CLI submission from a body file; the script must validate its own
inputs instead of assuming a web form's required fields apply to API-created issues. [R13-R14]
Keep generic transport/record behavior with its generic owner and personal capture/default policy with
its explicit personal owner, following the ownership split below.

Existing-record updates require the supplied canonical identity. Retry reconciliation uses a stable
request identifier and an observed remote result; it does not promise atomic semantic deduplication or
blindly recreate a record after an uncertain network response. Missing fields fail before submission;
partial remote success is reported with its known identity for recovery. Type/label and Project changes
are configured/preflighted capabilities, not permission to modify organization settings automatically.

Extend pilot acceptance with all five kinds, validation failure without a write, reproducible rendering,
correct configured type/label mapping, an existing-item update, JSON identity output and an uncertain
submission/retry case. No template should require the model to generate headings, boilerplate or a second
Markdown copy of the submitted work item. Script source and installed-host tests remain future work.

### Proposed everyday workflow

| Information | Canonical proposed owner |
| --- | --- |
| Outstanding feature, bug or deliberate debt | One issue in the causal source repository, with a small label set such as `feature`, `bug`, `debt` and `process`; evidence and resolution condition in its body. |
| Substantial implementation design | One repository plan linked from the issue. Small fixes need no extra plan. Code-dependent documentation follows its code's branch and PR. |
| Repeated observation or progress evidence | A comment on the existing issue or active PR. An already fixed minor slip needs no separate issue merely to prove that an agent noticed it. |
| Agent/process mistake requiring prevention | An actionable issue owned by the causal standard/component. Preserve incident evidence there; put the verified, reusable prevention rule or test in its actual source owner. |
| Durable project knowledge | Concise maintained docs and relevant agent instructions, reviewed with the change that establishes them. Avoid loading the entire historical incident log into every session. |
| Native session IDs, local writer/process state and credentials | Local runtime state; link a relevant session from the issue when useful. Do not synchronize a live local session database as the project tracker. |

Proposed recording threshold: create a new item for an outstanding action or a prevention change that
needs its own owner. Add evidence to existing work when it already owns the correction. This preserves
automatic capture of material problems without a new issue, file and publication cycle for every typo.
Tommy must approve that threshold; the existing mandatory recording behavior is still current source.

Issue writes are remote publication too. Future personal-policy approval would need to authorize routine
issue creation/updates in designated repositories; this research authorizes none. Use the actual source
repository and its visibility, not a public personal inbox for private material. Reading an issue does not
authorize implementing it, and creating it does not start a second repair owner.

For concurrency, use server-assigned issue identities, keep one active work owner, and append evidence as
separate comments. Limit edits of the canonical issue body to its owner. Searching before creation reduces
duplicates but is not an atomic deduplication guarantee. Reconcile duplicate observations into one causal
issue without erasing evidence. An assignee or `in-progress` label is coordination metadata, not a
distributed lease; two agents using Tommy's account are still different sessions. Initially allocate
distinct issues explicitly. Automatic contested task claiming needs its own tested coordinator before
parallel autonomous dispatch is advertised.

When offline, code work and local notes can continue. Any unpublished observation must be reported as
local and unsynchronized. An optional outbox would use a stable request ID and reconcile uncertain remote
results before retrying; it is not a second authoritative backlog. If full offline task browsing and
editing is essential, select the file-based candidate for evaluation instead of expanding this proposal
into an elaborate issue cache. Hosted issues also need a separate export/backup decision: cloning code
does not back up the issue discussion.

For the original file-based candidate, every participating agent would need the same locked
read/reconcile/allocate-ID/write path in the primary checkout, with crash-safe replacement and checks for
unexpected edits. Core already has Windows/POSIX locking examples in `hook_runtime.py` and
`agent_recovery.py`; these are reuse evidence, not a completed record writer. Preserve existing IDs and
other writers' entries. A nonparticipating editor or a second clone is outside that local guarantee.
The scale of this extra coordination favors the hosted queue for the stated online case.

### Generic capabilities and personal policy ownership

| Ownership alternative | Tradeoff |
| --- | --- |
| Only repository settings in Core | Small distribution change, but leaves Tommy's policy source and release coupling in the generic owner. A boolean alone does not remove mandatory publication assumptions. |
| An opt-in personal plugin inside Core | Viable smaller repository count, provided dependency edges never activate it for Core consumers. Still couples personal workflow changes to Core's source repository. |
| Separate personal-policy source package | Viable for broader personal standards. The latest naming/boundary proposal below recommends one `tj-agents/work-items` source owner for this tracking capability, without requiring another personal repository first. |

Core keeps the common evidence/identity contract, explicit `write-*` and `address-*` interfaces, causal
deduplication, repository-declared destinations, repair lifecycles and generic documentation correctness.
Its entry points must support an owning issue or declared file register without imposing Tommy's automatic
capture, primary-checkout placement, retention cadence or per-observation delivery on every consumer.
Existing callers remain valid: change the shared destination resolution they use rather than cloning six
skills into the personal package. Default file behavior for an explicit write request remains compatible;
mere installation must not mandate the personal workflow.

The personal owner supplies automatic-capture criteria, the selected tracker convention, shared working
notes, curated learning and batch cadence. Work/employer owners supply their own tracking and publication
rules. Update Core session guidance, problem-record consumers, documentation/commit boundaries and the
hardcoded handoff-admission checks together with the new contract. A missing selected backend must produce
a real blocked state, not silently create another register or change work repositories' behavior.

Adopt the personal workflow explicitly through each approved personal repository's committed plugin lock
and generated host settings. Add its real published package to the marketplace and adoption roster first.
A checked inventory of approved canonical repository identities drives existing-repo adoption and new-repo
templates; keep private inventory data with its authorized owner. An explicit opt-out is retained in that
inventory and removes the project selection, so a later sweep does not re-add it. A machine-global install,
cached skill or directory outside `infonetica/` never proves adoption. Fresh computers consume the same
committed selections; installation and hook trust must still be verified on each host. Reuse the existing
catalog/source-ownership owners without extending the parent's Rolling Plugin Sync task.

### Proposed repository name and package boundary (latest direction)

Tommy now wants to proceed toward GitHub-backed personal work items and asks where the skills should
live, whether Core should be renamed, and whether a separate repository should be called documentation
or work-item. His Infonetica repositories must retain Azure DevOps while continuing to use Core.
Backend selection is settled in principle; source naming/ownership is the current design decision.
This turn prepares that concrete decision in the existing plan. No new repository or runtime source
has been created, and no employer tracking change is inferred.

Recommend `tj-agents/work-items` as the source repository and `work-items` as its explicitly adopted
plugin. These are proposed identities, not names claimed to be published or available remotely. Its
subject is the lifecycle of features, tasks, bugs, mistakes and debt: structured input, validation,
versioned templates, create/read/list/update/link/close operations and recovery of uncertain writes.
The first implementation uses GitHub. Do not build an Azure DevOps adapter or generic provider framework
in anticipation of an unrequested migration; the existing employer workflows already own that job.

| Concern | Recommended owner |
| --- | --- |
| Shared agent/session helpers, generic repair and execution lifecycle | Existing Core packages. They consume an optional repository-declared tracker integration without choosing GitHub for every user. |
| GitHub work-item commands, templates, schemas and tests | New `tj-agents/work-items` source package, with one canonical implementation shipped to both hosts. |
| Which personal repositories adopt it and when agents record automatically | Explicit repository selections plus the approved personal adoption inventory/policy. A global Core install supplies no adoption evidence. |
| Azure DevOps work items and employer-specific rules | Existing Infonetica/work-repository owners; existing commands, approval gates and destinations remain theirs. |
| Actual feature/task/problem records | The source project's own GitHub Issues, not one organization-wide inbox in the new tooling repository. |
| Designs, specifications and cross-repository proposals | Their existing source-repository plan owners or this docs repository according to its README. |

A single work-items repository is sufficient for the first delivery. The earlier separate `personal`
package suggestion covered broader personal policy. Do not create both repositories merely to deliver
this one reusable tracking capability; a broader personal standards owner can be decided independently.
The reusable scripts must not import mandatory personal cadence into Core. Existing `write-*` callers
need a compatibility route to the selected tracker; the transport/template implementation belongs to the
new owner rather than being copied into Core or employer skills.

Recommended selection behavior: explicitly adopted personal repository -> work-items/GitHub; Infonetica
repository -> existing employer/Azure DevOps; no selected tracker -> generic helpers remain usable and
no GitHub write is inferred. A failed or missing selected integration is actionable failure, never an
excuse to silently choose a different destination. Do not use folder names, installed cache contents or
absence of employer detection to turn the new plugin on.

Keep `tj-agents/core` for this change. Its README and source map already identify shared `base`,
`engineering` and `machine` packages; separating optional tracking is compatible with that foundation.
A rename would affect published repository references, marketplaces and callers while solving none of
the selection problem. If Tommy wants a more descriptive name later, assess `agent-tools` separately
with an explicit migration and compatibility boundary. No rename is selected here.

Naming rationale: `work-items` identifies the records and operations; `documentation` includes a much
larger concern already owned by docs; `planning` omits ongoing bug/debt tracking; `tracking` is broader
and could be confused with local agent/session state. The optional preference question recommends
`work-items`; no separate question about adopting GitHub is needed again.

First implementation candidate after the source boundary/name is resolved: scaffold the source owner
through kit and apply its declared plugin standards before governed code; implement compact JSON input,
preview/validation and deterministic rendering for the five kinds; then add GitHub create/get/list/update
and closure/link operations in reviewable slices. Test rendering and invalid-input rejection without
network writes, then transport recovery against a controlled test backend and an authorized GitHub pilot.
Do not represent feature creation as starting implementation automatically.

The rollout outcome is all approved personal repositories adopting the workflow, with selected existing
records migrated through the identity-preserving mapping below. The source package is tooling, not the
migration's central record store. Per-repository adoption and migration need an observed inventory and
must exclude employer repositories; archive/deletion, live installation and external publication keep
their actual gates. Rolling Plugin Sync retains its existing parent and scope throughout.

### Batching, migration and acceptance

Recommended batch trigger for the remaining shared Markdown notes: an explicitly authorized docs-maintenance
task in that repository. Its accepting agent owns one scoped batch. No count, timer, session exit or code
commit silently triggers publication. Documentation needed for a code change still travels with that change.
With the proposed issue backend, live queue updates need no Markdown docs PR; curating durable lessons is
the separate batch. If Tommy prefers automatic curation at the next relevant authorized docs delivery,
record that as a separate decision before implementing it.

The batch owner snapshots only selected notes, prepares a scoped candidate outside a dirty shared checkout,
and leaves later observations pending. Following verified merge, reconcile the published snapshot with the
live notes under the same writer coordination; never restore an older whole file over newer observations.
GitHub issue writes and repository automation effects need their own authorized, observed verification.

Migration preserves every existing `B`/`M` identity, M001-M007 learning history, record fields and repair
links. Do not bulk upload, delete or renumber records during a pilot. If the issue backend is approved,
move only selected actionable items with an explicit old-ID-to-issue mapping. Mark their old entries as
moved with a link, then maintain status in the issue alone. Keep unresolved/unmapped entries visible and
preserve resolved historical evidence. Debt deletion rules require deliberate reconciliation before any
register is retired. Backlinks from plans and published skill callers must continue to resolve.

| Acceptance case | Proposed pass condition; none is claimed tested yet |
| --- | --- |
| Personal primary checkout | Explicit project adoption loads the personal policy and resolves one canonical source-repo issue/register owner. |
| Personal feature worktree | Resolves the same tracker identity; no duplicate backlog in the worktree. Its implementation plan stays with its actual delivery owner. |
| Concurrent agents | Independent issues preserve both agents' evidence; contention on one item is reconciled before a second executor starts. No assignment-as-lock claim. File candidate tests also cover simultaneous creation/update and unique IDs. |
| Second computer/developer | Reads the same hosted issue state without copying machine-local files. Repo docs become visible after Git delivery; unsent notes remain explicitly local. |
| Work repository using Core | Generic capabilities still work with the employer destination; no personal recording rule, issue destination or docs cadence is inherited. |
| Explicit personal opt-out | Lock/settings regeneration removes personal behavior and the adoption sweep preserves the exception. Existing records are retained. |
| Recording and publication boundaries | Observation capture creates no code commit, push or docs PR. Issue writes occur only under separately approved tracker authority. This research creates neither. |
| Offline or missing credentials | Useful authorized code/research work continues; unsent observations retain evidence and are not reported synchronized or recorded remotely. |

### Next implementation slice after a decision

The latest package-boundary proposal above supersedes the earlier manual-pilot-first sequence. Tommy
requires deterministic scripts/templates as part of the intended workflow. Resolve the new source
identity, then scaffold its kit layout and apply the declared plugin standards before governed code.
The first reviewable source slice implements JSON input, kind-specific schema selection, validation,
preview/rendering and structured results for feature, task, bug, mistake and debt. It makes no live
tracker writes. Reuse the existing generic record fields and preserve unknown causes explicitly.

Follow with the GitHub transport and a small authorized pilot: one feature, one bug/debt observation,
a repeated observation, a linked plan, repair/closure evidence and a second-computer read. Exercise
invalid input, absent auth/network, ambiguous submission results and duplicate-owner attempts. The pilot
verifies that one causal item is visible across computers without a per-observation documentation PR;
it does not establish an automatic distributed scheduler. Use controlled test transport before any
live pilot records, and identify the pilot repository and its issue-write scope first.

Core owns its backend-neutral record/admission contract and compatibility path; the work-items source
owner owns the selected GitHub tools/templates; marketplace/machine owners add its published selection.
Consumer adoption and identity-preserving migration then follow in reviewable repository slices. Review
actual Python/package mechanisms in those source repositories before calling the larger rollout
implementation-ready. Revalidate Windows/Linux and both installed hosts. Coordinate Core's generic
policy change and personal adoption so no work-policy leakage or silent personal behavior gap is
represented as a finished migration. No Core rename or employer workflow replacement is selected.

### Sources and verification

- [R1: Git worktree topology](https://git-scm.com/docs/git-worktree) and [Git history/sharing](https://git-scm.com/book/en/v2/Git-Basics-Working-with-Remotes).
- [R2: Backlog.md documentation](https://github.com/MrLesk/Backlog.md) and [mutation implementation](https://github.com/MrLesk/Backlog.md/blob/main/src/core/backlog.ts), notably `withCreateLock` and `updateTaskFromInput`.
- [R3: GitHub pricing](https://github.com/pricing) and [Issues/Projects availability](https://github.com/features/issues).
- [R4: Issue dependencies](https://docs.github.com/en/issues/tracking-your-work-with-issues/using-issues/creating-issue-dependencies).
- [R5: GitHub CLI issue commands](https://cli.github.com/manual/gh_issue) and [issue creation](https://cli.github.com/manual/gh_issue_create).
- [R6: GitHub's issue-to-cloud-agent workflow](https://docs.github.com/en/copilot/how-tos/use-copilot-agents/cloud-agent/use-cloud-agent-on-github). This illustrates an approach, not a required service purchase.
- [R7: Current Beads upstream](https://github.com/gastownhall/beads), [Dolt architecture](https://github.com/gastownhall/beads/blob/main/docs/architecture/dolt.md) and [claim interface source](https://github.com/gastownhall/beads/blob/main/claim.go). The old `steveyegge/beads` address redirects to this owner.
- [R8: Azure DevOps billing FAQ](https://learn.microsoft.com/en-us/azure/devops/organizations/billing/billing-faq?view=azure-devops).
- [R9: OpenSpec](https://github.com/Fission-AI/OpenSpec/blob/main/docs/README.md).
- [R10: GitHub Spec Kit](https://github.com/github/spec-kit).

- [R11: GitHub issue types](https://docs.github.com/en/issues/tracking-your-work-with-issues/using-issues/managing-issue-types-in-an-organization) and [intended uses of issues](https://docs.github.com/en/issues/tracking-your-work-with-issues/learning-about-issues/about-issues).
- [R12: GitHub Projects views](https://docs.github.com/en/issues/planning-and-tracking-with-projects).
- [R13: Issue templates](https://docs.github.com/en/communities/using-templates-to-encourage-useful-issues-and-pull-requests/configuring-issue-templates-for-your-repository) and [form syntax](https://docs.github.com/en/communities/using-templates-to-encourage-useful-issues-and-pull-requests/syntax-for-issue-forms).
- [R14: CLI create flags](https://cli.github.com/manual/gh_issue_create) and [issue API](https://docs.github.com/en/rest/issues/issues).

Source inspection and public documentation support this assessment. No popularity ranking, fresh installed
integration test, atomic cross-machine claim, free-tier capacity beyond the cited features, or implemented
personal package is claimed. The narrower assessment is ready for Tommy's decision; the larger runtime
design remains conditional on the pilot and source-owner review.

Documentation verification on 15 October 2026 passed: plan graph (zero errors and warnings),
relative file links, unique research/next-step sections, the plan-stage host-coverage validator and
`git diff --check`. Ownership and proposal/current-behavior distinctions were checked against the cited
sources. This is research validation, not a frozen independent runtime review or installed-host test.

```agent-host-coverage
{
  "schema_version": 1,
  "shared_source": "Proposed work-items package and personal adoption policy consuming Core's shared problem-record and repair contracts; this research changes only docs/plans/problem-management/PLAN.md",
  "hosts": [
    {
      "host": "claude",
      "behavior": "Select the repository-adopted personal policy, use the same canonical issue or register, and preserve work-repository and publication boundaries",
      "source": "Proposed personal canonical policy with Core record/admission consumers and published harness dependencies",
      "mapping": "Generate Claude project settings from the repository lock and load the selected policy through its declared host entry points",
      "verification": {
        "level": "planned",
        "result": "pending",
        "evidence": "Pilot and installed-host acceptance matrix above; no Claude installation or runtime behavior changed in this research"
      }
    },
    {
      "host": "codex",
      "behavior": "Select the repository-adopted personal policy, use the same canonical issue or register, and preserve work-repository and publication boundaries",
      "source": "Proposed personal canonical policy with Core record/admission consumers and published harness dependencies",
      "mapping": "Generate Codex project settings from the repository lock and qualify declared hook trust and policy entry points separately from installation",
      "verification": {
        "level": "planned",
        "result": "pending",
        "evidence": "Pilot and installed-host acceptance matrix above; native research-session identity is recorded below and no Codex profile was changed"
      }
    }
  ]
}
```

## Approved execution (16 October 2026)

Tommy approved the concrete work-items proposal and instructed this session to implement it all.
This supersedes the research-only restrictions recorded in the historical handoff. Create
`tj-agents/work-items`, implement deterministic templates and GitHub issue tooling, integrate
Core through explicit repository selection, publish the package and adopt it in personal repositories.
Keep Core's name and preserve Infonetica's Azure DevOps policy. GitHub Issues in each source
repository stores its work; the tooling repository is the first live pilot. Existing records retain
facts and stable identities during migration. No employer repository or unrelated workflow is in scope.

Owner: `codex:01a1415f-6448-7123-8b17-c7fb67aee637`.
Rolling Plugin Sync remains with parent `codex:01a13fa0-a1c6-7051-b3ce-a63fb26916da`.
The parent checkout, branch and goal remain outside this owner's work.

### Delivery map

1. New package foundation: scaffold the optional utility plugin using Template, inject pinned
   project standards, add JSON contracts, five deterministic templates, validation and preview.
   New repository base; focused Python tests, generator/manifest/host checks. Expected under
   1,000 substantive lines. Commit and review this coherent slice before growing transport scope.
2. GitHub transport and live pilot: create/read/list/update/link/close, strict repository selection,
   request identity/reconciliation, compact output and failure coverage. Base on delivered foundation.
   Demonstrate real writes in `tj-agents/work-items`; close pilot records with observed evidence.
3. Core compatibility: backend-neutral problem identities and admission, selected tracker dispatch,
   existing published skill names and file-backed compatibility. Fresh Core base isolated from parent.
   Include enforcement/caller tests atomically; split assessment before exceeding review budget.
4. Publication and selection: marketplace registration and machine roster/injector support with
   generated manifests and settings checks. Base each repository on its current remote default.
5. Personal adoption: inventory eligible repositories, preserve their existing configuration and
   histories, migrate actionable records with legacy links, and verify both host selections.
   Source-specific plans and measured PR boundaries live in the corresponding source checkout.

Completion requires delivered tooling, observed GitHub pilot, compatible Core behavior, selectable
published package and verified personal adoption. A completed foundation slice is partial progress.
Source runtime changes and implementation details belong in their source repositories; link their
plan slices here. Existing unrelated dirty documentation remains untouched.

## Implementation checkpoint (16 October 2026)

The optional repository `tj-agents/work-items` exists. Tommy explicitly approved making this generic
tooling public after GitHub refused to start private-repository jobs due to billing/spending limits.
It is public; no other repository visibility changed. Foundation PR #3 at 8ec0b6a has clean native full
and incremental review, five tests, 37-file generation/conformance and successful Windows/Linux/host CI.
Tommy approved its CI-caller stop class; PR #3 merged at 66aadc23819835469e72d8604d5a788da7b74211.
Its causal main CI 38831521132 passed. Source plan:
[work-items foundation](../../../work-items/plans/work-items/PLAN.md).

Template prerequisite PR #12 merged at 15609a6 after Tommy's explicit merge/release approval. Both-host
CI and its causal main run passed; immutable v1.6.1 now points to that landing. The canonical updater
moved the work-items generator/configuration/CI caller to that release. Template's source repair and
B001 preserve their evidence in its source repository.

Transport PR #5 merged at 76c2640018326aa3f1ddd4c011c929c488f7d95a. Its reviewed head d7fe04f includes its immediate parent's
Template pin merged into the child. The first native transport review was clean. Its controlled pilot
then exposed B001: immediate sequential creates produced issues #1 and #2 for one request ID. Current
markers parse correctly; the immediate list response was not captured, so a stale list is a reproduced
failure model rather than a proven upstream cause. Durable local submission intent and returned identities
now prevent reposting even when lists omit fresh records. Cross-machine/receipt-loss retries have an
explicit reconciliation-only mode. Twenty-three tests and 49-file generation pass. The repair's native
review requested equivalent reconciliation-only handling for appends; that correction passed its final
native review and both-host source coverage check. A fresh persisted request created issue #4; its immediate
repeat returned the same issue, hash-checked update passed, a repeated note reused the same comment, linking
passed and verified closure succeeded. Failed pilot issues #1 and #2 are closed with truthful verification evidence; their original
failure and history remain preserved. Installed-host and live Core admission acceptance remain separate pending checks.
Active transport slice: [source plan](../../../work-items/.worktrees/Feature-GitHubTransport/plans/work-items/PLAN.md).

Core's generic opt-in provider integration is isolated on Feature/ProblemRecordBackends, from 6be8c45.
The initial 39 focused tests and package/harness checks passed. Native review found a helper-import
resolution issue, now corrected with a shadow-module regression; parent inspection also corrected native
discovery error handling and actual-host receipt binding. All 41 focused tests pass. The follow-up generated-host path finding is rejected with executable
evidence: all four entry points pass in an isolated package directory without a source-checkout fallback.
The host layouts correctly resolve parents[3]/hooks.
Generated distribution/catalog files stay outside its authored PR. Its source plan owns implementation:
[Core provider slice](../../../core/.worktrees/Feature-ProblemRecordBackends/plans/problem-record-backends/PLAN.md).
Core PR #272 merged at 6aea302b1562b714bc2d1dd9f8e010898bfe2dac. Its causal main CI 38834317856 passed; generated publication is 1509abf8. Installed acceptance remains pending.
The parent's Rolling Plugin Sync worktree, branch, ownership and goal remain untouched.

The proper dependent Feature/CoreRecordAdapter branch owns the package's current integration progress:
[adapter plan](../../../work-items/.worktrees/Feature-CoreRecordAdapter/plans/work-items/PLAN.md).
It adds coordinated explicit tracker/provider declarations, read-only current-record transport and typed
problem facts/disposition rendering. Thirty-four tests and 53-file generation pass. The adapter at fb463ab passed native and workflow/security review. PR #7 merged at 7c4dcd2147a46005020ee4f2b68db563d71a52a5 and causal main CI 38836538305 passed. Published v0.1.0 resolves to that reviewed landing. Both native hosts loaded the package and admitted live controlled issue #9; stale-callout and recovered-evidence cases were rejected on both hosts. Issue #9 closed with those observations. Consumer adoption remains pending.
Core's injector accepts qualified foreign selections and pins, but still forces the aggregate Core triplet. The generic compatibility slice below preserves existing producer identities without global changes; no backend-specific registry is added.

Optional discovery passed 26 tests, both generated catalogs, native Claude marketplace validation and independent review. Marketplace PR #11 merged at 691f795aa0f91c8a8bfd299b5d8c8bf183e4375a; causal main CI 38840748429 passed. It pins the actual v0.1.0 tag and verified peeled commit. Source owner: [discovery slice](../../../marketplace/.worktrees/Feature-WorkItemsPlugin/plans/work-items/PLAN.md).

Task ownership is registered to codex:01a1415f-6448-7123-8b17-c7fb67aee637. Continuation initialization and
foreground claim succeeded, but scheduler registration failed because the configured inbox powershell.exe
is unavailable. Work continues in the foreground; no unattended wake or installed-host acceptance is claimed.

## Next Steps

Resume the original personal GitHub work-items rollout using the now-published unversioned selection contract. First reconcile `problem-management/personal-policy` ownership through the supported session-store CLI; this session remains its recorded owner, so a successor must follow an actual ownership transfer rather than create a second writer. Read the current Core `machine:plugin-selection` and work-items `manage` contracts from their advertised locations. Reuse the completed research and delivered tracker; do not rebuild them or repeat the storage survey.

Start with docs and work-items as explicit adoption pilots: preserve each consumer's existing plugin selections and local permissions, select the optional package through the current injector, then use the shipped tracker adoption command to write `.work-items.json` and `.problem-records.json` together for that repository's verified origin. Verify actual installed-host discovery and reading/writing the selected tracker. Then refresh the 35-repository inventory from 16 October before applying the same adoption to the remaining eligible personal repositories under their own instructions and delivery gates. Preserve active owners; exclude employer repositories.

Migrate existing bugs, mistakes, debt and queued feature/task records deliberately using the shipped schemas and lifecycle. Preserve legacy IDs, source/history links, state, ownership, repair links and verification evidence; reconcile existing managed issues before creating another. Persist and reuse request IDs. Do not delete or retire a local register until its records have verified canonical issue identities and links. Keep substantial plans and curated documentation with their source owners. Record per-repository adoption and migration evidence so completion is demonstrable rather than inferred from plugin installation.

Scope: original authorized optional GitHub tracker delivery and personal rollout.
Current slice: explicit consumer adoption through the delivered versionless selection contract.
Remaining scope: eligible personal-repository rollout, legacy-record migration and installed-host acceptance.
Done when: each eligible repository is verified adopted or has a concrete recorded exclusion/blocker, and every in-scope legacy record is reconciled with its canonical issue without losing history. Shipped tooling alone does not meet this condition.


## Rollout checkpoint ? 16 October 2026, 01:43 UTC

Foundation PR #3, transport PR #5 and retained pilot-evidence PR #6 are merged with successful causal main CI. Core provider PR #272 and its generated main publication are delivered. Pilot #4 verified immediate retry reconciliation, update, repeated note, PR link and evidence-backed close; failed #1/#2 remain closed with retained B001 evidence and unknown original list-response cause.

The adapter's accepted review findings are corrected: managed body integrity, kind binding without rejecting arbitrary Markdown examples, serialized adoption/rollback and foreign-provider preflight. Old four-field managed issue bodies remain readable; Core admission requires a managed update to add kind binding. Independent native and workflow/security review passed with 34 source tests. Installed-host acceptance remains pending.

Source inspection found schema-3 project injection forces aggregate Core identities even where the machine uses producer identities. A separate generic compatibility slice preserves existing aggregate defaults and permits one producer Core triplet with an immutable pin, explicit conversion and unchanged global settings. It owns implementation and 83 focused tests here: [producer plugin locks](../../../core/.worktrees/Feature-ProducerPluginLocks/plans/producer-plugin-locks/PLAN.md). This is part of the already authorized project selection outcome. No employer profile or parent Rolling Plugin Sync worktree is changed.

Read-only inventory deduplicated local clones by canonical GitHub source and found 35 writable, unarchived, issues-enabled personal repositories. Employer scopes and unavailable/non-writable sources are excluded. Consumer writes and legacy-record migration have not started; read each consumer's actual instructions and preserve active primary-checkout owners before isolated adoption branches. Optional marketplace discovery is prepared but awaits the actual immutable producer publication; its older bootstrap-capabilities prose must be corrected to current plugin-lock behavior before publication.

## Delivery and headache checkpoint - 16 October 2026

Delivered: Template PR #12/v1.6.1; work-items foundation #3, transport #5, retained pilot evidence #6, Core adapter #7/v0.1.0, retained delivery incident #8; Core provider #272 and producer-lock compatibility #273; marketplace discovery #11. Work-items #8 landed c52456c7c0d2f407dda8718eb92f0639885c261c with successful main run 38838523809. Core #273 landed 944cc2aac501c7ceef2e5e6d0e8d69c0aaa9b668; its causal main run 38840514845 completed successfully, observed by the exact-run monitor. Generated publication is 8bddc8ef158f02704377656ce7c6dce6dfa44979. No other owned implementation PR remains open.

Both native loaders installed Base, Engineering, Machine and work-items in isolated temporary profiles. Codex fetched exact remote commit pins. Claude loaded Core from a verified published checkout and work-items from its remote v0.1.0 tag. Both actual installed admission entry points resolved the installed provider, read current GitHub issue #9, accepted its controlled typed disposition, rejected an unrelated callout, and rejected it after the prerequisite became readable. This was a disposable acceptance fixture, not an actual product defect or dispatched repair. Issue #9 is closed with this verification. Normal user profiles and all consumers are not claimed configured.

Tommy reported excessive elapsed time (roughly four hours), requested notes of every concrete headache and instructed this owner to finish without a repair detour. Work-items primary MISTAKES.md M002 retains that incident; it remains unresolved. Comparing all six skill files changed by Core WorkflowProportionality PR #268, commit 2380644a, proves both the installed package and active session hook snapshot exactly contain that fix. The visible 2.1.16 package directory is not proof of stale instructions. Repeated review cycles, path/command mistakes and rollout preparation were avoidable owner overhead. Native Core Windows validation was also a material observed remote wait; do not attribute all elapsed time to CI.

Concrete headaches and dispositions:
- GitHub initially refused private work-items CI due to account billing/spending limits. Tommy approved only that generic tooling repository becoming public; CI then ran. No other visibility was changed.
- Template required-config checking and stale CI owner reference were genuine prerequisite defects, repaired and released in v1.6.1.
- Immediate pilot creates returned two issues for one request ID. B001 retains the unknown original list-response cause. Durable intent/returned identity and reconciliation-only retry handling were repaired and verified with fresh issue #4.
- Adapter review found body/kind integrity and adoption serialization/preflight gaps; corrected before release. Core helper discovery and observed-host receipt binding were corrected before its merge. Installed positive and negative admission now pass.
- The delivery command continued after a failed prerequisite. M001 records the confirmed unchecked native exit, correction, and missing historical pre-merge binding without claiming a retroactive one. Later dependent commands fail closed.
- Marketplace dependency metadata validates Base but does not auto-install it. Corrected explicit Base and qualified producer instructions passed review; do not add another dependency mechanism.
- Claude repository shorthand tried unavailable SSH authentication. HTTPS with a release tag worked. HTTPS with a raw commit ref attempted a branch clone and failed. The verified local published checkout proved package loading, not reproducible remote Core selection; retain that distinction.
- Existing consumer settings include legacy/foreign plugin identities and local permissions; the injector must preserve them. The read-only 35-repository inventory is not adoption or migration evidence.
- Continuation scheduler registration failed because its configured inbox powershell.exe was unavailable. This owner remains foreground-only; no unattended continuation was promised.

The separate Rolling Plugin Sync/latest-release PR remains with parent codex:01a13fa0-a1c6-7051-b3ce-a63fb26916da. Tommy explicitly confirmed that owner is removing stale version selection and forcing current releases; do not start a competing versioning repair or migrate user profiles here. Personal rollout depends on reconciling that delivered selection contract with the observed Claude raw-commit clone failure and preserving each consumer's current selections. The immutable work-items release is ready for that owner. Existing local records remain intact; no blanket record migration has been performed.

Next action: complete causal Core main validation/publication, reconcile the separate latest-release selection owner, then apply and verify personal adoption through that contract. Do not claim the original all-personal rollout complete or solve the same versioning problem in parallel. The user-facing report must distinguish delivered tooling from that remaining dependency and list which headaches are already fixed versus addressable follow-up.

### Remaining dependency and requested reflection

Core PR #269 is the verified existing Fix/RollingPluginSync delivery at 81dce32ea5f69deb1947ed6136824f33b45132da. Its PR body explicitly replaces versioned locks with unversioned repository selection, migrates schemas 2/3, refreshes actual plugin bytes before launch and preserves current session snapshots. It reports clean review and green CI; its source owner reserves merge to Tommy. This session neither changes nor merges that delivery. Committing versioned adoption to 35 consumers now would conflict with its imminent cutover. Consumer rollout and record migration therefore remain blocked by that concrete dependency, not reported complete. Resolver: PR #269's existing owner/Tommy. Resume condition: #269 is merged, causal generated publication passes and its shipped injector/native refresh contract is available. Next action: adopt work-items and docs through that contract, then the remaining inventoried personal repositories, preserving each existing selection and register history. No employer repository is included.

Tommy requests an evidence-based reflection after this delivery: do not presume Core is the cause or that removing hooks is desirable. Distinguish productive implementation, checks that caught real defects, remote CI waiting, environment/CLI friction and avoidable agent orchestration. Discuss specific checks/hooks to retain, simplify, batch or remove, with observed benefits and costs. This is discussion authority, not permission to disable hooks or launch another runtime repair now. Six relevant PR #268 skill files match the active snapshot, so those recent proportionality fixes were in use. The separate versioning work remains with PR #269.

Read-only integration with #269: archived exact reviewed candidate 81dce32e into a temporary fixture, then ran its replacement plugin-selection injector with the producer Core triplet and work-items@work-items-agents. Both write and check passed, generating .agents/plugins.json and both host settings without revisions. This verifies prospective composition only; #269 is not merged/installed here, no parent checkout was edited, and no consumer was migrated. The required future command shape is therefore confirmed rather than another design question.

Read-only integration check after #273 publication: `git merge-tree --write-tree --name-only origin/main 81dce32e` exited 1 and identified six conflicts: `.agents/catalog/catalog.json`, `.agents/catalog/plugins.schema.json`, `.agents/hooks/tests/test_plugin_lock.py`, `.agents/machine/utility/plugin-lock/SKILL.md`, `.agents/machine/utility/plugin-lock/scripts/adopt_plugins.py`, and `.agents/machine/utility/plugin-selection/scripts/plugin_selection.py`. No branch, index or checkout changed. #269's owner must reconcile current main before its prior green review/CI evidence can cover the integrated candidate. Preserve #272's generic provider protocol and use #269's unversioned selection as the destination; do not retain a second competing versioned adoption interface. This is a concrete coordination headache introduced by parallel source work, not evidence that the active proportionality fix was missing. Parent checkout and PR remain untouched.

Final validation: all nine owned delivery PRs have successful causal main CI. Core #273's final monitor recorded 1,020 seconds of remote waiting; this is measured waiting for that monitor window, not a claim that all elapsed time was idle. Publication 8bddc8ef contains the delivered source. No own implementation PR remains open. Broad personal adoption and legacy-record migration are explicitly pending the separately owned #269 integration and published unversioned contract; the overall rollout is not complete.

### Reflection for the requested discussion

This was substantive work across four source repositories and nine delivered PRs, including a new deterministic tracker, live retry protection, provider admission and both-host packaging. Reviews earned their cost where they found actual kind/body integrity failures, overlapping adoption/rollback, wrong helper resolution and host-binding errors. Those protections should remain. Windows runtime CI also supplied genuine cross-platform validation, while adding material elapsed time.

There was avoidable owner overhead: failed guessed paths and command syntax, repeated small documentation-review cycles, two record-only delivery PRs, and implementing current-lock compatibility while the existing #269 work was replacing that interface. The proportionality fix was active; this is not evidence that stale versions explain the four hours. The new GitHub provider removes record-only Markdown PR delivery after adoption. Concrete mitigation candidates for discussion are batching factual records, reusing exact-head verification evidence, batching independent review lenses, coordinating the selection cutover before expanding consumer scope, and measuring the slow Windows runtime steps before selecting narrower checks. Do not remove safety hooks or required cross-platform coverage merely from elapsed time. No hooks were disabled and no competing latest-version fix was started.

Observed final Core run timings: verify-windows ran 02:27:29-02:46:51 UTC (19m22s); verify-linux ran 02:27:29-02:31:07 UTC (3m38s). Both passed. Completed #273, marketplace #11 and retained-evidence #8 delivery bindings were released successfully. All owned CI monitors are terminal. The existing #269 owner retains the source integration/merge dependency; this owner does not claim the pending personal rollout complete. Retain working checkouts and evidence for that continuation and the requested discussion.

### Validation-efficiency investigation handoff - 16 October 2026

Tommy explicitly requested the bounded follow-up handoff after discussing validation costs. Its source owner is [Core validation-efficiency goal](../../../core/.worktrees/Investigate-ValidationEfficiency/plans/validation-efficiency/GOAL.md), branch Investigate/ValidationEfficiency, from fetched main 8bddc8ef158f02704377656ce7c6dce6dfa44979. Authority is investigation, measurement and recommendations for discussion; no runtime, hooks, CI or consumer changes. One L3 Codex successor is being submitted through the supported launcher. Actual pickup must be recorded in that goal; submission alone is not acknowledgement.

The existing Fix/RoutineReviewAndImpactCi checkout has unfinished merge-review/auto-merge edits and an overlapping goal. It is preserved as read-only input, not claimed or silently resumed. The successor must compare that proposal with delivered proportionality changes before recommending more work. PR #269 remains with its existing versioning owner. This side investigation neither transfers nor completes the original personal rollout.

Handoff pickup verified: the packaged launcher submitted exactly one native Codex 0.163.0-alpha.1 session at lane L3 (gpt-6.1-sol/high), using C:/Users/TommySeery/AppData/Local/Temp/core-validation-efficiency-handoff.txt. Native history identifies successor codex:01a1447f-62b8-70e0-a7a3-20a040f97690 at the exact Investigate-ValidationEfficiency checkout. That successor has acknowledged sole ownership in its source goal. The originating session will not write its investigation artifacts. Runtime implementation remains outside this investigation's authorization.
