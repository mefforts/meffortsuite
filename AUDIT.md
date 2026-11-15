# MeffortSuite 1.1.4 release audit

The banking inclusion list is additive to ordinary crafting-reagent deposits and uses the same exact-name or numeric-ID format as exclusions. Keep in bags wins over both inclusion forms. The list defaults to empty and is stored per character; existing preferences and exclusions are retained.

The bank controller uses the selective transfer path whenever either list has entries. Missing selective capabilities or unavailable character-bank access refuse the operation; the code does not fall back to a bulk reagent request. Native auto-deposit support is checked for bulk requests, while manual selective transfers use character-bank access checks where available. The automatic coordinator waits for selective completion and performs bank sorting afterward, including long batches.

Eligibility is rechecked before each pickup. An explicit inclusion may override an absent or false reagent flag, but still requires a known item name and valid stack limit. Exclusions are checked first. Partial-stack splitting, destination readback, source/destination count confirmation, compatible-source restoration, and bounded retries remain in place. The bank still enforces its own item restrictions.

The Bags settings page labels the additional list Also deposit and explains exclusion priority, character scope, and list-change cancellation. Both fields retain independent drafts. Deposit items now and /msuite bank now use the same selection. Commands, status messages, and documentation are written for players without conversational instructions or prompt remnants.

The 1.1.3 dialogue changes and blocked-action diagnostics are retained. Unrelated Lua modules, spell data, textures, bindings, and licensing are unchanged. The package builder validates versions, the explicit TOC manifest, residue, permissions, and ZIP integrity.

Automated inventory tests simulate slot updates and transfer ordering; they do not emulate engine protection, server permission decisions, or live client timing. In-game checks are listed in VALIDATION.md. This archive is prepared for testing and is not submitted to CurseForge or published as a cloud environment.
