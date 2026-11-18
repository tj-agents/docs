# Workflow and Agent Store boundaries

Managed sessions use `tj claude` or `tj codex`, preserving the provider's native conversation interface.
Foreground launch, handoff, start and recovery share the same managed lifecycle. The operational commands
belong to [Agent](https://github.com/tj-agents/agent#managed-sessions) and
[CLI](https://github.com/tj-agents/cli#managed-sessions).

## Responsibilities

| Owner | Responsibility |
| --- | --- |
| Base | Shared behavior and routing to the project's selected capabilities. |
| Workflow | One owner of the whole authorized goal, including planning, execution, continuation and handoff. |
| Engineering | Software design, implementation, diagnosis, testing, review and delivery operations. |
| Agent | Native host interpretation, session launch and recovery, messaging integration, installation and project selection. |
| CLI | Deterministic processes, terminals, message routing, completion transitions and durable receipts, and guarded cleanup. |
| Agent Store | Session and launch identities, work-item links and atomic worktree claims. |
| Work Items | Tracker operations through the project's selected provider. |
| A selected profile and organization | Applicable policy, tracker configuration and delivery gates. |

The link store does not infer task completion or process liveness. A profile does not establish another
whole-goal owner. Repository ownership and installed plugin availability do not establish profile adoption;
[project selection](PLUGINS.md) owns that distinction.

## Ownership and coordination

Workflow keeps the whole requested outcome across phases. Bounded delegation returns evidence to that
owner; an ownership handoff transfers a self-contained goal to another session. Handoffs explicitly choose
one recorded parent or independence. Independent sessions inherit no reporting obligation from ambient
session variables. Parented sessions retain the exact parent across recovery, on either provider.

Every agent sends through `tj message`. TJ resolves the recipient and chooses the provider implementation.
Claude-to-Claude sends use the checked native adapter; other provider pairs use session feeds. Native
permissions remain authoritative, and native refusal or uncertainty never causes a feed fallback. A stored
or submitted message does not prove recipient acceptance or reading. Agent's
[messaging contract](https://github.com/tj-agents/agent/blob/main/.agents/agent/utility/message/SKILL.md)
owns agent usage, and [CLI](https://github.com/tj-agents/cli#tj-message-and-tj-feed-messaging-between-sessions)
owns transport receipts and retry identity.

## Completion and recovery

The agent requests completion with `tj finish` after delivering the whole authorized outcome and its
validation, then writes the native final response. The matching native turn boundary supplies that response.
Intent alone, a merged PR, tracker Done or a native Stop event alone does not complete the session. A turn
without a disposition remains visibly incomplete; the runtime does not create another model turn or guess
completion from prose.

The durable record separates the final result, routed parent delivery, tracker completion and cleanup.
Managed completion delivers the final response through the common message implementation; agents do not
send another manual final report. `tj receipt --launch <launch-id>` exposes the record after a terminal closes.
`tj status` combines that lifecycle state with separate native liveness and linked work-item information.
Sessions without a work item remain visible, and native identity does not require a tracker profile.

Genuine pending work is recorded with `tj wait`; user keep-open requests use a persistent `tj hold`.
A hold permits result delivery but prevents closure, survives new input and remains in force after recovery.
Submitted native input withdraws pending completion. An unsent draft is not a native turn event.
Failures retain the result and completed step receipts for recovery;
retries do not resend a claimed native message or repeat tracker work that already has a receipt.

Agent reads host-native liveness. Managed Codex uses an owned native process; CLI verifies its process
identity, creation time and wrapper relationship before Agent records that observation. Threads still
loaded in Codex's shared daemon remain competing evidence. A dead wrapper or an ended store row does not
prove the native conversation is gone. Recovery refuses a live or ambiguous owner and preserves the
conversation, relationship and ownership while recording a new launch rather than rewriting its history.

Launch responses distinguish dispatch, verified process startup and a verified first turn. Codex recovery
can verify the process before the user submits a turn, but that does not prove the native interface has
loaded the conversation. Agent keeps conversation confirmation pending without submitting synthetic input.
The [launch and recovery contract](https://github.com/tj-agents/agent#lifecycle) owns these evidence stages.

## Worktrees and repository state

Managed worktrees are created only under `<repository-root>/.worktrees/<name>` through
[Core's shared creator](https://github.com/tj-agents/core/blob/main/.agents/engineering/operation/open-worktree/SKILL.md).
Agent binds the native session and launch; Agent Store records exact claims. CLI verifies ownership,
repository integration, authored changes and competing writers before cleanup. Primary checkouts and
unverified or unfinished work are preserved. Interrupted cleanup retains its proof for an explicit retry.

Startup and plugin refresh check repository instructions and configuration without rewriting them. Explicit
adoption, install reconciliation or `tj prepare --write` owns repository convergence. Generated instruction
drift therefore reports an action instead of creating tracked dirt during a managed session.

## Verification boundaries

| Evidence | What it establishes |
| --- | --- |
| Source checks | Canonical code, generated payloads, declarations and tests agree. |
| Publication | The intended revision was generated and distributed by its source owner. |
| Native activation | The installed provider accepted and loaded the selected package. |
| Installed behavior | The real Windows or Linux entry point performs the required lifecycle operation. |

These are separate gates. A selection file, passing fixture or version command does not establish native
handoff, delivery or cleanup. Source work and its PR retain implementation, review and acceptance evidence;
this reference explains the responsibility boundaries without duplicating that execution history.
