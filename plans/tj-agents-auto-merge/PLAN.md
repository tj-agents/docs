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

- GitHub `allow_auto_merge` was inspected for all twelve targets. It is enabled on the nine public repositories; it remains false on private `work`, `infonetica` and `docs` because the organization plan does not provide that feature. No billing, visibility or protection change was made.
- Core's merged runtime accepts `.agents/delivery-authorization.json` with `standing_authorization: auto` and a recorded instruction, while retaining review and required-check gates. The newer `auto_merge` boolean is not accepted by the merged schema.
- The separate configurable-auto-merge source feature is at `a41bdace0d6757009519fb90c253bc78aed28970`, has a complete approved local review dated October 8, and has no PR. Its original owner PID 43300 remains registered and live, although the recorded lease expired at 1791573094.7468004. Read-only status checks do not transfer ownership; preserve that recovery dependency.
- The repository-plugin setup decision was one-time setup and remains a separate unfinished workstream; merge permission alone cannot implement the missing `configure-repo-plugins` entry point.

The shared standing-merge policy resolves the repository instruction, affected paths and hold labels before reviewed delivery proceeds. The source record below distinguishes source-level checks and exact-head CI from installed-profile activation; Core PR183 delivered the approved generic five-class capability, while repository activation and the configuration object remain unfinished.

```agent-host-coverage
{
  "schema_version": 1,
  "shared_source": ".agents/workflows/delivery_runtime.py and .agents/delivery-authorization.json",
  "hosts": [
    {
      "host": "claude",
      "behavior": "Resolve repository standing-merge policy for reviewed delivery; preserve hold and stop-class decisions and require current review and terminal checks before merging.",
      "source": ".agents/workflows/workflow_ops.py, .agents/hooks/delivery_binding_gate.py, .agents/hooks/merge_review_gate.py, and .agents/hooks/persistent_workflow_merge_gate.py",
      "mapping": ".agents/plugins/manifests/claude/engineering-hooks.json wires the native hooks; .agents/plugins/harness/engineering.json declares shared sources for Claude and Codex.",
      "verification": {
        "level": "source",
        "result": "limited",
        "evidence": "Core183 generic five-class source capability, Core182 both-host handoff contracts, and Core184 shared Stop mechanism are merged with exact PR and causal main CI. Native enforcement c007490 remains changes-requested for SD08/SD10/SD11; 244 tests with9 skips passed, while one unchanged Windows wiring subcase timed out. Extractor preparation is paused for a reproduced generic binder timeout on exact base. Budget repair is bounded to a separate checked source goal; heartbeat metadata has a sole implementation worker. Neither native-gate publication nor repository configuration activation is complete."
      },
      "exception": {
        "constraint_evidence": "Stop at202b330 resolves only the event checkout, so this native Rust session is not associated with its separate Docs controller. Reciprocal authenticated association design is accepted but not implemented. Both-host source delivery is distinct from normal-profile activation; the latter remains unverified.",
        "supported_other_host_outcome": "Claude and Codex share the affected extractor and current harmless native and inert gate probes reproduce remaining executable-script false allows. Neither host has approved current native enforcement or normal-profile activation."
      }
    },
    {
      "host": "codex",
      "behavior": "Shared sources resolve standing authorization, holds and stop classes; Codex-specific merge-review/enqueue enforcement remains in the core-owned source slice.",
      "source": ".agents/workflows/workflow_ops.py, .agents/hooks/delivery_binding_gate.py, .agents/hooks/merge_review_gate.py, and .agents/hooks/persistent_workflow_merge_gate.py",
      "mapping": "Shared sources are declared in .agents/plugins/harness/engineering.json; equivalent native Codex merge-review/enqueue enforcement remains in the core-owned source slice.",
      "verification": {
        "level": "source",
        "result": "limited",
        "evidence": "Core183 generic five-class source capability, Core182 both-host handoff contracts, and Core184 shared Stop mechanism are merged with exact PR and causal main CI. Native enforcement c007490 remains changes-requested for SD08/SD10/SD11; 244 tests with9 skips passed, while one unchanged Windows wiring subcase timed out. Extractor preparation is paused for a reproduced generic binder timeout on exact base. Budget repair is bounded to a separate checked source goal; heartbeat metadata has a sole implementation worker. Neither native-gate publication nor repository configuration activation is complete."
      },
      "exception": {
        "constraint_evidence": "Stop at202b330 resolves only the event checkout, so this native Rust session is not associated with its separate Docs controller. Reciprocal authenticated association design is accepted but not implemented. Both-host source delivery is distinct from normal-profile activation; the latter remains unverified.",
        "supported_other_host_outcome": "Claude and Codex share the affected extractor and current harmless native and inert gate probes reproduce remaining executable-script false allows. Neither host has approved current native enforcement or normal-profile activation."
      }
    }
  ]
}
```
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

## Delivered source and retained dependencies

PROGRESS.md is the current execution snapshot and owns exact heads, test results, owners and gates. Eleven initial policy PRs landed; Infonetica9 and Work1 retain billing failures before job steps. Work1 communications do not implement the separate repository-plugin setup workstream.

Core175 delivered the general Claude/Codex plan coverage requirement. Core182 corrected both machine handoff contracts so a bounded side handoff retains the unfinished parent. Core183 delivered the user-approved generic five-class authority capability, retaining explicit holds and authorization-policy stops. Core184 delivered the shared Stop mechanism. Their exact-head and causal publication checks are recorded in PROGRESS.md and the source plans. They do not activate all repository preferences or prove installed prevention.

Native enforcement remains at c00749018acf5a791eb8049155416cb42536a861, reviewed with retained Unix-profile and PowerShell-prefix/version findings. Preserve the original Fix/ScopedAgentDelivery checkout, frozen review and stashes. Land the compatible extractor preparation first, then integrate published main and deliver native wiring sequentially. No stacked PR. Preparation exposed a generic binding timeout also reproduced on its exact base; a separate budget repair retains the ten-second deadline and authority checks before preparation resumes.

## Selected repository configuration design

Use authored `.agents/configuration.json` in any producer or consumer checkout, with one versioned envelope:

```json
{
  "schema_version": 1,
  "configuration": {
    "core": { "auto_merge": true }
  }
}
```

Core owns the generic reader and its own namespace; future marketplaces own their namespaces, such as dotnet. Well-shaped unknown namespaces remain opaque JSON and are preserved. Core validates core.auto_merge as a strict boolean and rejects unknown core fields rather than silently ignoring misspellings. Missing preference defaults false; existing invalid configuration is an error, never a fallback to enabled behavior. This file records preferences separately from delivery authority, hold labels and authorized stop classes. No repository slug allowlist belongs in Core.

Envelope validation requires exactly schema_version and configuration; version is actual integer1, excluding booleans. Namespace names match ^[a-z][a-z0-9-]*$ and namespace values are objects. Reject duplicate JSON keys, unreadable/malformed files and invalid consumed Core fields. Read only the caller's actual checkout root: no ancestor, common-directory, installed-profile or environment preference lookup. Opaque namespaces never install or execute a plugin. Changing configuration is itself non-exemptible authorization-sensitive work, so enabling the preference cannot authorize that same PR.

Compatibility: the new file, when present, is authoritative. Missing core/key then means false; legacy true must not fill holes or override false. Only when the new file is wholly absent may a bounded compatibility window read the old strict auto_merge boolean from a fully validated delivery authority file. Explicit adoption preserves other namespaces and all authority fields while removing only the migrated legacy preference. Kit defaults auto_merge false in new templates and preserves existing configuration during updates.

Implementation owner: Feature/ConfigurableAutoMerge owns delivery_policy.py, the guarded merge command and permission consumers. Its original native PID43300 and creation identity were reverified live on October10. A reader-only layer would be unconsumed; writing those consumers now would overlap its atomic source slice. Resume the Core configuration follow-on after that owner publishes its source slice or explicitly releases the affected paths. Then add the shared reader, migrate all behavioral consumers atomically, ship it to both hosts and preserve PR183's full authorized_stop_classes validation in the actual extracted validator. Follow with Kit allowance/template/check/update support and reviewed adoption in the twelve authorized tj-agents repositories.

Supplemental design evidence: C:/Users/TommySeery/source/repos/tj-agents/rust/.worktrees/Fix-RustStandardDiscovery/.agents/continuation/scalable-repo-configuration-design.json. This is a concrete design, not an implemented setting or normal-profile installation; Concertable configuration/activation remains outside this rollout.

## Selected parent-continuation prevention

The failure combined contradictory launcher instructions with a missing controller association. Core182 fixes the instruction cause for Claude and Codex. Core184 now blocks premature Stop for its supported event-checkout owner, but this session's canonical rollout owner lives in a separate Docs controller. A sparse route timestamp cannot authenticate that relationship. Successful side submission, pickup or delivery therefore cannot be treated as parent completion.

Accepted L1 design: add a token-validated associate-session operation to the existing shared continuation runtime, an exact-session keyed locator in the native checkout, and reciprocal owner metadata tied to native PID/creation identity and current lease generation. The locator is a lookup hint; Stop must authenticate the reciprocal controller before using its goal, binding and completion checks. Recheck generation at decision time, preserve the parent lease after side handoff, reject stale/forged/unrelated associations, and distinguish full-goal transfer from bounded side work. This does not relax base:cd or invent a native /cd interface.

Own the follow-on atomically in five source paths: continuation_runtime.py, continuation_stop.py, their two existing test files, and persistent-workflow/SKILL.md. Core184 publication is verified; wait for the heartbeat source writer's reviewed publication/release before assigning this overlapping runtime lease. No duplicate Stop/runtime writer, owner scan, daemon or configuration/authority expansion. Supplemental authenticated design evidence (the contract and matrix are maintained below): C:/Users/TommySeery/source/repos/tj-agents/rust/.worktrees/Fix-RustStandardDiscovery/.agents/continuation/controller-goal-stop-association-design.json, SHA2562642a0901375309d2d7a87b52a715d8e893bf8e8e8846325ca3ce57e92c082ba.

The proposed operation is `associate-session --owner CANONICAL_OWNER --token EXISTING_FOREGROUND_TOKEN --session-id HOST_SESSION_ID --session-cwd NATIVE_EVENT_CWD`; it is not currently available. Require the existing canonical root/owner lock, working state, exact current foreground token, live non-unknown PID creation identity and no competing child. Preserve goal, authority, lease and limits. Register one controller per resolved native cwd/session; exact repeat is idempotent and conflicting tuples cannot be forced.

Store a locator at `<native-cwd>/.agents/continuation/sessions/<sha256(session-id)>.json` and reciprocal optional owner `session_association`. Match session/cwd, canonical owner path/id, controller repo/worktree/branch/goal, originating PID/creation identity and lease generation derived from the token. Never expose the raw token. Serialize index then owner locks; write and read back both artifacts before success. Partial publication is unsuccessful and preserves the lease; a same-token/tuple retry may reconcile it. Locator storage is independent of temporary routing receipts and never constitutes authority alone.

Stop looks up only the current session locator, proves reciprocal identity plus genuine nearest native CLI PID/creation and session boundary, then uses the controller root for its owner, binding, completion and scheduler checks. Keep native cwd/session for user controls. An authenticated controller takes precedence over an unrelated local owner. Unproven/stale pointers retain local behavior without foreign-owner mutation; authentic but invalid controller state gates reconciliation. Recheck generation before decision with bounded reevaluation. Same-user filesystem/hook trust is the boundary; do not claim adversarial tamper resistance or recover a lost locator by scanning.

Successful token-authenticated yield/checkpoint marks the association released while retaining its originating provenance. A new claim invalidates its generation. Full transfer uses existing release/claim and distinct successor pickup proof. Bounded side handoff preserves the association and claim. A waiting Stop requires actual foreground/child release plus a matching enabled scheduler and observed wake; registration alone is insufficient. Explicit current-session pause/cancel controls retain precedence and suspension across status; quoted/foreign controls do not apply. Child nonce/result exceptions remain confined to the selected owner and never complete the parent.

Exact follow-on source paths: `.agents/workflows/continuation_runtime.py`, `.agents/hooks/continuation_stop.py`, `.agents/hooks/tests/test_continuation_runtime.py`, `.agents/hooks/tests/test_continuation_stop.py`, `.agents/engineering/workflow/persistent-workflow/SKILL.md`.

| Case | Required result |
| --- | --- |
| P1: Native root A has unrelated blocked/no-foreground owner; controller B has the exact parent claim and valid association; route receipt contains only routed_at. | Stop selects B, blocks foreground completion, leaves both owners/leases unchanged. |
| P2: P1 with missing receipt, malformed non-authoritative receipt, or unrelated read-only/status receipt. | The independent association still selects B; no route obligation is needed. |
| P3: Bounded side handoff submission followed by repeated Stop, including stop_hook_active; child succeeds or fails pickup. | Parent association/token survive and B continues to block while actionable/foreground-owned; side progress does not complete B. |
| P4: Valid same tuple registered twice with current token. | Idempotent association; no release/reclaim, no changed token/creation identity, no budget reset. |
| P5: Authenticated yield to waiting; no child; matching enabled scheduler action plus observed owner-matching wake. | Stop validates B's scheduler/root and permits ending. Positive native acceptance on Windows only at the pin; source adapter predicate may be injected on Linux without calling that native support. |
| P6: Associated complete owner with valid canonical completion evidence versus missing/open-task evidence. | Permit only verified full completion; rejected checkpoint/Stop leaves unfinished ownership intact. |
| P7: Documented genuine blocker and explicit direct Pause/Cancel/Stop; then Status and explicit Resume. | Existing genuine-gate and user-control behavior is honored, status retains suspension, resume re-enables enforcement. No synthetic completion or foreign owner mutation. |
| P8: External absolute goal with same-cwd owner and no association. | Current supported lifecycle continues unchanged. |
| N1: No association at all, including fresh local execution and ordinary read-only sessions. | Existing local Stop behavior remains; never search for a remote controller. |
| N2: Correct pointer but no matching reciprocal owner metadata; forged owner id/path/session/cwd/generation; copied pointer into another session. | No foreign owner adoption or mutation; local fallback. A locator alone supplies no blocking authority. |
| N3: Wrong token, missing foreground lease, unknown or dead creation identity, wrong state, or live competing child when registering. | associate-session fails without changing owner, foreground, goal or index authority. |
| N4: Unrelated live native process, PID reused with different creation identity, inaccessible identity, or nearer foreign CLI; both same-host and mixed-host nested sessions. | No inherited adoption of B. If nearest/native session identity cannot be proven by the supported host, report that capability limitation rather than weakening authentication. The existing same-executable check is not evidence of general mixed-host isolation; native acceptance must establish that additional case. |
| N5: Old index after yield/new claim, recreated owner with the same deterministic owner_id, or controller/session registration conflict. | Old generation cannot target the new writer; conflict is explicit and cannot be forced or treated as transfer. |
| N6: Foreign owner copied into local canonical file, aliased owner file, nested non-Git root, path traversal/symlink/junction redirection, case/separator variants. | Canonical path and true worktree-root checks remain. Normalize valid Windows paths while retaining Linux case sensitivity; aliases cannot impersonate a different canonical owner. |
| N7: Authentic association but changed controller repo/branch/head/binding, missing goal, or malformed owner state. | Gate reconciliation for the proven parent/controller; do not fall back to the unrelated root's blocked/complete owner. |
| N8: Working with no foreground, a merely missing/deleted lease, held foreground despite scheduler, or headless child still writing. | Stop blocks; absence of a lease is not proof of supported release. |
| N9: Waiting after release but scheduler receipt stale/disabled, wrong owner/path/root/action, wake missing or belonging to another owner. | Stop blocks until existing scheduler/wake gates are genuinely met. |
| N10: Linux waiting after release with only a Windows scheduler receipt at this pin. | Stop remains gated because scheduler_ready returns False off Windows; do not add a scheduler adapter in this follow-on. |
| N11: Pause/cancel appears in a quote, task output, another session, or another cwd; sparse receipt has no actual control. | Does not suspend this association. Explicit current user control still takes precedence over malformed runtime artifacts. |
| N12: Child has matching versus wrong nonce/result/owner triple; side child copies parent locator or only environment fields. | Existing supervised child exception applies only to its selected owner; parent association cannot be used to release/complete parent. |
| N13: Concurrent register attempts, partial owner/index writes, failed readback, index eviction or owner replacement between reads. | No false setup success, unauthorized target or lease loss; failed setup is explicit, one-sided evidence does not confer authority, snapshot/generation changes trigger bounded reevaluation. |
| N14: Same native session/cwd after full transfer with old index and actual successor claim. | Old association is invalidated; no enforcement of successor ownership against predecessor, no second writer, and transfer completion is not inferred from submission. |

Require both host Stop entries, repeated callbacks after successful and failed side pickup, sparse/missing receipts, lease reclaim/PID reuse, reciprocal path/identity conflicts, partial-write races and foreign-owner isolation. Positive controls require verified completion, explicit pause, or actual foreground release plus a matching observed registered wake. Linux native scheduler acceptance is unsupported at the inspected source; injected source tests cannot claim that acceptance. Normal-profile installation and live acceptance for both hosts remain a separate authorization boundary.

Heartbeat repair preserves the existing foreground lease while updating nonempty reason/next-action metadata after ownership checks. Its one native submission failed before pickup; exact native history and unchanged checkout justified recovering the unclaimed implementation via one sole L4 worker, without a second native launch. Parent owns frozen review and delivery after stable candidate release. No direct owner JSON edit or release/reclaim workaround.

The delivery-binding budget repair is independent of the live configuration owner's atomic preference/guard layer. It reuses invocation-local authenticated Git context, derives fresh origin once, keeps both fresh paginated GitHub reads and all state containment/revalidation checks, simplifies the Windows fixture dispatch, and strengthens the original held-label success oracle. Owned-tree timeout drainage in existing hook_runtime.py is a separate useful follow-on; the observed surviving child and unproven historical lock owner must not be conflated. The complete accepted repair design is in the Rust controller's shell-preparation-binding-budget-repair-design.json, SHA25690f7b96fd2dcfec844853fe0fe64497c42eeb930fa5a0be0daa2680c71cd8524.

## Next Steps

Scope: retain the whole authorized twelve-repository rollout and both-host requirement.
Current slice: qualify the recovered budget worker, diagnose heartbeat suite failures before review/delivery, and preserve paused extractor and live configuration owners.
Remaining scope: publish budget repair; qualify and land extractor preparation then native wiring; deliver authenticated parent Stop association and timeout drainage; migrate configuration after its owner publishes/releases, then deliver Kit support and reviewed twelve-repo adoption.
Done when: every authorized slice is delivered with truthful both-host evidence or has its concrete external/ownership gate, resolver and resume condition recorded; repository activation conditions are accounted for; the canonical terminal transition represents the whole goal.

Follow PROGRESS.md for exact executable actions. A completed phase, side handoff, open PR, started CI or source merge never completes this parent. Preserve Work1/Infonetica9 billing holds without retry or bypass. Preserve the live Feature/ConfigurableAutoMerge owner; lease expiry is not release. Only that exact owner can publish or durably release its paths; no verified profile/app-server transport is currently available. After source publication/release, implement the selected namespaced migration atomically and preserve Core183's full strict authorized_stop_classes validation.
