# Plugin catalog and project selection

`tj-agents/marketplace` owns the `tj-agents` plugin identity, the set of available plugins, each
plugin's source repository, and the plugin dependency graph. Its authored `catalog.json` generates
the Claude and Codex marketplace manifests. Producer repositories own their plugin contents.

Core Machine owns the generic project selector: it expands requested plugins and curated stack
choices, then writes a project's `.agents/plugins.json` and native Claude/Codex settings. Its
offline catalog snapshot is generated from a recorded Marketplace commit, never maintained as
another plugin roster. Core may know the Marketplace location, but does not decide whether a
project is personal or work based on its owner or path. Profile owners such as Personal own their
specific adoption rules.

Every repository selecting a `*@tj-agents` plugin declares `tj-agents/marketplace` in
`.agents/plugins.json`. A source repository can publish elsewhere when that is its explicit
catalog identity; directory placement under `tj-agents` does not change its publisher. Plugin
availability, project selection, installation, trust, and effective skill loading are distinct
checks. A project declaration alone does not prove the host loaded a plugin.

## Catalog change

1. Edit only Marketplace's `catalog.json` for plugin names, sources, and dependencies; regenerate
   both host marketplace manifests and validate them.
2. Regenerate Core Machine's pinned offline snapshot from the merged Marketplace commit with
   `scripts/update_marketplace_catalog.py`. The snapshot records that source commit. Keep Core's
   `plugin_stacks.json` for curated project types; every stack entry must name a catalog plugin.
3. Verify selection of the changed plugins and the native settings written in a fresh project.
   Publish the Marketplace change before the Core snapshot update that refers to it.

Do not create a second authored plugin registry in Core or a new injector repository merely to
mirror Marketplace. Revisit a separate selector repository if the selector gains an independent
release cycle or consumers outside Core; it must still consume the same Marketplace catalog and
have a working fresh-machine bootstrap path.
