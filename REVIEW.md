# MeffortWand 1.0.3 review

Reviewed the uploaded MeffortWand 1.0.2 source and implemented fixes plus a standalone `/mwand` settings panel. The original upload is retained unchanged. MeffortSuite source files were not modified.

## Bugs found and corrected

| Priority | Previous behavior | Result in 1.0.3 |
| --- | --- | --- |
| Critical | A deleted or reordered macro could leave the secure button pointing at a different player macro. | `UPDATE_MACROS` withdraws the old binding and macro attributes synchronously out of combat, then coalesces recovery and verifies the exact Shoot body before rebinding. |
| High | Clearing and reinstalling the same native state driver could remove input while the mouse stayed over an enemy: unregistering leaves the old `state-*` value behind. | An unchanged valid installation stays intact. Rebuilds reset the persisted states before registering again. |
| High | Wand's v2 library could replace Suite's newer v6 manager depending on addon load order. | v7 retains newer managers, upgrades known older tables in place, and reaches old captured login-cleanup callbacks without deleting macros. Both load orders were exercised. |
| High | Initialization or registration failure could leave partial state while frame existence still claimed readiness. | Initialization is guarded, readiness requires eligible verified setup, and rollback unregisters both possible driver states and clears action attributes. |
| Medium | A combat mode change made camera handling follow the newly saved mode while the old binding remained applied. | Camera handling uses the applied mode. Settings show pending and applied choices separately; peer handoff is retained until it can run after combat. |
| Medium | Macro renaming could reorder slots while acquisition continued using the old index. | Macro writes are verified using the returned index or a fresh exact-identity scan. Synchronous macro notifications are protected against reentrant mutation. |
| Medium | Repeated clicks could retarget during an active wand channel. | Both targeting and casting use the localized Shoot channel guard. |
| Medium | Login acquisition/cleanup removed recognized duplicates even while the feature was off. | Ordinary login, acquisition, and on/off changes do not delete macros. Duplicate removal requires explicit cleanup. |
| Medium | Camera polling ran continuously, and unrelated equipment or item-data changes could rebuild controls or interrupt a drag. | The camera watchdog exists only during an owned mouse-look session. Relevant events are filtered/coalesced; unchanged setup does not rebuild. |

Additional fixes cover corrupt saved state, loading after login, combat startup, missing native functions, known-spell provider failures, delayed localized spell data, fishing poles, and name collisions with custom or account macros.

## Macro and disable behavior

- Turning the feature off retains the macro and its action-bar references.
- Custom edits and account macros are not overwritten or deleted. An exact safe macro can be reused read-only.
- Macro creation uses `MeffortAim` or the fixed alternate `MeffortRC`; conflicts and full slots produce an unavailable status instead of a destructive fallback.
- Explicit cleanup only removes recognized, unchanged character macros for Shoot and retains a keeper. Other attacks and unrelated/custom macros remain.
- Cleanup verifies identities before each deletion and checks the native count afterward. A failed or unconfirmed step stops the cleanup.
- Combat requests retain the current applied controls until protected changes become legal. The UI makes that pending state visible.
- The shared manager corrects legacy Suite state values before a peer handoff. Older no-argument cleanup callbacks become non-destructive while v7 is installed.

## Settings and login notice

`/mwand`, `/mw`, and `/meffortwand` open the same small standalone panel. It uses Blizzard dialog textures, gold headings, native buttons, help tooltips, and a stock wand icon, without requiring MeffortSuite assets.

Controls include on/off, remembered right-click or Shift + right-click activation, the per-character login notice, setup checks, and explicit duplicate cleanup. The header is draggable; Escape closes the panel; viewport scaling and tooltip ownership are handled without idle polling.

The login notice points to `/mwand` and can be hidden per character. Existing mode commands remain supported. `/mw diagnostics` reports setup and macro identity without printing macro bodies.

## Verification

- Three addon modules compile with Lua 5.1.
- Both standard and Camelot manifests load the same modules in the correct order and declare 1.0.3 / Interface 16001.
- 61 automated tests pass across runtime, macros, settings, and combined-module integration.
- The mocks preserve native state attributes across unregistering and fire synchronous macro-update events. Tests therefore reproduce the specific binding and stale-index failures instead of assuming every registration invokes a callback.
- Actual Suite v6 shared-manager and ranged-module source is exercised in both load orders where the companion checkout is available.
- The installable ZIP contains exactly eight required files under one `MeffortWand/` root. Tests, review notes, tools, temporary files, and previous archives are excluded. ZIP entries use regular-file permissions and repeatable metadata.

These checks validate code paths and contracts. They do not prove the target client's native mouse dispatch, taint behavior, font rendering, or actual wand channel timing.

## In-game checks before release

1. Open `/mwand` on an existing character and a new character; check saved OFF/Shift choices, header dragging, Escape, hover help, and several UI scales. Toggle the login notice and reload.
2. Test both activation modes against living hostile targets, friendly targets, corpses, NPCs, unit frames, action buttons, and the game world. Confirm camera drag/release, looting, and normal interaction.
3. Change modes and turn the feature off during combat. Check the pending/applied text and confirm the saved choice applies after combat. Equip/remove the wand and equip a fishing pole; confirm the secure conditions withdraw or restore the shortcut appropriately.
4. Delete, rename, edit, and reorder macros. Confirm right-click never calls a shifted custom macro, custom edits remain untouched, and a verified Shoot macro is recovered when possible. Test full slots and reserved-name conflicts.
5. Create recognizable duplicate character macros and run explicit cleanup. Check the retained macro/action-bar entry, other attacks, account macros, and custom text. Disable the addon and reload; verify normal controls and retained macros.
6. Test with MeffortSuite enabled and disabled, in both load orders. Check standalone priority, suite fallback after ordinary/combat changes, and recovery after macro changes.

No environment or CurseForge publication was performed.
