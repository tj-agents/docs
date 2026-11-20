# Workflow and Agent Store boundaries

Managed sessions preserve the provider's native conversation interface through `tj claude` and `tj codex`.
Agent's installer binds plain shell `claude` and `codex` launches to those managed entry points.
Foreground launch, handoff and recovery share the same lifecycle. [Agent's lifecycle](https://github.com/tj-agents/agent#lifecycle)
and [CLI's managed sessions](https://github.com/tj-agents/cli#managed-sessions) own operational procedures.

## Responsibilities

| Owner | Responsibility |
| --- | --- |
| Base | Shared behavior and routing to the project's selected capabilities. |
| Workflow | One owner of the whole authorized goal, including planning, execution, continuation and handoff. |
| Engineering | Software design, implementation, diagnosis, testing, review and delivery operations. |
| Agent | Native host interpretation, session launch and recovery, messaging integration, installation and project selection. |
| CLI | Deterministic processes, terminals, message routing, completion transitions, durable receipts and guarded cleanup. |
| Agent Store | Session and launch identities, work-item links and atomic worktree claims. |
| Work Items | Tracker operations through the project's selected provider. |
| A selected profile and organization | Applicable policy, tracker configuration and delivery gates. |

The link store does not infer task completion or process liveness. A profile does not establish another
whole-goal owner. Repository ownership and installed plugin availability do not establish profile adoption;
[project selection](PLUGINS.md) owns that distinction. Producers declare plugin dependencies; Marketplace
validates and publishes that graph. Core consumes declared, pinned Agent exports without retaining
another authored runtime.

## Ownership and coordination

Workflow keeps the whole requested outcome across phases. Bounded delegation returns evidence to that
owner; an ownership handoff transfers a self-contained goal to another session. Agent handoff defaults
the parent to the calling session, preserves an explicit override and carries the standing reporting rule.
An existing work-item link is optional; the launcher does not create an item or require a tracker for an
unlinked session. [Agent's handoff contract](https://github.com/tj-agents/agent/blob/main/.agents/agent/utility/handoff/SKILL.md)
owns arguments and parent behavior. Recovery preserves the recorded relationship.

[Agent's messaging contract](https://github.com/tj-agents/agent/blob/main/.agents/agent/utility/message/SKILL.md)
owns transport choice, permitted sends, waits and delivery evidence. Submission or storage alone does
not prove that the recipient read a message. A parent relationship does not authorize progress messages
contrary to the task's standing reporting instructions.

## Completion and recovery

Completion requires the whole authorized outcome and its validation. In a managed session, the agent
requests `tj finish` and then writes the native final response; intent alone is not completed delivery or
cleanup. A durable receipt distinguishes result delivery, any linked tracker operation and cleanup.
Genuine pending work uses `tj wait`, and a user's keep-open request uses `tj hold`.
[CLI's completion contract](https://github.com/tj-agents/cli#completion-waits-and-keep-open) owns the
state transitions, parent delivery, hold release and receipt inspection. Workflow owns whether the
authorized goal is actually complete. A merged PR, tracker Done or native Stop event alone is insufficient.

Agent reads host-native liveness. Managed Codex owns the frontend process and explicitly connects it to
the native default local daemon. Process evidence identifies that transport; loaded daemon threads and
any separate embedded engines remain distinct observations, including when they share a conversation UUID.
A dead wrapper or ended store row does not prove that the conversation is gone. Recovery reconciles a live
or ambiguous owner and preserves the conversation and relationship while recording a new launch.
The shared daemon does not expose which thread a particular frontend currently displays after an internal
picker switch. A matching directory or inherited server environment does not establish that relationship.

Launch evidence distinguishes dispatch, verified process startup and a verified first turn. Process
startup alone does not prove that the conversation loaded. Agent keeps missing confirmation visible
without sending synthetic input. Codex turn completion does not reveal every unsent draft or native
activity, so its window remains open until normal exit before cleanup is rechecked. The owning
[Agent lifecycle](https://github.com/tj-agents/agent#lifecycle) and
[CLI closeout contract](https://github.com/tj-agents/cli#safe-closeout-and-recovery) define these checks.

## Worktrees and repository state

[Core's shared creator](https://github.com/tj-agents/core/blob/main/.agents/engineering/operation/open-worktree/SKILL.md)
owns managed worktree creation under `<repository-root>/.worktrees/<name>`. Agent binds the native
session and launch, and Agent Store records exact claims. CLI verifies ownership, repository integration,
authored changes and competing writers before cleanup. Primary checkouts and unfinished or unverified
work are preserved.

Preparation checks repository settings by default. Explicit adoption, installer reconciliation or
`tj prepare --write` applies authorized configuration changes. Local-only adoption validates plugin
availability while preserving the owner's instruction files. [Project selection](PLUGINS.md) describes
scope and freshness evidence; Agent owns the concrete commands and failure handling.

## Verification boundaries

| Evidence | What it establishes |
| --- | --- |
| Source checks | Canonical code, generated payloads, declarations and fixtures agree. |
| Publication | The intended revision was generated and distributed by its source owner. |
| Native inventory | The selected dependency closure is installed, enabled and accepted by the current loader. |
| Executing hook package | Which Agent hook package is executing; other cached session content remains unverified. |
| Loaded Codex hooks | The thread's hook declarations, trust and build paths; a declaration-only hash does not attest file contents. |
| Installed behavior | A supported entry point performs the required lifecycle operation. |

These are separate gates. Source checks, a selection file or a version command do not establish that a
running session loaded every updated plugin. Publication and installed acceptance remain with the source
delivery; this reference does not replace their evidence.
