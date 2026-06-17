# External fixes reviewed

This file tracks external commits suggested by the community for protocol 1001 issues.

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

Related issues:

- item use in air;
- throwable items;
- food consume desync;
- goat horn/fireworks/potions/wind charge behavior.

Local status:

- Tested in the BladeOfSteel environment as part of v3 hotfix.
- Reported working after applying the full v3 hotfix.

### 2. Fix entity attack action mapping

Commit:

https://github.com/Plutonium-Mcpe/PocketMine-MP/commit/8cfa22cf5aaae0abad969c7cf3dcc3f348fdc36c

Summary:

- File: `src/network/mcpe/handler/InGamePacketHandler.php`
- Routes `UseItemOnEntityTransactionData::ACTION_ITEM_INTERACT` to `attackEntity()` together with `ACTION_ATTACK`.

Reasoning from commit:

- Bedrock 1.26.30 clients may send melee attacks on entities as `ACTION_ITEM_INTERACT` instead of the legacy `ACTION_ATTACK`.
- Right-click interactions still arrive as `INTERACT`, so attack action types can be routed to `attackEntity()`.

Related issues:

- hitting entities/mobs;
- PvP/entity combat;
- attacking players or mobs after protocol 1001 update.

Local status:

- Included in the BladeOfSteel v3 hotfix.
- Needs longer PvP/mob testing, but no immediate interaction regression was reported.

## Additional local fix discovered

The successful v3 hotfix also required removing a diagnostic global entity packet block in `NetworkSession`.

The previous diagnostic build skipped packets such as:

- `AddActorPacket`
- `AddPlayerPacket`
- `RemoveActorPacket`
- `SetActorDataPacket`
- `MobEquipmentPacket`
- `MobArmorEquipmentPacket`
- `MoveActorAbsolutePacket`
- `MovePlayerPacket`
- `PlayerListPacket`

This prevented projectiles and item trajectories from rendering client-side even after item actions started working server-side.

## Final local status

The v3 hotfix was reported to restore:

- food;
- wind charges;
- bow and arrow;
- ender pearls;
- trident;
- potions;
- goat horns;
- item/projectile trajectory and rendering.

Further testing is still recommended before treating this as production-ready.
