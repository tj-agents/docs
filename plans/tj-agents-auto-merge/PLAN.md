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
        "evidence": "Core183 generic five-class source capability, Core182 both-host handoff contracts, and Core184 shared Stop mechanism are merged with exact PR and causal main CI. Native enforcement c007490 remains changes-requested for SD08/SD10/SD11; 244 tests with9 skips passed, while one unchanged Windows wiring subcase timed out. Extractor preparation is paused for a reproduced generic binder timeout on exact base. Budget repair is bounded to a separate checked source goal; heartbeat source is released from the collaboration writer, while archived qualification and the resumed native candidate require parent reconciliation. Neither native-gate publication nor repository configuration activation is complete."
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
        "evidence": "Core183 generic five-class source capability, Core182 both-host handoff contracts, and Core184 shared Stop mechanism are merged with exact PR and causal main CI. Native enforcement c007490 remains changes-requested for SD08/SD10/SD11; 244 tests with9 skips passed, while one unchanged Windows wiring subcase timed out. Extractor preparation is paused for a reproduced generic binder timeout on exact base. Budget repair is bounded to a separate checked source goal; heartbeat source is released from the collaboration writer, while archived qualification and the resumed native candidate require parent reconciliation. Neither native-gate publication nor repository configuration activation is complete."
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

Authoring gate: parent /root owns this global design and must promote the deciding mechanisms below into a Core-owned configuration implementation plan, then publish its immutable Git/PR reference. That execution plan is not yet promoted. The live Feature/ConfigurableAutoMerge owner must first publish or explicitly release its atomic paths. No scratch artifact is an execution or recovery prerequisite; the contract, path mapping, compatibility decisions and acceptance conditions in this document are the recoverable design.

### Configuration mechanism examples and implementation standards

### Intended paths and standards read

| Proposed implementation area | Applicable source actually read |
| --- | --- |
| Core `.agents/workflows/repository_configuration.py`, `delivery_policy.py`, `delivery_runtime.py`, `workflow_ops.py`, `auto_merge.py`; hook `.agents/hooks/delivery_binding_gate.py`; machine `.agents/machine/utility/bootstrap-capabilities/scripts/harness_permissions_sync.py` | Core root [AGENTS.md](https://github.com/tj-agents/core/blob/8b656fb197771916c58aea4418934aaa7648b1c0/AGENTS.md), [CODE_CONVENTIONS.md](https://github.com/tj-agents/core/blob/8b656fb197771916c58aea4418934aaa7648b1c0/CODE_CONVENTIONS.md), [PACKAGING.md](https://github.com/tj-agents/core/blob/8b656fb197771916c58aea4418934aaa7648b1c0/PACKAGING.md), and README layout/runtime prerequisite |
| Core `.agents/schemas/repository-configuration.schema.json`, `docs/workflows/REPOSITORY_CONFIGURATION.md`, `.agents/hooks/tests/test_repository_configuration.py`, affected existing tests, `.agents/plugins/sources.json`, persistent-delivery contract | Same Core root instructions and packaging; Python conventions for tests; installed `engineering:plans`, `engineering:lanes` and `base:plan-artifacts` for deciding examples/readiness |
| Kit `.agents/kit/utility/check/standard.json`, `check/scripts/check.py`, `new-plugin/templates/repository/.agents/configuration.json.in`, `update/scripts/update.py`, `.agents/tests/test_check.py`, `test_new_plugin.py` | Published Kit root [AGENTS.md](https://github.com/tj-agents/kit/blob/28b551300c54061801b2c68b2b5fecd5efd7bbc1/AGENTS.md), plus actual checker, standard, template renderer and updater contracts at that pin; global zero-comment instruction |
| Generated package/host output | Core PACKAGING and AGENTS: explicit canonical mappings, installed-relative dependencies, authored sources only; Kit AGENTS: template-first edits, generation/checks and release rules |

Read-only `skill_router.py --skills-for <intended paths>` queries in both repositories returned “no readable .agents/skill-routes.json … no skill is owed”. Missing route tables are normal, not a defect; declared instructions and applicable tier conventions still govern. The source-tree ancestor scan found only Core `.agents/plugins/harness/AGENTS.md`, outside these proposed paths; Kit has only its root AGENTS. Kit has no CODE_CONVENTIONS.md or PACKAGING.md. No stack/product convention is inferred from repository identity.

### Generic reader: no current implementation; proposed Core module

Use Python 3.9+ and the standard library. Caller supplies the actual absolute checkout root. Return `(configuration, absent)`; `namespace` returns the opaque object or an empty object. A missing path is distinct from an existing unreadable file/directory/dangling link. Duplicate keys and non-JSON constants fail even inside future namespaces. The loader has no authority, namespace-owner registry, repository slug, ancestor/profile/environment search or plugin activation.

```python
import json
import re
from pathlib import Path


ABSENT = object()


class ConfigurationViolation(ValueError):
    pass


def unique_object(pairs):
    result = {}
    for key, value in pairs:
        if key in result:
            raise ConfigurationViolation(f"duplicate JSON key: {key}")
        result[key] = value
    return result


def invalid_constant(value):
    raise ConfigurationViolation(f"invalid JSON constant: {value}")


def read_document(path):
    try:
        path.lstat()
    except FileNotFoundError:
        return ABSENT
    except OSError as error:
        raise ConfigurationViolation(f"{path}: {error}") from error
    try:
        return json.loads(path.read_text(encoding="utf-8"),
                          object_pairs_hook=unique_object,
                          parse_constant=invalid_constant)
    except (OSError, UnicodeError, ValueError) as error:
        raise ConfigurationViolation(f"{path}: {error}") from error


def validate_envelope(document):
    if not isinstance(document, dict) or set(document) != {
        "schema_version", "configuration"
    }:
        raise ConfigurationViolation("expected schema_version and configuration")
    if type(document["schema_version"]) is not int or document["schema_version"] != 1:
        raise ConfigurationViolation("schema_version must be integer 1")
    configuration = document["configuration"]
    if not isinstance(configuration, dict):
        raise ConfigurationViolation("configuration must be an object")
    for name, value in configuration.items():
        if not re.fullmatch(r"[a-z][a-z0-9-]*", name) or not isinstance(value, dict):
            raise ConfigurationViolation(f"invalid namespace: {name!r}")
    return configuration


def load(root):
    root = Path(root)
    if not root.is_absolute():
        raise ConfigurationViolation("checkout root must be absolute")
    document = read_document(root / ".agents" / "configuration.json")
    return ({}, True) if document is ABSENT else (validate_envelope(document), False)


def namespace(configuration, name):
    return configuration.get(name, {})
```

The proposed schema documents the open envelope; the runtime and Kit reader retain the decisive strict version-type check, using integer `const: 1`, required envelope keys, no additional envelope keys, and namespace `patternProperties` with object values and no unmatched names. Do not add Core's internal fields to the generic schema. Runtime explicit `type(...) is int` excludes Python booleans; JSON Schema's integer type also excludes booleans. Future namespace contents remain opaque and unchanged.

### Core resolver, absent-only compatibility and authority composition

Current feature code in `delivery_runtime.StandingMergeAuthorization.resolve` reads `auto_merge = policy.get("auto_merge", False)`; `workflow_ops.standing_authorization` directly returns its authority resolution. Its permission and direct-hook consumers independently parse legacy authority. Those preference reads are replaced. The inspected current deciding statements, in their respective existing function bodies, are:

```python
auto_merge = policy.get("auto_merge", False)
return delivery_runtime.StandingMergeAuthorization().resolve(policy, changed_paths, labels)
```
 Keep authority resolution pure and attach the effective preference in the caller.

Proposed additions in `delivery_policy.py` below use the existing `PolicyViolation` and `validate(policy)`. Place the module-loading statements after the existing PolicyViolation definition. Load the generic sibling from the same package, including when the machine consumer loads this policy module by file specification; do not rely on the caller's import path. The existing validator retains all instruction/mode/path/label/strict legacy-boolean checks. Before its existing return, call the new stop-class helper and allow `authorized_stop_classes` in its actual `AUTHORIZATION_KEYS`. This composes Core183 into the feature's extracted validator. Insert this exact call immediately before validate's existing return:

```python
validate_authorized_stop_classes(policy)
```

```python
import importlib.util
from pathlib import Path

reader_path = Path(__file__).with_name("repository_configuration.py")
reader_spec = importlib.util.spec_from_file_location(
    "core_repository_configuration", reader_path)
if reader_spec is None or reader_spec.loader is None:
    raise PolicyViolation(f"configuration reader unavailable: {reader_path}")
repository_configuration = importlib.util.module_from_spec(reader_spec)
reader_spec.loader.exec_module(repository_configuration)

AUTHORIZATION_KEYS.add("authorized_stop_classes")
EXEMPTIBLE_STOP_CLASSES = frozenset({
    "ci-workflow", "migration", "auth", "money", "published-contract"})


def validate_authorized_stop_classes(policy):
    entries = policy.get("authorized_stop_classes", [])
    if not isinstance(entries, list) or any(not isinstance(x, str) for x in entries):
        raise PolicyViolation("authorized_stop_classes must be a list of strings")
    if len(set(entries)) != len(entries) or set(entries) - EXEMPTIBLE_STOP_CLASSES:
        raise PolicyViolation("authorized_stop_classes must be unique known classes")
    if entries and policy["standing_authorization"] not in {"auto", "merge"}:
        raise PolicyViolation("authorized_stop_classes requires auto or merge")


def read_authority(root):
    try:
        policy = repository_configuration.read_document(
            Path(root) / ".agents" / "delivery-authorization.json")
    except repository_configuration.ConfigurationViolation as error:
        raise PolicyViolation(str(error)) from error
    return None if policy is repository_configuration.ABSENT else validate(policy)


def effective_auto_merge(root):
    try:
        configuration, absent = repository_configuration.load(root)
    except repository_configuration.ConfigurationViolation as error:
        raise PolicyViolation(str(error)) from error
    if absent:
        policy = read_authority(root)
        return False if policy is None else policy.get("auto_merge", False)
    core = repository_configuration.namespace(configuration, "core")
    if set(core) - {"auto_merge"}:
        raise PolicyViolation("configuration.core contains unknown fields")
    value = core.get("auto_merge", False)
    if type(value) is not bool:
        raise PolicyViolation("configuration.core.auto_merge must be a boolean")
    return value
```

Only a wholly absent new file reaches legacy fallback, and the entire legacy authority policy must pass the composed validator. Present empty configuration/core or missing key gives false; new false beats legacy true. Present invalid input raises before fallback. A new true is only preference: invalid/absent authority still fails the authority gates. Preserve all other authority fields and opaque namespaces during explicit adoption; remove only legacy auto_merge. Reads never write. The compatibility release window remains bounded; removal release requires consumer inventory, not an invented date.

Proposed complete `workflow_ops.standing_authorization` replaces its current read/return body. Existing imports supply `delivery_runtime` and `WorkflowOperationError`; obtain the same policy resolver through `delivery_runtime.delivery_policy`, which the feature runtime already imports.

```python
def standing_authorization(root, changed_paths, labels):
    policy_module = delivery_runtime.delivery_policy
    try:
        policy = policy_module.read_authority(root)
        absent = policy is None
        if absent:
            policy = {"standing_authorization": "absent", "instruction": None,
                      "hold_label": "human-gate"}
        resolution = delivery_runtime.StandingMergeAuthorization().resolve(
            policy, changed_paths, labels)
        if absent and resolution["stopped_by"] is None:
            resolution["stopped_by"] = {"class": "no-recorded-authorization"}
        resolution["auto_merge"] = policy_module.effective_auto_merge(root)
        return resolution
    except (policy_module.PolicyViolation,
            delivery_runtime.DeliveryContractViolation) as error:
        raise WorkflowOperationError(str(error)) from error
```

Runtime retains its validated authority/stop resolution; replace its preference read with the following statement so only this caller attaches the effective value:

```python
auto_merge = False
```

Preserve Core183's filtering of authorized exemptible classes and custom repository stops. Replace only the existing non-exemptible standing-authorization tuple's regex with:

```python
("standing-authorization", re.compile(
    r"(?:^|/)delivery-authorization\.json$|^\.agents/configuration\.json$"))
```

Neither standing-authorization, repository-declared nor hold-label can be exempted. Preference edits therefore cannot authorize their own unattended merge.

The following deciding current `auto_merge.current_authorization` lines remain the proposed lines; no guard replica is added. Its fresh call now receives the attached preference:

```python
resolution = workflow_ops.standing_authorization(root, changed, labels)
if not binding["auto_merge"] or resolution["auto_merge"] is not True:
    raise AutoMergeError("repository auto_merge is not enabled")
```

Retain the surrounding scoped-approval restrictions, current-authority/binding equality, hold and path stops; `arm` keeps exact local identity, fresh PR identity/green exact head, current review and `--match-head-commit`. Current false or invalid configuration rejects arming even when the saved binding says true.

### All behavioral consumers and packaged dependency

Proposed direct-hook `auto_merge_enabled` uses the runtime's already imported policy module. Its caller's existing ValueError handler reports errors and blocks direct auto merge.

```python
def auto_merge_enabled(root):
    policy_module = delivery_runtime.delivery_policy
    enabled = policy_module.effective_auto_merge(root)
    return policy_module.read_authority(root) is not None and enabled
```

For the hook's existing `from delivery_runtime import ...` imports, add `import delivery_runtime` beside them after the existing package path setup. This does not change the wrapper, trust or direct-command gates.

Machine's current `auto_merge_enabled(project)` reads legacy JSON, validates, then returns `policy.get("auto_merge") is True`. Proposed replacement retains the existing `policy_validator()` helper, inspected at the feature pin: it loads delivery_policy from the plugin's own resource root (or canonical source root for source tooling). It does not search another plugin. Pass the existing warnings list at its one call in `auto_merge_roots`:

```python
def auto_merge_enabled(project, warnings):
    if project is None:
        return False
    validator = policy_validator()
    if validator is None:
        warnings.append("auto-merge permissions: packaged resolver unavailable")
        return False
    try:
        enabled = validator.effective_auto_merge(project)
        return validator.read_authority(project) is not None and enabled
    except validator.PolicyViolation as error:
        warnings.append(f"auto-merge configuration: {error}")
        return False
```

Use `auto_merge_enabled(project, warnings)` in the existing early guard. Invalid configuration yields an explicit diagnostic and no conditional grant; the normal permission reconciliation removes formerly derived grants. Preserve exact-root guarded wrapper grants, enabled/applicable installed-plugin and trusted publisher/package-byte verification, safe root checks, both-host renderers and existing permission validation.

Engineering already maps `.agents/workflows` to `workflows`. Add this resource item beside machine's existing delivery_policy mapping in `.agents/plugins/sources.json`:

```json
{"plugin": "machine",
 "source": ".agents/workflows/repository_configuration.py",
 "destination": "resources/machine/scripts/repository_configuration.py"}
```

Both hosts use each owning plugin's generated copy of the same canonical reader/resolver bytes. No author-checkout dependency or runtime cross-plugin lookup. Keep generated plugins uncommitted in Core; verify both host layouts and installed-relative sibling loading. The present-new-file resolver reads preference only. The hook and permission caller examples explicitly retain their current requirement for a present, fully validated delivery authority document: both call read_authority, which uses the composed shared validate function. At the inspected feature pin, delivery_binding_gate.auto_merge_enabled calls StandingMergeAuthorization().validate_policy(policy), and harness_permissions_sync.auto_merge_enabled calls validator.validate(policy); both reject a missing document. The proposed callers preserve those checks for present new configuration too. A valid policy with standing_authorization absent still passes structural validation and grants no merge authority. workflow_ops.standing_authorization also calls read_authority, and the unchanged guarded current_authorization checks actual standing/scoped authority and binding equality. Legacy fallback independently uses that same full validator; neither preference true nor a wrapper permission replaces these authority gates. Update persistent-delivery and the new reference document with the preference/authority boundary.

### Published Kit allowance, scaffold and update preservation

At the published pin, standard agents_files already includes delivery-authorization.json. Proposed standard adds configuration.json to that allowance; it is optional, not root_files and not vendored. The proposed scaffold template has no placeholder:

```json
{"schema_version": 1, "configuration": {"core": {"auto_merge": false}}}
```

Current `new_plugin.plan` recursively visits every repository `*.in`; this exact loop already picks up the new template, so no renderer change is required:

```python
for source in sorted((TEMPLATES / "repository").rglob("*.in")):
    sources.append((source, PurePosixPath(
        source.relative_to(TEMPLATES / "repository").as_posix())))
```

Current `vendored_files` iterates the explicit VENDORED tuple only; configuration is absent from that tuple. Current update iterates only `new_plugin.vendored_files(...)` and updates kit.json's version afterward. Preserve both loops unchanged. Thus the false template creates config only in a new scaffold, while default update neither touches existing authored bytes nor inserts an absent envelope that would disable legacy true. No create-if-missing adoption option is introduced in this slice.

For optional generic validation in `check.py`, use a Kit-owned local implementation of the complete generic reader block above, with identical structural helpers and no Core import or Core field validation. No registry or dependency on installing Core. Add this helper and `problems += check_configuration(root)` after the existing check_agents_entries call:

```python
def check_configuration(root):
    try:
        load(root)
    except ConfigurationViolation as error:
        return [f".agents/configuration.json: {error}"]
    return []
```

Kit accepts any well-shaped namespace object, including future Core fields that Core's consumer may reject. Add checker/scaffold/preservation tests in the existing Kit test files; use their temporary rendered repository fixtures. Template-first and Kit release rules apply if generator, vendored files or workflow change. No generator discovery or vendored-file change is required for this configuration template.

### Follow-on acceptance and scope limits

Focused Core tests belong in the proposed `.agents/hooks/tests/test_repository_configuration.py` and affected existing runtime, hook, auto-merge, workflow, permission-sync and source-layout tests. Required cases: identical producer/unrelated-consumer roots; arbitrary nested namespaces; absent versus present empty/missing/false/true; strict bool and integer rejection; duplicates, unknown envelope/core keys, unsupported version, malformed/unreadable/directory/dangling path; separate worktree preferences and paths with spaces/non-ASCII on Windows/Linux. Test absent-only legacy fallback through the complete composed authority validator, including all Core183 stop-class failures. Test no fallback on new errors, authority absent with preference true, changed preference after binding, and preference-edit stops even with all five exemptions. Exercise every real consumer and generated own-package copy on both hosts.

Kit tests must prove allowance is optional, malformed envelope fails, future namespaces/internal fields are accepted, new scaffolds render false, and update preserves exact authored config bytes (true/false plus unknown namespaces) and absence, including legacy true. Package checks cover shipped reader/resolver byte identity, both generated host layouts and trust gates; source acceptance does not prove profile activation.

The deciding examples were syntax-checked with `ast.parse`; JSON blocks were decoded for syntax only. No snippets are executed; no runtime suites, live probes, profile installation, source edits, publication, Goal promotion or owner/native-session changes are authorized by this artifact. Parent must incorporate the deciding mechanisms into the current canonical design and Core-owned plan before source handoff. The syntax result is reported with the artifact hash to the parent.

## Selected parent-continuation prevention

The failure combined contradictory launcher instructions with a missing controller association. Core182 fixes the instruction cause for Claude and Codex. Core184 now blocks premature Stop for its supported event-checkout owner, but this session's canonical rollout owner lives in a separate Docs controller. A sparse route timestamp cannot authenticate that relationship. Successful side submission, pickup or delivery therefore cannot be treated as parent completion.

Accepted L1 design: add a token-validated associate-session operation to the existing shared continuation runtime, an exact-session keyed locator in the native checkout, and reciprocal owner metadata tied to native PID/creation identity and current lease generation. The locator is a lookup hint; Stop must authenticate the reciprocal controller before using its goal, binding and completion checks. Recheck generation at decision time, preserve the parent lease after side handoff, reject stale/forged/unrelated associations, and distinguish full-goal transfer from bounded side work. This does not relax base:cd or invent a native /cd interface.

Own the follow-on atomically in five source paths: continuation_runtime.py, continuation_stop.py, their two existing test files, and persistent-workflow/SKILL.md. Core184 publication is verified; wait for the heartbeat source writer's reviewed publication/release before assigning this overlapping runtime lease. No duplicate Stop/runtime writer, owner scan, daemon or configuration/authority expansion. Authoring gate: parent /root must promote this embedded association contract and deciding mechanisms into a Core-owned implementation plan after heartbeat qualification/publication and source release, then publish an immutable Git/PR reference. No Core execution plan has been promoted yet; do not execute from a controller scratch draft.

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

### Standards and owned APIs

All five paths inherit the actually read global `C:/Users/TommySeery/AGENTS.md`, [Core AGENTS.md](https://github.com/tj-agents/core/blob/8b656fb197771916c58aea4418934aaa7648b1c0/AGENTS.md), and [Core CODE_CONVENTIONS.md](https://github.com/tj-agents/core/blob/8b656fb197771916c58aea4418934aaa7648b1c0/CODE_CONVENTIONS.md). Checked filesystem ancestors and relevant Core subdirectories contain no additional AGENTS.md. The exact five-path `skill_router.py --skills-for` invocation returned no readable local route table. Absence of that table is normal; the repository still owes its tier conventions. The declared owners below were read explicitly.

| Planned path | Additional read owner or test standard |
| --- | --- |
| [.agents/workflows/continuation_runtime.py](https://github.com/tj-agents/core/blob/8b656fb197771916c58aea4418934aaa7648b1c0/.agents/workflows/continuation_runtime.py) | [engineering:persistent-delivery](https://github.com/tj-agents/core/blob/8b656fb197771916c58aea4418934aaa7648b1c0/.agents/engineering/policy/persistent-delivery/SKILL.md) and [engineering:persistent-workflow](https://github.com/tj-agents/core/blob/8b656fb197771916c58aea4418934aaa7648b1c0/.agents/engineering/workflow/persistent-workflow/SKILL.md). |
| [.agents/hooks/continuation_stop.py](https://github.com/tj-agents/core/blob/8b656fb197771916c58aea4418934aaa7648b1c0/.agents/hooks/continuation_stop.py) | The same persistence owners; this hook's existing process identity, native controls, completion, blocker, supervised-child and scheduler/wake contracts. |
| [.agents/hooks/tests/test_continuation_runtime.py](https://github.com/tj-agents/core/blob/8b656fb197771916c58aea4418934aaa7648b1c0/.agents/hooks/tests/test_continuation_runtime.py) | The same persistence owners; Core cross-platform disposable-fixture rules and this file's `ContinuationTests`/`self.cli`/`self.state`/`mock` pattern. |
| [.agents/hooks/tests/test_continuation_stop.py](https://github.com/tj-agents/core/blob/8b656fb197771916c58aea4418934aaa7648b1c0/.agents/hooks/tests/test_continuation_stop.py) | The same persistence owners; Core cross-platform disposable-fixture rules and this file's `ContinuationStopTests`/`self.owner`/`self.write_owner`/`patch` pattern. |
| [.agents/engineering/workflow/persistent-workflow/SKILL.md](https://github.com/tj-agents/core/blob/8b656fb197771916c58aea4418934aaa7648b1c0/.agents/engineering/workflow/persistent-workflow/SKILL.md) | [engineering:skill-authoring](https://github.com/tj-agents/core/blob/8b656fb197771916c58aea4418934aaa7648b1c0/.agents/engineering/convention/skill-authoring/SKILL.md), [engineering:docs-and-debt](https://github.com/tj-agents/core/blob/8b656fb197771916c58aea4418934aaa7648b1c0/.agents/engineering/convention/docs-and-debt/SKILL.md), and the persistence owners. |

The installed engineering 2.1.16 plans entry/canonical convention and base 2.1.16 plan-artifacts owner were read; the [pinned plans mechanism gate](https://github.com/tj-agents/core/blob/8b656fb197771916c58aea4418934aaa7648b1c0/.agents/engineering/convention/plans/SKILL.md) was also inspected. This artifact applies their code/example requirements without reproducing their rules. The accepted base:cd and lane boundaries remain.

Reused existing runtime APIs, inspected at [runtime.py](https://github.com/tj-agents/core/blob/8b656fb197771916c58aea4418934aaa7648b1c0/.agents/workflows/continuation_runtime.py#L26): `read(path)`, `git(root, *args)`, `locked(directory)` yielding a nonblocking-acquisition boolean, `check_identity(state, allow_terminal_release=False)`, `process_identity(pid)`, `alive(record)`, `writer_records(state)`, `operate(path,state,args)`, and `parser()`. `atomic_json(path,value)` is already imported from [workflow_ops.py](https://github.com/tj-agents/core/blob/8b656fb197771916c58aea4418934aaa7648b1c0/.agents/workflows/workflow_ops.py#L227): UTF-8 same-directory replacement with Windows sharing retries. It does not refresh foreground activity or owner progress. Existing `save` still persists lifecycle changes after `operate`.

Reused hook APIs are the [inspected hook](https://github.com/tj-agents/core/blob/8b656fb197771916c58aea4418934aaa7648b1c0/.agents/hooks/continuation_stop.py#L14)'s `workflow_root()`, `module(name,root)`, `read_json(path,required=False)`, `foreground_owns_current_process(owner,runtime)`, `supervised(owner)`, `read_receipt(session)`, and `direct_control(prompt)`. The one mechanical rename below defines `owner_outcome` from the exact pinned existing `outcome`; it hides no new gate implementation.

### Registration, ordering and publication

Current runtime has no association command. Its existing main validates canonical owner/Git roots and locks only the owner; its claim generates a new token and its yield/checkpoint clear foreground directly. New registration lives in the same runtime module and uses its existing imports.

```python
def associate_session(path, token, session, cwd):
    path, native = Path(path), Path(cwd)
    if (not path.is_absolute() or path != path.resolve()
            or not native.is_absolute() or native != native.resolve()
            or not isinstance(session, str) or not session.strip()):
        raise Gate("canonical-owner-and-native-session-required")
    directory = native / ".agents/continuation/sessions"
    locator = directory / (hashlib.sha256(session.encode("utf-8")).hexdigest() + ".json")
    if directory != directory.resolve() or locator != locator.resolve():
        raise Gate("session-locator-redirected")
    if Path(git(native, "rev-parse", "--show-toplevel")).resolve() != native:
        raise Gate("canonical-native-worktree-required")
    with locked(directory) as indexed:
        if not indexed:
            raise Gate("session-association-lock-busy")
        with locked(path.parent) as acquired:
            if not acquired:
                raise Gate("owner-lock-busy")
            state = read(path)
            if (not isinstance(state, dict) or not isinstance(state.get("owner_id"), str)
                    or not state["owner_id"]):
                raise Gate("owner-identity-invalid")
            root = Path(state["worktree"])
            expected = root / ".agents/continuation/owner.json"
            if (not root.is_absolute() or root != root.resolve()
                    or path != expected or expected.parent != expected.parent.resolve()
                    or Path(git(root, "rev-parse", "--show-toplevel")).resolve() != root):
                raise Gate("canonical-owner-path-required")
            check_identity(state)
            lease = state.get("foreground")
            if (state.get("state") != "working" or not isinstance(lease, dict)
                    or not isinstance(token, str) or not token
                    or token != lease.get("token") or type(lease.get("pid")) is not int
                    or not 0 < lease["pid"] < 2**31
                    or lease.get("identity") in (None, "unknown")
                    or process_identity(lease["pid"]) != lease["identity"]):
                raise Gate("foreground-session-identity-invalid")
            if any(record and alive(record) for record in writer_records(state)):
                raise Gate("headless-writer-already-owned")
            values = {
                "session_id": session, "session_cwd": str(native),
                "owner_path": str(path), "owner_id": state["owner_id"],
                **{key: state[key] for key in ("repo", "worktree", "branch", "goal")},
                "pid": lease["pid"], "identity": lease["identity"],
                "generation": hashlib.sha256(token.encode("utf-8")).hexdigest(),
            }
            current = state.get("session_association")
            if current is None:
                binding = dict(values, created_at=time.time())
            else:
                binding = current.get("binding") if isinstance(current, dict) else None
                if (not isinstance(binding, dict)
                        or current.get("released") is not False
                        or set(binding) != set(values) | {"created_at"}
                        or type(binding["created_at"]) not in (int, float)
                        or not 0 < binding["created_at"] < float("inf")
                        or any(binding[key] != value for key, value in values.items())):
                    raise Gate("owner-session-association-conflict")
            try:
                previous = read(locator)
            except FileNotFoundError:
                previous = None
            if previous is not None and previous != binding:
                stable = ("session_id", "session_cwd", "owner_path", "owner_id",
                          "repo", "worktree", "branch", "goal")
                if (not isinstance(previous, dict) or set(previous) != set(binding)
                        or any(previous[key] != binding[key] for key in stable)
                        or not isinstance(previous["generation"], str)
                        or len(previous["generation"]) != 64
                        or any(c not in "0123456789abcdef" for c in previous["generation"])
                        or previous["generation"] == binding["generation"]
                        or type(previous["pid"]) is not int or not 0 < previous["pid"] < 2**31
                        or not isinstance(previous["identity"], str)
                        or previous["identity"] in ("", "unknown")
                        or type(previous["created_at"]) not in (int, float)
                        or not 0 < previous["created_at"] < float("inf")):
                    raise Gate("native-session-controller-conflict")
            if current is None:
                state["session_association"] = {"binding": binding, "released": False}
                atomic_json(path, state)
            if previous != binding:
                atomic_json(locator, binding)
            if read(path) != state or read(locator) != binding:
                raise Gate("session-association-readback-mismatch")
            return {key: binding[key] for key in
                    ("owner_id", "owner_path", "session_id", "session_cwd", "generation")}
```
The immutable binding is repeated in the locator and owner; only the owner's release marker changes at yield/checkpoint. The locator is a hint until owner reciprocal, session/cwd and native process all prove it. The token-derived generation does not publish the token. Registration lock order is always native index then owner; normal lifecycle paths keep only the owner lock and never request the index. It refuses a foreign controller tuple. A successor token may replace only a structurally valid prior generation for the same stable owner/session/controller identity.

Owner replacement precedes locator replacement. Either write/readback failure leaves the foreground claim intact; an identical authenticated retry repairs an owner-only publication and preserves created_at. A successful identical repeat writes neither file. Until both readbacks succeed, setup is incomplete; nobody may claim Stop protection or pickup from that partial state.

Add this standalone subparser after the existing subparser loop, before `return result`:

```python
p = subs.add_parser("associate-session")
p.add_argument("--owner", required=True)
p.add_argument("--token", required=True)
p.add_argument("--session-id", required=True)
p.add_argument("--session-cwd", required=True)
```
Insert the following in current `main` after the `_child` special case, before `args.root` access or the general owner lock:

```python
if args.operation == "associate-session":
    result = associate_session(
        Path(args.owner), args.token, args.session_id, args.session_cwd
    )
    print(json.dumps(result, sort_keys=True))
    return 0
```
### Claim and true release

Keep the existing claim checks and token creation. Immediately after assigning the new foreground and before transition/save, invalidate the prior reciprocal:

```python
state.pop("session_association", None)
```
Define this helper in the same runtime module:

```python
def release_foreground(state):
    lease = state["foreground"]
    association = state.get("session_association")
    if association is not None:
        binding = association["binding"]
        if (association["released"] is not False
                or binding["pid"] != lease["pid"]
                or binding["identity"] != lease["identity"]
                or binding["generation"] != hashlib.sha256(lease["token"].encode()).hexdigest()):
            raise Gate("foreground-session-generation-invalid")
        association["released"] = True
    state["foreground"] = None
```
Replace the existing `state["foreground"] = None` assignment in each yield/checkpoint branch with `release_foreground(state)`. Preserve the enclosing token/alive check, yield transition, checkpoint receipt construction and `apply_receipt` validation, then the existing common save. Keep the independently maintained heartbeat branch intact. Thus release marker and cleared foreground reach one atomic owner replacement; failed checks never save. Claim's new token plus removed reciprocal makes the old locator inert without requiring an index lock.

### Stop selection and the existing gate body

Current [outcome lines 227–294](https://github.com/tj-agents/core/blob/8b656fb197771916c58aea4418934aaa7648b1c0/.agents/hooks/continuation_stop.py#L227) derives `root = Path(cwd).resolve()` and `owner_path = root / ".agents" / "continuation" / "owner.json"`. Reuse that entire current function body as `owner_outcome(data, controller=None)`; rename the function and change exactly its existing root/matching_receipt assignments as follows. Every other current gate stays in that one body.

```python
root = Path(cwd).resolve() if controller is None else controller
matching_receipt = controller is None and receipt.get("worktree") == str(root)
```
Inside its existing try block, after loading runtime/completion and before `binding_active`, add:

```python
if (controller is not None
        and Path(runtime.git(root, "rev-parse", "--show-toplevel")).resolve() != root):
    raise RuntimeError("canonical-worktree-root-required")
```
This defines `owner_outcome` by a precise transformation of inspected source rather than an unexplained helper: original lines 228–294 remain, except those two assignments and the shown canonical-root guard. It retains JSON/binding validation, owner identity and goal checks, local route freshness, existing foreground process filtering, supervised exception, complete/blocked/state/lease/child gates and exact scheduler/wake validation. It reads its own fresh owner snapshot. Controller evaluation suppresses transient native receipt obligation/control matching; the wrapper below processes real native controls first.

Add the reciprocal selector:

```python
def associated_owner(root, session, runtime):
    try:
        directory = root / ".agents/continuation/sessions"
        path = directory / (runtime.hashlib.sha256(session.encode()).hexdigest() + ".json")
        if directory != directory.resolve() or path != path.resolve():
            return None
        hint = read_json(path)
        if (not isinstance(hint, dict) or hint["session_id"] != session
                or hint["session_cwd"] != str(root)):
            return None
        controller = Path(hint["worktree"])
        path = Path(hint["owner_path"])
        if (not controller.is_absolute() or controller != controller.resolve()
                or path != controller / ".agents/continuation/owner.json"
                or path != path.resolve() or path.parent != path.parent.resolve()):
            return None
        owner = read_json(path)
        association = owner["session_association"]
        if (owner["owner_id"] != hint["owner_id"]
                or association["binding"] != hint
                or type(association["released"]) is not bool
                or type(hint["pid"]) is not int or not 0 < hint["pid"] < 2**31
                or hint["identity"] in (None, "unknown")):
            return None
        process = {"pid": hint["pid"], "identity": hint["identity"]}
        if not foreground_owns_current_process({"foreground": process}, runtime):
            return None
        lease = owner.get("foreground")
        if lease is not None and (
            not isinstance(lease, dict) or not isinstance(lease.get("token"), str)
            or association["released"] or lease["pid"] != hint["pid"]
            or lease["identity"] != hint["identity"]
            or runtime.hashlib.sha256(lease["token"].encode()).hexdigest() != hint["generation"]
        ):
            return None
        return path, controller, owner, association
    except (OSError, RuntimeError, ValueError, KeyError, TypeError):
        return None
```
Replace the public `outcome` entry with this wrapper. Invalid or unproven pointers use the unchanged local evaluation. Authenticated controller identity or unverified release gets a reconciliation reason; it does not silently use the unrelated native-cwd owner. A re-read authenticates again after evaluation, including generation/PID reuse. Two evaluations bound concurrent churn.

```python
def outcome(data):
    if (data.get("hook_event_name") or data.get("hookEventName")) != "Stop":
        return None
    session, cwd = data.get("session_id") or data.get("sessionId"), data.get("cwd")
    if not isinstance(session, str) or not session or not isinstance(cwd, str) or not cwd:
        return None
    root, receipt = Path(cwd).resolve(), read_receipt(session)
    if receipt.get("worktree") == str(root) and (
        direct_control(str(receipt.get("prompt", ""))) in {"pause", "cancel", "stop"}
        or receipt.get("execution_suspended") is True
    ):
        return None
    try:
        workflows = workflow_root()
        if str(workflows) not in sys.path:
            sys.path.insert(0, str(workflows))
        runtime = module("continuation_runtime", workflows)
    except (OSError, RuntimeError, ValueError, KeyError, TypeError):
        return owner_outcome(data)
    selected = associated_owner(root, session, runtime)
    for _ in range(2):
        if selected is None:
            return owner_outcome(data)
        path, controller, owner, association = selected
        if any(owner.get(key) != association["binding"][key]
               for key in ("repo", "worktree", "branch", "goal")):
            reason = "Reconcile the canonical continuation owner: identity changed."
        elif (not supervised(owner) and not owner.get("foreground")
              and association["released"] is not True):
            reason = "Reconcile the canonical continuation owner: release unverified."
        else:
            reason = owner_outcome(data, controller)
        refreshed = associated_owner(root, session, runtime)
        if refreshed == selected:
            return reason
        selected = refreshed
    if selected is None:
        return owner_outcome(data)
    return "Reconcile the canonical continuation owner: association changed during Stop."
```
The current native session ID and native root remain the control scope; controller root determines goal/binding/scheduler scope. A sparse or absent receipt cannot erase a valid association. Repeated Stop never gets a bypass. If a new claim invalidates the association during evaluation, normal local selection resumes. The final read is an observed snapshot, not a lock over external Git/scheduler work or a guarantee about changes after return.

### Representative disposable tests

The first context fragment is a new method body in existing `ContinuationTests`; all `self` methods/imports already exist in that pinned class. It fault-injects one real replace, verifies lease preservation, then repairs and proves idempotence.

```python
native = self.root / "native \u00e9"
subprocess.run(["git", "init", "-q", str(native)], check=True, timeout=30)
claim = self.cli("claim", "--owner", str(self.owner), "--pid", str(os.getpid()))
token, replace = claim["foreground"]["token"], runtime.atomic_json
locator = native / ".agents/continuation/sessions"
locator /= runtime.hashlib.sha256(b"parent").hexdigest() + ".json"

def fail_locator(path, value):
    if path == locator:
        raise OSError("locator write failed")
    return replace(path, value)

with mock.patch.object(runtime, "atomic_json", side_effect=fail_locator):
    with self.assertRaisesRegex(OSError, "locator write failed"):
        runtime.associate_session(self.owner, token, "parent", native)
self.assertEqual(self.state()["foreground"], claim["foreground"])
self.assertFalse(locator.exists())
runtime.associate_session(self.owner, token, "parent", native)
with mock.patch.object(runtime, "atomic_json", side_effect=AssertionError("rewrite")):
    runtime.associate_session(self.owner, token, "parent", native)
```
The following is a new method body in existing `ContinuationStopTests`, using its current disposable Git owner fixture. It covers both host labels, actual current-process identity, absent receipt and repeated Stop, forged pointer, actual token-authorized yield, missing/matching observed wake, and real claim invalidation. The lease is fixture data; `operate` performs the actual release/reclaim checks. No launcher or native host is used.

```python
for host in ("claude", "codex"):
    runtime = continuation_stop.module("continuation_runtime", continuation_stop.workflow_root())
    native = (self.root.parent / f"native {host} \u00e9").resolve()
    subprocess.run(["git", "init", "-q", str(native)], check=True, timeout=30)
    lease = {"pid": os.getpid(), "identity": runtime.process_identity(os.getpid()),
             "token": "fixture-token", "activity": 1}
    self.write_owner(self.owner(state="working", foreground=lease, harness=host))
    path = self.root.resolve() / ".agents/continuation/owner.json"
    runtime.associate_session(path, lease["token"], "parent", native)
    payload = {"hook_event_name": "Stop", "cwd": str(native), "session_id": "parent"}
    locator = native / ".agents/continuation/sessions"
    locator /= runtime.hashlib.sha256(b"parent").hexdigest() + ".json"
    binding = runtime.read(locator)
    with patch.object(continuation_stop, "read_receipt", return_value={}):
        for active in (False, True, True):
            self.assertIn("foreground ownership", continuation_stop.outcome(
                dict(payload, stop_hook_active=active)))
        runtime.atomic_json(locator, dict(binding, owner_id="forged"))
        self.assertIsNone(continuation_stop.outcome(payload))
        runtime.atomic_json(locator, binding)
        state = runtime.read(path)
        args = runtime.parser().parse_args(["yield", "--owner", str(path),
                                           "--token", lease["token"]])
        with runtime.locked(path.parent) as acquired:
            self.assertTrue(acquired)
            runtime.operate(path, state, args)
        with patch.object(continuation_stop, "scheduler_ready", return_value=True):
            self.assertIn("Register and enable", continuation_stop.outcome(payload))
            (path.parent / "events.jsonl").write_text(
                json.dumps({"owner_id": state["owner_id"], "event": "wake"}) + "\n",
                encoding="utf-8")
            self.assertIsNone(continuation_stop.outcome(payload))
        args = runtime.parser().parse_args(["claim", "--owner", str(path),
                                           "--pid", str(os.getpid())])
        with runtime.locked(path.parent) as acquired:
            self.assertTrue(acquired)
            runtime.operate(path, runtime.read(path), args)
        self.assertIsNone(continuation_stop.outcome(payload))
```
The scheduler boolean in this compact test is an external-boundary stub. Retain the existing [pinned scheduler-receipt/action tests](https://github.com/tj-agents/core/blob/8b656fb197771916c58aea4418934aaa7648b1c0/.agents/hooks/tests/test_continuation_stop.py#L97); the P1–N14 matrix above remains the acceptance checklist for invalid actions, locks, reads, races, and owner isolation. These are proposed tests, not tests run.

### Scope, skill wording and acceptance

Add one bounded paragraph to the existing persistent-workflow owner after claim setup: register this exact native session/cwd against its existing canonical owner with `associate-session --owner <canonical-owner> --token <existing-token> --session-id <native-session-id> --session-cwd <native-event-cwd>`; use `python` on Windows and `python3` on Linux/macOS with the existing shipped runtime path. Require successful readback before reporting association active; repair partial publication without releasing/reclaiming. A bounded side handoff preserves the parent claim. Full-goal transfer follows existing token release plus verified pickup. Registration is neither native /cd nor proof that host commands can execute. Native /cd remains preferred where actually supported; its documented full-goal fallback is valid and must not be misrepresented as verified by launch alone.

The five-file implementation remains one sequential atomic slice, estimated below 1000 changed source+tests+Goal lines (about 950 including removed/refactored code and remaining assertions). No new helper module, configuration/authorization schema, daemon, transport, manifest or cache installation.

Run meaningful disposable behavior tests on Windows and Linux with spaces/non-ASCII paths. Reject unknown/dead/reused PID, wrong token, competing writer, malformed/redirected paths, stale/forged/copied-session reciprocal, foreign live association and lock/readback failures without changing ownership. Preserve current completion, typed blocker, supervised-child and explicit native pause/cancel controls. Test both Claude/Codex native payloads and real hook ancestry separately after normal publication; same-executable ancestry protection is not a universal mixed-host topology proof. Both-record rewriting by the same local authority remains outside reciprocal authentication's trust boundary.

At this pinned source, scheduler_ready returns false on Linux. Running the Windows validator's mocked positive fixtures on Linux does not supply a Linux scheduler or establish native waiting acceptance. A held foreground still blocks regardless of wake evidence; a released waiting owner needs the existing exact registered/enabled scheduler and matching observed wake. No scheduler adapter belongs in this slice.

These examples are syntax-only proposals; source remains unimplemented, and runtime tests plus native acceptance remain outstanding.

Heartbeat repair preserves the existing foreground lease while updating nonblank reason/next-action metadata after ownership checks. The first native turn failed before pickup; its later resumed turn produced a rebased candidate and a delivery gate. PROGRESS.md records that newly observed reconciliation boundary and immutable archived qualification. Parent must validate the actual current ownership, exact-head review and delivery; no direct owner JSON edit or release/reclaim workaround.

The delivery-binding budget repair is independent of the live configuration owner's atomic preference/guard layer. It reuses invocation-local authenticated Git context, derives fresh origin once, keeps both fresh paginated GitHub reads and all state containment/revalidation checks, simplifies the Windows fixture dispatch, and strengthens the original held-label success oracle. Owned-tree timeout drainage in existing hook_runtime.py is a separate useful follow-on; the observed surviving child and unproven historical lock owner must not be conflated. The active Core owner is `plans/delivery-binding-budget/GOAL.md` in branch `Fix/DeliveryBindingBudget` from8b656fb; parent /root owns its exact-head review, publication and subsequent immutable reference. This local source goal is not yet remotely published. The separate timeout-drain follow-on must likewise receive its own promoted Core plan before execution.

## Next Steps

Scope: retain the whole authorized twelve-repository rollout and both-host requirement.
Current slice: qualify the recovered budget worker, diagnose heartbeat suite failures before review/delivery, and preserve paused extractor and live configuration owners.
Remaining scope: publish budget repair; qualify and land extractor preparation then native wiring; deliver authenticated parent Stop association and timeout drainage; migrate configuration after its owner publishes/releases, then deliver Kit support and reviewed twelve-repo adoption.
Done when: every authorized slice is delivered with truthful both-host evidence or has its concrete external/ownership gate, resolver and resume condition recorded; repository activation conditions are accounted for; the canonical terminal transition represents the whole goal.

Follow PROGRESS.md for exact executable actions. A completed phase, side handoff, open PR, started CI or source merge never completes this parent. Preserve Work1/Infonetica9 billing holds without retry or bypass. Preserve the live Feature/ConfigurableAutoMerge owner; lease expiry is not release. Only that exact owner can publish or durably release its paths; no verified profile/app-server transport is currently available. After source publication/release, implement the selected namespaced migration atomically and preserve Core183's full strict authorized_stop_classes validation.
