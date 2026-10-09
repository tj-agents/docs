# Enable reviewed delivery for tj-agents repositories

## Outcome and authorization

Tommy's current instruction: enable auto-merging without the agent asking again, once reviews and
required checks pass, specifically for his tj-agents repositories. This authorizes the GitHub
repository setting and repository-owned standing merge policy; it does not authorize bypassing
reviews, failed checks, billing restrictions, or changing unrelated repositories.

Tommy subsequently reiterated that every agent fix must cover both Claude and Codex. This rollout
uses the single host-neutral policy and requires verified wiring and equivalent gate behavior in
both native host payloads; no Codex-only permission or configuration is sufficient. This is a general
requirement for every future agent plan and fix, not an exception for this rollout.

Targets: tj-agents/core, cpp, dotnet, rust, react, nvim, kit, marketplace, work, infonetica, docs, cli.
Keep each existing source owner and active checkout intact. The unfinished configurable-auto-merge
feature has a live independent owner in core/.worktrees/Feature-ConfigurableAutoMerge; do not create
a second writer there. The work-plugin delivery remains a distinct existing workstream.

## Evidence

- GitHub allow_auto_merge was false on all eleven queried standards repositories. The cli repository
  is included by Tommy's clarification to all his tj-agents repos and requires the same inspection.
- Core's current merged runtime already accepts .agents/delivery-authorization.json with
  standing_authorization: auto and a recorded instruction. It still validates reviews and delivery
  checks before merging. The newer auto_merge boolean is not accepted by the current merged schema;
  do not ship that field until its source feature is delivered.
- The configurable-auto-merge feature is implemented and reviewed locally at a41bdace, has no PR,
  and its registered owner PID 43300 is still running. This rollout will use the current supported
  standing policy rather than take over that checkout.
- The newer repository plugin setup decision was one-time setup and remained unfinished; merge
  permission alone cannot implement the missing configure-repo-plugins entry point.

## Execution

1. Lane L5: enable GitHub's repository auto-merge capability for the exact targets and read it back.
2. Lane L5: prepare one narrowly scoped policy PR per target from its current remote default branch,
   preserving any existing policy fields. Use the current supported standing-authority schema.
3. Lane L4: independently review the immutable policy diffs and validate each JSON against the merged
   policy schema and the exact requested repository scope.
4. Publish the reviewed candidates, observe each exact-head CI result, and merge each green candidate
   under Tommy's explicit authorization for this rollout. Do not enable auto-merge while a review or
   required check is missing. Record platform failures as actual gates with their resolver.
5. Read back the final policies and settings. Keep each blocked repository's exact PR/head/result
   recoverable; do not claim fleet completion until every target is configured or a real gate is recorded.

## Progress and next action

GitHub readback now confirms auto-merge enabled for core, cpp, dotnet, rust, react, nvim, kit,
marketplace and cli. The private work, infonetica and docs repositories continue to report false
after an update. The organization is on GitHub Free, which lacks native auto-merge for private
repositories; ordinary agent merging after terminal checks remains a separate supported path. No billing, visibility
or branch-protection change is authorized or attempted. Settings evidence is saved at
`C:\Users\TommySeery\source\repos\tj-agents\rust\.worktrees\Fix-RustStandardDiscovery\.agents\continuation\tj-agents-auto-merge-settings.json`, `C:\Users\TommySeery\source\repos\tj-agents\rust\.worktrees\Fix-RustStandardDiscovery\.agents\continuation\tj-agents-auto-merge-candidates.json`, and `C:\Users\TommySeery\source\repos\tj-agents\rust\.worktrees\Fix-RustStandardDiscovery\.agents\continuation\tj-agents-auto-merge-review-descriptors.json`.

Shared core delivery-runtime tests passed (28); shared delivery-binding tests passed (30). Core ships the shared delivery-binding gate and common workflow resources. Native host enforcement is still uneven: Claude has merge-review and enqueue hooks, while Codex has no equivalent native merge-review/enqueue path. Shared resolver packaging does not prove both hosts enforce the same reviews and required checks. Isolated policy checkouts are being prepared by one
serialized mechanical writer. All twelve candidates are now committed, clean and accepted by the
current policy schema; a regular source path resolves to auto and an explicit human-gate label stops.
The parent retains review and delivery decisions. The frozen policy reviews are complete. Eleven
non-docs PRs are published; docs is held for this canonical progress correction and incremental review.
Next action: diagnose the failed verification jobs and deliver only candidates with terminal green gates.

Current source-owned follow-ups are tracked in [the both-host agent changes plan](C:/Users/TommySeery/source/repos/tj-agents/core/.worktrees/Fix-BothHostAgentChanges/plans/both-host-agent-changes/PLAN.md)
and [the scoped agent delivery goal](C:/Users/TommySeery/source/repos/tj-agents/core/.worktrees/Fix-ScopedAgentDelivery/plans/scoped-agent-delivery/GOAL.md).
Both implementations are committed and undergoing independent review. The general repair adds
mechanical host-evidence checks to planning, review and preflight. The independent delivery slice adds
native Codex merge-review and enqueue enforcement, preserving the existing authority schema and all
six fixed stop classes. Focused local checks passed; source fixtures and package generation establish
source verification, while exact-head CI and installed-profile activation remain separate evidence.
Sensitive-class exemptions were rejected before application and await Tommy's explicit decision.
These goals retain their existing core source ownership.

Configuration alone does not fulfill unattended standards delivery: current fixed stop classes match
authored contract skills and permission tools. Some native review/merge hooks are Claude-only, so
shared resolver packaging is not proof of equivalent native enforcement. Core source delivery owns
these gaps. The separate bounded core source workstream owns the general future-plan
both-host requirement; it must implement, validate and deliver the shared rule, not merely add a local
reminder. The live configurable-auto-merge checkout must remain intact. The Rust discovery goal remains
separate from this policy rollout.

## Next Steps

The parent retains rollout ownership. The companion PROGRESS.md owns the executable Next Steps and
current source-approval gate. Finish the twelve exact-head policy reviews and deliveries. Bind each
delayed PR to its own continuation, record real platform gates, and reconcile core source fixes before
claiming the requested outcome. Configurable sensitive-class exceptions are proposed and await Tommy's
explicit informed approval after automatic review rejected that patch. Native enforcement parity can
proceed independently while every existing fixed stop remains active.
Lane L5 owns mechanical policy preparation; L4 owns ordinary review and delivery; L3 owns bounded
source diagnosis; L2 owns authorization-security review where the descriptor requires it.
