# MeffortSuite 1.1.11 loot review

## Fast auto loot

The independent FastLoot module adds an account toggle under Bags, off by default. It uses the native LOOT_OPENED auto-loot decision; if that flag is absent, it requires readable native default/modifier booleans and uses their XOR. Manual loot remains manual. The pass is deferred once to the next frame so all loot-open listeners can record contents and classify inventory/fishing loot before requests begin. It also calls the float module's idempotent preparation entry point before requesting any slots.

A pass requests item, coin and currency slots in reverse order, at most once per window, with a 100-slot bound. It ignores unknown/empty slots. Each step rechecks visit generation, feature/master state and readable out-of-combat status. Combat retains native handling. Close, world transition, disabling, confirmation, supported inventory errors and refused/blocked requests stop pending work. It does not confirm binds/rolls, modify loot CVars, hide/reparent/hook the native loot window, take mouse bindings, change native frame methods or add idle polling/repeating retries.

LootSlot uses the suite's client-call guard. A synchronous blocked event records the operation, gives the existing export instructions and suppresses subsequent guarded attempts in that context until reload. Snapshot-only floats remain independent: disabling Floating loot value does not disable fast loot. Native full-bag/confirmation behavior stays available. Actual loot speed, request acceptance and protection behavior require a Forever check; simulated calls cannot establish them.

## Vendor and AH together

Show vendor + AH together is a separate account preference, off by default and captured when the loot window opens. Vendor total appears first; an adjacent 13-point muted blue-grey font shows `(AH estimate)` against the primary 16-point gold text. Both use native coin icons and the same rising/fading, click-through parent. The combined width is measured and clamped to the screen; narrow screens reduce font/icon sizes. Single-value display retains its normal styling, and pooled frames hide/reset the secondary label when reused.

The actual text is `(AH <coin amount>)`. The tooltip and settings summary identify it as an estimate. Both figures include received coins and the selected item qualities: they are alternative valuations to compare, not additive amounts. The AH side uses Auctionator automatically, with existing vendor fallback and bind-on-pickup/quest checks. The prior single-value AH preference is saved unchanged and resumes when combined display is disabled. No second Auctionator request is added: each receipt keeps one price lookup plus its native vendor value.

Both totals must be ready and within the existing bounds. A zero-vendor item with a positive AH value still displays. Missing vendor metadata follows the existing bounded request/retry path; uncertainty is not replaced with invented copper. Late receipts and reused floats retain independent baselines for both sides. Preview demonstrates the selected layout with fixed sample values. Diagnostics retain primary vendor value, AH estimate and item-source counts.

## Verification

The full suite passes: 33 regression scripts, 468 unit-test methods and five tooltip script checks. New tests cover native intent/modifier combinations, listener ordering, cancellation before/during requests, combat and missing APIs, confirmations/full bags, explicit refusal/error/blocked calls, slot compaction and integration with actual receipt/exclusion logic in both listener orders. A real Core guard test verifies the recorded operation, export guidance and blocked retry suppression.

Combined-display tests cover exact coins, mixed prices, missing/invalid/failed providers, bound items, grey filtering, zero-vendor positive-AH items, metadata waits without extra provider calls, mode snapshots, retained single-value settings, late receipts and pool reuse, limits on both sides, preview reuse and narrow-screen font/anchor geometry. Settings/Core tests verify default-off persistence and normalization. Mock geometry does not prove actual font rendering.

In Forever, test both native Auto Loot states with the modifier, normal and AoE loot, currencies, full bags, bind confirmation, fishing/containers, combat and other loot addons. Confirm unclaimed items remain usable through native controls. Compare both totals against actual coin receipts, vendor values and Auctionator's cached per-unit data. Check previews, rapid/late receipts and UI scaling. Export before reloading if a native blocked action appears. No CurseForge submission or environment publication is part of preparation.
