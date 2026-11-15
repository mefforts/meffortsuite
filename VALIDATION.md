# MeffortSuite 1.1.4a validation

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
