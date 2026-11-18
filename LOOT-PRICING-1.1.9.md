# MeffortSuite 1.1.9 loot pricing review

## Behavior

Bags > Use Auctionator AH values is an account preference and starts off. When enabled, eligible self-loot receipts use Auctionator's cached per-unit copper estimate multiplied by the confirmed received quantity. Real coin receipts remain unchanged. The existing all-quality/grey-only choice still applies. Both preferences are captured when each loot window opens.

The adapter calls `Auctionator.API.v1.GetAuctionPriceByItemLink("MeffortSuite", fullItemLink)`. It preserves link variants and accepts only positive finite whole-copper prices within the existing display bound. Missing/zero/negative/fractional/nonfinite/secret/oversized prices and provider errors use normal vendor fallback. Bind-on-pickup and quest items also use vendor values. It does not substitute generic item-ID prices, inspect Auctionator's private database, initiate scans, register background price callbacks or add polling.

One query is allowed per included receipt after item metadata is ready; that receipt's price stays fixed. A later loot window can obtain an updated price. Uncached native item metadata uses the existing one-request/bounded retry path. Unresolved vendor fallback still omits the batch rather than inventing a value. Oversized aggregate values receive an explicit display-limit status. Existing corpse positioning, pooled animations, receipt verification, loot exclusions and master/feature cleanup remain in place.

Auctionator is an optional TOC dependency. Its absence leaves vendor totals working and preserves the saved preference. The settings summary reports a missing item-link API. Diagnostics include the selected pricing mode and the last displayed total's AH/vendor item counts.

## API evidence

The public item-link call and per-item multiplication are independently demonstrated by WarbankValue, a consumer with a Camelot TOC, at commit `764da5eaef5fb9431372f797afa80bdc563332fe`: `Scanner.lua` lines 240–255 and 421–423. Its full-link call includes a caller identifier. ForeverProfit's `Prices.lua` documents and uses the same `Auctionator.API.v1` family on Interface 16001, although it uses the generic item-ID endpoint. Neither consumer is bundled or copied into this release.

- https://github.com/danilomagro/warbankvalue/blob/764da5eaef5fb9431372f797afa80bdc563332fe/Scanner.lua#L240
- https://github.com/konderziller/ForeverProfit

The installed Auctionator build and scan cache have not been inspected in the game. Builds lacking the public item-link endpoint use vendor fallback. Cached AH estimates depend on Auctionator's data and do not predict completed sales.

## Verification

New regressions exercise variant links, stack counts and exact coins; default-off behavior; missing/unsupported/failed providers; invalid and secret prices; grey filtering; bind-on-pickup/quest items; zero-vendor auctionable items; mixed sources; mid-window toggles; stable receipt pricing and next-window refresh; metadata loading; bounded failed-provider calls; late provider loading; unreceived/other-player loot; overflow; preference normalization and settings persistence. The complete suite's output is retained in VALIDATION-RESULTS.txt.

In Forever, compare a received tradeable stack with Auctionator's per-unit tooltip value, then repeat with coins, a missing price, bind-on-pickup items and grey-only mode. Turn the toggle off and disable Auctionator in turn to check vendor behavior. Live API/data/rendering checks remain separate from the simulated tests.
