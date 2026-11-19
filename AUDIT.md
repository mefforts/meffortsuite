# MeffortSuite 1.1.11 release audit

This release adds optional Fast auto loot and Show vendor + AH together under Bags. Both start off and save account-wide. LOOT-REVIEW-1.1.11.md records implementation, coverage and client checks.

Fast loot follows native auto-loot intent, waits one frame for snapshots and requests eligible slots in reverse order. It stops on cancellation, combat, confirmation, inventory errors or refused/blocked calls. The existing guarded-call export workflow records native blocks and suppresses retries. Master off/on cannot revive a cancelled pass. No mouse binding, native window replacement/hiding, automatic confirmation, CVar change or idle polling is introduced.

Combined floats show vendor value first with smaller muted parenthetical AH value, using native coin icons. Both include received coins and the quality filter; missing/non-auctionable prices use vendor fallback. The single-value AH preference is retained. One provider request per receipt supplies the AH side while native metadata supplies vendor value. Both totals retain bounds, metadata waits, mode snapshots and independent late-receipt/pool baselines. Preview and diagnostics include the combined mode.

All 33 regression scripts pass: 468 unit-test methods plus five tooltip script checks. All 29 shipped text/source/data files pass the package's prompt/model/transcript scan. New comments explain event ordering and receipt matching. Legal and attribution notices are byte-identical to 1.1.10.

The archive contains one MeffortSuite folder and exactly 33 files, including 22 Lua modules and four textures. Tests, reviews, snapshots, build tools and prior archives are excluded. TOC, runtime, About fallback, player documentation, notes and filename agree on 1.1.11. Source/archive equality, reproducibility, permissions and integrity are checked by packaging and regression tests.

Actual Forever auto-loot speed, protected-action behavior, server timing, font rendering and installed Auctionator data require in-game validation. Preparation does not submit to CurseForge or publish the environment.
