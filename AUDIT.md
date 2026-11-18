# MeffortSuite 1.1.7 release audit

This release makes Enchant Queue's Next action discoverable beside Blizzard's Enchant button, with a Queue opener/count and a compact fallback above the native button. It allows Next/keybindings while configuration is closed, preserves owned tracking across configuration-only close, handles late native data/layout, and adds chat/status/export feedback. ENCHANT-REVIEW-1.1.7.md records the design, native contracts, tests and remaining client checks.

Native geometry is read without native reparenting or writes. The secure control stays under UIParent, withdraws through restricted combat state handling, and requires the native recipe control to be visible. No automatic craft or confirmation was added. Existing target/recipe/quantity, replacement and uncertainty checks remain covered. Visible-window layout updates are deduplicated and stop with the feature/window or combat.

All 32 regression scripts pass: 401 unit-test methods and five tooltip script checks. Lua 5.1 compilation, bindings/TOC, whole-addon settings/master transitions, ranged/Wand coexistence, package contents and reproducibility remain checked. The installable archive contains one MeffortSuite folder and 32 files: 21 Lua modules, metadata, bindings, four textures, documentation and legal notices. Audit/test/build files and prior originals are excluded.

All 28 shipped source/data/text files pass the prompt/model/transcript residue scan. Player instructions describe the application's controls and support workflow. License and attribution notices are byte-identical to 1.1.6. Current runtime, TOC, About fallback, documentation, upload notes and ZIP filename agree on 1.1.7. Source/archive bytes, permissions, references and integrity are validated.

Actual Forever placement, keyboard input, protected native clicks and server acknowledgement need the client checks in the Enchant review and VALIDATION.md. Earlier functionality is retained and covered by the full suite; the previous full feature audit remains FEATURE-AUDIT-1.1.6.md. Preparation does not upload to CurseForge or publish the environment.
