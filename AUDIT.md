# MeffortSuite 1.1.9 release audit

This release adds optional Auctionator AH estimates to floating loot totals under Bags. The preference starts off, applies from the next loot window and is saved account-wide. LOOT-PRICING-1.1.9.md records the API evidence, fallback rules, coverage and client checks. Earlier feature/Enchant Queue audits remain available.

The public v1 item-link adapter preserves variants and makes at most one request per included receipt. Actual coins, confirmed quantities and the quality filter remain unchanged. Missing/invalid prices, unsupported providers and bind-on-pickup/quest items use vendor values. Finite integer bounds, guarded provider calls, metadata retries and aggregate limits protect totals. No scans, private database reads or background price polling are introduced. Diagnostics identify the selected pricing mode and last displayed total's sources.

All 32 regression scripts pass: 428 unit-test methods plus five tooltip script checks. All 28 shipped text/source/data files pass the package's prompt/model/transcript scans. The added comment explains the non-auctionable binding check. Legal and attribution notices are byte-identical to 1.1.8.

The ZIP contains one MeffortSuite folder and exactly 32 files: 21 Lua modules, bindings/metadata, four textures, player documentation and legal notices. Tests, review records, snapshots, build scripts and prior archives are excluded. Current runtime, TOC, About fallback, documentation, notes and ZIP filename agree on 1.1.9. Packaging verifies source/archive equality, permissions, reproducibility and integrity.

The installed Auctionator build and its cache still require an in-game compatibility/value comparison. Builds lacking its supported public item-link endpoint fall back to vendor values. Native gameplay input, taint, rendering and server behavior remain client checks. Preparation does not upload to CurseForge or publish the environment.
