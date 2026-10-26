# Action bar

Public patterns for server messages displayed in the action bar on SuperAwesome.
These patterns are loaded separately from `chat/message_types.tsv`; an action-bar
pattern must never be applied to player chat.

`message_types.tsv` uses the same two-column format as the chat data:

- `messageRegex`: a Java regular expression matched against the entire message.
- `MessageType`: a stable message identifier understood by the addon.

The addon removes Minecraft formatting codes and trims surrounding whitespace
before matching. Patterns should be mutually exclusive. Do not change an
identifier without updating the addon; unknown identifiers are ignored. Multiple
patterns may use the same identifier when the server has alternate wording.
Changes are loaded when the addon starts again.

## mcMMO activations

Each of the eight abilities has its own `MCMMO_<ABILITY>_ACTIVATED` identifier.
The identifier selects the ability; the pattern needs no capture groups. Message
wording belongs here, while ability durations and cooldowns remain in the addon.
Only match the player's activation confirmation, never readiness, exhaustion,
or ability-expired messages. Repeated confirmations do not restart a running timer.

The `**GIGA DRILL BREAKER ACTIVATED**` message is confirmed from an in-game
screenshot. The other seven entries use the same expected mcMMO format and still
need in-game confirmation; update their patterns here if their wording differs.

Merge these patterns before distributing the addon version that loads this file.
Older addon versions continue using their existing chat patterns.
