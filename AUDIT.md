# MeffortSuite 1.1.8 release audit

This release fixes Enchant Queue setup construction and the flow from native selections to a queued action. ENCHANT-REVIEW-1.1.8.md records the client-contract finding, regression proof, changes and live checks. The previous full feature audit remains FEATURE-AUDIT-1.1.6.md.

The target uses the native ItemButton intrinsic. Setup stays hidden until complete; failures discard partial UI references, preserve data, record the error and allow retry. Add selected, a default repeat count of one and an empty-list instruction make adding explicit. Native recipe/target selection can populate an unconfigured queue without casting or changing the native allocation. Existing targets remain protected from silent replacement. Readiness now updates with configuration closed and after returning to the recipe tab. Status/tooltip text reports the current block, enabled state, construction error and build.

Recipe/target GUID/quantity checks, native craft delegation, matching-cast tracking, separate replacement confirmation, uncertainty handling and combat withdrawal remain in place. Adding/configuring never casts. The 1.1.7 layout, protected UIParent ownership and visible-window-only positioning remain unchanged.

All 32 regression scripts pass: 410 unit-test methods plus five tooltip script checks. The Enchant Queue fixture now enforces the specific missing-template contract instead of accepting every template. All 28 shipped text/source/data files pass prompt/model/transcript scans; comments are concise safety/API notes. Legal and attribution notices are byte-identical to 1.1.7.

The ZIP contains one MeffortSuite folder and exactly 32 files: 21 Lua modules, bindings/metadata, four textures, player documentation and legal notices. Tests, review records, snapshots, build scripts and prior archives are excluded. Current runtime, TOC, About fallback, documentation, notes and ZIP filename agree on 1.1.8. Source/archive equality, references, permissions, reproducibility and integrity are validated.

The original live report lacked a constructor exception, so the strict-contract reproduction is not presented as a captured client stack. Live layout, native input and server response checks remain necessary. New setup exceptions are recorded for export before reload. Preparation does not upload to CurseForge or publish the environment.
