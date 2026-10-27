# Plugins and project selection

`tj-agents/marketplace` owns the `tj-agents` plugin identity, the set of available plugins, each
plugin's source repository, and the plugin dependency graph. Its authored `plugins.json` generates
the Claude and Codex marketplace manifests. Producer repositories own their plugin contents.

Agent owns the generic project selector (`agent:plugins`): it expands requested plugins and curated stack
choices, then writes a project's `.agents/plugins.json` and native Claude/Codex settings. Its
offline plugins snapshot is generated from a recorded Marketplace commit, never maintained as
another plugin roster. The selector may know the Marketplace location, but does not decide whether a
project is personal or work based on its owner or path. Profile owners such as Personal own their
specific adoption rules.

Every repository selecting a `*@tj-agents` plugin declares `tj-agents/marketplace` in
`.agents/plugins.json`. A source repository can publish elsewhere when that is its explicit
plugin identity; directory placement under `tj-agents` does not change its publisher. Plugin
availability, project selection, installation, trust, and effective skill loading are distinct
checks. A project declaration alone does not prove the host loaded a plugin.

## Plugins change

1. Edit only Marketplace's `plugins.json` for plugin names, sources, and dependencies; regenerate
   both host marketplace manifests and validate them.
2. Regenerate Agent's pinned offline snapshot from the merged Marketplace commit with
   `.agents/agent/utility/plugins/scripts/update_marketplace_plugins.py`. The snapshot records that source commit. Keep Agent's
   `plugin_stacks.json` for curated project types; every stack entry must name a plugin.
3. Verify selection of the changed plugins and the native settings written in a fresh project.
   Publish the Marketplace change before the Agent snapshot update that refers to it.

Do not create a second authored plugin registry in a producer repository. Agent consumes the same
Marketplace plugin roster; Core owns the reproducible machine setup and sync entry points that install it.

## Skill ownership

The approved ownership decision of 2026-10-25 separates three reusable source repositories:

| Source | Published namespaces | Responsibility |
| --- | --- | --- |
| [Core](https://github.com/tj-agents/core) | `base`, `workflow`, `engineering`, `machine` | Common behavior, workflow and engineering policy, machine setup and OS utilities |
| [Agent](https://github.com/tj-agents/agent) | `agent`, `agent-store`, `codex` | Agent sessions, coordination, history, selection and refresh; persisted identities; Codex hooks and memory configuration |
| [CLI](https://github.com/tj-agents/cli) | `cli` | Deterministic terminal, process and explicit linked-worktree operations, alongside the existing CLI application |

Agent resolves conversation and session meaning, then delegates explicit process/tab targets to CLI.
`agent:handoff --host claude|codex -- <host arguments>` selects a private native launch handler;
`agent:open` recovers existing sessions. Shared operations use one Agent namespace across both hosts.
`cli:close` preserves the checkout; `cli:closeout` additionally removes its separately eligible linked
worktree. Neither operation infers agent completion or sweeps other worktrees.

The dependency graph stays acyclic: CLI consumes Base; Agent consumes Base, Agent Store, Machine and
CLI; Workflow and Engineering consume Agent capabilities. Core embeds declared, receipted runtime
exports where its generic hooks require them, without retaining another authored implementation.

This is the approved target architecture. Publication, plugin activation and fresh Windows/Linux
native-host acceptance remain the migration owner's delivery obligations; this document does not
claim that pending packages are already installed.
