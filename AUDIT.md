# MeffortSuite 1.1.3 release audit

The dialogue module leaves Blizzard's extent calculator, sizing prototypes, and ScrollBox update callbacks unchanged. It adds a left number only when the native caption can keep its current line layout. Long or unsupported titles retain native geometry and keyboard shortcuts. Row recycling restores an owned inset and recalculates that row's original text height without requesting a full ScrollBox update.

The restricted binding owner stays under UIParent. Native dialogue frames and their buttons no longer become ancestors of that protected owner. Native close hooks clear bindings out of combat; the restricted combat driver clears them during combat. These changes remove two identified risk paths; they do not establish the origin of every client-side taint report.

Diagnostics now record ADDON_ACTION_BLOCKED, ADDON_ACTION_FORBIDDEN, MACRO_ACTION_BLOCKED, MACRO_ACTION_FORBIDDEN, and the generic ERR_CLIENT_LOCKED_OUT warning. Generic warnings are matched using native localized constants or GetGameMessageInfo, with no English-message parsing. Histories are session-only, bounded, and aggregate consecutive duplicates. Reports state when a source or action was not supplied and distinguish client events from Lua errors. A single local notice directs players to the report command; capture does not open a popup.

The /msuite export and /msuite report commands open an owned copy window. The About page provides the same action. Report text contains build/version details, feature preferences, menu-label status, recent client events, and guarded-operation errors. It contains no prompt instructions or conversation transcript, and is never sent to other players automatically. Optional tooltip-status failures are isolated so they do not prevent blocked-action exports.

The source and package guards check numeric release versions, TOC membership, XML, residue, file permissions, and ZIP integrity. Player-facing command help, report text, settings labels, and documentation were reviewed for direct, application-appropriate wording. Legal notices, spell data, textures, and unrelated modules are retained.

Automated layout and protected-state tests use mocks. They cannot establish actual font rendering, hardware input, engine taint state, server behavior, or the cause of an unrecorded prior warning. Target-client checks are listed in VALIDATION.md. The archive is prepared for testing; it is not submitted to CurseForge and the cloud environment is not published.
