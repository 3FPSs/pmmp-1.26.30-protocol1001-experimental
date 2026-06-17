# Developer Notes

This document collects technical notes for developers inspecting the experimental PMMP 1.26.30 / protocol 1001 build.

## Current high-level status

The build appears to have passed the earlier critical stage where clients crashed while rendering maps/chunks.

The v3 local hotfix was also reported to restore item interactions and projectile/entity rendering.

## Working areas

- Login/session reaches in-game state.
- Real chunks with blocks can render.
- Basic container UI opens.
- Block placement works.
- Food consumption works in v3 local test.
- Projectile and item-use behavior works in v3 local test.
- Entity/projectile trajectory rendering works in v3 local test.

## Important findings

### Item use in air

Protocol 1001 clients may report item use in air as:

```text
UseItemTransactionData::ACTION_BREAK_BLOCK
```

instead of:

```text
UseItemTransactionData::ACTION_CLICK_AIR
```

Routing `ACTION_BREAK_BLOCK` through the same handler path as `ACTION_CLICK_AIR` restored multiple item interactions in local testing.

### Entity attack mapping

Protocol 1001 clients may report entity attacks as:

```text
UseItemOnEntityTransactionData::ACTION_ITEM_INTERACT
```

instead of only:

```text
UseItemOnEntityTransactionData::ACTION_ATTACK
```

Routing `ACTION_ITEM_INTERACT` through `attackEntity()` should be tested for PvP/mobs.

### Entity/projectile packet blocking

A previous diagnostic build globally skipped entity packets in `NetworkSession`, including `AddActorPacket`, `SetActorDataPacket` and `MoveActorAbsolutePacket`.

This prevented projectiles and item trajectories from rendering client-side.

Removing this diagnostic block was necessary for the successful v3 local test.

## Focus areas for clean patching

```text
src/network/mcpe/handler/InGamePacketHandler.php
src/network/mcpe/NetworkSession.php
vendor/pocketmine/bedrock-protocol/src/types/inventory/UseItemTransactionData.php
vendor/pocketmine/bedrock-protocol/src/types/inventory/UseItemOnEntityTransactionData.php
```

## Useful debug logs

Recommended debug points:

- log incoming `InventoryTransactionPacket` transaction data class;
- log `UseItemTransactionData` action type;
- log `ReleaseItemTransactionData` action type;
- log `ItemStackRequestPacket` request/action classes;
- log `PlayerActionPacket` action IDs;
- log item in hand, hotbar slot and selected slot;
- log outgoing entity packets while testing projectiles.

## Upstream contribution path

Before opening an upstream PocketMine-MP pull request, convert findings into clean source patches and avoid submitting a binary-only report.

Recommended split:

1. protocol 1001 item-use-in-air mapping;
2. protocol 1001 entity attack mapping;
3. removal/replacement of local diagnostic packet blocking;
4. source/diff cleanup;
5. test report and reproduction steps.
