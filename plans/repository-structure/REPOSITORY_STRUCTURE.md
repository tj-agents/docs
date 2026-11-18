# Repository structure design

Date: 2026-10-29. Status: agreed design; execution authorised by Tommy's "ok lets go?". Implementation and installed acceptance remain incomplete.

Design discussion checkpoint, 2026-10-29: Tommy accepted the namespace/skills/subject layout, with kind stored only in metadata, and requested idiomatic names that can be discussed against their actual contents. Learning is a distinct kind, not policy. This agreement establishes those design decisions; the complete migration inventory and delivery design below remain planning work rather than evidence of a completed rollout.

## Outcome and current authority

Tommy asked for research into Python project structure and a correction across tj-agents repositories to the overuse of utility and unclear folders such as runtime. He required seeing the final design before conclusion, then explicitly expanded the design to reorganising everything, including broader kind categories and finding all distinctions. This document presents the proposed end state, its source owners and migration acceptance. Template source layout and generated projections are implemented on Refactor/SubjectSkillLayout. The reviewed producer candidate passes local checks and exact-head Windows/Linux/pinned-host CI. Other repository layouts and installed entry points remain to migrate.

The task spans the tj-agents workspace. This is its one cross-repository design artifact. Existing owner implementation work and unrelated local changes remain with their owners. Tommy has authorised execution of the agreed migration. Next, reconcile the Template/Core producer contracts and existing delivery ownership, then deliver coherent source/generator/caller changes before dependent publisher moves.

## Execution checkpoint

Execution authorised on 2026-10-29 in this conversation. The first implementation concern is the shared layout producer and its consumers, starting with Template's checker/generator and Core's discovery/standards-reader contract. This does not narrow the cross-repository goal. The exact slice/base/head and remaining semantic classifications are established before source moves, not invented from the initial candidate counts.

The native session remains attached to C:/Users/TommySeery/source/repos/tj-agents/template. Template delivery branch Refactor/SubjectSkillLayout starts at fetched origin/main 772a05cf83c58e160afd3bdb33f8ece545410d45. Its [implementation plan](../../../template/plans/subject-skill-layout/TEMPLATE_LAYOUT_PLAN.md) and [progress](../../../template/plans/subject-skill-layout/TEMPLATE_LAYOUT_PROGRESS.md) own the source slice. Template producer candidate 9b64b05252d6dff684ae3cd2a4a4850bb356f3b5 is published in [draft PR #56](https://github.com/tj-agents/template/pull/56). Full local verification passed 301 tests and 27 subtests with one existing Windows symlink skip. Review found two native YAML projection defects, both repaired; incremental review passed all 136 generator tests and found no actionable regressions. [Exact-head CI](https://github.com/tj-agents/template/actions/runs/40913201037) passed Windows/Linux checks, pinned host acceptance and system-Python packaged-library delivery. The existing older Template structure goal was inspected as historical related delivery; PR #56 owns this new producer slice. Core implementation continues in its exact isolated checkout with explicit workdirs; Tommy rejected a manual /cd prerequisite.

Template's rolling-main consumers still need their source and workflow-path migrations. Prepare and qualify those candidates against the exact Template producer before landing a breaking producer. Core's generator, kind vocabulary and standards reader are being migrated in `core/.worktrees/Refactor-SubjectSkillLayout`, branch `Refactor/SubjectSkillLayout`, from fetched `origin/main` `db97302002ba692399f7cd650cb8a0b4527361a0`. This current base already removed Agent/CLI/Machine ownership: Core publishes only Base, Workflow, Engineering and Docs, with 57 authored skills. The publisher inventory below is refreshed against the exact main snapshots; candidate migrations are recorded separately. The same cross-repository goal remains active; no global rollout or installed-host acceptance is claimed.

### Current producer and standards checkpoint

Template draft PR56 carries head9b64b05252d6dff684ae3cd2a4a4850bb356f3b5. Its final one-line CI delta includes the selected Template checkout as a reference inventory root. Native incremental review passed37 focused tests and found no actionable regression; fresh security review covered the trunk-to-head sensitive range and verified all304 exported files. Exact-head CI40913201037 passes. Prior full301test/27subtest and136generator-test results remain applicable to unchanged source.

Core draft PR528 carries head727476610c65721215baf65d8ad734fec3e61314, migrating57 skills and114host entries. Exact-head run40911729542 passes all435 source/package and583 shared-runtime tests on both Windows and Linux. Both native startup acceptance jobs still fail because current main's test requires retired Base policy preloading/acknowledgment. That existing contract mismatch remains open; no full-native or merge qualification is claimed. Native incremental and fresh full-range security reviews are complete, with no new finding. The namespace/depth status root check Tommy rejected was replaced by nearest declared package ownership and has relocated/nested-boundary coverage.

Python [draft PR20](https://github.com/tj-agents/python/pull/20) carries head7da6695e5f69ca2c23d05940648707fe8a49c42d from base0c4ee816692ea8a4f1265eb94291bc1272098aaa. Its15 discoverable skills comprise12standards,1learning,1reference and1operation. Learner knowledge and goal/status data are supporting resources; knowledge bytes retain SHA256b12716d5ad09ba90f4a7ad19e7dc5ef04ba367d3dd7eae4f7d3c9e98e9b9a905. Structure/modules distinguish owner-qualified house naming from Python requirements and use cohesive packages and declared resource boundaries. Exact-producer qualification40914850658 passes Windows/Linux repository tests, conformance, references, freshness and native marketplace/plugin acceptance; a copied-plugin probe executes scaffold through both hosts' declared paths. Ordinary CI40914850708 uses old Template main and rejects the new learning resource layout as expected.

Python review found one required delivery dependency, PY-1: installed old Core readers omit or reject new metadata. Core's pending candidate already addresses both readers; the paired actual-payload probe discovers all12standards and accepts all15skills. Keep Python draft until coordinated Core publication and fresh installed-reader acceptance resolve PY-1. Fresh security review has no additional finding. Remove Python's temporary exact-producer qualification workflow after Template main carries the new producer and revalidate ordinary CI. See the [Python implementation plan](../../../python/.git/worktrees/Refactor-SubjectSkillLayout/agent-workflow/repository-structure/PYTHON_LAYOUT_PLAN.md).

### Required directory-transfer repair

Open follow-up, explicitly required by Tommy on 2026-10-29. Owner: this conversation. Tommy subsequently
directed the structure fixes to continue first and the background-terminal repair to follow afterwards.
Retain this follow-up across continuation or context recovery; it does not block the structure migration.
The `/cd` request failed with `Active background terminals block /cd.` The current `base:cd` procedure
omits command disposal and native terminal readiness before asking the user to switch repositories.

- [ ] Apply the prepared [cleanup patch](../../../template/plans/subject-skill-layout/cd-terminal-cleanup.patch)
  to Core's canonical `base:cd` definition, adapting its path if the source layout moves first.
  Require parent and delegated commands to finish or be stopped when obsolete, consume their completion,
  and inspect the native terminal inventory when available before invoking or requesting `/cd`.
- [ ] Preserve the evidence distinction: an unknown command handle or empty OS process scan does not
  prove the native list is empty. If the host guard still fails or native controls are unavailable,
  establish the exact limitation and supported recovery; do not send Tommy through another unchecked retry.
- [ ] Validate and deliver the canonical change, regenerate the shipped host entries, and verify fresh
  discovery. Exercise a repository switch after an owned background command finishes and its completion
  is consumed. Close this follow-up only with the source revision, publication/refresh evidence and
  observed native transfer result; otherwise record exactly which verification remains pending.

The patch is prepared and passes `git apply --check`; it is not applied, published or installed yet.
The original structure migration remains open. This follow-up is implementation work, not another
request for design approval.

Execution steering, 2026-10-29: Tommy rejected further manual `/ps`/`/cd` prerequisites and directed this
conversation to resume the structure work. Continue using explicit repository/worktree paths while
retaining the same owner. Do not describe per-command working directories as a native session retarget.

## Proposed decisions

1. Organise skill source by namespace and subject. Keep kind in frontmatter, out of the directory path and public identity.
2. Present four broad groups: Rules, Work, Learning and Context. Store only the specific responsibility in kind: policy, standard, operation, workflow, learning or reference. The group is derived, not another metadata field. Learning owns teaching, assessment and learner progression as a distinct responsibility. Remove utility as a category and distinguish maintained learning data from instructions.
3. Repository presets select starter content and required capabilities. They do not restrict the kinds of additional skills. Rename the generic utility preset to plugin to remove the overloaded name, migrating its active CLI/template callers without an alias.
4. Put reusable Python implementation in ordinary named import packages. Keep host-loaded skill scripts and hooks as small entry points when an actual host contract requires file invocation.
5. Separate authored source, native host configuration and generated distribution. Preserve public skill names when relocating their source.
6. Apply the shared skill layout across publishers. Let each repository's actual language and independently consumed packages determine its code layout; do not impose a Python workspace on every repository.

## Authored skills

The source root becomes `.agents/<namespace>/skills/`. A folder's relative subject path determines its public name; kind does not participate.

```text
.agents/
  engineering/
    skills/
      commit/
        SKILL.md
      review/
        SKILL.md
      incremental/
        review/
          SKILL.md
  python/
    skills/
      structure/
        SKILL.md
      modules/
        SKILL.md
  template/
    skills/
      structure/
        SKILL.md
      check/
        SKILL.md
```

For example, `.agents/engineering/operation/commit/SKILL.md` moves to `.agents/engineering/skills/commit/SKILL.md` and still publishes `engineering:commit`, with `kind: operation`. Changing a skill's classification later changes metadata, rather than its directory or identity.

Use a family folder when its members form a real subject that benefits from grouping. A shared word, prefix or suffix alone does not require a family. Existing families can retain their subject paths and therefore their public names. The existing rule that mechanically groups matching first or last words is removed. Discovery rejects duplicate flattened names, including collisions between `foo-bar/` and `foo/bar/`.

A skill may keep its own `scripts/`, `references/`, `templates/` and `assets/` when they support that skill. Shared supporting content has a specific role, rather than a replacement catch-all resources directory:

| Content | Source location | Consumer |
| --- | --- | --- |
| Skill instructions | `.agents/<namespace>/skills/<subject>/SKILL.md` | Selected native skill |
| Shared explanatory documents and support contracts | `.agents/<namespace>/references/` | The owning skills that explicitly read them |
| Maintained learner proficiency, goals and progress | `.agents/<namespace>/learning/` | The existing authorised learning owner |
| Shared templates or output assets | `.agents/<namespace>/assets/` | The generator/operation that copies or consumes them |
| Importable implementation and its runtime data | Its named language package | Normal imports and package-data APIs |
| Running session/cache/database state | The existing configured state store outside source | The existing state owner |

Keep skill-local supporting files with that skill; use a shared directory only for genuinely shared material and create it only when needed. The learning directory contains maintained learner data, not Python DTOs or record classes. Name other maintained data by its actual subject and owner rather than introducing a generic records directory.

The resulting repository shape is:

```text
.agents/
  <namespace>/
    skills/<subject>/SKILL.md
    references/
    learning/
    assets/
  plugins/
  tiers/
  hooks/
.codex/
.claude/
src/<import_package>/
tests/
scripts/
plugins/
```

Directories are optional and role-specific. For multiple independently packaged or mixed-repository libraries, the package-member layout below replaces the single-package src root. Native host hook files are thin adapters; scripts contains actual repository commands, not a second importable library. Plugins is generated distribution output in migrated publishers. A non-Python repo retains its language's actual source tree. Legacy authored plugins publishers are explicitly migrated rather than silently treated as generated output.

## Responsibility kinds

Core remains the shared vocabulary owner. The current corpus uses policy, convention, utility, workflow, knowledge and legacy contract/operation labels. Their meanings overlap and some labels describe unlike responsibilities. The proposed taxonomy expresses six distinct roles under four broad navigation groups:

| Group | Kind | Selection test | Example |
| --- | --- | --- | --- |
| Rules | policy | Governs agent conduct, authority or action selection within scope | engineering:committing |
| Rules | standard | Defines criteria for constructing or assessing an artifact or system | python:structure; proposed template:structure |
| Work | operation | Accepts bounded input and returns a concrete result to its caller | engineering:commit; template:check; workflow:status |
| Work | workflow | Retains task ownership through distinct stages, including unresolved acceptance and subsequent actions | workflow:run; skill:update |
| Learning | learning | Owns teaching, assessment and learner understanding or progression | python:learning |
| Context | reference | Supplies independently useful descriptive orientation without owning execution or normative rules | the descriptive part of python:direction |

Several commands, an internal retry loop, long duration or saved intermediate state do not automatically make a workflow. An operation can diagnose, repair and validate what it needs to produce its bounded result. A workflow owns the continuing task, selects constituent operations and remains responsible when their individual results leave its acceptance unmet. An executable helper does not make its owning standard an operation.

Classify every entry by its primary responsibility and observable ownership. The read-only corpus audit supports the following concrete corrections; these are proposed classifications, not applied edits:

| Entry | Current label | Proposed disposition and reason |
| --- | --- | --- |
| skill:new; skill:update | utility | workflow: own authoring/cutover through integration and terminal verification, while their deterministic helpers are operations or modules |
| template:check; python:scaffold | utility | operation: return a conformance result or generated project |
| work:ask | utility | policy: governs recipient/context selection, drafting, clipboard handover and send authority for other drafting operations |
| engineering:committing | contract | policy: governs when an agent commits and publishes |
| workflow:plan-artifacts | contract | standard: defines maintained artifact and evidence requirements |
| engineering:failure-provenance | contract | operation: returns a pipeline-history investigation and classification |
| react:testing | contract | policy: its actual concern is authority to introduce a test tier; suite construction stays with its separate standard |
| Older stack learning skills | knowledge | learning: own teaching, assessment and learner progression; separately consumed rules about changing conventions remain with their rule owner |
| python:structure and actual style/build/design rules | convention or contract | standard: criteria for an artifact/system, rather than an executable task |
| Personal address-work-item | workflow | workflow: retains the selected item's repair/delivery acceptance |
| Personal work-item; create-work-item | utility | operation: read an existing record or create one bounded record |
| Stack knowledge tables | knowledge | maintained learner data: move to the owner's learning directory, preserving every value and its existing update authority |
| Stack direction documents | knowledge | reference for orientation; move learner goals and progress to learning data, task roadmap state to its existing planning owner, and normative rules to their existing Rules owner |

Do not globally replace utility with operation or contract with standard: the counterexamples above demonstrate why that would retain the current error under new names. Existing operation labels also require semantic review; the proposed spelling does not certify their content. No public skill name changes merely because its kind changes.

A mixed entry keeps incidental constraints needed for its task, but references separately owned rules rather than duplicating them. Split only independently consumed responsibilities. For example, a document combining merge authority with queue execution needs the policy in its rule owner and execution in the existing merge/monitor owner, not a new mixed kind. A router, native adapter, helper script, schema, checklist or template is not a separate kind: classify the capability it serves, or keep it as an ordinary supporting asset.

Reference is not a replacement catch-all. It contains descriptive material with a real independent consumer. A proficiency table, progress log, target roadmap or current execution status is maintained data, not another discoverable instruction merely because it is Markdown. The existing learning or task owner and actual user authority determine who can change it. Retain a separate reference entry only when it serves an independent request; otherwise its owning skill reads the supporting data directly. Removing a public entry requires caller migration and retirement in the same cutover. A learning skill can impose incidental teaching constraints without becoming a policy, just as a workflow can impose incidental execution constraints without becoming a policy.

## Distinctions kept independent

| Question | Representation | What it must not decide |
| --- | --- | --- |
| Who owns this capability? | Source repository plus plugin namespace | Kind or permission |
| What subject is it about? | Skill name and useful subject families | Role, applicability or package boundary |
| What responsibility does it supply? | kind, using the six roles above | Folder path, authority or automatic loading |
| When does it apply? | Existing descriptions, profiles, prerequisites and selected scope | A policy is not automatically global; a standard is not automatically selected |
| Is this baseline, house or employer guidance? | Existing provenance and explicit selection | Different kinds or different language architectures |
| Who may act or modify state? | Owning policy and actual user authority | An operation label never authorizes a write or send |
| Is this a rule, operation or maintained fact? | Skill role versus owned data/resource | Not all Markdown becomes a skill |
| Does it retain a goal or return a result? | Workflow versus operation contract | Number of steps or runtime duration |
| Is it native-host-specific? | Native configuration or named host implementation modules | Duplicate shared instructions or another generic kind |
| Is it importable implementation? | Named language package/module | Instruction/resource folders as an improvised library layout |
| Is it an independent distribution? | Explicit consumer/deployment boundary and package metadata | One distribution per skill, namespace or folder |
| Is it authored, generated or installed? | Source map and generation/installation evidence | Multiple competing authored copies |

The four broad groups can be generated in indexes from kind alone. Do not add a second category field, task-specific kind vocabulary or separate classification of the same entry for each host.

Every preset accepts valid skill kinds. Stack/tool/profile presets retain their meaningful required capabilities and applicability rules. The generic plugin preset starts without teaching or profile requirements. A profile still requires a policy, but may ship reference material, standards, learning capabilities, workflows and operations, with maintained data in its subject-specific owned location.

## Python code

Python does not require one application architecture or a runtime layer. Keep the distinction between language/package mechanics and our selected defaults explicit:

| Choice | Status in this proposal |
| --- | --- |
| Modules and qualified package namespaces | Python's normal import model |
| src versus flat layout | Both supported ecosystem layouts; src remains our chosen default for installable code |
| A packages directory | Our convention for package members when separate distribution roots are warranted |
| uv and a shared workspace lockfile | Our selected tooling, appropriate for interconnected members with compatible environments |
| runtime, services or infrastructure folders | Application-specific choices requiring a real responsibility, never a universal Python scaffold |
| py.typed | Include for a library distributing inline type information; not a reason to turn standalone scripts into libraries |

Update existing standards that present our choices as Python requirements. Public projects are evidence of workable options, not authority for our house decisions: Requests and pip also have utils modules, and the inspected projects use different build backends. We retain our responsibility-naming preference and selected toolchain without claiming every Python project follows them.

Python does not prescribe an org_reponame import root. PEP 8 recommends short lowercase module and package names; underscores are permitted in module names for readability and discouraged in package names. PyPA nevertheless explicitly documents prefixed regular packages as a simple alternative to shared namespace packages. Our owner-qualified regular import roots, such as tj_agent_store, remain a deliberate house choice for cross-repository libraries rather than a universal Python requirement. Do not mechanically derive an import root from every repository's organisation and name.

Distinguish the installed distribution (for example, tj-agent-store), its import package (tj_agent_store), subpackages (tj_agent_store.storage) and modules (tj_agent_store.sessions). Multiple modules do not require multiple distributions or a shared namespace package. Subdirectories under a regular package are ordinary subpackages when they contain __init__.py. A shared native namespace such as tj_agents.agent and tj_agents.agent_store is an alternative only when independently installed distributions intentionally contribute to that namespace; omit __init__.py at the shared tj_agents level and verify the selected build backend and installed combination.

Use familiar names where their responsibility fits: tests for tests, scripts for repository commands, cli for command-line handling, and domain names such as sessions or repositories for cohesive implementation. None of cli, api, models, schemas, storage, services or runtime is a mandatory Python layer. Choose a module first when one file suffices; introduce a subpackage when the subject actually needs multiple modules. Keep proposed internal folder names open to discussion until their contents and boundaries have been reviewed. Python:structure owns the root/distribution distinction, python:modules owns internal names and cohesion, and imports/build own cross-repository dependency delivery.

For a single installable Python project, use the existing preferred source layout:

```text
pyproject.toml
uv.lock
src/
  price_check/
    __init__.py
    prices.py
tests/
  test_prices.py
```

For a script/mixed-language repository containing independently consumed Python libraries, or multiple independently packaged libraries, use the existing package-member convention. A folder does not become a separate distribution merely because it contains several modules.

The proposed Agent example has two package members because Agent Store is a separately consumed leaf dependency, while Agent owns session operations and host integrations:

```text
agent/
  pyproject.toml
  uv.lock
  packages/
    tj-agent-store/
      pyproject.toml
      src/tj_agent_store/
        __init__.py
        py.typed
        sessions.py
        repositories.py
        reader.py
      tests/
    tj-agent/
      pyproject.toml
      src/tj_agent/
        __init__.py
        py.typed
        sessions/
        recovery.py
        refresh/
        hosts/
          claude/
          codex/
      tests/
  .agents/
    agent/skills/
    agent-store/skills/
    codex/skills/
    hooks/
    plugins/
    tiers/
```

This is the proposed responsibility map, not a claim that those packages already exist. Agent Store remains the dependency leaf; Agent imports its public API. Host implementations are ordinary modules under `tj_agent.hosts`. Public distribution naming and import roots are collision-checked against actual selected dependencies before implementation; the names shown are the proposed targets.

Current Agent examples map as follows:

| Current authored material | Proposed owner |
| --- | --- |
| `.agents/agent-store/runtime/session_store.py` and `repository_identity.py` | `tj_agent_store.sessions` and `tj_agent_store.repositories` |
| `.agents/agent/runtime/agent_recovery.py` | `tj_agent.recovery` |
| `.agents/agent/runtime/plugin_refresh.py` and related refresh implementation | `tj_agent.refresh` |
| `.codex/runtime/*.py` and `.claude/runtime/*.py` | `tj_agent.hosts.codex` and `tj_agent.hosts.claude` |
| Skill-only command adapter | The owning skill's `scripts/`, importing the delivered package |
| Python library nested in a skill's `runtime/`, such as Personal work items | A package member in its actual owner repository; templates remain with the capability that consumes them |

Use a responsibility name for modules and subpackages. `runtime` can be valid when it identifies an actual execution engine; it is not a standard Python layer or the automatic home for all executable code. The same test applies to `common`, `shared`, `helpers`, `utils`, `services` and `infrastructure`: a generic label does not establish a cohesive responsibility. This is a design test, not a regex ban on words.

Retain standalone scripts when they are genuinely independent and the host invokes them by path. Do not package every tiny script or create a distribution per skill. Once scripts share substantive implementation, put that implementation in its owner's package rather than growing a parallel loose-module framework.

## Host configuration and installed delivery

`.codex/` and `.claude/` keep actual native configuration, hook wiring and discovery output. Python implementation follows its import package even when it targets one host. This explicitly replaces Agent/Core's current requirement to author host-specific Python under host runtime folders.

Generated `plugins/<plugin>/` payloads remain separate from source. Their native skill entry paths remain flat where the host expects them; source grouping does not force a native host path change. Shared prose has one authored home; generators produce all installed and local projections.

Canonical project metadata and native host metadata are different contracts. Keep kind and the other project selection fields in the canonical definition. Generate native discovery entries using only that host's supported keys; project extensions go in supported native metadata rather than being copied as unknown top-level fields. For a Codex projection, the proposed role projection is:

```yaml
---
name: structure
description: Define Python distribution and source-folder layout. Use when creating or reorganising Python projects.
metadata:
  tj-agents-kind: standard
---
```

This is a metadata example, not a complete duplicate skill body. The native entry references its shipped canonical definition and contains only any genuine host invocation differences. Update consumers such as Core's review standards reader to recognise the generated metadata projection. That reader currently admits only top-level convention/contract, so changing canonical labels alone would silently lose selected standards. Validate canonical metadata with Template and generated native entries with the appropriate native validator. The independent design check observed an existing Codex validator rejection of the current custom top-level fields; that is a format-validation gap, not observed proof that current native discovery is broken.

Use Template's existing locked-distribution resource support to bundle Python libraries. Proposed resource destination for Python modules is `python/` within each installed plugin. A hook or skill adapter establishes that plugin-local import root at the entry boundary, then uses normal qualified imports. Preserve existing supported Python-interpreter requirements; bundling a pure Python wheel does not provide an interpreter.

```json
{
  "plugin": "agent",
  "distribution": "tj-agent",
  "destination": "python"
}
```

Declare and bundle each runtime distribution required by the plugin, including Agent Store where Agent consumes it; do not assume bundling the main wheel recursively supplies its dependencies. Template's existing collector requires each bundled distribution to be a direct runtime dependency of the publisher's root pyproject and present in its committed lockfile; workspace membership alone is insufficient. Installed entry points may not search sibling source checkouts or another plugin's installation. Tests exercise the delivered bundle with producer checkouts unavailable. Package data travels through its package or the owning skill's explicit assets.

Core remains a multi-namespace source owner. Its own Python implementation is grouped by actual independently consumed packages using the same rule; this proposal does not mechanically create a distribution for each namespace. Agent is the final authored source owner of Agent Store, consistent with Marketplace's publisher selection. Core consumes its delivered package and retires its hand-maintained Agent Store implementation and stale source-owner declarations through the existing extraction owner's cutover. Generated or provenance-pinned external staging remains delivery evidence, not a second source owner. CLI retains its Rust `src/` tree. Reference-only publishers need no Python package. Marketplace remains a catalog aggregator.

## Source owners and cross-repository scope

| Owner | Changes it owns |
| --- | --- |
| Core | Kind definitions, engineering skill-authoring guidance, source-map discovery, kind-based standards readers/selection and write gates, shared source-layout policy, runtime/package source rules and affected hooks/tests |
| Template | Proposed template:structure, generator/checker/scaffold layout, generic plugin preset, resource mappings, vendored instructions, update operation and tests |
| Skill, published by Template | Native authoring instructions and checks; source discovery and kind decisions |
| Python | structure for project roots and layout claims; modules for cohesion/naming; imports/build for actual package delivery; corresponding scaffolds and cross-references |
| Agent | Agent Store/Agent implementation packaging, host modules, hooks, installed entry points, source instructions and tests |
| CLI | Canonical skill paths, packaging consumers and any Python helpers; retain its Rust layout |
| Personal, Work, Work-items, Learning and other selected publishers | Canonical skill paths, kind review, owned Python implementations, declarations and generated host discovery |
| Other stack/tool/profile repositories | The common skill-source migration and Template refresh; change their language layout only where their own standards and actual code require it |
| Marketplace | Catalog changes only if the migration changes an actual publication/dependency; no ownership move is assumed |
| Docs | This shared design and cross-repository acceptance; implementation details remain with source owners |

Template:structure owns the tj-agents plugin-source layout; template:check runs its structural checks. Python standards do not encode `.agents` paths. Core does not keep a competing general plugin-folder rule: its source map and documentation describe its concrete owners and refer to the shared layout.

Inspect canonical source across non-Python stack repositories as an audit subject without selecting that stack's standards for unrelated code. Preserve genuine repository exceptions, such as authored legacy publisher layouts, until their owner is included in the planned migration. The implementation inventory must enumerate every catalog publisher and every supported entry point; the inspected examples above are not a complete migration inventory.

## Migration and acceptance

### Publisher inventory and delivery order

Freshly fetched Marketplace main is c6df0d81dc95dfb2f6455c3c577c779e7560b1b6 and lists28plugins from16publishers. Other source counts below use each checkout's existing origin/main snapshot, exclude dependencies, native/generated projections and worktrees, and do not claim freshly fetched source heads. Core main owns only Base/Workflow/Engineering/Docs. Cpp's local base scope maps to cpp publication; it does not publish Core's base identity. Machine and Kit are absent from this roster; Codex is published by Agent.

| Repository | Marketplace publications | Authored source skills | Required migration concern |
| --- | --- | --- | --- |
| Core | base, workflow, engineering, docs | 57 | Vocabulary, discovery, standards readers, source maps and hooks |
| Template | template, skill | 6 | Generator/checker/scaffold/update and native authoring |
| Python | python | 16 | Standards, learning data and scaffolding; candidate15skills |
| Agent | agent-store, agent, codex | 15 | Package boundaries, host integrations, installed entry points and store consumers |
| CLI | cli | 3 | Skill paths, shared Python delivery and Rust callers |
| Cpp | cpp, gpp, msvc, win32 | 19 | Map local base scope to cpp publication; kinds and learning data |
| Dotnet | dotnet, efcore | 50 | Publication projections, scaffold consumers and semantic kinds |
| React | react | 24 | Testing authority, construction standards and learning state |
| Rust | rust, tauri, rust-sqlx | 16 | Publication projections, learning state and kinds |
| Azure | azure | 14 | Kinds, learning state and source layout |
| GitHub Actions | github-actions | 15 | Kinds, learning state, workflow callers and layout |
| Nvim | nvim | 3 | Teaching, maintained learner data and orientation |
| Personal | personal | 7 | Work-item implementation and policy/operation/workflow boundaries |
| Work | work | 7 | Draft/send authority and bounded operations |
| Learning | learning | 3 | Learning responsibilities and active callers |
| GitHub | Absent from this roster | 1 | Local publication/selection and delivery ownership |
| Work-items | Absent from this roster | 7 | Existing record ownership and active consumers |
| Marketplace | 28plugins,16publishers | 0 | Catalog publication facts and exact producer dependencies |
| Docs | Shared design owner | 0 | Cross-repository design and acceptance |


Deliver the rules and their consumers together, then migrate publishers against the exact producing candidates. The dependency order is Core/Template contract and discovery reconciliation; Python naming/layout guidance; Agent/CLI/shared-package delivery; then the remaining publisher migrations with their owning rules available. Independent publishers can be separate delivery slices once the producer contract is concrete. Marketplace changes follow actual publication changes, not folder-only moves. Each source move includes its native projections and active callers rather than waiting for a final bulk regeneration.

Remaining inventory work before an implementation-ready verdict: enumerate each candidate's final kind and destination; reconcile stale duplicate source owners; identify every selected local/noncatalog publisher, current producer revision, installed binding and supported platform; assign exact reviewable checkout/branch slices and acceptance commands. The table does not claim these checks are complete.

1. Freeze the complete source/discovery/packaging consumer inventory, reconcile live owners and existing Template structure work, and decide this proposal with Tommy. Resolve actual publication ownership against Marketplace and source maps: a matching path in another repository may be a staged projection rather than another authored owner. Inventory legacy authored publishers as well as .agents-layout repositories. Do not implement around an unresolved design decision.
2. Deliver the owner rules, discovery/generation behavior and their directly affected source moves as coherent replacements. Test each slice against fixtures of its intended new layout. Do not leave a producer whose actual current consumers cannot operate with it.
3. Migrate each publisher's authored skills, manifests, source maps, package resources, tests, caller paths and vendored files in the coordinated rollout. Preserve qualified skill names for path-only moves. Plan cross-repository boundaries against exact candidate producer revisions; remove superseded layouts and active callers rather than adding compatibility aliases or a permanent dual-layout parser.
4. Move shared implementation packages together with their imports, host adapters, dependencies and packaged entry points. Generate both native host projections from their one source. Do not merely move folders while retaining old dynamic import/path machinery.
5. Verify the complete catalog and known installed bindings before calling the rollout complete. A source generation pass alone is insufficient.

Acceptance includes kind-correct mixed-responsibility repositories; source/public-name collision rejection; repeated generation without drift; exact shipped references and resources; no imports from old source paths; focused package and hook tests; Windows/Linux execution of relocated entry points; and fresh Claude/Codex skill discovery plus actual affected entry-point behavior with author checkouts unavailable. Kind-based readers must still load the selected standards and native-authoring gate after the rename; valid generation is not proof those consumers recognise standard instead of convention/contract. Reject retired labels as active kind values after cutover, while allowing ordinary English words and historical evidence. Classification remains a semantic review: a valid kind string does not prove it is the right kind.

The design is agreed and execution is authorised. Template is a qualified producer candidate; the remaining repository slices still need semantic classification, source/caller migration and installed-entry acceptance. Its draft PR and exact validation evidence are recorded above. No producer merge or complete workspace rollout is claimed.

## Proposal verification

An independent read-only design pass checked realistic role classifications, current source owners, Python boundaries and native format validation. This revision resolves its stale-kind wording, makes native metadata projection explicit, names Agent as Agent Store's final authored owner, and records the existing bundler's direct-dependency requirement. The proposed native metadata sample passed Codex's native quick validator in a temporary directory. The host-coverage record passed its plan-stage validator, and all 15 local evidence links resolved. These checks qualify this proposal for user design review; they are not a completed implementation-design or runtime acceptance review.

## Research and observed evidence

Assessment complete for the design choice: preserve the existing generator and distribution-resource mechanism, change their source-layout model, and use ordinary Python packages. Adopting an unrelated monorepo framework or adding another taxonomy would not resolve the demonstrated coupling.

- [PyPA: src layout versus flat layout](https://packaging.python.org/en/latest/discussions/src-layout-vs-flat-layout/): both layouts exist; src isolates importable code from the repository root. It does not prescribe runtime folders or capability architecture.
- [Python tutorial: modules and packages](https://docs.python.org/3/tutorial/modules.html): packages provide hierarchical module namespaces.
- [PEP 8: package and module names](https://peps.python.org/pep-0008/#package-and-module-names): short lowercase names, with distinct guidance on underscores for modules and packages.
- [PyPA: distribution package versus import package](https://packaging.python.org/en/latest/discussions/distribution-package-vs-import-package/): installable distribution names and Python import names are separate concepts and need not match.
- [PyPA: namespace packages](https://packaging.python.org/en/latest/guides/packaging-namespace-packages/): independently distributed contributions to a shared import namespace; prefixed regular packages are a simpler alternative.
- [uv: workspaces](https://docs.astral.sh/uv/concepts/projects/workspaces/): package members share a lockfile; workspace membership is a packaging choice, not a reason to split every module.
- [Requests source](https://github.com/psf/requests/tree/main/src/requests), [Click source](https://github.com/pallets/click/tree/main/src/click), and [pip internal source](https://github.com/pypa/pip/tree/main/src/pip/_internal): examples of named Python packages and responsibility-specific modules/subpackages. These are examples, not one universal architecture.
- [Current Core kind definitions](../../../core/SKILL_KINDS.md), [source-layout contract](../../../core/SOURCE_LAYOUT.md), and [source map](../../../core/.agents/plugins/sources.json).
- [Current Template standard](../../../template/.agents/template/skills/check/standard.json), [checker](../../../template/.agents/template/skills/check/scripts/check.py), [authored generator template](../../../template/.agents/template/skills/new/plugin/templates/repository/.agents/sync_generated.py.in), and [scaffolder](../../../template/.agents/template/skills/new/plugin/scripts/new_plugin.py). At the baseline source snapshot, the utility-only restriction existed in both validation and generated instructions; its contribution to misclassification was an inference, not an observed agent trace. The linked working source now implements the producer correction recorded above.
- [Current Python structure](../../../python/.agents/python/convention/structure/SKILL.md), [modules](../../../python/.agents/python/convention/modules/SKILL.md), [imports](../../../python/.agents/python/convention/imports/SKILL.md), and [build](../../../python/.agents/python/convention/build/SKILL.md), inspected as standards-source audit subjects.
- [Agent source instructions](../../../agent/AGENTS.md) and [resource mappings](../../../agent/.agents/plugins/payloads.json) show the current shared/host runtime split.
- Existing [Template structure goal](../../../template/plans/template-structure/GOAL.md) concerns the shared layout and must be reconciled at implementation admission. The broader [standards composition proposal](../standards-composition/STANDARDS_COMPOSITION_PLAN.md) concerns applicability and remains a separate design; this proposal does not approve or duplicate its selection mechanism.

Local source snapshots inspected: Template `8de27ca70c99e205024a33e197f304608d14c541`; Agent `aa8c71a93de6bb660f863aaecff81c3b99b1ba1a`; Core `ddd0789eda30f9eb68a7c7617e9aef2317b4583c`; Python `20a3bc9cae92e9a7f919c08a0ef1b42d34f22f11`. Local inspection does not prove these are current remote heads or deployed plugin versions.

## Agent host coverage

```agent-host-coverage
{
  "schema_version": 1,
  "shared_source": "template/.agents/template/skills/structure/SKILL.md",
  "hosts": [
    {
      "host": "claude",
      "behavior": "discovers the same public skill identities from generated native entries and executes bundled package entry points",
      "source": "template/.agents/template/skills/new/plugin/templates/repository/.agents/sync_generated.py.in",
      "mapping": "canonical namespace/skills subject paths to Claude discovery and plugins/<plugin>/skills",
      "verification": {
        "level": "planned",
        "result": "pending",
        "evidence": "fresh Claude discovery and affected installed entry-point execution on Windows and Linux"
      }
    },
    {
      "host": "codex",
      "behavior": "discovers the same public skill identities from generated native entries and executes bundled package entry points",
      "source": "template/.agents/template/skills/new/plugin/templates/repository/.agents/sync_generated.py.in",
      "mapping": "canonical namespace/skills subject paths to Codex discovery and declared packaged codex-skills entries",
      "verification": {
        "level": "planned",
        "result": "pending",
        "evidence": "fresh Codex discovery and affected installed entry-point execution on Windows and Linux"
      }
    }
  ]
}
```

### Publisher execution update

GitHub Actions candidate `09aad864fd665a739bd2df42028951216b43ee6d` is pushed at draft PR38:14subject-based skills, separate learner data, direct caller/action/harness migration and exact-pinned Template qualification. Local155tests, workflow variant actionlint/zizmor,119generated-file freshness, Template conformance,14native creator validations and six isolated plugin command checks pass. Native/security review and remote qualification remain open.

CLI candidate `0d029b3d61db1b32519972acc1b2454bb7394849` has approved full native/security source review and recorded host coverage; exact-head qualification40918557896 and Rust CI40918556061 pass. Further approved package implementation is in progress, so that candidate is not the final rollout head.

Agent package implementation is active: independent `tj_agent_store` leaf; `tj_agent` capability packages for sessions/plugins/hosts/installation/lanes; existing `tj_cli` owns deterministic process and terminal primitives. Shared implementation moves out of runtime folders and skill-local loose libraries. Thin actual entry adapters establish the declared package boundary; ordinary modules use qualified imports and declared package resources. Interpreter-floor and copied installed payload checks remain acceptance conditions.

Core current native SessionStart proof passes isolated Windows positive and deliberate failed-hook probes for Codex and Claude, without retired Base preload/acknowledgment. Parent integration identified that the initial test rewrite must preserve the repository unittest CI collection; correction is required before commit/review/CI.

### Next publisher checkouts

Created clean structure branches from fresh remote main without switching occupied checkouts: React3bd62a902fad4b6fde217f753aa1b9f232b75d8c; C++8d4641a9f7d1c48e788453977ab62060eb31222f; Rust307c598dc2af1056ec43b1cdad355390715662c2. Rust scaffold assets/caller paths are moving with their operation. Native skill authoring for these checkouts remains pending.

C++ has a repository-specific generator and route/scaffold resources plus a localbase scope mappedto publishedcpp. It needs an explicit producer/source-map migration; generic Template update cannot replace it blindly. Win32 overview is a reference; Win32 knowledge is learner state. Preserve compiler/API independence and historical signed provenance.

Ownership refinement: Template retains the standardized standalone stdlib pre-import Codex snapshot/bootstrap. Agent owns Codex integration modules and thin native adapters; after verified snapshot selection they establish only that selected declaration’s own Python bundle, refusing missing bundles and outside fallbacks. No duplicate snapshot module or Agent-specific generic producer branch.

Producer qualification caught stale cached local wheels after source-only edits. The named distribution is now reinstalled/refreshed before inspection. A real warm-cache regression verifies changed module bytes, added entry files and removed resource files; the former producer reproduces the failure. Core63f3bcb3 passes complete Windows/Linux CI40941318396 and native/security review. CLI’s final dependency pin waits corrected producer integration and copied-watcher acceptance.
