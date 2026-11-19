# MeffortSuite 1.1.12 release audit

This release adds native reward vendor labels, clearer settings guidance and slower/adjustable loot floats. Reward values start enabled under Quests and use full-stack vendor copper without selecting or claiming rewards. REWARD-SETTINGS-REVIEW-1.1.12.md records contracts, geometry guards, context handling, verification and client checks.

Independent reward overlays read native geometry without changing names, layout or input. Compact/unsupported label space falls back to recognized reward tooltips. Item requests are bounded; stale contexts, invalid/secret values, clipping, row reuse, close, combat and world transitions are guarded. Queued-close cancellation prevents old refreshes reviving labels. Existing diagnostic reports include reward status.

Setup guidance, section headings, task links, prerequisites and report-copy steps are available in the panel. Back retains page/scroll and text drafts. Loot controls have a Bags subpage and direct command. Merchant retry checks its context. Floats now last six seconds by default, with 2–12 second duration captured per new animation. Existing quality filters, Auctionator totals, pool baselines and gameplay controls are retained.

All 34 regression scripts pass: 498 unit-test methods and five tooltip script checks. All 30 shipped text/source/data files pass the package's prompt/model/transcript scan. The new source comment explains overlay ownership. Legal and attribution notices are byte-identical to 1.1.11.

The archive has one MeffortSuite folder and exactly 34 files, including 23 Lua modules and four textures. Tests, reviews, snapshots, build tools and old archives are excluded. TOC, runtime, About fallback, player documentation, notes and filename agree on 1.1.12. Packaging and regression checks validate references, source/archive equality, reproducibility, permissions and integrity.

Native font rendering, tooltip/scroll behavior, protected actions and server timing still require Forever validation. Preparation does not upload to CurseForge or publish the environment.
