# Native host duplication inventory

Audit date: October 27, 2026. Status: migration approved by Tommy on October 27, 2026; conditional parity checks remain required before the affected removals.

## Outcome and authority

Remove implementations of behavior the host already provides. Keep one capability name and intent across Claude and Codex. A host with a native implementation receives a thin instruction wrapper; an unmet requirement receives one custom implementation, packaged only for the hosts that need it. Generated distribution copies are not independently authored implementations.

Authority is Tommy's instruction to follow `handoff-native-duplicates.md` from the Agent checkout. That handoff explicitly requires presenting the inventory and proposed deletions before substantial removal. It also says never to close this or any other session. This document is the canonical approved inventory. At the initial checkpoint, no runtime implementation, installation, hook changes, publication or deletion had occurred. Tommy subsequently confirmed the single-wrapper/native-first model and approved D1-D11 within their recorded conditions. His follow-up requires checking both hosts and keeping each host's custom behavior in its separate runtime/adapter so neither host receives an unusable wrapper.

This is a source and documentation audit, not installed acceptance testing. A documented feature and installed CLI help establish availability claims, not that a particular account, private frontend, plugin, permission scope, or OS workflow has been exercised successfully.

## Scope and evidence

All 20 repositories returned by `gh repo list tj-agents --limit 100` were fetched. Each was inspected in a new, initially clean worktree at fetched `origin/main`, under `<repo>.worktrees/Audit-NativeDuplicates-20261027`. Learning had no local clone; its repository was cloned before creating its audit worktree. Existing checkouts and in-flight branches were preserved.

The complete roster of 286 authored skills and their measurements is in `capability-catalog.csv`. `source-snapshot.json` records full frozen SHAs, paths, counts and method. The tables below group related skills and enumerate additional non-skill runtime capabilities. There is no claim that every helper script is an independent user capability.

Measurements are physical lines including blank lines. Generated `plugins/*`, host discovery copies, tests and fixtures are excluded unless explicitly stated. Infonetica's `plugins/infonetica` is authored source and is included. Core's figures include canonical instructions, data and runtime; Agent executable totals exclude instructions/data. CLI production Rust counts exclude trailing inline test modules. Different measurement scopes are labeled. Shared helpers overlap capability rows: do not sum row sizes to estimate deletions.

The audit used three bounded L3 read-only investigators for Agent/CLI, Core, and the other repositories. The parent verified official documentation and installed help. No model session was used as a process-test fixture. No hook was disabled or bypassed.

## Verified native mechanisms

Source identifiers resolve in the source register below. These concise statements are the native facts used by the decision tables.

| ID | Native fact and boundary | Evidence |
| --- | --- | --- |
| N1 | Claude discovers independent reachable sessions with `ListAgents` and sends with `SendMessage`. Windows support is documented from 2.1.234. It also offers a one-shot notice when another local session becomes idle or exits. This is distinct from a child subagent. | A1 |
| N2 | Installed Codex exposes `agents` for the shared daemon and `queue --thread ... --message ...` for an existing UUID/name. Official documentation confirms those commands; `agents` does not support `--no-daemon`. Private frontend delivery and recipient-history proof were not exercised. | O1; L1 |
| N3 | Both hosts have native subagents and native background execution mechanisms. Independent terminal sessions, cross-host aggregation and subagents have different lifecycles. | A2; O2; L1; L2 |
| N4 | Both hosts provide `/goal`. Claude checks the completion condition after turns. Codex documents Goal mode in CLI, IDE and desktop surfaces. Neither grants broader permissions. | A3; O3 |
| N5 | Claude provides `/loop` and scheduling tools, plus independent Desktop/cloud tasks. Codex scheduled tasks exist in supported desktop/web surfaces; its CLI and IDE do not provide the Scheduled management interface. Native CLI goal continuation is available separately. | A4; O4 |
| N6 | Claude provides `--worktree`, `EnterWorktree`, and managed cleanup; Codex has native worktrees and installed CLI `--worktree`. These do not establish equivalence to arbitrary externally owned worktree retirement or exact merged-head eligibility. | A5; O5; L1; L2 |
| N7 | Claude bundles `/code-review` and `/security-review`; the latter targets the branch diff against origin's default. Codex has `review --base`, `--commit`, and `--uncommitted`. Codex Security also has a first-party change-review plugin and a cloud PR service, with separate prerequisites. | A6; A7; O6; O7; L1 |
| N8 | Both hosts load skills/plugins and manage marketplaces natively. Installed Codex has marketplace add/list/upgrade/remove and plugin add/list/remove; Claude has native plugin/marketplace management and update. | A8; O8; L1; L2 |
| N9 | Codex officially controls memories through `features.memories` and `memories.*`; its reference does not document `autoMemoryEnabled` or `.codex/settings.local.json`. Installed `features list` reports memories false, hooks/goals/multi_agent/plugins true. | O9; L3 |
| N10 | Both hosts provide native hook event execution and permission controls. Native hook support executes custom policies; it does not implement the house invariant carried by every hook. No blanket hook-deletion inference follows. | A9; O10 |
| N11 | Native resume/history surfaces are present: Claude `--resume`, `--continue`, `/resume`; Codex `resume`, `fork`, `agents`. Machine-readable cross-host regex search and house execution ownership are not established by those facts. | A6; L1; L2 |
| N12 | Claude `/copy` copies an assistant response. No equivalent for arbitrary-file UTF-8 plus HTML/plain clipboard flavors and verified OS readback was established in the reviewed native surfaces. | A6; local CLI source |

Installed versions observed: Claude Code `2.1.282`; Codex CLI `0.163.0-alpha.1`. Help inspection was read-only. Help and official docs differ in some details: the installed `codex resume --help` lists `--worktree`, while O1 says resume does not accept it. No deletion depends on that disputed combination.

## Capability table: Agent, Agent Store and CLI

Paths are repository-relative. `WRAP` means thin native wrapper for the overlapping behavior. `DELETE` means retire superseded implementation after caller migration. `KEEP` means a requirement remains outside established native equivalence; keep one shared implementation, or one Codex-only implementation where explicitly indicated. `CONDITIONAL` names evidence required before deletion. These are approved migration directions, not completed migration; conditional rows retain their proof requirements before deletion.

| ID / capability | Where it lives: repo, path, measured size | Claude native equivalent | Codex native equivalent | Decision |
| --- | --- | --- | --- | --- |
| A01 message | agent `.agents/agent/utility/message/scripts/codex_followup.py`, 355 code lines; skill 84 | N1 | N2 | WRAP on both. Retire custom send/steer transport when required recipient types are proved reachable. Keep no Claude message reimplementation. Any private Codex exception must be demonstrated and packaged Codex-only; native queue does not by itself prove receipt. |
| A02 peer listing/inspection | agent `.agents/agent/utility/peer/scripts/peer_cli.py`, 133; peer script family 10 files/2,626 shared lines; skill 128 | N1, native agent view | N2 | WRAP same-host list/inspect. KEEP only separately required cross-host aggregation, exact OS identities and focus/close behavior. |
| A03 listen | agent `.agents/agent/utility/listen/SKILL.md`, 46; host adapters one line each, zero runtime | N3; native completion notices | N3 | Already WRAP. No custom listener daemon to remove. Trim stale instructions only. |
| A04 handoff/independent launch | agent `.agents/agent/utility/handoff/scripts/handoff.py` 58, `.agents/agent/resources/handoff/launch_claude.py` 162, `.agents/agent/resources/handoff/launch_codex.py` 163; 383 total | Native CLI/background launch | Native CLI/exec launch | WRAP native launch; KEEP only required checkout/lane/identity/pickup contract. Do not substitute a child agent for a requested independent session. |
| A05 open | agent `.agents/agent/runtime/agent_recovery.py`, 903 shared; skill 49 | N11 | N11 | WRAP resume. KEEP cross-host exact resolution, observed-live focus and duplicate-writer refusal until replaced. |
| A06 recent | agent `.agents/agent/runtime/history.py`, 180 shared; skill 39 | N11 | N11 | WRAP ordinary recent listing. Decide separately whether cross-host/tool-input worktree filters remain required. |
| A07 search | agent same history 180; host session parsers `.claude/runtime/sessions.py` 307 + `.codex/runtime/sessions.py` 300 + `.agents/agent/runtime/transcripts.py` 34 shared; skill 32 | Native history search, N11 | Native session picker, N11 | CONDITIONAL: native basic search; KEEP one cross-host/regex/worktree-tool search if required. Parser modules have other callers and are not wholesale deletion targets. |
| A08 recover/work-item sessions | agent `.agents/agent/runtime/agent_recovery.py` 903 + `.agents/agent/runtime/work_item_sessions.py` 788 + `.agents/agent/utility/recover/scripts/work_item_sessions.py` 33; 1,724 shared lines | Native resume | Native resume | WRAP host resume; KEEP application execution-key/owner/provider-reference recovery until requirements change. |
| A09 current Agent close | agent `.agents/agent/utility/close/scripts/agent_close.py` 231, `.agents/agent/runtime/close_lifecycle.py` 108, `.agents/agent/utility/peer/scripts/client_close_watcher.py` 130; 469 | `/exit`/background stop cover narrower cases | Session/subagent close/archive cover narrower cases | KEEP one completion/identity bridge: final-turn binding, new-prompt cancellation, exact frontend, stable idle. No equivalent proved for automatic exact external frontend closure. Never invoke during this task. |
| A10 legacy close flow | agent `.agents/agent/utility/peer/scripts/close.py` 111 + `.agents/agent/utility/peer/scripts/finish_reaper.py` 119 | Native exit/stop; N3 | Native session control | DELETE candidate: 230 lines, after public/historical entry-point and caller proof. Shared `session_close.py` remains live. |
| A11 terminal focus/close adapter | agent `.agents/agent/utility/peer/scripts/close_tab.py` 607 + `.agents/agent/utility/peer/scripts/windows_terminal_uia.ps1` 59 | Native agent view/attach for native sessions | Native agent command center for native sessions | Consolidate with CLI terminal capability; CONDITIONAL deletion of 666 lines. Recovery focus and startup Windows inventory still call it; migrate those first. |
| A12 refresh-plugins | agent `.agents/agent/utility/refresh-plugins/scripts/refresh_plugins.py` wrapper 18; refresh/install cluster 14 files/4,376 shared lines; relaunch 2/357; skill 43 | N8 | N8 | WRAP native update/reload. Review publisher-head comparison, trust/readiness, cross-host convergence and same-conversation relaunch independently; not all 4,376 lines are redundant. |
| A13 plugins/selection | agent `.agents/agent/utility/plugins/scripts`, 9 Python/1,943 + 237 JSON; skill 134 | N8 | N8 | WRAP native install/list/remove. KEEP house roster, dependency closure, explicit profile selection and host projections only. Do not rebuild native marketplace managers. |
| A14 install/shell delivery | agent `.agents/agent/runtime/install.py` 1,015; root installers 5; shell 10 files/1,582 | Native host installer/update/doctor; N8 | Native update/doctor; N8 | Separate OS shell/runtime installation from native host/plugin installation. KEEP required OS/house setup, replace duplicated host management with N8 calls. No install was run. |
| A15 lanes | agent `.agents/agent/policy/lanes/SKILL.md` 166, resolver 112, tables 141 JSON, prompt bodies 14 | Native model/effort/subagent selection | Native model/effort/subagent selection | KEEP house pricing/capability policy and one data mapping. WRAP native execution; no second dispatcher for native subagents. |
| A16 Agent Store/inspect | agent `.agents/agent-store/runtime/{session_store,repository_identity,reader}.py` + `.agents/agent-store/utility/inspect/scripts/inspect.py`; 4/1,068 | Native sessions/history | Native daemon sessions/history | KEEP execution ownership/provider/branch/head/predecessor schema. Replace redundant host observations where possible. A native session list is not this application model. |
| A17 session registration/lifecycle hooks | agent `.claude/hooks/agent.json`, `.codex/hooks/agent.json`; register/startup and peer identity runtime | N10 | N10 | KEEP minimal unmet house observations; delete a binding only with duplicate/caller proof. No current Machine duplicate registration found. Full event table below. |
| A18 Codex memory utility | agent `.agents/codex/utility/memory/scripts/memory.py` 51; skill 21 | Native memory settings, different host | N9 | DELETE wrong JSON-setting implementation; replace with thin native-memory guidance/config control. Do not carry its default-true claim forward. |
| A19 Codex hook-control utility | agent `.agents/codex/utility/hooks/scripts/hook_control.py` 469; skill 37 | Native hook settings, A9 | Native `features.hooks`, O10 | WRAP native setting control; decide whether previous-value snapshot/guarded restore remains needed. This audit never disables hooks. |
| A20 Agent shell history picker | agent `shell/cr.ps1` 1,102 + `shell/agents.ps1` 41 | N11 | N11 | DELETE superseded parsing/index/picker after mapping to native resume and CLI `cr`. One implementation if cross-host picker remains required. |
| A21 folder picker | agent `shell/fuzzy.ps1` 103; cli `src/f.rs` 183 production | No established agent-native equivalent | No established agent-native equivalent | DELETE Agent duplicate after profile migration to existing CLI implementation; preserve required `fp` target explicitly. This is intra-suite duplication. |
| A22 other shell tools | agent `shell/worktrees.ps1` 114, `shell/procs.ps1` 102, Docker 19, env 9, profile 8, hidden Bash C75/profile9 | Native worktrees only overlap a subset | Same | KEEP OS utilities outside native-duplicate scope; ownership move to CLI is a separate decision. Do not bundle unrelated tool removals into this sweep. |
| C01 close | cli `.agents/cli/utility/close/scripts/{close,process_identity,terminal,windows_console_probe}.py`, UIA PS; 5/769 | Native exit/stop narrower | Native close/archive narrower | KEEP deterministic exact supplied process/terminal identity operation until an equivalent exists. Distinct from Agent's completion decision. |
| C02 closeout | cli `.agents/cli/utility/closeout/scripts/closeout.py`, 235 | Native managed worktree cleanup, N6 | Native managed worktree cleanup, N6 | KEEP external fresh merged/pushed/head/ownership eligibility plus exact close. Native managed cleanup does not prove parity. |
| C03 clip | cli `.agents/cli/utility/clip/scripts/copy_draft.py`, 668; skill 94 | N12 | No established arbitrary-file/flavor/readback tool | KEEP one shared OS utility for exact file/HTML/plain/readback behavior. Use native response copy when that alone is requested. No Agent clip implementation exists on current main. |
| C04 cross-host history CLI | cli `src/cr`, 6 production files/1,414; `mod.rs` 427, index 220, parse 342, render 205, scope 137, text 83 | N11 | N11 | WRAP native resume; retain one cross-host picker/search only if desired. This is the existing destination for A20, not a new implementation. |
| C05 CLI installation/shell wrapper | cli Linux installer 141, Windows 120, shell functions 24, `src/init.rs` 35 | No native installer for custom tj CLI | Same | KEEP custom binary setup, with no duplicate Agent definitions of `f`/`cr` after migration. |

Agent measured executable source: 82 files/20,498 lines. CLI: 23 files/3,736 production lines, or 3,902 including inline Rust tests. These are inventory sizes, not projected deletion totals.

## Capability table: Core

Core currently authors Base, Workflow and Engineering. Its five canonical capability/runtime trees contain 137 files/24,200 lines: Base 9/309; Workflow 13/1,518; Engineering 60/7,889; hooks 14/6,000; workflows runtime 41/8,484. All 62 skills are covered below and in the CSV.

| ID / capability | Where it lives: repo, path, measured size | Claude native equivalent | Codex native equivalent | Decision |
| --- | --- | --- | --- | --- |
| K01 goal/plan/status/resume/handoff | core `.agents/workflow`, 7 skills/566; status script 303, transfer script 335 | Native `/plan`, N4, N11 | Native planning, N4, N11 | WRAP host planning/goal/continuation. KEEP canonical artifact, selected-tracker status, execution ownership and explicit transfer proof only. A prompt-only request does not launch a session. |
| K02 external continuation scheduler | core `.agents/workflows/continuation_scheduler.py` 568 + Engineering persistent-workflow `delivery_continuation.py` 359 | N5 | N5: CLI Scheduled management absent | Remove Claude external scheduler transport after native acceptance. KEEP at most one Codex-only implementation if durable CLI scheduling remains required; otherwise select native supported surface and delete it too. 927 lines are a conditional transport boundary. |
| K03 goal owner and continuation state | core `.agents/workflows/continuation_runtime.py` 655; delivery runtime 581, completion 310 shared | N4 | N4 | WRAP goal continuation; separate genuinely additional delivery authority/owner/lease/budget checks. Do not retain a second generic goal engine. Metadata says in-chat scheduling while implementation launches new headless sessions: correct this mismatch. |
| K04 native roles/subagents | core `.agents/workflows/host_runtime.py` 719; roles 5/46; Codex installer 397; host JSON declarations | N3 | N3 | WRAP native role dispatch. KEEP role policy/lease/result checks only. Installer deletion CONDITIONAL on native package role discovery/model/permission parity; current docs do not prove the package claim. |
| K05 worktree create/inventory/prune | core Engineering `operation/open-worktree`, utilities `worktree`, `prune-worktrees`, `unmerged`; 4 skills/473 | N6 | N6 | WRAP create/use. KEEP only required external cleanup/owner safety. `worktree` is already 27-line delegation; do not invent another engine. |
| K06 git commit/push/pull/sync/stack | core Engineering operations/utilities/policies, 12 skills/922 | Native tools execute git | Native tools execute git | Thin command guidance plus house staging/branch/stack/verification policy. DELETE redundant convenience selectors `commit-push`, `pull-main`, `sync`, `sync-all` only after callers migrate; native shell execution does not replace policy judgments. |
| K07 review selectors and evidence | core Engineering review family, 7 skills/778; review rules 184; workflow review evidence 154 | N7 | N7 | Already WRAP native reviewer. KEEP selected-standard hashes/frozen candidate/coverage/delivery receipts; simplify duplicate entry selectors separately. Correct blanket claim that Codex lacks native security review; availability remains conditional. |
| K08 PR/merge/delivery lifecycle | core Engineering 9 skills/1,614; cleanup proof+sweep 886 shared | Native git/forge tools; native review | Same | KEEP house publication authority, exact review/check evidence and safe external cleanup. WRAP forge/Git primitives. No new custom native reviewer or plugin manager. |
| K09 implementation/repair | core Engineering 8 skills/669 | Native editing/debug/review | Same | KEEP selected lifecycle/issue provenance policy; native host performs code work. No duplicate general coding engine found. |
| K10 docs/guide/plan/routing/auth conventions | core 10 remaining Engineering skills/1,258; Base 5/158 | Native skills/instructions/permission rules | Same | KEEP house standards and domain artifacts; compare repeated context emission separately. Protected routing and credential work excluded. |
| K11 generic workflow runtime | core `.agents/workflows/workflow_runtime.py` 1,047; `workflow_ops.py` 2,422 | Native agents/review/goal primitives | Same | CONDITIONAL surgical reduction of orchestration. Repository state, review bundle/preflight/records and delivery checks are separate from native dispatch. No blanket deletion of 3,469 lines. |
| K12 context emitters | core Base/Workflow/Engineering session scripts, 6/263 | Native scoped instructions/skills | Native AGENTS/skills | CONDITIONAL deletion/consolidation when equivalent selected instructions actually load. Workflow prompt handler emits only a close reminder; native goal alone does not deliver that house policy. |
| K13 hooks and loader | core `.agents/hooks`, authored host manifests/adapters; dispatch 332, runtime 392; delivery gate 478, credential gate 196 | N10 | N10 | Keep required custom invariants; remove native-equivalent mechanics only after proof. Never remove hooks merely because native hooks exist. Routing/auth hold applies. |

Source details: review already selects native assessment in `.agents/engineering/utility/review/SKILL.md:59` and both authored host adapters. Continuation's `continuation_runtime.py:195-218,374-432` starts `codex exec`/`claude -p`; line 397 explicitly rejects a same-chat claim. `hosts/codex.json:68` labels it in-chat scheduled work. Review rule loading imports `tier_gate.py`, so review cleanup must not accidentally change protected tier behavior.

## Capability table: other repositories

No native implementation claim below is inferred from a host's general ability to generate code. A prescribed scaffold, tracker schema, publisher projection or employer policy is additional behavior. N8 proves native loading, not a native implementation of those domain rules.

| ID / capability | Where it lives: repo, path, measured size | Claude native equivalent | Codex native equivalent | Decision |
| --- | --- | --- | --- | --- |
| R01 skill creation | template `.agents/template/utility/new/skill`, 1/82 | Discovered native Skill Creator | Native skill-creator | Already WRAP; keep ownership/layout brief and checks. No second authoring engine found. |
| R02 plugin creation/check/update | template `utility/check` 5/1,554; `new/plugin` 34/2,644; `update` 2/140 | N8 | N8 | KEEP cross-host publisher/generator/validation contract; WRAP native admission. Loader comparison is conditional; route removal excluded under #44. |
| R03 hook snapshot loader templates | template `new/plugin/templates/repository/.codex/hooks/{bootstrap,snapshot}.py.in`, 17+111 | Native plugin loading/hooks | N8, N10 | CONDITIONAL removal only after proving native package-relative execution/trust/integrity meets required behavior. Ten vendored copies are generated delivery, not ten source implementations. |
| R04 marketplace projection | marketplace `generate.py` 135 + `plugins.json` 32 | N8 | N8 | KEEP one roster projected into native formats; no custom marketplace manager found. |
| R05 employer worktree | infonetica authored `plugins/infonetica/skills/worktree/SKILL.md`, 189 | N6 | N6 | WRAP native worktree operation; remove inline duplicate create/list/remove and unsafe machine-local junction/settings assumptions after mapping employer naming/layout. Preserve employer policy. |
| R06 employer tracker/team policy | infonetica 22 skills/1,431; create-work-item 11/2,030, work-item 2/79, address 21, visibility 2/92 | Connected external tools, not prescribed schema | Same | KEEP employer schema/state/receipt/visibility rules; no equivalent host implementation established. |
| R07 employer hooks | infonetica `plugins/infonetica/hooks`, 4/243: context 67, origin gate 133 plus manifests | N10; native instructions/scoped permissions | Same, without equal existing gate binding | CONDITIONAL instruction-delivery simplification; preserve employer selection/origin boundary. Claude Skill PreToolUse differs from Codex SessionStart. |
| R08 Personal rule delivery | personal `.agents/personal/utility/use`, 2/300; rule context 34 + scope 37 | Native CLAUDE import/instructions | Native AGENTS | DELETE redundant SessionStart emission after fresh-host adoption proves the existing native rule block loads; retain scoped adoption/projection. |
| R09 Personal invariants/auth/tracker | personal rules 6/553, bot identity 3/987, create 2/60, work-item 16/1,689, address 2/81 | Native permissions/auth/external tools cover portions | Same | KEEP custom schema/receipt/identity and clean-cut invariant until actual parity. `clean_cut.py` 357 inspects removed skill references in commits; not generic permission duplication. |
| R10 external tracker management | work-items `.agents/work-items/utility/manage` 18/2,841; write 7/230 | Connected tracker tools | Same | KEEP one provider/schema/receipt abstraction; no native prescribed GitHub/Azure tracker implementation established. |
| R11 GitHub collaboration | github `.agents/github/utility/collaboration`, 2/650; script 553 | Native/connected forge tools | Same | CONDITIONAL simplification only after expected-head/actor, anchor validation, marker and uncertain-write reconciliation parity. No verified replacement identified. |
| R12 work communication/rendering | work ask 4/123, respond 30, draft 2/154, Confluence 2/178 | Native connected collaboration tools | Same | KEEP communication policy and extra pending-review/Mermaid shape checks; avoid reimplementing external transport already supplied by gh/connectors. |
| R13 C++ profile context | cpp `.agents/hooks/session_context.py`, 113; 19 skills/2,155 skill lines | Native instructions/skills | Same | CONDITIONAL context replacement; do not fold #56 routing work into this audit. Domain scaffolds/toolchains/attestation remain. |
| R14 C++ scaffolds/toolchains | cpp gpp 13/382, msvc 12/402, win32 8/266, shared templates 10/99, attester 287 | No prescribed scaffold/attester equivalent established | Same | KEEP domain code/policy. Source inspection does not apply C++ teaching standards to the docs audit. |
| R15 .NET scaffolds/debug | dotnet 51 skills/4,339 skill lines; scaffold 147/4,435; debug 4/127; skill-routes 2/317 | Native shell/debug tools, not prescribed harness | Same | KEEP component scaffold and repository-harness discovery. Routing work #85 excluded. |
| R16 Azure scaffold | azure 14 skills/707; scaffold 64/4,351, script 2,624 | No prescribed infrastructure generator established | Same | KEEP domain scaffolding/standards. |
| R17 GitHub Actions | github-actions scaffold 10/1,509; machine-events 4/195 + action21; merge-policy 3/394 + action23 | No house workflow/policy service established | Same | KEEP workflow generation, publication hints and GitHub ruleset checks. |
| R18 Python/Rust scaffolds | python 14 skills/811, scaffold 11/263; rust 16 skills/693, scaffold 13/257 | No prescribed scaffold equivalent established | Same | KEEP language/project scaffolds and standards. Rust #17 routing work excluded. |
| R19 React/Nvim standards | react 24 skills/1,523; inert scaffold skill27; nvim 3/131 | Native skills loading | N8 | KEEP domain guidance. React unfinished scaffold is separate debt, not native duplication; #32 excluded. No host runtime/hook implementation found. |
| R20 Learning guide/teaching | learning 3 skills/138; guide-build 2/161, builder133 | No prescribed guide builder established | Same | KEEP teaching/progress and local guide generator. |
| R21 shared documentation | docs no authored skills/runtime/hooks | Native Markdown/files | Same | KEEP shared cross-repository design. No native duplicate implementation found. |

## Every authored behavior-hook family

Native hooks are the execution interface (N10). Their presence does not make a custom policy native. This table distinguishes current bindings from remembered historical bindings.

| Owner/source | Claude events | Codex events | Responsibility and decision |
| --- | --- | --- | --- |
| agent `.claude/hooks/agent.json`, `.codex/hooks/agent.json` | SessionStart register + orphan notice; UserPromptSubmit Store prompt + close prompt; Stop Store stop + close stop; SessionEnd Store end | Same first three events; no SessionEnd binding | One current lifecycle registration family. `register_session.py:426-443` starts/attaches Store in-process; no second direct Store SessionStart binding. Review observations per A17; preserve exact close behavior. |
| agent-store and codex package manifests | None | None | No duplicate registration found in these packages. |
| core Base manifests | SessionStart dispatcher; PreToolUse routing | Same with Codex adapter | Protected routing/context work. No Stop/SessionEnd. |
| core Workflow manifests | SessionStart context; UserPromptSubmit context | Same | Prompt hook only emits close reminder. No close process launched by this hook. Context simplification conditional. |
| core Engineering manifests | SessionStart; combined credential/delivery PreToolUse dispatcher | SessionStart; two credential/delivery PreToolUse adapters | Preserve publication/credential invariants; coordinate with auth work. No Stop/SessionEnd. |
| personal rule manifests | SessionStart; shell PreToolUse clean-cut | Same | SessionStart duplicate native rule delivery candidate; custom clean-cut invariant retained. |
| infonetica authored payload | Origin-filtered SessionStart; Skill PreToolUse origin gate | Origin-filtered SessionStart | Employer scope policy; not equivalent host bindings. |
| cpp manifests | SessionStart context | SessionStart context | Scoped profile context; native instruction replacement needs acceptance. |
| Template Codex loader templates | Not applicable | Bootstrap/snapshot loader infrastructure | Single authored template, vendored to template/work/azure/github-actions/nvim/python/personal/dotnet/react/rust. Not ten independent policy hooks. |

No additional authored behavior-hook family was found in cli, docs, marketplace, work-items, github, learning, azure, github-actions, nvim, python, dotnet, react or rust. Loader copies and generated payloads are accounted for above.

The handoff's claim that current Core Machine and Agent both register `session_store`/`close_lifecycle` is stale: the frozen Core main has no Machine package or such registration. Do not resurrect cached historical code as a deletion target.

## Proposed removals and packaging boundaries

Tommy approved the concrete groups below on October 27, 2026, subject to the stated conditions. Numbers are measured source boundaries, not a promised final diff. Caller migration, both host entries, manifests, payload inclusion, permissions, tests and installed bindings belong to the same cutover.

| Group | Proposed change after approval | Evidence / stop condition |
| --- | --- | --- |
| D1 Native message/session interface | Make one message/peer intent on both hosts delegate to N1/N2. Remove redundant send/list plumbing for demonstrated recipient types. | Do not delete private Codex delivery or required receipt proof on an assumption. Prove reachability with a controlled authorized fixture/session only at implementation time. |
| D2 Duplicate shell implementation | Remove Agent `cr.ps1` 1,102 + `agents.ps1` 41 + `fuzzy.ps1` 103 after profile/caller migration to native/CLI behavior. | 1,246 lines of superseded implementation; compare supported filters/picker/`fp` behavior first. Preserve one chosen CLI implementation where native behavior is insufficient. |
| D3 Legacy Agent close | Retire peer `close.py` + `finish_reaper.py`, 230 lines, after entry-point/caller confirmation. | Do not delete shared `session_close.py`, live watcher or detached-launch helpers merely by proximity. Never execute closure in this task. |
| D4 Terminal API duplicate | Consolidate Agent 666-line close-tab/UIA family into one CLI-owned terminal capability if focus/inventory callers can use it. | Unresolved focus/inventory contract prevents immediate deletion. No second replacement engine. |
| D5 Wrong Codex memory setting | Delete 51-line JSON writer; native-memory thin wrapper uses O9 semantics. | No writing settings in this audit. Fresh effective-config verification required later. |
| D6 Native goal and scheduling | Replace generic goal continuation on both hosts with N4; replace Claude external scheduling with N5. | 927-line scheduler/adapter boundary is conditional. Retain Codex-only durable CLI scheduling only if that unsupported-native-interface requirement is still required. Separate 655-line owner runtime before deleting. |
| D7 Duplicate convenience selection | Consolidate Core `worktree`, `commit-push`, `pull-main`, `sync`, `sync-all`: five skills/245 canonical lines plus host entries. | Preserve useful staging/ownership/verification rules in their existing owners. This removes duplicate selectors, not native Git safety policy. |
| D8 Native plugin management | Reduce refresh/install/selection transport to N8, leaving explicit house roster/projection/trust policy with one owner. | No wholesale removal of 4,376-line refresh cluster; many callers share it. Installer/profile-role code requires native discovery proof. |
| D9 Repeated instruction delivery | Remove Personal repeated SessionStart body where existing AGENTS/CLAUDE delivery is verified; examine Core context emitters and cpp context separately. | No selected-standard loading regression. Excluded routing work remains with existing owners. |
| D10 Employer worktree wrapper | Replace Infonetica's 189-line inline worktree procedure with native operation plus employer naming/layout policy. | No copying machine-local `.Codex` settings or guidance junctions into a fresh checkout. Verify employer-compatible native path or keep the necessary policy wrapper. |
| D11 Native review facts | Keep existing native reviewer wrapper and house delivery evidence; correct outdated capability claims and redundant selectors. | No independent new review engine; security plugin/service availability is checked, not assumed. |

These groups deliberately retain custom behavior for which neither host has an established equivalent. That is not a fourth native replacement strategy: it is the boundary of the native-duplicate scope. A capability lacking on both hosts has one shared implementation, not two implementations.

## Remaining potentially Codex-only custom pieces

| Piece | Why it could remain | What removes the exception |
| --- | --- | --- |
| Durable scheduling from CLI | O4 explicitly directs CLI users to desktop/web for Scheduled management. A requirement to survive the original session using only CLI has no verified native equivalent. | Tommy chooses native desktop/web scheduling for that use case, or a supported native CLI scheduler is verified. No Claude scheduler backend remains after migration. |
| Private independent-session message transport | `codex agents` excludes no-daemon sessions; installed help alone does not prove native queue reaches every currently supported private frontend or supplies recipient receipt semantics. | Demonstrated native delivery to each required frontend/profile. This is a conditional gap, not proof custom transport is still necessary. |
| Hook previous-value restore convenience | Native feature flags exist, while restoring one exact prior global/project value is additional behavior. | Retire that convenience or show native equivalent. Never use it to bypass gates. |
| Packaged role/profile installation | Core claims native plugin-role loading unavailable and ships a 397-line profile installer. Official subagent configuration proves native roles, not this packaging path. | Fresh native plugin role discovery and model/effort/permission inheritance acceptance. Retain no duplicated dispatcher. |
| Loader snapshot integrity/trust bridge | Existing loader binds packaged hook code to a verified snapshot; plain native hook execution is not proof of identical integrity semantics. | Source and fresh-host proof that native package paths/trust supply the required invariant; then remove Template source and regenerate copies once. |

Exact frontend/terminal closure, clipboard, execution ownership, tracker records, domain scaffolds and employer policy are shared custom requirements, not Codex-only native deficits. Their native overlap is split explicitly above.

## Coordination and protected work

All seven handoff PRs were read from GitHub on the audit date and were OPEN. Their files/branches were not changed. Provider URLs are recorded in `source-snapshot.json`.

| Repo/PR | Observed branch/head | Current subject / coordination |
| --- | --- | --- |
| core #512 | `Fix/TierGateUntrackedScan` / `2c0fd994bd5e54f62f44fe08b3b94f5968d43ce1` | Cached bounded untracked scan; the handoff's description as routing removal is inaccurate for this PR. Preserve its ownership. |
| cpp #56 | `Refactor/RemoveSkillRoutes` / `49ddea35352cf81654ac5d4a1f85a10949327263` | Route removal owner; excluded. |
| dotnet #85 | `Refactor/RemoveSkillRoutes` / `19b8aab572fb87654ae39336e992aaf3f272f21d` | Route removal owner; excluded. |
| template #44 | `Refactor/RemoveSkillRoutes` / `f7f4dcf6e36bee51600398f65ae7d7eb702c49f8` | Route removal owner; excluded. |
| react #32 | `Refactor/RemoveSkillRoutes` / `40cce7d9e63755a1e30893618a85627657384103` | Route removal owner; excluded. |
| rust #17 | `Refactor/RemoveSkillRoutes` / `0d87f09b12ec2458c22f3f791831cc9027fccb21` | Route removal owner; excluded. |
| agent #22 | `Fix/NativeAuthDenyRules` / `48b94c1bcfd5488241d580169ce6f575390976d4` | Native credential-widening deny rules; exclude runtime/auth files and coordinate overlapping packaging. |

Coordination so far is read-only reconciliation, not a sent message or an agreement with another owner. No external messages were authorized or sent. Before an approved overlapping slice, re-read the PR state and integrate its landed result or resolve the dependency with its existing owner.

## Assessment and execution readiness

The initial solution assessment is complete for this inventory: use current native host mechanisms wherever equivalence is established; reuse existing CLI capabilities for remaining OS behavior; keep one minimal shared policy/data implementation for additional house requirements. A fork, third-party scheduler, new generic dispatcher or second marketplace manager is unnecessary. Native claims were checked against primary docs and installed help. Additional behavior and interface limitations are explicit, not treated as native absence proven by a search.

Authority: implement D1-D11 repo by repo, with one PR per affected repository and the existing parity/caller conditions. The inventory approval gate is satisfied. Conditional groups are not automatically implementation-ready; resolve their named interfaces before removal. L3 investigation is complete; specified approved removals can use L4/L5, with fresh L3 judgment only for the named unresolved parity contracts. No model switch is claimed by naming a lane.

Suggested repo sequence after approval, one PR per affected repo: Agent/CLI caller map first; CLI consolidation if needed before Agent removes callers; Agent native wrappers and duplicate removal; Core native goal/scheduler/convenience migration; Personal repeated delivery; Infonetica worktree simplification; Template loader change only if its parity condition is met, then consumer refreshes coordinated with protected route work. Keep each repository's atomic caller/tests/manifest cutover together. Rebase each implementation worktree onto newly fetched origin/main before edits rather than reusing this dated audit base blindly.

Before authoring skill consolidation/rename, re-enter Template's resolved authoring brief and the host-native creator; before runtime edits, load the owning Engineering lifecycle and target repository instructions. The current audit loaded `template:new-skill` and `engineering:skill-authoring` to assess the proposal, but did not author a skill. Per-repo standards selection and precise code snippets remain owner-slice work after approval; this inventory does not invent those details.

PRs must include Why and What, use the host's own attribution, contain no new code comments, and carry required generated changes according to that repository. Core's generated payload exclusion differs from Template-layout publishers; do not use one blanket staging rule. No implementation PR exists yet.

Acceptance: one intent/name on both hosts; native-backed host has no reimplementation/runtime behind its wrapper; custom unmet behavior has one owner and ships only where needed; all known callers and installed registrations migrate; excluded work remains untouched; generator checks and target suites pass; fresh Claude/Codex discovery and Windows/Linux supported entry points are exercised. A limited host/platform acceptance must be reported with its resolver, never called passed.

## Verification and delivery state

Completed: all 20 fetched bases and clean initial worktrees; 20-repository capability/hook/source audit; official native documentation reads; installed help/version/features reads; seven protected PR state reads; catalogue and frozen-source evidence; planning host-coverage validation and document consistency checks are recorded in the progress file.

No runtime code changed, so runtime suites were not run for the inventory. No generated skill/payload source changed, so generation was not run against all 20 unchanged repositories. Neither observation is a claim that implementation tests pass. Implementation must run Agent's unittest and generated checks; CLI fmt/clippy/test; Core checks and focused runtime suites; each changed publisher's generator/check and documented suite; installed acceptance on supported hosts/platforms.

```agent-host-coverage
{
  "schema_version": 1,
  "shared_source": ".agents/plugins/payloads.json",
  "hosts": [
    {
      "host": "claude",
      "behavior": "native wrappers for verified host capabilities; one custom implementation only for additional unmet behavior",
      "source": ".claude/hooks/agent.json",
      "mapping": "Agent and owner-specific host adapters and payload inclusion reviewed by capability in this inventory",
      "verification": {
        "level": "planned",
        "result": "pending",
        "evidence": "Frozen source audit and official documentation only; fresh installed acceptance follows approval"
      }
    },
    {
      "host": "codex",
      "behavior": "native wrappers for verified host capabilities; custom host-specific exceptions require demonstrated native interface gaps",
      "source": ".codex/hooks/agent.json",
      "mapping": "Agent and owner-specific host adapters and payload inclusion reviewed by capability in this inventory",
      "verification": {
        "level": "planned",
        "result": "pending",
        "evidence": "Frozen source audit plus installed CLI help/features; no live recipient, scheduler, or installation probe"
      }
    }
  ]
}
```

## Source register

All web sources below were opened on October 27, 2026. OpenAI's developer documentation redirects several former `developers.openai.com/codex` pages into its official `learn.chatgpt.com` documentation. Those redirect targets are primary OpenAI sources. URLs are recorded literally for recovery.

| ID | Official page or installed command |
| --- | --- |
| A1 | `https://code.claude.com/docs/en/cross-session-messaging` |
| A2 | `https://code.claude.com/docs/en/sub-agents` |
| A3 | `https://code.claude.com/docs/en/goal` |
| A4 | `https://code.claude.com/docs/en/scheduled-tasks` |
| A5 | `https://code.claude.com/docs/en/worktrees` |
| A6 | `https://code.claude.com/docs/en/commands` |
| A7 | `https://code.claude.com/docs/en/skills` (bundled skill status) |
| A8 | `https://code.claude.com/docs/en/plugins`; installed `claude plugin update --help`, `claude plugin marketplace --help` |
| A9 | `https://code.claude.com/docs/en/permissions` |
| O1 | `https://learn.chatgpt.com/docs/developer-commands` (official developer command reference; installed help comparison) |
| O2 | `https://learn.chatgpt.com/docs/agent-configuration/subagents` |
| O3 | `https://learn.chatgpt.com/docs/long-running-work` |
| O4 | `https://learn.chatgpt.com/docs/automations` |
| O5 | `https://learn.chatgpt.com/docs/environments/git-worktrees` |
| O6 | `https://learn.chatgpt.com/docs/code-review` plus installed `codex review --help` |
| O7 | `https://learn.chatgpt.com/docs/security/security-review`; `https://learn.chatgpt.com/docs/security/plugin/code-changes` |
| O8 | `https://learn.chatgpt.com/docs/plugins` plus installed marketplace/plugin help |
| O9 | `https://learn.chatgpt.com/docs/config-file/config-reference` (features.memories, memories.*, features.goals) |
| O10 | `https://learn.chatgpt.com/docs/hooks` (native event and setting execution, with surface limitations) |
| L1 | `codex --version`, `--help`, `agents --help`, `queue --help`, `resume --help`, `exec --help`, `review --help`, `app-server --help`, `plugin --help`, `plugin add --help`, `plugin marketplace --help`, `plugin marketplace upgrade --help` |
| L2 | `claude --version`, `--help`, `agents --help`, `plugin update --help`, `plugin marketplace --help` |
| L3 | `codex features --help`; filtered `codex features list` for goals/hooks/memories/multi_agent/plugins |

## Approved execution and next action

Tommy confirmed the model and approved D1-D11 after the inventory checkpoint. This grants implementation and the requested per-repository PR delivery; no session closure is authorized. One canonical capability contract uses native host operations through separate host adapters. Custom behavior survives only for a demonstrated unmet requirement and remains in that host's runtime.

Fresh Agent base: `438783a2ba1049f2afbecc16d62677cb4b8fd1ac`. Agent PR #24 already landed D2's 1,246-line shell removal at this head; reconcile its caller/tests evidence rather than repeat its deletion. Agent implementation checkout: `C:\Users\TommySeery\source\repos\tj-agents\agent.worktrees\Refactor-NativeWrappers`, branch `Refactor/NativeWrappers`.

Protected-work reconciliation: Core #512 is now the actual routing-removal PR at `1268140a639b649632593f75b2c9ff0b26a4a5fe`; its audit-time subject/head above remains historical evidence. Do not touch its routing/context files. Agent #22 remains open; the latest reconciled head is `03aa0472bf38959960d6787cb3d424d6544a7e8d`, superseding its audit-time head. Re-read protected PRs before overlapping owner slices.

Current action: the approved Agent, Core, Personal and Infonetica source cutovers are published as Agent #26, Core #517, Personal #41 and Infonetica #31. The progress ledger owns exact heads, tests and review state. Source reviews and genuine Core platform validation passed; publish this reviewed checkpoint. D4 retains its unresolved focus/inventory caller contract and protected-owner boundary; no CLI extraction is claimed. Native plugin/role/context/loader cases retain the additional requirements recorded above. Source PR delivery does not establish installed scheduling or transfer existing external registrations. Keep every session open.
