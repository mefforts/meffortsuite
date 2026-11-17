# MeffortSuite 1.1.5 validation

Automated checks and client validation are separate. Run `python tests/run_tests.py` from the repository to see the current automated results. An automated pass is not evidence of taint-free or server-confirmed behavior.

## Implemented coverage

- Saved Compare mode and master toggles, resource-warning preservation, owned tooltip cleanup.
- Exclusion changes, cancellation callbacks, partial-stack splits, safe source restoration, delayed slot updates, bounded timeouts, cursor/combat/bank closure, missing APIs, sort option changes, and merchant money retries.
- Verified enchant staging failure/async recipe selection, master gating, target/recipe readback, owned cast tracking and confirmations, queue scrolling/undo, invalid saved entries and missing capabilities.
- Exact localized macro identity, custom/account macro preservation, secure binding ownership/state cleanup, fishing release/failure handling, unsupported-API fallbacks.
- Arcane visibility/layer/scale/cache, hidden cast tracking, range controls, action-label preview/drag behavior.
- Settings history, full-row toggles, drafts and apply/discard, master counts, contextual action rechecks, viewport scaling, and page construction.
- Space quest priority without changing numbered menu order; single-line keys in a left column, quest-greeting and gossip anchors, named legacy icons, paired/center anchors, safe single-line fallback, native icon preservation, native wrapped-title spacing, native-layout restoration, live ScrollBox membership, and row reuse/scroll/combat cleanup.
- Single-option shop/trainer/bank/flight shortcuts with quest/cost/confirmation guards, Shift/master gates, and coordinated legacy handlers.
- Native caption overhang and icon texture padding; engine-normalized anchors, applied-layout ownership, and repeated refresh/disable restoration without accumulating insets.
- Whole-TOC load/login and master transitions with optional APIs absent.

## Compatibility boundaries

Target: WoW Forever, Interface 16001. The interface declaration remains unchanged. No claim is made for other WoW products or server builds.

- Unconfirmed enchant results pause for player verification. Check result never crafts; it offers Count complete / Keep paused / Nothing applied. Missing popup support keeps the operation paused with native-control guidance.
- Enchant Queue requires actual recipe and item-allocation readback, a verifiable one-craft quantity, secure state handling, and timers. If unavailable, it refuses the queued action and directs the user to Blizzard's craft controls. It does not guess an allocation or fall back to unverified clicks.
- Selective banking leaves unidentified items and non-reagents without an explicit inclusion in bags. Partial-stack transfers require the split API; confirmation requires matching source and destination updates. Changing exclusions stops future steps but cannot reverse an already-sent transfer request.
- Combat-safe quest/fishing withdrawal uses Blizzard restricted binding ownership and state/visibility handlers. Quest ownership remains under UIParent; native dialogue frames are not made ancestors of the protected owner. Actual Forever support must be checked in-game. Right-click ranged preference changes requested during combat remain pending until legal after combat.
- Spell description/header parsing remains English. Numeric item/NPC/weapon identities and localized spell lookups improve compatibility without pretending the prose is translated.
- UI layout tests use simulated geometry and cannot establish actual font wrapping, clipping, texture appearance, or high-DPI behavior.

## Added 1.1.3 checks

- Native extent calculators and sizing prototypes remain untouched. Labels skip titles wider than the available inset and do not force ScrollBox updates. Row reuse restores original width and native height.
- Blocked, forbidden, macro, and generic interface-failure events remain available in a bounded session report without a Lua exception. Tests cover localized error detection, source attribution, repeated-event grouping, optional-provider failure, and secret-value handling.
- The copy window opens only from an explicit command or settings action, selects report text, clears focus on close, and scales to smaller viewports. Report wording is player-facing and contains no conversational instructions.

## Added 1.1.4 checks

- Explicit non-crafting inclusions supplement reagents using exact names or numeric IDs; exclusion names and IDs override either inclusion form.
- Both lists are per character, normalized independently, and have independent settings drafts and save/discard behavior.
- List-only automatic deposits use the selective coordinator, including batches longer than the native bulk-deposit settle interval. Sorting waits for completion.
- Tests cover unknown reagent classification with explicit inclusion, unavailable stack metadata, partial and non-stackable items, bank-access loss, rejected placement, list removal during a transfer, and missing selective support without native bulk fallback.
- In game, verify a small included item, an item on both lists, a non-stackable item, and a changed list while the bank remains open. Confirm saved character scope, normal bank restrictions, and manual/automatic deposits.

## Added 1.1.4a checks

- Existing accounts receive one chat announcement per login or reload, including when the suite master switch is off. An explicit false preference suppresses it; malformed preferences return to the enabled default.
- Native Settings canvas registration prefers the modern API, supports a legacy fallback, retries on addon loads if the API is delayed, and registers only once without polling or opening a window.
- The launcher uses the existing suite settings window and respects the native Close confirmation for unapplied changes. The native checkbox and About toggle share the saved account preference.
- In game, confirm the AddOns category is listed, the launcher opens above the game after closing Options, and native unapplied graphics changes still receive their normal confirmation. Check chat on login/reload with the announcement on and off, and verify small-screen text wrapping.

## Added 1.1.4b checks

- Ten new tests cover late caption/icon displacement, unchanged-anchor visual drift, width resets, invalid immediate placement, paused-label lifetime, close-before-refresh cleanup, external position/width ownership, unsupported baseline spacing, and fractional visual rounding.
- When an owned inset becomes unstable, restore native geometry, pause that row's label for the conversation, and retain its keyboard binding. Do not recapture the modified row as a new baseline or repeatedly retry it. Stable rows remain decorated.
- In Forever, test Koma's single bank choice with the bank shortcut bypassed by Shift. Leave the menu open, hover and click options, close/reopen rapidly, and repeat with available/active/long quests and other UI addons. Verify that bank text remains readable near its native icon, numbers never push text to the right edge, and skipped numbers retain their keyboard behavior. Check combat entry/exit and UI scale changes.

## Added 1.1.4c checks

- Interaction and item probes do not run in combat. Supported spell-range queries remain active; a blocked query becomes unknown rather than an out-of-range result.
- Twelve focused tests simulate native blocked events without Lua exceptions, 80 repeated requests, per-operation/combat-context suspension, nested scope restoration, bounded stack capture, unavailable/secret stacks, delayed-event correlation, supported and refused spell range, and camera start/release handling.
- A synchronous blocked event records the wrapped call and suppresses its later requests in that combat context until reload. A deferred event records recent calls within one second as correlation only and does not disable an unproven source.
- A blocked owned camera release stops its frame polling and retries once after combat. Stored ranged mode and macro action remain intact. Exports include applied mode, pending changes, camera status, and the range-warning preference.
- In game, test the same combat that produced UNKNOWN(), with right-click attacks, camera press/hold/release, the range warning on/off, different targets, UI hover, and combat entry/exit. Export before reloading if the failure repeats. Confirm camera release, spell range behavior, and that the report identifies the call or bounded stack when the client supplies it. Automated events do not establish real engine delivery timing or a confirmed taint source.

## Added 1.1.4d checks

- Twenty-five focused loot tests cover exact coin denominations and stacked grey vendor prices, non-grey exclusion, missing cache data and bounded requests, unknown-price omission, grouped/split/guild money, chat-line deduplication, repeated ready/open events, full bags and other players, localized positional messages and native money-texture formats, invalid values and variants, manual/late/rapid loot windows, nameplate/cursor positioning and scale, combat query withdrawal, idle animation cleanup, bounded popup reuse, previews, master/feature disable, and container/fishing exclusion.
- Whole-TOC tests build the Bags page and open the explicit preview, then verify immediate master-disable cleanup on private UIParent-owned frames. Settings tests verify the saved toggle and preview availability.
- In Forever, test auto-loot and manual looting with only coins, only greys, mixed qualities, grey stacks, full bags, split money, AoE loot, rapid corpse changes, an uncached grey item, and a second player looting nearby. Compare displayed values with the receipt amounts and per-item vendor values. Confirm how the server batches money receipts into money slots; live event order is not established by the mocks.
- Judge the font, native coin textures, rise, fade, screen clamping, and placement using Bags > Preview loot value, then real corpses with nameplates on/off and multiple UI scales. Confirm the cursor fallback and that the overlay remains click-through. Screen coordinates are not world anchoring, and hidden corpses cannot be tracked through camera movement.
- Confirm the feature and master switches clear all active floats and pending totals, with no automatic popup at login and no idle OnUpdate work after animations finish. Keep the existing combat-failure checks enabled; the feature never reparents, anchors to, or changes native nameplates.

## Added 1.1.4e checks

- All item qualities contribute confirmed quantity times integer per-item vendor value by default. Actual loot money is still added; zero vendor prices contribute zero.
- Four new loot scenarios cover qualities 0 through 8, stacked quantities and zero-value items, both directions of a mode change during a loot window, and uncached non-grey prices. The previous grey-only checks now select that mode explicitly.
- The Bags quality checkbox and summary persist across navigation. Saved false preferences survive core normalization and login. Each loot window snapshots its mode, so a changed preference affects the next window without altering pending receipts.
- In Forever, loot coins and mixed grey/white/green/blue/purple items, verify quantities and vendor prices, switch to grey-only mode, and repeat. Check zero-value quest items, item-cache delays, and changing the mode while a loot window remains open. Confirm the displayed total follows the mode captured when that window opened.

## Added 1.1.4f checks

- Ten new action-text tests reproduce native range-color updates, styling/binding/page refreshes while red, native return-to-range behavior, disabling and re-enabling styles, initial-red capture, font methods that reset color, user-selected red, combat write deferral, secret RGB/alpha, late native APIs, hook deduplication, pet/multibar warnings, hidden range indicators and unmanaged buttons. Eight scenarios expose missing safeguards in the previous 1.1.4e source.
- Range-state colors come from Blizzard's existing range-indicator update. The addon adds no range polling or new protected action queries. Hooks record readable native colors; all custom color and geometry writes remain outside combat. Unknown colors are left untouched.
- A lexical comparison confirms that comment cleanup leaves executable tokens and string literals unchanged in other feature modules. Model/prompt scans include the entire spell data, shipped text, secure strings and comments. Required MIT and CC BY notices remain included.
- In Forever, configure a distinctive custom bar-text color, move into/out of range repeatedly, change target, page and bindings, open/close settings and change fonts, and toggle styling/master while red. Repeat on pet and multibars, in combat and outside combat. Verify native red remains visible and ordinary colors resume appropriately. Other action-bar addons can affect native update timing; actual rendering and taint remain client checks.

## Added 1.1.4g checks

- Double-click tests capture binding ownership before mouse-down delivery, then dispatch the protected action on release. They cover camera-hidden focus, single-frame and frame-list APIs, explicit UI rejection, unknown focus, long holds, expiry, combat, equipment changes and queued callback cancellation. Actual client input ordering remains an in-game check.
- Coexistence tests load the actual local MeffortWand 1.0.4 modules and both shared-library load orders. Equipping a pole leaves no ranged owner; fishing temporarily owns only its binding; removing the pole restores exactly one correct owner without editing wand macros. The mock retains native state attributes after unregistering a driver.
- Service tests cover hidden IDs with zero-based native order indexes, absent icon overrides, delayed options, close-before-retry, duplicate-event coordination, Shift release after opening, cost/confirmation rejection, and dedicated Orgrimmar banker selection with general shortcuts disabled.
- Quiet-audio tests verify the per-character opt-in, only the three named channels changing, restoration after channel stop/disable/master-off/combat/logout, preserved manual changes, validated saved recovery, retry after failed restoration, other-unit filtering and no idle polling. Sound effects and master volume remain unchanged.
- In Forever, equip a pole and double-right-click the world, turn the camera with a single click, click UI and the bobber, hold the button, change equipment and enter combat mid-gesture. Repeat with standalone MeffortWand enabled/disabled and Suite ranged modes. Confirm ranged controls return after removing the pole.
- Visit Soran, Karus and Koma with general service shortcuts both on and off; verify one bank opening and Shift bypass. Test a single-option vendor, a quest-bearing NPC, repeated menu refreshes and closing quickly.
- Enable Quiet fishing audio under Professions. Compare the three channel volumes before/during/after fishing, cancel a cast, catch a fish, adjust a volume manually, toggle the feature/master, reload and relog. Confirm effects retain their existing volume and the bite remains audible. Native sound-channel behavior and logout persistence need client verification; a hard crash cannot guarantee newly saved recovery data.

## Added 1.1.4h checks

- Reproduce successful empty focus queries while native camera turning is still inactive. Cover empty arrays, nil returns, modern and legacy APIs, UIParent background, known UI frames, absent APIs and failed queries. The simulated second hardware release reaches the already-bound casting button once.
- Quiet audio activates before any spell has been cast. Equipment changes control muting/restoration during combat and outside combat. Casting, channel stop/failure, looting and other-unit inventory events cannot switch it off. Sound effects and master volume stay unchanged; manual adjustments and failed-restoration recovery remain covered.
- The whole-TOC master-disable test now runs without any channel API to verify restoration and retention of the character preference. MeffortWand ownership checks continue to exercise the actual local standalone modules in both load orders.
- In Forever, confirm double-right-click casts with the camera stationary and that ordinary UI clicks, single camera clicks and bobber clicks retain their expected behavior. If casting still fails, /msuite fishing status now distinguishes empty background from unavailable focus APIs and includes physical casting-button release counts.
- Enable quiet audio with a pole already equipped before casting, cast and cancel repeatedly, loot the bobber, enter combat, remove/re-equip the pole, toggle the feature/master and reload. Check the three affected channels restore on removal/disable and manual adjustments survive. Other effects remain audible at their current volume.

## Added 1.1.5 checks

- Both blocked and forbidden events provide numbered Windows/Mac export, copy and paste instructions, the Mefforts recipient, triggering-action/NPC/window context and reload/logout warnings. Eighty repeats generate one notice even with the suite master and login message disabled.
- A blocked tracked Suite call produces help when the client attributes it to another addon. Unrelated addon/macro events remain recorded without Suite notices. Generic localized interface warnings, unavailable/secret values, bounded histories and no-Lua-error reports retain coverage.
- The explicit report window includes constrained multiline help, automatic text selection, Select report, focus cleanup, window reuse and small-screen scaling. It never opens automatically from an error event. Exported report contents use player-facing sharing instructions.
- In Forever, verify chat visibility and the numbered steps after a naturally occurring blocked action. Use /msuite export before reload, click Select report and copy/paste into an external text editor. Check the complete report, the three help lines at different UI scales, Mac shortcuts if applicable, and that repeated events do not flood chat or open windows. No deliberate protected-action failure is needed to preview the export window.
- The user reports that the 1.1.4h fishing/audio changes appear to work in-game. This supports those specific changes; it does not establish complete client validation of every feature or taint path.

## Required in-game checks

Record the client build and test with Lua errors visible. Use /msuite export before reloading if an interface failure occurs; a Lua error is not required. Use a test character and inexpensive materials for inventory/crafting checks.

1. **Load and settings:** clean install, existing 1.1.1 SavedVariables, second character, explicit OFF settings, relog/reload; all launcher pages; Home/Colors/nested Back; Enter/Apply/Discard/Escape; closing/reopening unsaved drafts; multiple resolutions and UI scales. Verify pending combat status.
2. **Quest keys:** gossip/quest accept/progress/reward screens; NPC moving away/death; combat starts while a dialogue is open, then it closes. SPACE and 1–9 must immediately return to their normal actions. Test available > ready > unfinished quest priority while numbered choices keep menu order; inline labels on legacy and scrollable menus, inherited layers, anonymous rows, and menu-label diagnostic counts; bank/flight/general service shortcuts with Shift bypass, quest choices, ambiguous menus, repeated events, and disabled preferences.
3. **Fishing/ranged:** invalid fishing location, no spell knowledge, long right-button hold, single/double mode, UI clicks, bobber loot, modifiers, combat during a press; each weapon type and localized spell name; macro name collisions/full slots/deletion; standalone MeffortWand coexistence. Verify original camera behavior and no lingering override.
4. **Enchanting:** ready recipe, asynchronous recipe load, target moved/equipped/sold, allocation mismatch, empty reagents, multi-craft quantity previously selected, wrong recipe type, failed/interrupted cast, matching manual cast, popup cancel/confirm, queue edits/clear/undo, master disable, close/reopen, combat starts, keyboard and mouse activation. Confirm one intentional action per input and exact queued counts. Specifically measure SENT/START/STOP/SUCCEEDED event order and delayed acknowledgement behavior.
5. **Banking:** native and excluded deposits, uncached item info, explicit non-reagents, multiple partial stacks, no split API, full bank, locked stacks, occupied cursor, exclusion change mid-job, late bag updates, early bank closure, rapid reopen. Confirm no item swaps and safe restoration/clear error when a move is rejected.
6. **Merchant:** junk sale funding repair immediately and asynchronously, insufficient funds, vendor cannot repair, close before retry, master change, combat. Verify actual gold/durability/item changes; request status alone is insufficient.
7. **Combat display:** CDM hidden ancestors, independent scale, edit-mode movement, unrelated dialogs above it, aura expiration/reset, duplicate cast events, feature/master off/on in combat, combat reload. Validate estimates against the actual aura. Test range warnings with friendly/hostile targets and unavailable probes.
8. **Tooltips/action labels:** insufficient resources, missing reagents, forms/range warnings, compare across reload/master off/on, other addons refreshing tooltip text, action-label drag/release, failed styling and restoration after disable.

Repeat relevant checks with supported standalone addons and common UI/bag replacements. Record actual client results before uploading the release. Automated results do not establish in-game completion.
