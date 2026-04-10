# SkyeHands tar-vs-zip recovery report

- ZIP analyzed: `SkyeHands-main_stage40_pass38_stage9_fallback_full (3)(1).zip`
- TAR analyzed: `SkyeHands_3_1_9_FULL_PROJECT_COMPLETE (1).tar.gz`
- ZIP total entries: **31,858**
- TAR total entries: **35,658**
- ZIP regular files: **28,426**
- TAR regular files: **31,694**
- Paths present in ZIP but missing from TAR: **353**
- Paths present in TAR but not ZIP: **4,153**
- Common paths with size mismatch: **135**

## What is actually missing from the TAR

The missing set is dominated by one omitted workspace snapshot lane:

- `workspace/volumes/pass38-fallback-1775682095610-manager/fs/...` → **320** paths

Outside that snapshot, the TAR is also missing these top-level launch/bootstrap files from the ZIP:

- `.skyequanta/workspace-runtime/remote-default/agent.log`
- `.skyequanta/workspace-runtime/remote-default/ide.log`
- `.skyequanta/workspace-runtime/remote-default/state.json`
- `Makefile`
- `README.md`
- `START_HERE.sh`
- `package.json`
- `skyequanta`
- `skyequanta.mjs`

## Biggest things the TAR has that the ZIP does not

- `workspace` → 3,451 paths
- `dist` → 459 paths
- `.skyequanta` → 216 paths
- `docs` → 18 paths
- `platform` → 5 paths
- `DEEP_SCAN_REPORT.md` → 1 paths
- `apps` → 1 paths
- `client-handoff-for-procurement.html` → 1 paths
- `stage11_smoke_full.log` → 1 paths

## Common files that changed size between both archives

- `.skyequanta/audit-chain.ndjson`
- `.skyequanta/audit-log.json`
- `.skyequanta/remote-executor/executor-state.json`
- `.skyequanta/remote-executor/executor.log`
- `.skyequanta/remote-executor/workspace-runtimes.json`
- `.skyequanta/runtime-bus/events.ndjson`
- `.skyequanta/runtime-bus/workspaces/local-default.json`
- `.skyequanta/runtime-bus/workspaces/preview-stage8.json`
- `.skyequanta/runtime-bus/workspaces/remote-default.json`
- `.skyequanta/runtime-dependency-repair.json`
- `.skyequanta/runtime-recovery/journal.ndjson`
- `.skyequanta/workspace-runtime/local-default/ide.log`
- `.skyequanta/workspace-runtime/local-default/state.json`
- `.skyequanta/workspace-runtime/preview-stage8/ide.log`
- `.skyequanta/workspace-runtime/preview-stage8/logs/activity.ndjson`
- `.skyequanta/workspace-runtime/preview-stage8/logs/log-retention.json`
- `.skyequanta/workspace-runtime/preview-stage8/state.json`
- `.skyequanta/workspace-runtime/remote-default/logs/activity.ndjson`
- `.skyequanta/workspace-runtime/remote-default/logs/log-retention.json`
- `.skyequanta/workspace-scheduler-state.json`
- `.skyequanta/workspaces.json`
- `apps/skyequanta-shell/bin/workspace-proof-stage10.mjs`
- `apps/skyequanta-shell/bin/workspace-proof-stage11.mjs`
- `apps/skyequanta-shell/bin/workspace-proof-stage4.mjs`
- `apps/skyequanta-shell/bin/workspace-proof-stage9.mjs`
- `apps/skyequanta-shell/bin/workspace-smoke-lifecycle.mjs`
- `apps/skyequanta-shell/lib/deployment-packaging.mjs`
- `apps/skyequanta-shell/lib/runtime-containment.mjs`
- `apps/skyequanta-shell/lib/workspace-runtime.mjs`
- `apps/skyequanta-shell/python/__pycache__/skyequanta_app_server.cpython-313.pyc`
- `apps/skyequanta-shell/python/__pycache__/skyequanta_runtime_bootstrap.cpython-313.pyc`
- `dist/production-release/SANITIZED_RELEASE_MANIFEST.json`
- `dist/production-release/skyequantacore-current-truth.tar.gz`
- `dist/production-release/skyequantacore-current-truth/apps/skyequanta-shell/bin/remote-executor.mjs`
- `dist/production-release/skyequantacore-current-truth/apps/skyequanta-shell/bin/workspace-proof-stage10.mjs`
- `dist/production-release/skyequantacore-current-truth/apps/skyequanta-shell/bin/workspace-proof-stage11.mjs`
- `dist/production-release/skyequantacore-current-truth/apps/skyequanta-shell/bin/workspace-proof-stage4.mjs`
- `dist/production-release/skyequantacore-current-truth/apps/skyequanta-shell/bin/workspace-proof-stage8.mjs`
- `dist/production-release/skyequantacore-current-truth/apps/skyequanta-shell/bin/workspace-proof-stage9.mjs`
- `dist/production-release/skyequantacore-current-truth/apps/skyequanta-shell/lib/apparmor-policy.mjs`

## Read on this comparison

The TAR is not simply a strict subset of the ZIP. It actually contains thousands of extra files, especially under `workspace/volumes/repo-default`, `.skyequanta`, and `dist/`, but it is missing the pass38 fallback manager workspace snapshot that exists inside the ZIP. That means the TAR looks more like a different packaging state rather than a clean newer superset.
