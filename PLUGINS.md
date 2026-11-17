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

## Standards loading and worktrees

Agent checks the current checkout's native plugin settings and standards index before a managed launch.
A checkout's own `.agents/plugins.json` takes precedence. When it is absent in a linked worktree, readers
use the primary checkout's selection through Git's worktree metadata. This includes selections kept out
of version control in employer repositories. Invalid local selections remain errors; they do not silently
inherit another selection. Explicit adoption, installer reconciliation or `tj prepare --write` writes to
the current checkout; startup and refresh report drift without rewriting repository instructions or
configuration. Reading an inherited selection leaves its primary copy unchanged. CLI owns the shared filesystem resolver; Agent's launch,
adoption and permission generation and Core's context readers consume it.

Configuration scope is explicit when requested. Otherwise a Git project with a tracked selection uses
project scope, and one without a tracked selection uses local scope; outside Git the default is project
scope. Repository owner names do not select a profile or scope. Omitted permission preferences preserve
the provider's native settings. Agent's [repository selection and permissions contract](https://github.com/tj-agents/agent#repository-selection)
owns the commands and precedence rules.

Skills load on demand from their descriptions on Claude and Codex. The agent selects the standards relevant
to its task and reads their full bodies and needed references before editing. TJ skill entries point to
their canonical definitions; a name in a catalogue or index alone is not a loaded standard. Agent's compact
repository index and Core's SessionStart context provide routing, rather than injecting every stack's
standards or requiring a fixed list of reads. Repository activation keeps unrelated plugins out of discovery.

This loading path applies to every selected stack, including .NET, React, Azure, GitHub Actions and Python.
It relies on the agent choosing and applying the relevant skills. Mechanical checks enforce the rules they
can test, and review assesses the remaining judgments; reading a document alone proves neither. Core's
separate host-memory, settings, state and worktree boundaries remain active.

## Plugin kinds

Marketplace's `plugins.json` declares exactly one `kind` for every catalog entry. The
[Marketplace README](https://github.com/tj-agents/marketplace#plugin-kinds) owns the field
reference and how to add each kind.

| Kind | What it is | A repository selects |
| --- | --- | --- |
| `shared` | A capability any repository may use: stacks, tools and lifecycle plugins | Any number |
| `profile` | How the repository is worked on: `personal` or `work` | At most one; selected explicitly or required by an organization |
| `organization` | One organization's layer on one profile: tracker settings, context, standards, declarations and enrollment | At most one, with its profile |

An organization declares `"extends": "<profile>"` and lists that profile in `requires`, so
selecting the organization brings its profile. Shared plugins and profiles are generic: they name
no organization, person, repository or user path, and Marketplace CI rejects a generic plugin whose
pinned source names an organization. An organization is specific.

Agent's selector (`agent:plugins`, adoption and `tj install` reconciliation) enforces selection. It
refuses more than one profile after `requires` expansion. It also refuses any profile other than the
one an organization extends, such as `personal`, in a repository that organization's installed
employer declaration matches by Git origin or names as its own source repository.

```json
{ "name": "work", "repository": "work", "revision": "...", "requires": ["engineering", "teams"], "kind": "profile" },
{ "name": "example-employer", "repository": "example-employer", "revision": "...", "requires": ["work"], "kind": "organization", "extends": "work" }
```

## Plugins change

1. Edit only Marketplace's `plugins.json` for plugin names, sources, and dependencies; regenerate
   both host marketplace manifests and validate them.
2. Regenerate Agent's pinned offline snapshot from the merged Marketplace commit with
   `.agents/agent/utility/plugins/scripts/update_marketplace_plugins.py`. The snapshot records that source commit. Keep Agent's
   `plugin_stacks.json` for curated project types; every stack entry must name a plugin.
3. Verify selection of the changed plugins and the native settings written in a fresh project.
   Publish the Marketplace change before the Agent snapshot update that refers to it.

Do not create a second authored plugin registry in a producer repository. Agent consumes the same
Marketplace plugin roster; Agent owns installation and repository selection.

## Skill ownership

The source owners separate shared guidance from session behavior and operating-system mechanics:

| Source | Published namespaces | Responsibility |
| --- | --- | --- |
| [Core](https://github.com/tj-agents/core) | `base`, `workflow`, `engineering`, `docs` | Common behavior, workflow, engineering policy and documentation guidance |
| [Agent](https://github.com/tj-agents/agent) | `agent`, `agent-store`, `codex` | Agent sessions, coordination, history, selection, installation and refresh; link-store inspection; Codex hooks and memory configuration |
| [CLI](https://github.com/tj-agents/cli) | `cli` | Deterministic terminal, process and explicit linked-worktree operations, alongside the existing CLI application |

Agent resolves conversation and session meaning, then delegates explicit process and terminal operations
to CLI. `tj claude` and `tj codex` retain native conversation interfaces. Handoff, start and recovery use
the same managed lifecycle; `tj message` chooses the appropriate messaging implementation for both hosts.
[Workflow and Agent Store boundaries](WORKFLOW_AGENT_STORE.md) describes completion and recorded identity.
The [Agent Store repository](https://github.com/tj-agents/agent-store) owns its database and binary; Agent's
inspection skill consumes that API.

Marketplace owns the dependency graph. Core consumes staged, pinned Agent runtime exports where its
generic hooks require them, without retaining another authored implementation. Generated plugin payloads
remain publication output, and source changes alone do not establish native activation.
