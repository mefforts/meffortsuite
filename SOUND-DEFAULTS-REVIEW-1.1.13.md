# MeffortSuite 1.1.13 sound, defaults and removal review

## Sound controls and scope

The launcher now exposes Sounds; tooltip colors remain accessible through Tooltips. Native pet muting and targeted sound-file muting both start off and save account-wide. Quiet fishing audio remains per character and is available on both Sounds and Fishing.

The native control uses Sound_EnablePetSounds, present in the inspected Camelot-compatible audio settings reference. It affects the native pet-sound category, potentially including combat pets; it is not a per-companion or footsteps-only filter. Some companion walking files may use shared creature routing and remain audible. SFX/master/music/ambience/dialogue values are untouched by this control.

Advanced muting accepts up to 64 verified positive numeric sound-file IDs within a 500-character list. It does not accept pet names, spell IDs, paths or sound-kit IDs, and no unverified companion profiles ship. MuteSoundFile/UnmuteSoundFile must both be available before a new file mute is attempted. Muting a shared file affects every source using it, including other pets/NPCs. No automatic sound discovery, download or unit-source interception is claimed. Exact companion support requires verified mappings and live testing.

Native changes store the original value before muting and verify the resulting setting. Manual game changes override that control for the current session. File changes record only accepted mute requests. Disabling, master off, logout and world transitions restore recorded changes; missing/refused cleanup retains recovery entries. Previous-session file recovery must complete before claiming new file mutes. The suite's guarded calls record blocked actions and suppress repeated native requests. There is no idle polling. The API does not expose prior per-file mute ownership from other addons, so the settings advise against managing the same IDs in multiple sound addons; independently managed IDs are not touched.

The earlier sound-file API investigation demonstrated the established public mute/unmute pattern in a Leatrix Plus reference. No source or sound dataset from that addon is bundled or copied. Forever API availability is checked at runtime. Actual footstep routing and sound-file mappings are not verified by mock tests.

## Restore Defaults

Restore Defaults is visible on the launcher and in Help/About. /msuite defaults opens its review page, not the reset itself. The page describes account/current-character scope, default behaviors, retained lists and reload. Only Restore defaults & reload confirms execution; navigation or Back performs no reset.

The operation rechecks readable out-of-combat/cursor state, releases held right-click input as a prerequisite, and requires ReloadUI. It stops Suite work through the existing master cleanup, restores quiet-fishing/pet/file audio, and refuses staging while any recovery remains. A saved marker stages the reset, with the suite off until reload. Preferences are cleared at the next addon initialization before login caches build, avoiding live replacement of cached module tables. Installation/legacy-migration markers are retained so old addon preferences are not imported again.

Known account preferences and current-character feature settings reset. Banking inclusion/exclusion lists, the custom sound-file list, macros, native game keybindings, other addon data and other characters' personal settings remain. Automatic bag/merchant/bank defaults can become enabled after reload; the review says so. The general game settings are not reset. Failed reload keeps the request and exposes Reload UI for retry; the master cannot reactivate beforehand. Pending audio recovery is never discarded by startup application.

## Enchant Queue removal

The implementation, Queue/Next controls, layout ticker, protected button, popup/recipe/cast handlers, settings, aliases and diagnostic provider are removed from the shipped feature set. Bindings.xml was dedicated to this feature and is removed from the TOC and archive. No SetBinding/SaveBindings/DeleteMacro calls are introduced; the definition/control is retired without rewriting the player's native binding configuration.

Old enchantQueue character data is pruned on load. Retired slash aliases only explain that the feature is no longer included and direct players to native Enchanting. The deleted implementation's third-party license and attribution section are removed; the suite MIT license and CC BY spell-data attribution remain. Historical changelog entries remain historical records. No Enchant Queue code is loaded from an old loose file left on disk because it is no longer referenced by the TOC.

## Verification

All 35 regression scripts pass: 480 unit-test methods plus five tooltip script checks. The 48 tests dedicated to the removed implementation were retired; 30 sound/defaults/UI tests were added. Sound checks cover category-only changes, original/manual values, list normalization and refusal, independent IDs, missing APIs, pending restoration, session/world/master recovery, quiet-fishing coexistence and real blocked-call suppression. Defaults checks cover staged execution, unsafe/unknown cursor and combat, audio gates, failed reload, preserved data, master withdrawal and fresh whole-TOC startup defaults for Mage/Warrior without legacy re-import. UI checks cover review-before-reset, separate sound controls and removal of Enchant Queue guidance.

Live Forever checks remain necessary: compare the native Pet Sounds effect on the intended companions; test verified file IDs and shared sources; disable/change zones/reload and confirm restoration. Review defaults out of combat with a clear cursor, confirm retained lists and startup choices, and inspect native Enchanting without addon controls. Preparation does not upload to CurseForge or publish the environment.
