# MeffortSuite 1.1.4e release audit

Floating loot value now includes vendor prices for every item quality by default. The account-wide Include all item qualities toggle under Bags returns to grey-only totals when off. The existing display toggle, preview, exact coin denominations, receipt confirmations and bounded animation pool remain available.

Each loot window records its quality mode when opened. Confirmed receipts inherit that mode, so changing the preference cannot mix accounting rules inside the same pending total. In all-item mode, cached and asynchronously loaded vendor prices are accepted across qualities. In grey-only mode, known non-grey loot contributes zero without requiring price metadata. Zero vendor prices contribute zero in either mode, while missing, invalid or fractional prices use the existing bounded wait and omission behavior.

Coins remain the player's confirmed loot receipts, including the player's share of split/guild loot. Item quantities are bounded by the recorded loot slots and deduplicated chat IDs. No-sell values are zero. AoE loot remains a combined interaction total. Unclaimed items, other players' receipts, fishing and inventory-item loot retain their existing handling.

Only the loot module, core preference normalization, settings labels/controls, numeric patch version and player documentation change in this release. Other feature modules, textures, bindings, licensing, combat query guards and dialogue geometry fixes retain their previous source bytes. The nameplate/cursor fallback, private UIParent-owned floats and idle cleanup are retained.

Four new accounting scenarios and a settings test cover the added mode. Saved false preferences are checked through core login normalization. The complete runner also checks previous receipt, localization, cache, combat, UI ownership and packaging regressions. Client verification remains necessary for actual Forever loot timing, native rendering and prices. The package is prepared without submitting to CurseForge or publishing a cloud environment.
