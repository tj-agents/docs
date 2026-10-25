# tj-agents documentation

Global architecture, cross-repository designs, decisions and roadmaps for [tj-agents](https://github.com/tj-agents).
This is the shared documentation home; each source repository owns its implementation and operational details.

[Plugin catalog and project selection](PLUGIN_CATALOG.md) records the cross-repository ownership boundary
for Marketplace, Core Machine, and profile adopters.

## Current design work

| Topic | Design | Progress | Roadmap |
| --- | --- | --- | --- |
| Scoped standards composition | [Proposal](plans/standards-composition/STANDARDS_COMPOSITION_PLAN.md) | [Current state and next action](plans/standards-composition/STANDARDS_COMPOSITION_PROGRESS.md) | [Remaining outcome](plans/standards-composition/STANDARDS_COMPOSITION_ROADMAP.md) |
| Durable plan persistence | [Proposal](plans/plan-persistence/PLAN_PERSISTENCE_PLAN.md) | [Current state and next action](plans/plan-persistence/PLAN_PERSISTENCE_PROGRESS.md) | [Remaining outcome](plans/plan-persistence/PLAN_PERSISTENCE_ROADMAP.md) |
| Reviewed auto-merge rollout | [Rollout plan](plans/tj-agents-auto-merge/PLAN.md) | [Current state and next action](plans/tj-agents-auto-merge/PROGRESS.md) | [Remaining outcome](plans/tj-agents-auto-merge/ROADMAP.md) |
| Agentic delivery across independent workstreams | [Roadmap](plans/agentic-delivery/ROADMAP.md) | [Selected next work](plans/agentic-delivery/ROADMAP.md#selected-next-work) | [Next steps](plans/agentic-delivery/ROADMAP.md#next-steps) |
| Bugs, mistakes and debt | [Problem skills](plans/problem-management/PLAN.md) | [Scope](plans/problem-management/PLAN.md#scope-of-the-next-slice) | [Dependent handoff policy](plans/handoff-priority/PLAN.md) |
| Controlled agent orchestration | [Gameplan](plans/agent-orchestration/GAMEPLAN.md) | [Readiness and next action](plans/agent-orchestration/GAMEPLAN.md#readiness-and-next-action) | [Proposed delivery sequence](plans/agent-orchestration/GAMEPLAN.md#delivery-sequence) |
| Workflow and Agent Store boundaries | [Standing architecture](WORKFLOW_AGENT_STORE.md) | [Dated delivery evidence](WORKFLOW_AGENT_STORE.md#decision-status) | [Acceptance gates](WORKFLOW_AGENT_STORE.md#gates-and-caller-acceptance) |

The standards-composition proposal awaits a design decision. Publishing or moving it does not approve runtime implementation.

## Documentation ownership

| Owner | What belongs there |
| --- | --- |
| This repository | Global design, architecture decisions, shared terminology, cross-repository dependencies and acceptance criteria |
| [core](https://github.com/tj-agents/core) | Common agent behavior, engineering process, machine utilities and their implementation plans |
| [agent](https://github.com/tj-agents/agent) | Agent sessions, coordination, history, plugin selection/refresh and their implementation plans |
| [cli](https://github.com/tj-agents/cli) | Deterministic terminal/process/worktree utilities, the CLI application and their implementation plans |
| [template](https://github.com/tj-agents/template) | Scaffolding, generators, templates and their implementation plans |
| Stack repositories such as [dotnet](https://github.com/tj-agents/dotnet), [react](https://github.com/tj-agents/react), [cpp](https://github.com/tj-agents/cpp) and [rust](https://github.com/tj-agents/rust) | Stack standards, package contracts, releases and their implementation plans |
| Employer and product repositories | Their conventions, product decisions, private evidence and implementation details |

Keep one canonical home for each document. A shared plan links to owner implementation plans and tracks their dependencies;
source repositories link back here instead of maintaining another copy. Existing owner plans keep their current owners.
Keep private employer and product material in its authorized repository; link to it without copying it here.

## Layout

Cross-repository plans live under `plans/<topic>/`, with the plan, progress record and roadmap together.
Standing architecture and decision documents use descriptive names without plan/progress suffixes.
Use the installed planning and review skills for process; do not vendor skills, hooks or generated plugin output here.
Keep proposals, approved decisions and verified implementation status distinct, with dated source evidence where needed.
