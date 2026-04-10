# SkyeHands recovered merge report

- Base used: TAR (`SkyeHands_3_1_9_FULL_PROJECT_COMPLETE (1).tar.gz`)
- Recovery donor used: ZIP (`SkyeHands-main_stage40_pass38_stage9_fallback_full (3)(1).zip`)
- Merge rule: keep TAR files when same path exists in both; restore only paths absent from TAR from the ZIP

## Counts
- ZIP regular files: **28426**
- TAR regular files: **13940**
- Merged regular files: **28597**
- Restored from ZIP into TAR base: **14657**
- TAR-only files preserved: **171**
- Same-path ZIP/TAR files left on TAR base because TAR looked newer/different: **51**
- ZIP files still missing after merge: **0**

## Restored from ZIP by top-level area
- `platform`: **10929**
- `dist`: **2227**
- `workspace`: **1248**
- `docs`: **170**
- `scripts`: **70**
- `.skyequanta`: **3**
- `public`: **2**
- `INVESTOR_VALUATION_2026-04-07_SECTION42.md`: **1**
- `Makefile`: **1**
- `README.md`: **1**
- `START_HERE.sh`: **1**
- `package.json`: **1**
- `skyequanta`: **1**
- `skyequanta.mjs`: **1**
- `src`: **1**

## TAR-only files preserved by top-level area
- `.skyequanta`: **85**
- `dist`: **85**
- `apps`: **1**

## Key root files that were restored from the ZIP
- `Makefile`
- `README.md`
- `START_HERE.sh`
- `package.json`
- `skyequanta`
- `skyequanta.mjs`
