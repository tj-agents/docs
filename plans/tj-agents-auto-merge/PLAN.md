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
Next action: reconcile the exact remaining PR/head states, keep blocked candidates bound to their own continuations, and deliver only after terminal green gates.

Current source-owned follow-ups are tracked in [the both-host agent changes plan](C:/Users/TommySeery/source/repos/tj-agents/core/.worktrees/Fix-BothHostAgentChanges/plans/both-host-agent-changes/PLAN.md)
and [the scoped agent delivery goal](C:/Users/TommySeery/source/repos/tj-agents/core/.worktrees/Fix-ScopedAgentDelivery/plans/scoped-agent-delivery/GOAL.md).
Both implementations are committed and undergoing independent review. The general repair adds
mechanical host-evidence checks to planning, review and preflight. The independent delivery slice adds
native Codex merge-review and enqueue enforcement, preserving the existing authority schema and all
six fixed stop classes. Focused local checks passed; source fixtures and package generation establish
source verification, while exact-head CI and installed-profile activation remain separate evidence.
The initial sensitive-class exemption patch was automatically rejected before application. Tommy explicitly approved a separate second slice on 2026-10-10 for `ci-workflow`, `migration`, `auth`, `money`, and `published-contract` across the twelve tj-agents repositories, after reviews and required checks. Holds and authorization-policy self-changes remain stops; other defaults are unchanged. The approved second slice is not implemented. Native enforcement parity remains separate and preserves every current fixed stop.
These goals retain their existing core source ownership.

Configuration alone does not fulfill unattended standards delivery: current fixed stop classes match
authored contract skills and permission tools. Some native review/merge hooks are Claude-only, so
shared resolver packaging is not proof of equivalent native enforcement. Core source delivery owns
these gaps. The separate bounded core source workstream owns the general future-plan
both-host requirement; it must implement, validate and deliver the shared rule, not merely add a local
reminder. The live configurable-auto-merge checkout must remain intact. The Rust discovery goal remains
separate from this policy rollout.


## Proposed repository configuration placement

A separate design investigation is considering one scalable repository configuration object shared by producers and consumers. The current proposal places it at `.agents/configuration.json` with a versioned object, for example `{"schema_version":1,"configuration":{"core":{"auto_merge":true}}}`. This is a placement proposal only: no file contract or implementation exists. Core would own the contract and both-host loader; kit would later scaffold and validate the released core contract; consumers such as Concertable would configure that same file. Future package namespaces (for example `dotnet`) would be owned by those packages. Current settings are core-only. This does not enable auto-merge in Concertable or authorize installation/migration. Coordinate with the existing `Feature-ConfigurableAutoMerge` owner; do not create a competing goal.

## Next Steps

The parent retains rollout ownership. The companion PROGRESS.md owns executable Next Steps and current source-approval gates. Reconcile exact PR/head states and retain each delayed delivery binding. Core #175 remote head `cd938` had green CI, then the existing owner integrated a newer candidate at `bd94fe2` that is under fresh review. Do not treat the earlier CI as acceptance of the integrated candidate or duplicate its owner. Core #174, cpp #38, marketplace #5, cli #2 and work #4 are recorded merged at exact landing heads in the Rust continuation ledger. Docs #2 remains a draft at `7fff64c2c45e80e39954959410f73e2563343eb9` and requires fresh incremental review after this update. The approved sensitive second slice is not implemented. The root cause of kit/dotnet/rust/react/nvim verification failures is kit 1.2.0's exact `.agents` allowlist omitting `.agents/delivery-authorization.json`; kit recovery is under review, and 1.2.1 is not published while consumers remain pinned to 1.2.0. Infonetica #9 verification did not start because GitHub reported failed account payments or a spending-limit issue; preserve the hold without retry.

Lane L5 owns mechanical policy preparation; L4 owns ordinary review and delivery; L3 owns bounded
source diagnosis; L2 owns authorization-security review where the descriptor requires it.
