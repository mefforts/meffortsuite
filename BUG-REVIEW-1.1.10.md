# MeffortSuite 1.1.10 bug review

## Confirmed findings and changes

1. **Excluded loot could leak into an earlier corpse total.** A corpse with unclaimed slots remained eligible for delayed receipts. Excluding the next fishing/container window made it unavailable for matching, so matching fell back to that corpse. Regressions against 1.1.9 incorrectly displayed 110 copper from the excluded window, both while open and after closing. Excluded windows now remain receipt barriers for the existing eligibility interval, including empty/unready windows. They never produce a float or query a price. New normal windows still match their own receipts. A genuine older receipt crossing such a barrier can be omitted conservatively; chat receipts do not identify their original corpse.

2. **A newer ID fallback could steal an older exact variant receipt.** Matching previously considered each window's exact match and ID fallback together. With different item variants and pricing preferences in successive windows, the newer fallback won before the older exact link was checked. Matching now searches exact links across eligible windows first, then uses the existing unambiguous ID fallback. Excluded-window barriers apply to both passes. Regression checks both the original position and vendor/AH choice, plus normal native link-change compatibility.

3. **A reused float could repeat value already shown.** After pool reuse, the next late receipt correctly created a delta float, but another receipt updated it to the full session total. Each assigned float now records the session value displayed before it was created. Updates subtract that baseline. A reproduction forces reuse with previews, then checks additions of 20 and 20 display 40, while session diagnostics correctly show the complete total of 140.

4. **Merchant actions did not recover from prolonged combat.** Initial retries ended after two seconds. Ending combat later generated no new attempt, leaving repair and junk sales pending indefinitely until another visit or explicit retry. Combat end now schedules bounded retries for unfinished work. Completed steps remain complete, so a completed junk sale is not repeated when only repair is pending. Every attempt still checks current merchant visibility, master/preferences, combat, cursor and native permissions.

5. **Merchant retries could outlive a world transition.** The visit token previously changed only on the merchant-close event. Leaving the world now ends the visit and invalidates pending merchant callbacks, clears its money-retry deadline and cancels queued bag-sort work. A later merchant visit receives a fresh token.

## Verification and scope

The old source failed the new exclusion, late-variant, popup-reuse, combat-recovery and world-transition regressions. These now pass with the rest of the complete suite. Additional checks cover empty excluded menus, a normal corpse following excluded loot, no unnecessary probes for known excluded windows, completed merchant steps, repeated combat-end events and changed settings/closed windows.

The source review also inspected shared fishing/ranged ownership and standalone Wand integration, range-red reconciliation, quiet-audio restoration, bank transfer rechecks and single-service guards. Existing regression coverage for those paths remains in the full run; this is not a claim that every native behavior was observed in game.

Loot processing remains bounded to 12 sessions, six floats and the existing receipt/cache deadlines. It adds no idle polling, protected input changes or native menu geometry writes. Auctionator remains optional and off by default. No model/prompt/transcript material or unnecessary commentary is added to the player package.

Live checks remain necessary for Forever event ordering, native input/taint behavior, visuals and Auctionator's installed API/cache. Test corpse/container/fishing transitions and late receipts, compare totals against receipts, and test combat recovery/cancellation at a merchant. Export `/msuite export` before reloading if the client reports a blocked action.
