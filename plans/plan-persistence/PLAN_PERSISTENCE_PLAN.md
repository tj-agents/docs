# Durable plan persistence

## Status

Proposed implementation design. Its implementation-readiness verdict belongs to the companion progress record. Publication of this design does not approve implementation.

## Scope

Source repositories own implementation plans and operational documentation. tj-agents/docs owns global designs and cross-repository plans. Non-repository standalone tasks remain under their existing task-directory contract and are outside this repository-publication proposal; they do not need an invented repository owner. This plan proposes lifecycle rules only; it does not authorize runtime, policy, workflow or CI changes.

## Requirements

- Create every future plan and progress record, plus any associated roadmap changes, in its owning repository's existing ordinary main checkout. Commit, push and verify initial publication before implementation or handoff. Do not mandate a roadmap where the selected lifecycle does not require one; do not create a planning branch or worktree.
- Keep source implementation plans and roadmaps in their source repository. Implementation branches inherit the tracked local plan and progress; source repositories link to global designs in tj-agents/docs.
- Publish global docs plan amendments immediately to docs main. Publish substantive source-plan-only amendments immediately to the current canonical owner branch: source main before execution begins, then the active delivery branch during execution. When code accompanies a plan/progress update, include all of it in the same substantive commit. Do not maintain a parallel live copy on source main during delivery.
- Retain plans through intermediate PRs and until the entire outcome is implemented and verified. A failed or abandoned PR leaves its plan on main.
- In the final source implementation PR, remove the source-local plan and progress after verifying the whole outcome. Keep and tick the roadmap. The deletion reaches main when the final PR merges; do not require an impossible MERGED state before preparing that PR.
- Link global-plan retirement to the final implementation delivery, then delete the plan and progress in the owning docs repository. Keep and tick its roadmap.
- Serialize publishers, preserve unrelated working-tree and index contents, and stage only owned files. Use ordinary non-force pushes and verify remote ancestry and content. Failed publication preserves local commits and blocks dependent work or handoff. Keep transport receipts outside tracked plan content.

## Source evidence

As of 2026-10-09, base plan-artifacts assigns plans to source repositories or standalone task directories; engineering plans assigns active delivery branches to source ownership and docs-PR publication; plan-checkpoint correlates plans with source checkouts and forbids transport-only updates. Reconcile repository-owned plan publication while preserving the existing non-repository standalone task-directory contract, whole-plan retention, meaningful checkpoints and code-review gates.

The existing source-rooted RepositoryStateProvider, validate_checkpoint and _repository_path_key in [workflow_runtime.py](https://github.com/tj-agents/core/blob/main/.agents/workflows/workflow_runtime.py), source plan discovery in [workflow_ops.py](https://github.com/tj-agents/core/blob/main/.agents/workflows/workflow_ops.py), same-repository --root behavior in [plan_graph.py](https://github.com/tj-agents/core/blob/main/.agents/hooks/plan_graph.py), and source-local ledger selection in [plan_handoff_stop.py](https://github.com/tj-agents/core/blob/main/.agents/hooks/plan_handoff_stop.py) are valid defaults for source-owned plans. They are not defects in local-plan support. Any global-doc artifact resolution is a bounded separate concern; never weaken source containment or leases to implement it.

The v2 [state schema](https://github.com/tj-agents/core/blob/main/.agents/workflows/contract/v2/state.schema.json) rejects unknown fields and has no artifact-repository field. Do not repurpose existing path strings or require an external provider/schema change for local plans. Reuse the existing absolute-goal behavior in continuation_runtime.initialize/check_identity and its test test_absolute_external_goal_survives_claim_yield_repair_and_wake; see the [external-goal continuation plan](https://github.com/tj-agents/core/blob/main/plans/external-goal-continuation/EXTERNAL_GOAL_CONTINUATION.md). Link the sibling [standards-composition proposal](https://github.com/tj-agents/docs/blob/main/plans/standards-composition/STANDARDS_COMPOSITION_PLAN.md) for its existing planning and auto-merge ownership; do not create a second scheduler.

Inspected on 2026-10-09 in the core checkout at `6e2e2db3d1ad48e095ca5c2a9889f1cdfb92c8f5`: [.github/workflows/ci.yml](https://github.com/tj-agents/core/blob/6e2e2db3d1ad48e095ca5c2a9889f1cdfb92c8f5/.github/workflows/ci.yml) has a Linux PR generated-path guard, Windows verification, and Windows regeneration on main pushes, with no docs classifier. tj-agents/docs has no Actions workflows. The [merge skill](https://github.com/tj-agents/core/blob/6e2e2db3d1ad48e095ca5c2a9889f1cdfb92c8f5/.agents/engineering/workflow/merge/SKILL.md) places goal deletion in a later docs closeout after completion checking. [completion.py](https://github.com/tj-agents/core/blob/6e2e2db3d1ad48e095ca5c2a9889f1cdfb92c8f5/.agents/workflows/completion.py) reads the goal file and requires every declared delivery PR to be MERGED. [continuation_runtime.py](https://github.com/tj-agents/core/blob/6e2e2db3d1ad48e095ca5c2a9889f1cdfb92c8f5/.agents/workflows/continuation_runtime.py) rejects an absent goal in check_identity before completion checking. These are current behaviors, not the proposed retirement mechanism. finish.ps1 owns host/worktree cleanup through cleanup_proof.py, not plan deletion.

## Mechanism constraints

- Keep source-plan identity rooted in its owning source repository. A global plan directly consumed by a source workflow may need an approved docs-repository identity and repo-relative goal directory, distinct from execution identity (source repo, worktree, branch and PR). Design that integration only if needed; exact schema/provider fields and code examples remain open.
- Initial publication uses the owning repository's existing ordinary main checkout. Substantive source plan-only amendments publish immediately to the current canonical branch: source main before execution, then the active delivery branch during execution. When code accompanies the amendment, plan, progress and code share the same substantive commit. Global docs amendments publish immediately to docs main; no parallel live source-main plan copy is maintained during delivery.
- Serialize publishers and stage only owned plan, progress and roadmap files. Verify origin, branch, ancestry and artifact contents after a normal non-force push. Accept a harmless later remote commit only when ancestry and content still prove publication. Reconcile same-plan conflicts explicitly; failed/offline/non-fast-forward publication retains local work and blocks dependent work.
- Design a narrow, tested docs-only classifier allowlist for plans/** and qualifying prose docs/**, based on the full changed-file diff, not branch names. Evaluate the entire pushed range or PR merge-base and both paths of renames. Skip expensive jobs through conditional jobs while preserving cheap checks behind a required gate, so required checks do not remain pending. Mixed or behavior-affecting paths, and missing change evidence, run the required full validation. Exclude .agents/skills Markdown from any blanket docs exemption.
- Preserve code checks for mixed runtime, skills, schema, hooks and CI changes. Do not claim CI optimization is implemented.

## Delivery and retirement

For a source plan, pre-merge retirement eligibility checks implementation, E2E, CI, review, pending work, acceptance gates and other non-merge prerequisites. Re-read the plan and delivered heads; changed revisions or new work block preparing deletion. Do not require completion_check, which requires MERGED delivery PRs, as a pre-merge prerequisite. Include plan and progress deletion in the final implementation PR only after pre-merge checks pass; the plan remains on main until that verified PR merges. If pre-merge E2E or CI fails, the main plan remains intact and restoring plan/progress on the delivery branch before resumed work must be automatic. After merge, validate authenticated Git/receipt evidence for the merged delivery and goal state, with the continuation consumer updated for that state. If post-merge validation fails, restore canonical plan/progress in an authorized follow-up correction; deletion alone is never completion. Keep this lifecycle evidence distinct from cleanup_proof.py removable-worktree receipts. finish.ps1 remains responsible for post-merge host/worktree removal, not plan deletion; do not rewrite its default flow unless its receipt interface changes. Intermediate PRs retain the plan; failed or abandoned delivery leaves it on main. Keep and tick the roadmap.

A global docs plan is retired by its owning repository after final source delivery is verified. Link the docs deletion to that delivery because the source PR cannot delete a file in docs. This separate owner action applies only to global plans.

## Acceptance

Cover repository-owned source plans in owner main and global plans in docs main; retain the existing task-directory contract for non-repository standalone tasks; no planning branch/worktree; verified initial publication; immediate source plan-only publication on the current canonical branch; same-commit plan/progress/code updates when code accompanies them; unrelated dirty/staged file preservation; concurrent remote advance, same-plan conflict and failed transport; source-root containment and lease protection; pre-merge E2E/CI failure with automatic branch-plan restoration; post-merge authenticated goal-state validation and authorized plan/progress restoration on failure; deletion alone not completing work; intermediate/failed/abandoned PR retention and completed multi-PR closeout; linked global-plan retirement; diff-based docs-only CI with conditional jobs plus cheap required gate; and ordinary review/merge gates.

The CI classifier must test plan add/update/delete, prose-doc updates, mixed behavior paths, renames using both old and new paths, and missing-base/change evidence. Keep packaged and fresh-host evidence distinct from generation.

Test owners include test_workflow_contracts.py, test_plan_graph.py, test_plan_handoff_stop.py and ownership tests, test_plan_workflows.py, test_continuation_runtime.py, test_completion.py, plus persistence and CI-classifier tests under their declared owners.

## Ordered owner slices

1. Policy and ownership contract. Goal: align plan-artifacts, engineering plans and plan-checkpoint with owner-local plans, global designs, initial main publication and stable source-branch checkpoints. Validation: retention, checkpoint and review rules remain intact.
2. Owner-aware publication and closeout. Goal: design safe publication, pre-merge retirement eligibility, recovery on pre-merge and post-merge validation failures, and authenticated post-merge goal evidence. Validation: final-PR deletion cannot lose the main plan on failed checks, resumed work restores the branch copy automatically, and post-merge failures restore the canonical plan through authorized correction.
3. Bounded global-plan support. Goal: determine whether workflows need direct global artifact resolution and define its identity/provider contract without changing local-plan requirements. Validation: local containment and leases hold; canonical global artifacts cannot be replaced by source copies.
4. Docs-aware CI classification. Goal: classify the full changed-file diff and skip expensive jobs with conditional jobs plus a cheap required gate. Validation: full-range/merge-base and rename cases select checks correctly, including missing evidence and mixed changes; ordinary review and merge gates remain.
5. Focused tests and host acceptance. Goal: qualify workflow behavior, host packages and fresh-host enforcement. Validation: named tests pass and enforcement evidence is distinct from generation.

The mechanisms below resolve the previously open interfaces. These remain proposed design slices; this plan does not authorize runtime, workflow, host-removal or CI implementation.

## Implementation standards and ownership

All proposed implementation belongs to core. Before writing these examples, core README.md and AGENTS.md, the installed base:plan-artifacts, engineering:plans, engineering:plan-checkpoint, engineering:review-lifecycle and engineering:lanes contracts, and the current merge workflow were read. The core router was queried from the core checkout for the proposed paths; it reports no readable route table and no owed routed skills. The tier gate reports no applicable stack tier. This is an observed routing gap, not an exemption from core ownership or the global zero-comment default.

| Intended paths | Standards and responsibility |
| --- | --- |
| `.agents/base/policy/plan-artifacts/SKILL.md`, `.agents/engineering/convention/plans/SKILL.md`, `.agents/engineering/contract/plan-checkpoint/SKILL.md`, merge workflow | Their named lifecycle contracts; reconcile publication and retention without adding a second rule owner |
| `.agents/workflows/plan_publication.py`, proposed `plan_retirement.py`, `completion.py`, `continuation_runtime.py`, `workflow_ops.py`, persistent-workflow/scripts/delivery-continuation.ps1 | Core AGENTS.md/README.md; existing repository containment, writer leases, portable v2 contract, continuation lock and host scheduler ownership |
| `.agents/hooks/plan_graph.py`, `plan_handoff_stop.py`, their tests | Core ownership; retain ordinary local graph validation and add only lifecycle-aware retirement entry points |
| Proposed `scripts/classify_docs_changes.py`, `tests/test_classify_docs_changes.py`, `.github/workflows/ci.yml` | Core authored-source/generated-output boundary; existing CI jobs and generated-path guard |
| `.agents/plugins/manifests/{codex,claude}/engineering*.json`, `.agents/plugins/sources.json` | Core packaging declarations; any new shipped utility, schema or hook must be included and tested in the same slice |

No code below is installed. Python examples are proposed deciding logic; referenced existing helpers retain their present signatures. Named new helpers have explicit contracts below. Owning implementation plans are to be created in core after authorization and linked to this global design; no source implementation plan exists for these slices yet.

## Publication transaction

Proposed owner: `plan_publication.py`, invoked by planning/checkpoint workflows. The synchronous input is repository root, canonical branch, operation (`initial`, `plan-only` or `mixed`), literal owned paths, expected path contents and reviewed candidate identity. The result is `published`, `conflict` or `transport-blocked`, with local commit, observed remote head, per-path Git object IDs and a private receipt path. Only `published` permits implementation, dependent work or handoff. Receipts live under the common Git directory's `agent-workflow/plan-publication/`; they never enter Markdown.

For initial publication, resolve the primary checkout from the first `git worktree list --porcelain -z` record and require that actual existing checkout to be on ordinary `main`, with an origin matching the declared owner. Do not create a checkout, switch an unrelated branch, or stash/reset user work. Initial paths include the plan, progress and associated roadmap changes. For a source amendment, resolve the single live ledger owner: main before execution, active delivery branch during execution. A docs amendment always targets ordinary docs main. Mixed changes use the delivery workflow's declared owned code and artifact paths in one substantive commit; they never call the plan-only committer to split the amendment from its code.

Acquire a repository-wide publisher OS lock using continuation_runtime.locked on `<common-git-dir>/agent-workflow/plan-publication`, then the existing writer lease for the exact paths in that checkout. Every automated publisher uses this same lock directory, including publishers in linked worktrees. A busy lock returns a retryable conflict; it does not steal a lease or launch a second publisher. Resolve symlinks/junctions and reject escape paths with `_repository_path_key`; reject unmerged index entries and in-progress Git operations. Freeze HEAD, branch, origin URL, owned worktree hashes and unrelated staged entries before committing. Recheck these under the lock immediately before commit.

Use normal Git hooks and literal pathspecs. Git's [commit --only](https://git-scm.com/docs/git-commit) leaves other staged paths out of the commit and retains them in the index. The deciding commit/publication sequence is:

```python
import subprocess


def git(root, *args):
    return subprocess.run(
        ["git", "--literal-pathspecs", *args], cwd=root,
        capture_output=True, check=True,
    ).stdout


def commit_owned(root, paths, message):
    git(root, "add", "--", *paths)
    git(root, "commit", "--only", "-m", message, "--", *paths)
    return git(root, "rev-parse", "HEAD").decode().strip()


def verify_publication(root, branch, candidate, paths):
    tracking = f"refs/remotes/origin/{branch}"
    git(root, "fetch", "origin", f"refs/heads/{branch}:{tracking}")
    remote = git(root, "rev-parse", tracking).decode().strip()
    git(root, "merge-base", "--is-ancestor", candidate, remote)
    difference = git(root, "diff", "--name-only", "-z", candidate, remote, "--", *paths)
    if difference:
        raise RuntimeError("remote owned artifacts differ from candidate")
    return remote


def push_owned(root, branch, candidate, paths):
    git(root, "push", "origin", f"{candidate}:refs/heads/{branch}")
    return verify_publication(root, branch, candidate, paths)
```

Before push, verify the commit's actual changed paths are a subset of the declared owned set, each owned Git blob/mode matches frozen intent, and unrelated staged entries and worktree bytes still match their saved signatures. Unexpected hook changes or concurrent edits preserve the commit and return conflict; they do not publish it. No `add .`, `commit -a`, force push, stash, or unrelated index reset is allowed. An absent owned artifact is represented by an absent tree entry, so deletion is verified too.

Fetch before commit and require the observed remote tip to be an ancestor of local HEAD, with every outgoing change owned and reviewed. A remote advance before push can reject the normal push; retain the local commit and return conflict. Reconciliation belongs to the same publisher owner: compare both versions, preserve unrelated dirt, integrate remote changes only when Git can do so without disturbing it, and explicitly resolve same-plan conflicts before a fresh review and retry. If integration cannot preserve the dirty index/worktree, stop at this conflict and await that checkout owner's reconciliation; do not hide it with autostash. A later remote commit after successful push is accepted only when candidate ancestry and exact owned content still prove publication, as in verify_publication. Offline/auth/verification failures return transport-blocked and keep local commits. Repeated transport observations do not generate commits.

## Source retirement contract

Proposed owner: `plan_retirement.py`, with a versioned private `plan-retirement/v1` record under `<common-git-dir>/agent-workflow/plan-retirement/<goal-key>/`. This record is separate from Workflow v2 state, transport receipts and cleanup_proof.py. Exact fields are: version, repository, goal_key, goal_path, progress_paths, roadmap_path, roadmap_item, snapshot_commit, snapshot_entries (path, blob, mode), final_delivery (repository, pr), candidate_head (nullable until deletion is committed), default_branch, phase, and recovery_authority. Unknown fields, invalid relative paths, duplicate paths and non-regular snapshot entries fail validation. Recovery authority records the original authorized outcome and permitted source correction; a record cannot grant permission.

`prepare` takes the active repository/lease and declared final PR identity and returns a durable snapshot record before touching tracked files. `bind` seals the deletion head into that record. `validate` returns fresh authenticated goal bytes plus delivery evidence, or an explicit blocker. `restore` returns the restored canonical paths and correction head, or a conflict. Calls are synchronous and lease-bound; no consumer treats a JSON `phase` value alone as proof. Operations are idempotent only at identical identities and object hashes.

| Phase | Entry and allowed behavior |
| --- | --- |
| active | Canonical plan/progress exist; normal provider and completion behavior |
| prepared | Whole outcome and all non-merge prerequisites verified at snapshot commit C; durable snapshot saved; no deletion yet |
| retiring | Deletion commit D bound; final PR still open; goal remains on main; only verify, delivery observation or restore may run without a worktree goal |
| merged-unverified | Forge reports exact D merged at M on owner main; validate outcome, merge, publication/sync and deletion state |
| retired | Fresh completion and post-merge goal validation pass; cleanup may consume its existing receipt interface |
| recovery-required | Any invalidation; restore before normal execution, then rebind and re-review the corrected candidate |

Snapshot C must contain the final verified goal/progress and completed acceptance evidence. Re-read the plan, every delivery head, review, E2E, CI, pending work and acceptance gates immediately before preparation. Earlier deliveries must already be MERGED. The final delivery need only be OPEN at the authorized head with green non-merge prerequisites; do not call the existing MERGED-only completion_check to prepare deletion. If new work or changed goal/delivery/evidence is observed, preparation fails. Commit any substantive acceptance/progress correction with its implementation before capturing C; never manufacture a transport-only snapshot commit.

Persist the exact Git objects reachable from C in a private Git bundle and record their object identities before deleting anything; flush/atomically replace the record and verify the bundle. Bind additionally archives D before sealing it, so the original PR's history remains recoverable after squash/rebase and branch cleanup. The directory key is SHA-256 of the canonical repository slug, one NUL byte, and the validated repository-relative goal path; it does not depend on worktree location. Snapshot entries cover exactly goal, progress and roadmap paths. This preserves recovery without requiring a second live plan or adding an archive to source main. Bind D only when its sole parent is C and the C..D diff consists exactly of the declared goal/progress deletions and the correct roadmap tick. No runtime edits or other plan changes may occur in D. The same final implementation PR includes C and D and still runs required E2E/CI and review against D; a passing C cannot stand in for a passing final head.

Under the existing lease and retirement lock, create the private ref at C for prepare, and at D for bind. An existing ref is idempotent only at the same object; never replace a different retained proof. [Git bundles require a named ref](https://git-scm.com/docs/git-bundle), so the concrete archive operation uses a runtime-private ref, not a planning branch:

```python
import os
import uuid


def archive_retirement(root, directory, key, phase, commit):
    ref = f"refs/agent-workflow/plan-retirement/{key}/{phase}/{commit}"
    lookup = subprocess.run(["git", "rev-parse", "--verify", ref], cwd=root, capture_output=True)
    old = lookup.stdout.decode().strip() if lookup.returncode == 0 else "0" * 40
    if old not in {"0" * 40, commit}:
        raise CompletionError("retirement archive ref changed")
    git(root, "update-ref", ref, commit, old)
    temporary = directory / f".{uuid.uuid4().hex}.bundle"
    git(root, "bundle", "create", str(temporary), ref)
    git(root, "bundle", "verify", str(temporary))
    with temporary.open("r+b") as stream:
        os.fsync(stream.fileno())
    target = directory / f"{phase}-{commit}.bundle"
    os.replace(temporary, target)
    return target
```

Directory, phase and commit are validated before this helper. Save the flushed record only after the archive succeeds. Recovery imports the bundle into private object/ref storage, then rechecks its named head, C/D relationship and snapshot entries against authenticated forge evidence; neither a filename nor bundle validity establishes delivery. Retain both archives and private refs through failed correction and until authenticated retirement and host cleanup no longer need them.

### Completion and continuation integration

Current completion entry point being extended:

```python
body, document = completion_document(goal)
acceptance, deliveries, pending, open_tasks = validate_document(document)
```

Refactor that parser into `completion_document_text(body)` and retain completion_document(path) as its file-reading wrapper. Retain the existing completion JSON schema and all acceptance, visible-task, open-task and forge checks. Add a `completion_check_text(body, bound_delivery, root, final_delivery=None)` entry point for validated snapshots. The deciding normalization occurs only for retirement:

```python
import copy


def bind_final_delivery(document, repository, pr, head):
    result = copy.deepcopy(document)
    matches = [item for item in result["deliveries"]
               if item["repository"] == repository and item["pr"] == pr]
    if len(matches) != 1:
        raise CompletionError("retirement requires one declared final delivery")
    matches[0]["head"] = head
    return result
```

The loader must validate the original document first. Its final entry's recorded head must be a real ancestor of C in that final PR's history. Replace only that entry's head in memory with authenticated D. This resolves the self-reference problem: a tracked document cannot contain its own future deletion commit SHA. Every other delivery retains its exact recorded head and MERGED requirement. Normal live-goal completion never performs substitution. The snapshot must contain no unchecked goal tasks or unresolved acceptance/open tasks.

`validate_retirement(root, record, forge)` refreshes the final PR through authenticated `gh` or the existing forge provider and returns `{body, final_delivery, merge_commit, snapshot_commit}` only after all of these checks:

1. Origin, root, lease/continuation owner, goal key and repository match; final PR number and head equal the sealed record. Fetch PR objects or load the saved Git bundle into repository-private object storage; prove C is D's parent and each saved blob/mode matches C. The bundle is recovery storage; Git object relationships and fresh forge identity are the proof.
2. Final PR state is MERGED and its mergeCommit.oid is M. Fetch owner main and prove M is an ancestor of its current tip; this works for merge, squash and rebase delivery. Missing M or unavailable authenticated forge evidence blocks completion.
3. Compare the inspected C..D closure diff and the goal/progress absence plus roadmap tick in M and current main. Check the final PR's delivered file content against D for every affected implementation/artifact path, accounting for base changes. A conflicting merge, restored goal, changed final head or reopened work invalidates retirement.
4. Revalidate exact-head reviews/checks/E2E and all acceptance evidence; then run completion_check_text with the authenticated final binding and require ready. Publication and causally owned downstream sync must be terminal too. A snapshot hash or deleted file cannot satisfy these gates.

Within validate_retirement, the following Git proof runs after strict record validation and loading its authenticated final PR. `paths` contains all affected final-PR paths from its merge-base diff plus the closure artifacts; all paths have already passed repository containment. `forge` is a refreshed PR document with number, headRefOid, state and mergeCommit.oid, obtained by a new retirement forge adapter. The current completion.forge_state only requests number/head/state/body and must remain compatible; it cannot supply this merge proof unchanged.

```python
import re


def roadmap_line(root, revision, record):
    body = git(root, "show", f"{revision}:{record['roadmap_path']}").decode("utf-8")
    token = f"`{record['roadmap_item']}`"
    lines = [line for line in body.splitlines() if token in line]
    if len(lines) != 1 or not re.match(r"^- \[[ xX]\] ", lines[0]):
        raise CompletionError("retirement roadmap item is missing or ambiguous")
    return lines[0]


def verified_snapshot(root, record, forge, paths):
    final = record["final_delivery"]
    candidate = record["candidate_head"]
    snapshot = record["snapshot_commit"]
    if (forge["number"] != final["pr"] or forge["headRefOid"] != candidate
            or forge["state"] != "MERGED"):
        raise CompletionError("retirement delivery identity or merge changed")
    merge = forge["mergeCommit"]["oid"]
    tracking = f"refs/remotes/origin/{record['default_branch']}"
    git(root, "fetch", "origin", f"refs/heads/{record['default_branch']}:{tracking}")
    remote = git(root, "rev-parse", tracking).decode().strip()
    git(root, "merge-base", "--is-ancestor", merge, remote)
    ancestry = git(root, "rev-list", "--parents", "-n", "1", candidate).decode().split()
    if ancestry != [candidate, snapshot]:
        raise CompletionError("retirement snapshot parent changed")
    before = roadmap_line(root, snapshot, record)
    if not before.startswith("- [ ] "):
        raise CompletionError("retirement roadmap item was already complete")
    expected = before.replace("- [ ] ", "- [x] ", 1)
    if any(roadmap_line(root, revision, record) != expected
           for revision in (candidate, merge, remote)):
        raise CompletionError("retirement roadmap transition changed")
    content_paths = [path for path in paths if path != record["roadmap_path"]]
    if git(root, "diff", "--name-only", "-z", candidate, merge, "--", *content_paths):
        raise CompletionError("merged affected content differs from verified head")
    for path in [record["goal_path"], *record["progress_paths"]]:
        for revision in (candidate, merge, remote):
            if git(root, "ls-tree", "-z", revision, "--", path):
                raise CompletionError("retired artifact is present")
    entries = {entry["path"]: entry for entry in record["snapshot_entries"]}
    for path, entry in entries.items():
        blob = git(root, "rev-parse", f"{snapshot}:{path}").decode().strip()
        if blob != entry["blob"]:
            raise CompletionError("snapshot object differs from record")
    return git(root, "show", f"{snapshot}:{record['goal_path']}").decode("utf-8")
```

Git nonzero exits and malformed/missing forge fields become explicit completion blockers at the boundary. The prepare/bind adapter additionally verifies modes and the exact closure path set before this reader is reachable. The item comparison includes current main while permitting unrelated roadmap items to change. If main advanced on an affected implementation path after M, rerun the acceptance gates for the current state or enter recovery; equality at M alone cannot approve a changed outcome.

Proposed consumer wiring in continuation_runtime.check_identity and apply_receipt is deliberately narrow:

```python
def canonical_goal(state, root, record):
    goal = Path(state["goal"])
    if goal.is_absolute() and goal.is_file() and goal.resolve() == goal:
        return goal.read_text(encoding="utf-8"), None
    if record is None or record["phase"] not in {"retiring", "merged-unverified", "retired"}:
        raise Gate("canonical-goal-unavailable")
    verified = validate_retirement(root, record, retirement_forge_state)
    return verified["body"], verified["final_delivery"]


def complete_retiring_goal(state, root, record):
    body, final_delivery = canonical_goal(state, root, record)
    if final_delivery is None:
        raise Gate("retirement-completion-requires-verified-delivery")
    result = completion_check_text(body, final_delivery, root, final_delivery=final_delivery)
    if not result["ready"]:
        raise Gate("completion-unverified: " + "; ".join(result["blockers"]))
    return result
```

Keep current repo/worktree/branch/head and delivery-binding checks before this loader. Extract them unchanged into `check_execution_identity`; `check_identity` calls it and then requires either a live canonical goal or a valid local retirement record whose current owner, C/D closure and freshly fetched PR identity match. That preliminary retirement check permits an OPEN final PR and does not certify completion. Resolve the record deterministically from the existing absolute goal path and repository identity; do not add arbitrary goal paths or artifact fields to portable v2 state.

In wake, after the existing writer/deadline checks and check_identity but before ordinary observe/launch, call the deciding dispatcher below. `retirement_observation` validates that preliminary identity and returns `wait` for an OPEN PR with checks still pending/green, `restore` for failed/ejected/closed-unmerged or new work, and `merged` for the exact merged PR. Invalid/unavailable authentication raises Gate and cannot authorize a child. `restore_before_repair` restores the snapshot's goal/progress into the existing checkout under the existing writer lease and reverses only the owned roadmap tick, preserving HEAD and its delivery binding until the repair context makes the combined restoration/repair commit. It rejects newer owned contents and unauthorized recovery. The repair then uses the existing apply_receipt rebind.old/rebind.new mechanism for its new head.

```python
def wake_goal(state, root, record):
    if Path(state["goal"]).is_file():
        return True
    action = retirement_observation(root, state, record)["action"]
    if action == "wait":
        transition(state, "waiting", "retirement-delivery-pending", "Verify final delivery")
        return False
    if action == "restore":
        restore_before_repair(root, state, record)
        transition(state, "waiting", "retirement-goal-restored", "Repair and rebind delivery")
        return True
    if action == "merged":
        complete_retiring_goal(state, root, record)
        transition(state, "complete", "authenticated-goal-retirement")
        return False
    raise Gate("retirement-observation-invalid")
```

The wake caller returns immediately when this returns False; it cannot fall through to launch. launch also independently requires the live canonical goal, as a backstop. In apply_receipt's `status == complete` branch, retain completion_check for a live goal with its original bound delivery, and call complete_retiring_goal for an absent goal. A retiring OPEN PR never calls the MERGED-only loader. Post-merge validation failure enters the corrective-owner path below rather than this before-merge restore helper. Initialization still requires an actual goal file; fresh recovery of a deleted goal first reconstructs its retirement record from the recorded final PR and authenticated snapshot objects. If those are unavailable, restore the prior main goal and re-evaluate the outcome; never guess completion. Existing scheduler and foreground writer ownership remain unchanged.

Workflow v2 RepositoryStateProvider and graph validation remain source-rooted and require live artifacts for normal resolve/checkpoint. Retiring operations consume the separate typed record rather than resolve an absent ledger. Plan-handoff stop/wake adapters may suppress a missing-artifact error only for an authenticated retiring delivery, route to verify/restore, and retain their lease checks. Reusing an absolute external goal is already supported by continuation initialization; this proposal adds no external-ledger provider.

### Recovery and owner closeout

Before-merge failure restores goal/progress from C into the existing delivery checkout under its writer lease, reverses only this retirement's roadmap tick, commits that restoration with the repair where applicable, and rebinds the delivery/continuation to the new head before resumed work. Invalidation clears the sealed retirement candidate; a later retirement needs fresh preparation. A crash after deletion but before bind is recovered only when HEAD has parent C and the exact closure diff; otherwise restore or return conflict. Preserve newly edited/restored paths rather than overwriting them. Main still retains the goal because the failed final PR has not merged.

After-merge validation failure sets recovery-required, blocks completion and cleanup, and restores goal/progress in the canonical owner through an authorized corrective source PR. Recovery is part of the approved implementation outcome when that authority exists; otherwise record a human authorization gate while preserving the snapshot. Restore the affected roadmap item to incomplete. Include the failed acceptance/next action in the restored progress. Fetch current main, avoid overwriting a newer canonical goal, re-review and run checks on the correction, and retain recovery storage until the correction lands. Network failure preserves recovery state and blocks terminal claims. No force push, branch rewind or unconditional write is permitted.

Post-merge correction uses terminal release followed by fresh initialization, not the existing same-PR head rebind. Under the old continuation owner lock, first authenticate the old repo/worktree/branch/head and merged PR, require no live child/foreground writer, persist the failed acceptance and snapshot pointer, transition that owner to `blocked` with reason `retirement-recovery-transferred`, and save it without marking the outcome complete. The current Windows delivery-continuation remove operation unregisters its scheduled task; strengthen that operation to verify absence before discarding its receipt, as shown below. A failed release leaves the correction unscheduled and retains the old state; never register two active owners. Core currently supplies no non-Windows scheduler adapter: such a host keeps foreground recovery ownership and cannot claim autonomous corrective pickup without its own separately authorized adapter.

Then select a corrective checkout from current owner main under git-branching, restore the canonical artifacts and failed next action, commit/publish the correction and bind its new PR identity. Only then run the existing continuation `init` against that actual restored goal and correction checkout. Preserve the original outcome/authority and remaining launch, failure and deadline budgets; exhausted budgets require renewed authority rather than resetting them. The new owner ID follows existing initialization's repo/worktree/goal fingerprint. Record its actual owner-state path and new delivery identity in the old private recovery record after verified pickup; an interrupted release-before-init is resumable from the retained snapshot and unscheduled old owner. No portable v2 fields change, and the old owner's branch/PR checks remain intact.

The separate private recovery.json has a strict `plan-retirement-recovery/v1` shape: version, retirement_record_path, failed_acceptance (criterion IDs and evidence locators), previous_owner (owner_id, owner_path, repository, worktree, branch, head, pr), next_owner (null until pickup, then the same fields), phase (`release-pending`, `released`, `picked-up`), and remaining_budget (launches, failures, absolute deadline). Derive authority from the original validated owner/retirement record; this file cannot extend it. Persist release-pending before stopping the old owner, released only after scheduler absence, and picked-up only after new init/binding/register evidence. Re-entry validates these identities and completes the unfinished step without duplicating registration.

The deciding release order, inside the proposed recovery adapter, is:

```python
def release_for_correction(owner_path, state, recovery_path, recovery, scheduler_script):
    if any(record and alive(record) for record in writer_records(state)):
        raise Gate("retirement-recovery-writer-still-alive")
    recovery["phase"] = "release-pending"
    atomic_json(recovery_path, recovery)
    transition(state, "blocked", "retirement-recovery-transferred", "Initialize authorized corrective delivery")
    save(owner_path, state, "retirement-recovery-release")
    subprocess.run(
        ["powershell.exe", "-NoProfile", "-NonInteractive", "-ExecutionPolicy", "Bypass",
         "-File", str(scheduler_script), "remove", "-OwnerPath", str(owner_path),
         "-Reason", "retirement recovery transfer"], check=True,
    )
    recovery["phase"] = "released"
    atomic_json(recovery_path, recovery)
```

Resolve scheduler_script through the existing packaged helper/registration identity, never an arbitrary record command. In the existing Remove-OwnedTask, retain its receipt/task identity checks and ShouldProcess guard, and require the following absent-task check before deleting scheduler.json. Also apply that check to its no-receipt return path so a missing receipt with a remaining deterministic task blocks release. It uses the already derived taskName; no second task-name implementation is introduced.

```powershell
if (@(Get-ScheduledTask -TaskName $taskName -TaskPath '\' -ErrorAction SilentlyContinue).Count) {
    throw 'Continuation task removal is unverified; preserve recovery and registration evidence.'
}
```

Recovery identity/authority and the old merged delivery must be validated before release_for_correction. New init/register is a separate subsequent action after correction binding; it cannot be hidden inside remove. Repeating release is idempotent; repeating init requires the same correction identity and authority. Add tests for a changed PR, failed task removal, a crash between release and init, old-writer liveness, finite-budget exhaustion, and verified new-owner pickup. finish.ps1 and its cleanup receipt are unaffected by this bounded scheduler-release verification.

For this global design, core deliveries use source-local execution plans linked here. Once all declared core deliveries and host qualification pass, docs owns a separate linked deletion of this plan/progress and ticks its roadmap. Docs closeout validates the source retirement evidence and final source delivery identities before its own publication. It cannot occur merely because a source PR merged. The global plan stays open until all owner slices ship. finish.ps1 and cleanup_proof.py keep their host/worktree interface; the merge workflow must establish authenticated goal retirement before invoking them, and preserve the recovery bundle outside any removed worktree.

## Docs-aware CI contract

Proposed owner: `scripts/classify_docs_changes.py`. Synchronous CLI input is the GitHub event JSON and checked-out repository; output is JSON and an Actions output `docs_only=true|false`, with base/head and a reason. No current implementation exists. A malformed/missing event, unknown event, absent objects, zero base, ambiguous merge-base, empty diff or malformed path record selects full validation. Ordinary classifier test failures fail the cheap job and block the required gate.

Push compares event.before to event.after after proving before is an ancestor of after; it examines the entire pushed range, never HEAD^. PR compares the unique merge-base of the event base/head to the event head. Fetch those exact objects, not a moving branch name. Checkout must be the event after/head; a mismatch blocks classification. When a repository enables merge queues, add merge_group and compare its base_sha to head_sha; until supported, unknown events select full validation. Core currently has no merge_group trigger, so do not claim queue coverage is installed.

The initial allowlist is regular Markdown below `plans/` and the exact prose debt file `docs/workflows/TECH_DEBT.md`. Other prose docs require an explicit classifier allowlist change with tests and review. All `.agents/`, skills, schemas, hooks, package metadata, README/AGENTS, generated distribution, scripts and CI changes select full validation. Inspect modes and both old/new names in `git diff --raw -z --no-abbrev --find-renames <base> <head>`; symlinks, submodules and type changes are full-validation paths. Classify renames and copies only if both paths qualify. A rename into plans from a behavior path remains full validation.

The proposed deciding parser/classifier is complete for raw diff records:

```python
from pathlib import PurePosixPath
import re


def allowed_prose(path):
    parts = PurePosixPath(path).parts
    return (
        bool(parts) and path == PurePosixPath(path).as_posix()
        and ".." not in parts and not path.startswith("/")
        and "\\" not in path
        and path.endswith(".md")
        and (parts[0] == "plans" and len(parts) > 1
             or path == "docs/workflows/TECH_DEBT.md")
    )


def docs_only(raw):
    if not raw or not raw.endswith(b"\0"):
        return False
    fields = raw[:-1].split(b"\0")
    count = 0
    try:
        while fields:
            header = fields.pop(0).decode("ascii").split()
            if len(header) != 5 or not header[0].startswith(":"):
                return False
            old_mode, new_mode, old_oid, new_oid, status = header
            if any(mode not in {"000000", "100644", "100755"}
                   for mode in (old_mode[1:], new_mode)):
                return False
            if (status[0] not in "AMDRC"
                    or any(not re.fullmatch(r"[0-9a-f]{40}", oid)
                           for oid in (old_oid, new_oid))):
                return False
            names = [fields.pop(0).decode("utf-8")]
            if status[0] in "RC":
                if not status[1:].isdigit() or not 0 <= int(status[1:]) <= 100:
                    return False
                names.append(fields.pop(0).decode("utf-8"))
            elif len(status) != 1:
                return False
            if not all(allowed_prose(name) for name in names):
                return False
            count += 1
    except (IndexError, UnicodeError):
        return False
    return count > 0
```

The event-to-diff caller uses the Git byte-returning helper shown in publication. It requires a unique merge-base for PRs and an ancestor range for pushes; fetching or parsing failures select full validation:

```python
import re


def classify_event(root, name, event):
    try:
        if name == "push":
            base, head = event["before"], event["after"]
        elif name == "pull_request":
            base = event["pull_request"]["base"]["sha"]
            head = event["pull_request"]["head"]["sha"]
        else:
            return False
        if any(not isinstance(sha, str) or not re.fullmatch(r"[0-9a-f]{40}", sha)
               or sha == "0" * 40 for sha in (base, head)):
            return False
        if git(root, "rev-parse", "HEAD").decode().strip() != head:
            return False
        git(root, "fetch", "origin", base, head)
        if name == "pull_request":
            bases = git(root, "merge-base", "--all", base, head).decode().splitlines()
            if len(bases) != 1:
                return False
            base = bases[0]
        else:
            git(root, "merge-base", "--is-ancestor", base, head)
        raw = git(root, "diff", "--raw", "-z", "--no-abbrev", "--find-renames", base, head)
        return docs_only(raw)
    except (KeyError, TypeError, ValueError, OSError, subprocess.CalledProcessError):
        return False
```

The CLI writes exactly one lowercase boolean output and its JSON diagnostic; unknown/missing change evidence returns `false` with a zero exit code so full verification runs. Test failure or an unhandled internal error exits nonzero and cannot grant an exemption.

Preserve existing trigger coverage and job steps. Add a cheap classification/docs job which runs classifier tests, plan_graph, whitespace checks and the existing PR generated-path guard; that guard remains enforced for every PR, including mixed ones. Fetch depth is zero. Use trusted base/default classifier code for PR classification so PR edits cannot exempt themselves; classifier/workflow changes already select full validation. No pull_request_target execution of candidate code or write credentials in PR jobs.

Conditional wiring around the existing core verify/regenerate jobs:

```yaml
jobs:
  classify:
    runs-on: ubuntu-latest
    outputs:
      docs_only: ${{ steps.classify.outputs.docs_only }}
    steps:
      - uses: actions/checkout@v4
        with:
          fetch-depth: 0
          persist-credentials: false
          ref: ${{ github.event_name == 'pull_request' && github.event.pull_request.head.sha || github.sha }}
      - uses: actions/checkout@v4
        if: github.event_name == 'pull_request'
        with:
          ref: ${{ github.event.pull_request.base.sha }}
          path: .ci-base
          persist-credentials: false
      - id: classify
        env:
          CLASSIFIER_ROOT: ${{ github.event_name == 'pull_request' && '.ci-base' || '.' }}
        run: |
          classifier="$CLASSIFIER_ROOT/scripts/classify_docs_changes.py"
          if [ -f "$classifier" ]; then
            python3 -B "$classifier" --root . --event "$GITHUB_EVENT_PATH" --output "$GITHUB_OUTPUT"
          else
            echo 'docs_only=false' >> "$GITHUB_OUTPUT"
          fi
      - run: python3 -B -m unittest discover -s tests -p test_classify_docs_changes.py
      - run: python3 -B .agents/hooks/plan_graph.py --root .
  verify:
    needs: classify
    if: needs.classify.outputs.docs_only != 'true'
    runs-on: windows-latest
  regenerate:
    needs: [classify, verify]
    if: github.event_name == 'push' && needs.classify.outputs.docs_only != 'true' && needs.verify.result == 'success'
    runs-on: windows-latest
  gate:
    needs: [classify, guard, verify, regenerate]
    if: always()
    runs-on: ubuntu-latest
    env:
      EVENT: ${{ github.event_name }}
      DOCS_ONLY: ${{ needs.classify.outputs.docs_only }}
      CLASSIFY: ${{ needs.classify.result }}
      GUARD: ${{ needs.guard.result }}
      VERIFY: ${{ needs.verify.result }}
      REGENERATE: ${{ needs.regenerate.result }}
    steps:
      - shell: bash
        run: |
          test "$CLASSIFY" = success
          if [ "$EVENT" = pull_request ]; then test "$GUARD" = success; fi
          if [ "$DOCS_ONLY" = true ]; then
            test "$VERIFY" = skipped
            test "$REGENERATE" = skipped
          else
            test "$VERIFY" = success
            if [ "$EVENT" = push ]; then test "$REGENERATE" = success; fi
          fi
```

This is job-dependency wiring, not a replacement workflow: existing guard and full verify/regenerate steps, credentials, permissions and regeneration concurrency remain. The second checkout pins PR classification to its trusted base revision while the first pins the examined tree to the candidate head. On the first classifier PR, that base has no classifier: the classify step must explicitly emit `docs_only=false` when the trusted script is absent and continue the full checks; subsequent PRs use the installed script. Install `ci / gate` as the branch-protection required check only after a full-validation trial proves failure/cancellation propagation; replace any old required full-job checks that would otherwise defeat docs skips. GitHub documents [workflow-level skip pending checks and always()/needs behavior](https://docs.github.com/en/pull-requests/how-tos/merge-and-close-pull-requests/troubleshooting-required-status-checks). No workflow-level paths filter or skip marker is part of this design.

Docs has no authored runtime or CI today. Any docs-repository cheap validation workflow is a separate owner-local CI change requiring authorization, not a dependency on core's full matrix or copied core tooling. Documentation publication now uses available local checks and review; it does not claim installed CI protection.

## Delivery map and verification

After explicit implementation authorization, create and publish core's source-local execution plan/progress and associated roadmap change from its existing ordinary main checkout before branching. Use the following sequential PR slices, each based on refreshed core main; allocate a checkout only for the active slice. Expected sizes are estimates, not permission to detach required tests.

| Slice | Contract delivered and dependency | Estimated authored change | Required validation |
| --- | --- | --- | --- |
| 1. Ownership/publication | Reconciled policy and publication CLI/receipts; callers publish before execution/handoff; no runtime retirement activated | 5–10 files, 300–600 lines | Publication temp-repository tests; retention/checkpoint contracts; dirty index/worktree, lock contention, remote advances and transport failures |
| 2. Retirement consumers and recovery | Record schema, prepare/bind/validate/restore plus completion/continuation/merge/stop adapters delivered atomically; depends on 1 | 10–18 files, 600–1,200 lines | completion, continuation, workflow, graph, handoff and ownership tests; all state transitions, final-head invalidation and restoration cases |
| 3. CI classification | Tested classifier and cheap gate with conditional existing jobs; depends on 1; no new provider or scheduler | 3–6 files, 200–450 lines | Add/update/delete, prose allowlist, whole multi-commit push, merge-base, modes, both rename paths, missing evidence, failed/cancelled/skipped job combinations; controlled full/docs PR and main-push trials |
| 4. Host qualification and global closeout | Package declarations shipped with each capability; test fresh hosts against owner-local/global-linked goals, then docs retirement | Owner qualification records and focused tests | Packaged dependency closure, fresh-host trust/write probes, source-local containment/leases, no duplicate continuation; verified linked docs closeout |

Slice 2 may split inactive parser/record primitives from activation if necessary, but deletion cannot activate until every consumer and recovery path ships together. Slice 3 is independent of retirement internals; sequential delivery keeps one live source ledger. Slice 4 does not substitute source generation for package or fresh-host enforcement evidence. Runtime tests are proposed gates, not checks executed during this docs design task.

The failure matrix must additionally cover: initial publication with an unrelated staged file; same-plan remote edits; harmless remote advance after push; failure after commit before transport; missing bundle/record; crash between deletion and bind; D CI/E2E failure or queue ejection; closed-unmerged PR; repair attempted with absent goal; intermediate multi-PR delivery; squash/rebase merge; forged/stale head or merge proof; missing authenticated API access; post-merge acceptance failure and correction authority; newer main goal on restoration; deleted goals never independently completing work; standalone tasks still using their task directory; and source execution linked to a global plan without a copied global ledger.

## Readiness

The bounded design chooses owner-local Workflow v2 state, normal Git publication, a separate Git-backed retirement contract with authenticated consumers and restoration, global designs linked from source execution plans, and full-diff CI selection behind a cheap required gate. The independent implementation-design review verdict and snippet validation are recorded in the companion progress artifact. Nothing here is shipped.

The next decision belongs to Tommy: approve core implementation of the proposed publication/retirement/CI slices, or request a design change. On approval, the first execution action is to create and verify publication of core's owner-local implementation plan, with the slice map and tests above, from its ordinary main checkout. Host qualification and global retirement remain part of the full outcome; approving publication of this document alone authorizes none of those runtime changes.
