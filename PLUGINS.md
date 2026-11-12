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

## Configuration scope

| Scope | Authority | What belongs there |
| --- | --- | --- |
| Common organization rules | Base's shipped `tier.json` context | Rules that apply across repositories, including configuration ownership and target repository resolution |
| Repository selection | `.agents/plugins.json`, expanded from Marketplace | The repository's complete selected plugin composition |
| Repository configuration | `.agents/settings.json` | Explicit repository choices, including Personal's separate bot-identity opt-in |
| Machine-local bindings | Native local host settings and owned local state | Resolved executable/cache paths, local permission grants and credential bindings |

Global scope does not mean that every installed profile applies everywhere. Common rules can load
globally; Work, employer, Personal and stack behavior follow the target repository's selection and
applicability. Resolve the repository containing the actual file or operation, including linked
worktrees and nested repositories. A startup directory, GitHub owner or another session's scope is
not a substitute for that repository's declarations.

Keep authored repository declarations portable across Windows, Linux and different usernames.
Resolve local paths when preparing a host and keep those values in locally owned, Git-excluded
settings. Agent preparation grants permissions from the verified selected payloads and removes its
own obsolete grants when selection changes. It preserves unrelated local settings. Cached payloads
alone cannot grant permissions or establish repository adoption.

Base's common context loads through the existing SessionStart hook. Repository preparation also
projects selected `always` contexts from their canonical declarations into the managed `AGENTS.md`
standards block. Claude imports that file through `CLAUDE.md`; Codex reads the repository's native
instruction file. Conditional contexts remain runtime decisions. A shared document online or a
skill listed in a menu does not establish that either host loaded the rule.

Protected global host configuration, shell profiles, persistent environment and global Git writes
belong in the owning repository's root `install.ps1`. A packaged installer is a declared,
byte-identical copy of that file. Python can discover, render and verify changes; the protected
mutation remains in that installer, including native commands or APIs that write global settings.
Common tooling installation uses this boundary without enabling repository profiles globally.

## Profile composition and credentials

review-drafting behavior. The `tj-agents/company` source repository and its worktrees are work
scope even though their GitHub owner is `tj-agents`.

Personal requires explicit repository adoption. Neither the repository owner, a home-directory
location nor permission to commit agent configuration selects it. Personal selection also does not
enable bot credentials by itself: the same repository must opt in separately:

```json
{
  "configuration": {
    "personal": {
      "bot_identity": true
    }
  }
}
```

This setting belongs in `.agents/settings.json`; it contains no token or machine path.
Repositories without both selections use their existing native human Git and GitHub CLI identity.
An opt-in for one repository does not cover another repository with the same owner. Existing global
credential helpers and unrelated authentication settings are not evidence of agent ownership and
must not be rewritten as part of repository preparation.

## Plugins change

1. Edit only Marketplace's `plugins.json` for plugin names, sources, and dependencies; regenerate
   both host marketplace manifests and validate them.
2. Regenerate Agent's pinned offline snapshot from the merged Marketplace commit with
   `.agents/agent/utility/plugins/scripts/update_marketplace_plugins.py`. The snapshot records that source commit. Keep Agent's
   `plugin_stacks.json` for curated project types; every stack entry must name a plugin.
3. Verify selection of the changed plugins and the native settings written in a fresh project.
   Publish the Marketplace change before the Agent snapshot update that refers to it.

Do not create a second authored plugin registry in a producer repository. Agent consumes the same
Marketplace plugin roster; Agent owns its host installation and refresh entry points.

## Skill ownership

The approved ownership decision of 2026-10-25 separates three reusable source repositories:

| Source | Published namespaces | Responsibility |
| --- | --- | --- |
| [Core](https://github.com/tj-agents/core) | `base`, `workflow`, `engineering`, `docs` | Common behavior, workflow, engineering policy and documentation standards |
| [Agent](https://github.com/tj-agents/agent) | `agent`, `agent-store`, `codex` | Agent sessions, coordination, history, selection and refresh; persisted identities; Codex hooks and memory configuration |
| [CLI](https://github.com/tj-agents/cli) | `cli` | Deterministic terminal, process and explicit linked-worktree operations, alongside the existing CLI application |

Agent resolves conversation and session meaning, then delegates explicit process/tab targets to CLI.
`agent:handoff --host claude|codex -- <host arguments>` selects a private native launch handler;
`agent:open` recovers existing sessions. Shared operations use one Agent namespace across both hosts.
`cli:close` preserves the checkout; `cli:closeout` additionally removes its separately eligible linked
worktree. Neither operation infers agent completion or sweeps other worktrees.

The dependency graph stays acyclic: CLI consumes Base; Agent consumes Base, Agent Store and
CLI; Workflow and Engineering consume Agent capabilities. Core embeds declared, receipted runtime
exports where its generic hooks require them, without retaining another authored implementation.

Marketplace records the published source revisions. Publication, plugin activation and effective
loading remain separate checks, including fresh native sessions on Windows and Linux.
