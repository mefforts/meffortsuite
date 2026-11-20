# MeffortSuite 1.1.14

## Upload details

- File: `MeffortSuite-1.1.14.zip`
- Display name: `MeffortSuite 1.1.14`
- Addon folder: `MeffortSuite`
- Client target: WoW Forever, Interface `16001`
- Dependencies: none required; optional MeffortWand compatibility and Auctionator pricing
- License: MIT code; bundled data attribution retained

Select only a CurseForge game-version entry that matches the intended client. Availability of a matching Forever entry has not been verified; do not substitute unrelated client metadata. No project ID or upload token is needed to upload manually.

Use `CURSEFORGE-DESCRIPTION.txt` for the project page and `CHANGELOG-1.1.14.txt` for upload notes.

## Project description

MeffortSuite brings inventory, profession, quest, combat, and travel tools together in a compact settings window with familiar Blizzard-style controls.

Configure tools individually with `/msuite` or Options > AddOns > MeffortSuite. The optional login announcement appears only in chat. Preferences are retained across reloads, with account and character scope clearly marked.

- Bags and banking: floating loot value for received coins and vendor prices across all item qualities, with optional grey-only mode, Auctionator AH estimates and combined vendor/AH display, fast auto loot, native backpack free-slot count, bag sorting, junk sales, personal-gold repairs, reagent deposits, bank sorting, and per-character item inclusion/exclusion lists.
- Fishing and sounds: pole-equipped right-click fishing, optional quiet fishing audio, native pet-category muting and advanced verified sound-file controls.
- Combat: right-click ranged attacks, a conservative range warning, and Mage Arcane Blast tracking on Blizzard Tracked Buffs.
- Quests and travel: full-stack reward vendor labels, quest-prioritized dialogue hotkeys, native menu key labels, waypoint arrows, and single-option service shortcuts with Shift bypasses.
- Interface: English spell explanations, tooltip badges and palettes, rank alerts, and action-bar keybinding labels.

Install the `MeffortSuite` folder in `Interface/AddOns` and open `/msuite`. Existing saved preferences are retained. Tooltip descriptions and header parsing use English data.

Quiet fishing audio is off by default under Fishing or Sounds. It mutes music, ambience and dialogue whenever a fishing pole is equipped, without requiring a cast. Removing the pole or disabling the feature restores previous volumes; manual volume changes are retained. Sound effects and master volume stay unchanged, so other effects remain audible alongside the bite.

## Release audit

BANK-BACKPACK-REVIEW-1.1.14.md records removal of the dedicated banker shortcut, default-on fast looting and native backpack count ownership/restoration. Earlier reviews are historical records. Native game behavior, protection and rendering still require Forever validation.

## Support reports

Blocked-action notices explain the export workflow once per UI session. Players should type `/msuite export` before reloading/logging out, click **Select report**, copy with **Ctrl+C** (**Command+C** on Mac), and paste outside the game into a bug report to Mefforts. Include the triggering action and NPC/window. The report captures client-reported blocks even without a Lua exception; reported addon names do not prove the original cause.

## File changelog

Use the `MeffortSuite 1.1.14` section from `MeffortSuite/CHANGELOG.txt` for the file's changelog.

## Final checks

- Automated tests and archive checks: record results in `VALIDATION-RESULTS.txt`.
- ZIP root: exactly one `MeffortSuite/` folder; required licenses and all referenced textures included.
- Version: TOC, runtime, About, README, filename, and upload display name agree on `1.1.14`.
- Source/text audit: no conversational transcripts, prompt remnants, draft labels, or scratch files in the archive.
- In-game validation: use `VALIDATION.md`; actual protected actions, server timing, and rendering remain unverified until tested in the target client.
- CurseForge acceptance/game-version selection: confirm on the upload page. Preparing this archive does not submit or publish it.
