# External fixes to review

This file tracks external commits suggested by the community for the remaining protocol 1001 issues.

## Plutonium-Mcpe/PocketMine-MP commits

### 1. Fix right-click item use in air

Commit:

https://github.com/Plutonium-Mcpe/PocketMine-MP/commit/113905c22bd6b934c692d0a8673b112ea649fdb2

Summary:

- File: `src/network/mcpe/handler/InGamePacketHandler.php`
- Adds `UseItemTransactionData::ACTION_BREAK_BLOCK` to the same handling path as `ACTION_CLICK_AIR`.

Reasoning from commit:

- Newer Bedrock clients / protocol 1001 may report right-click item use in air as `ACTION_BREAK_BLOCK` with trigger type `UNKNOWN` instead of legacy `ACTION_CLICK_AIR`.
- Actual block breaking is handled separately through `PlayerAuthInput` block actions.

Potentially related known issues:

- item use in air;
- throwable items;
- food consume desync;
- goat horn/fireworks/potions/wind charge behavior.

Recommended tests after applying:

- eat apple/bread;
- throw snowball/ender pearl;
- throw splash potion;
- use goat horn;
- use fireworks;
- verify normal block breaking still works.

### 2. Fix entity attack action mapping

Commit:

https://github.com/Plutonium-Mcpe/PocketMine-MP/commit/8cfa22cf5aaae0abad969c7cf3dcc3f348fdc36c

Summary:

- File: `src/network/mcpe/handler/InGamePacketHandler.php`
- Routes `UseItemOnEntityTransactionData::ACTION_ITEM_INTERACT` to `attackEntity()` together with `ACTION_ATTACK`.

Reasoning from commit:

- Bedrock 1.26.30 clients may send melee attacks on entities as `ACTION_ITEM_INTERACT` instead of the legacy `ACTION_ATTACK`.
- Right-click interactions still arrive as `INTERACT`, so attack action types can be routed to `attackEntity()`.

Potentially related known issues:

- hitting entities/mobs;
- PvP/entity combat;
- attacking players or mobs after protocol 1001 update.

Recommended tests after applying:

- hit mobs;
- hit players;
- interact with entities that should not be attacked;
- verify right-click entity interactions still behave correctly.

## Status

Not yet confirmed in this repository build. These commits should be tested before being treated as resolved.
