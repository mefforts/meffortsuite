# MeffortSuite 1.1.10 release audit

This release fixes five reproduced loot/merchant issues: excluded receipts reaching an earlier corpse, newer ID fallback taking an older exact variant, incremental popups repeating previously displayed value, unfinished merchant work not resuming after prolonged combat, and merchant callbacks surviving world transitions. BUG-REVIEW-1.1.10.md records the reproductions, fixes, compatibility limits and live checks.

Excluded loot remains a bounded receipt barrier. Exact full-link matches precede ID fallback across recent windows. Reused floats subtract the value already displayed. Merchant combat recovery preserves completed steps and uses the existing bounded retries and visit/state checks. World transitions invalidate pending visits. No idle polling, protected input changes or native menu geometry writes are introduced. Existing preferences, optional Auctionator pricing and standalone Wand compatibility are retained.

All 32 regression scripts pass: 440 unit-test methods plus five tooltip script checks. All 28 shipped text/source/data files pass the package's prompt/model/transcript scan. The added source comment explains why exact matches precede ID fallback. Legal and attribution notices are byte-identical to 1.1.9.

The archive contains one MeffortSuite folder and exactly 32 files, including 21 Lua modules and four textures. Tests, reviews, snapshots, build tools and old archives are excluded. TOC, runtime, About fallback, player documentation, notes and filename agree on 1.1.10. Packaging validates source/archive equality, permissions, reproducibility and integrity.

Full native gameplay, event ordering, taint, visual and installed Auctionator/cache validation remain client checks. A receipt crossing an excluded window can be conservatively omitted because chat receipts do not identify their original corpse. Preparing the download does not upload to CurseForge or publish the environment.
