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
| [agent-store](https://github.com/tj-agents/agent-store) | The link store between tracker work items and agent sessions |
| [work-items](https://github.com/tj-agents/work-items) | The tracker interface and its GitHub/Azure DevOps adapters |
| [cli](https://github.com/tj-agents/cli) | Deterministic terminal, process and explicit worktree utilities |
| [github](https://github.com/tj-agents/github) | General GitHub access and collaboration utilities |
| [template](https://github.com/tj-agents/template) | Scaffolding, generators and templates |
| Profile repositories such as [personal](https://github.com/tj-agents/personal) and [work](https://github.com/tj-agents/work), plus a specific profile such as an employer's (see [Generic and specific profiles](PLUGINS.md#generic-and-specific-profiles)) | Which tracker and policy apply where a project selects that profile |
| Stack repositories such as [dotnet](https://github.com/tj-agents/dotnet), [react](https://github.com/tj-agents/react), [cpp](https://github.com/tj-agents/cpp) and [rust](https://github.com/tj-agents/rust) | Stack standards, package contracts and releases |
| Employer and product repositories | Their conventions, product decisions, private evidence and implementation details |

Keep one canonical home for each topic and link to its owner. Reference documents use descriptive names.
Use installed skills for the documentation and review process.
