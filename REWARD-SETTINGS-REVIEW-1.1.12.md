# MeffortSuite 1.1.12 reward and settings review

## Reward prices

Reward vendor values starts enabled under Quests and saves account-wide. It recognizes native QuestInfoRewardsFrame and MapQuestInfoRewardsFrame RewardButtons, including choice and fixed item rewards. The item link and quantity come from the matching NPC or quest-log API context. A known quest ID must agree with the active context; missing log APIs never substitute NPC or another reward-kind API.

Full-stack copper values use the native item vendor price multiplied by the displayed quantity. Invalid, fractional, nonfinite, secret and oversized values are omitted. Missing item data is requested once per item during the open interaction and revisited on item events. Unsellable items say No vendor value. Neither reward selection nor claiming is automated.

Labels use independent click-through UIParent overlays, with native coin textures and small muted text below the item name. Placement reads native button/name rectangles, scale, rendered text height and justification, and checks clipping ancestors. It does not change native names, widths, heights, anchors, extents or click handlers. Crowded names, narrow prices and unsupported geometry omit the inline label; recognized item buttons retain an exact stack value in their reward tooltip. Unknown reward layouts retain native behavior.

Discovery is bounded to 80 native buttons. Post-hooks and queued refreshes follow native rebuilds; open-window-only updates follow geometry and item readiness. Scroll hooks immediately withdraw overlays before a queued clipping check. Row/parent hides, quest completion, master/feature disable, combat and world transitions withdraw labels. Generation checks prevent a queued refresh from reviving a closed interaction. Combat performs no reward/item/geometry queries, and no idle update loop remains when panels close.

The inspected upstream item templates use 147×41 large reward buttons and 134×30 small buttons. Tests cover those dimensions directly: a large one-line name permits a label; a compact button retains its tooltip value. Mainline and Vanilla QuestInfo sources both use RewardButtons with per-button type/index/objectType. These reference contracts do not establish identical Forever rendering.

## Configuration guidance

Every feature page has visible Start here guidance. Related controls have section headings. Fast loot, value modes, previews and the new duration control are grouped under Bags > Looting & loot value. Banking remains on the Bags page. Quests groups reward prices, dialogue shortcuts and service shortcuts. Professions separates fishing audio from enchanting.

The ? button stays available on home and feature pages. Setup & help links directly to common tasks, explains immediate choices versus text-field saving, identifies contextual prerequisites and gives player-facing report-copy instructions. Back preserves the actual previous page and scroll; drafts survive help navigation. Report copying stays available while the master is off. Merchant retry identifies an open merchant as its prerequisite and rechecks that state on click. Launcher counts include reward labels, fast loot and quiet audio.

Commands /msuite loot, /msuite rewards and /msuite bags open the corresponding pages. /msuite help opens setup guidance when available; status/chat fallback remains available. Opening these pages does not toggle features or take gameplay actions.

## Slower floats

The default rise/fade duration increases from 2.4 to six seconds. The existing 36-unit easing now rises more gently over the longer lifetime, with a steady first 65% and gradual final fade. Float duration offers 2–12 seconds and saves account-wide. Each new float/preview captures its duration, so changes cannot jump or restart an animation already in progress. The six-float pool, receipt verification, dual totals and independent late-receipt baselines remain intact.

## Verification

The complete run passes 34 regression scripts: 498 unit-test methods and five tooltip script checks. New reward regressions forbid native layout/name writes and claiming; exercise stack values, contexts and missing APIs, stale IDs/reuse/currencies, cache waits, compact/wrapped names, oversized prices, clipping/scroll withdrawal, queued-close cancellation, combat/world/master cleanup, invalid/secret/zero values, tooltip rebuilding, forbidden objects, late discovery and scale conversion. Settings tests cover help/back with drafts, reward toggles, duration controls, merchant rechecks and master-off report copying. Core tests cover routes, preferences and diagnostics; float tests cover longer reading/fade, bounds and stable existing animation timing.

In Forever, compare choice/fixed stack labels against native prices; test long names, compact/log rewards, scrolling, item delays, combat and UI scale. Confirm reward geometry and selection are unchanged. Navigate help with a draft, inspect unavailable actions and preview six/custom-second floats. Native typography, protection, event ordering and server behavior remain live checks. Preparation does not submit to CurseForge or publish the environment.
