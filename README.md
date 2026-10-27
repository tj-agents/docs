# tj-agents documentation

Reference documentation for the current [tj-agents](https://github.com/tj-agents) architecture,
cross-repository responsibilities and shared terminology. Each source repository owns its implementation
and operational details. Follow [AGENTS.md](AGENTS.md) when changing documentation.

## Reference topics

| Topic | Document |
| --- | --- |
| Plugins, project selection and skill ownership | [Plugins and project selection](PLUGINS.md) |
| Workflow lifecycle and recorded agent state | [Workflow and Agent Store boundaries](WORKFLOW_AGENT_STORE.md) |

## Documentation ownership

| Owner | What belongs there |
| --- | --- |
| This repository | Current architecture, cross-repository responsibilities and shared terminology |
| [core](https://github.com/tj-agents/core) | Common agent behavior, engineering process and workflow |
| [agent](https://github.com/tj-agents/agent) | Agent sessions, coordination, history, plugin selection and refresh |
| [cli](https://github.com/tj-agents/cli) | Deterministic terminal, process and explicit worktree utilities |
| [template](https://github.com/tj-agents/template) | Scaffolding, generators and templates |
| Stack repositories such as [dotnet](https://github.com/tj-agents/dotnet), [react](https://github.com/tj-agents/react), [cpp](https://github.com/tj-agents/cpp) and [rust](https://github.com/tj-agents/rust) | Stack standards, package contracts and releases |
| Employer and product repositories | Their conventions, product decisions, private evidence and implementation details |

Keep one canonical home for each topic and link to its owner. Reference documents use descriptive names.
Use installed skills for the documentation and review process.
