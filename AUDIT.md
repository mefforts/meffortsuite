# MeffortSuite 1.1.14 release audit

This release removes the dedicated Orgrimmar banker shortcut, defaults Fast auto loot ON without overriding saved OFF choices, and adds the native backpack free-slot counter under Bags. BANK-BACKPACK-REVIEW-1.1.14.md records behavior, ownership, regression coverage and live-client checks.

Banks use the general single-option service shortcut and dialogue keys. NPC-specific selection and delayed callbacks are removed; the retired preference is pruned. The independent flight-master setting remains. Fast auto loot continues to respect the native decision/modifier and existing failure/confirmation/combat guards.

The backpack feature enables the native display setting and delegates counting/rendering/updates to the game. It adds no bag scan, overlay or idle timer. Prior settings restore on disable, master off and world transitions; manual changes are honored, combat writes defer and failed restoration stays recorded. Reset checks this recovery before staging. Native specialty-bag counting and custom bar behavior require client validation.

All 36 regression scripts pass: 497 unit-test methods and five tooltip script checks. All 30 shipped text/source/data files pass the package's prompt/model/transcript scan. Added source comments were reviewed for necessity; no conversational or model text is shipped.

The ZIP has one MeffortSuite folder and exactly 34 files, including 25 Lua modules and four textures. Tests, reviews, build tools, archives and removed Enchant Queue files are excluded. TOC, runtime, About fallback, player documentation, notes and filename agree on 1.1.14. Packaging/tests validate references, source/archive equality, reproducibility, permissions and integrity. Suite MIT and spell-data attribution remain unchanged.

Native game behavior, protection and rendering still require Forever validation. Preparation does not submit to CurseForge or publish the environment.
