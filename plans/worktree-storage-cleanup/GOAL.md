# Reclaim storage from finished idle worktrees

Status: this maintenance pass is complete, verified on 2026-10-14T16:17:48.201707+00:00. The migration and other unfinished tasks remain with their owners.

## Authority and scope

Tommy authorized inspecting idle worktrees, preserving related finished work in Git, and deleting safely retired worktrees. Idle alone is not completion. Preserve active agents, unfinished migration tasks, unknown work, primary checkouts, nested worktrees, and unrelated machine state. No new native CLI, handoff, scheduler, feature delivery, or Core CLI-close repair is authorized by this maintenance task.

## Verified result

- Removed 30 finished inactive worktrees: 22 clean shipped checkouts and 8 additional checkouts after preserving their completed-task records. Directories and Git registrations are verified absent; local branch history is retained.
- Pushed and verified 9 exact remote archive commits under `Archive/StorageCleanup20261014/*` in cpp, nvim, and core. Only completed-task documentation changed; no source code or generated distribution was committed. All 19 original documents have verified byte-exact private copies; Git normalized one record's line endings.
- Preserved and hash-verified 35 ignored runtime files in Git-private ZIP archives. Private runtime state was not published.
- Removed both exact Rust build caches `cli/target/debug` and `cli/target/release`: 3,780 files totaling 1,129,492,091 logical bytes. Fresh process, tracked-file, path, and reparse checks passed; both directories are absent. Installed binaries are separate.
- C: currently has 9,927,901,184 bytes free (9.25 GiB). Free space at this resumed pass was 9,154,605,056 bytes; the earlier increase from 0.487 GiB is not attributed to this task.
- Five initially clean candidates remain protected because their ignored ownership records describe blocked, waiting, or unresolved work. Four clean unmerged candidates also remain protected because task completion is unknown. Dirty source, open PRs, ongoing migration, and unregistered directories with unknown state are retained.
- `Fix-SessionStoreHookRegistration` is restored and protected. Two agents resumed there after the earlier process snapshot. Git registration, all tracked source, the original merged code head `352312dafd3e6a43f9bc39911a7674868596e3e5`, and private runtime records were restored. Its completed records remain safe in the verified remote archive; newer working files and index were retained.
- All one-off destructive writers are retired and verified to refuse execution. No cleanup watcher, scheduler, or background writer is running for this task.

## Evidence

- `final-verification.json`: independent filesystem, registration, remote-head, document, backup, live-checkout, cache, and writer-refusal verification.
- `retirement-results.json`: exact 22 removals and five protected candidates.
- `preservation-results.json`: nine remote commits, eight removals, the restored protected checkout, document hashes, and private archive paths.
- `cache-proof.json`: exact cache paths, size, successful deletion, and observed free space.
- `retirement-guard-proof.json`: failed concurrency qualification and disabled writer evidence.
- `archive-compression-proof.json`: earlier partial NTFS compression preserved archive bytes; whole-sweep savings were not measured. Core archives and review evidence remain retained.
- Root inventory, classification, approval, native process and holder reports retain the original evidence. They are snapshots, not current cleanup authorization.

## M001 — A stale process snapshot allowed retirement to overlap resumed agents

- Kind: mistake. Observed: 2026-10-14. Confirmed cause: this maintenance implementation reused an earlier native-process snapshot during a multi-minute preservation loop. Native sessions `01a13725-d930-7340-8425-8eca8d8e37f0` and `01a1373d-fe0f-7b03-8410-cf0a1412911d` resumed in the last candidate before deletion. The no-active-worktree constraint was violated; no missing Core standard is inferred.
- Impact and priority: P1. The live checkout was temporarily emptied and deregistered. No unique source or record was lost: exact remote and private backups permitted restoration. The resumed agents' checkout and original code head are verified restored.
- Source owner: this standalone maintenance implementation, not the independent Core terminal-close repair.
- State: deferred for future concurrency prevention; immediate recovery is verified. Repair link: this goal, the retired local storage writers, and the restoration evidence in `preservation-results.json`.
- Reason and blocked_by: capability. A directory move and Windows handle check did not qualify prevention of concurrent native startup. Real disposable-process tests caught both inadequate designs. The handle check rejected an already occupied checkout, but a process could still start and use it during the retirement window.
- Correction: retirement must exclude concurrent native ownership before deleting any files; a process snapshot alone is insufficient. These one-off writers refuse further execution. Do not reuse or re-enable them as a qualified cleanup mechanism.
- Resolver and next action: a future authorized maintenance owner must qualify a shared startup/retirement admission protocol or a controlled no-launch maintenance window before performing another automated sweep. No new repair owner or job was dispatched.
- Resume and resolution condition: an authorized prevention design has a meaningful regression where a native process claims the checkout after inventory and retirement preserves its full source, registration, and runtime state. Until that passes, automatic reuse remains prohibited.
- Verification: the restored live checkout and original code head, all remote/private hashes, 30 absent retired checkouts, and refusal of all retired writers passed independent checks. Concurrent-startup prevention did not pass and is not claimed fixed.

This is the canonical standalone maintenance record. There is no remaining eligible deletion in the approved set; active, unfinished, and unknown tasks remain protected. The unresolved prevention observation grants no authority to launch another agent or modify Core's independent repair.
