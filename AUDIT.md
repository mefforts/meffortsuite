# MeffortSuite 1.1.13 release audit

This release adds optional native pet-category and verified sound-file controls, adds reviewed Restore Defaults with reload, and removes Enchant Queue. SOUND-DEFAULTS-REVIEW-1.1.13.md records behavior, ownership limits, reset scope, removal and client checks.

New sound controls start off. Native muting is broader than companion footsteps; shared-file muting affects all sources and needs verified IDs. No companion-specific routing or guessed preset is claimed. Prior values and accepted file mutes have recovery tracking, failed cleanup stays pending, and quiet fishing remains independent. Unsupported/refused APIs are reported and guarded; no idle polling is added.

Defaults require a review and explicit confirmation. The suite stops work and restores audio before staging; unsafe context or incomplete recovery refuses the reset. Startup applies account/current-character preference defaults before module caches initialize. Lists, macros, game bindings and other characters' personal settings are retained. Failed reload remains retryable with the suite off.

Enchant Queue implementation, controls, binding file, runtime handlers, diagnostics and active guidance are removed. Old character queue data is pruned. The dedicated upstream notice/attribution section is removed with that code; suite MIT and spell-data CC BY notices remain. The help description and older task-like changelog wording are tidied.

All 35 regression scripts pass: 480 unit-test methods and five tooltip script checks. All 29 shipped text/source/data files pass the package's prompt/model/transcript scan. The new comment explains applying defaults before cached module initialization.

The ZIP has one MeffortSuite folder and exactly 33 files, including 24 Lua modules and four textures. Tests, reviews, build tools, old archives, the removed module/binding and its obsolete notice are excluded. TOC, runtime, About fallback, player documentation, notes and filename agree on 1.1.13. Packaging/tests validate references, source/archive equality, reproducibility, permissions and integrity.

Native audio routing, installed sound-file mappings, protection, reset reload and rendering still require Forever validation. Preparation does not submit to CurseForge or publish the environment.
