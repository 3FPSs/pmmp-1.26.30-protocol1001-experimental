# Developer Notes

This document collects technical notes for developers inspecting the experimental PMMP 1.26.30 / protocol 1001 build.

## Current high-level status

The build appears to have passed the earlier critical stage where clients crashed while rendering maps/chunks.

The remaining failures appear concentrated around player item interactions rather than world rendering.

## Working areas

- Login/session reaches in-game state.
- Real chunks with blocks can render.
- Basic container UI opens.
- Block placement works.

## Suspected broken area

Since block placement works but item use in air does not, `ACTION_CLICK_BLOCK` handling appears to be working while air/release/consume paths may still be broken.

Focus areas:

```text
InventoryTransactionPacket
UseItemTransactionData
ReleaseItemTransactionData
ItemStackRequestPacket
PlayerActionPacket
PlayerAuthInputPacket
InGamePacketHandler
```

## Useful debug logs

Recommended debug points:

- log incoming `InventoryTransactionPacket` transaction data class;
- log `UseItemTransactionData` action type;
- log `ReleaseItemTransactionData` action type;
- log `ItemStackRequestPacket` request/action classes;
- log `PlayerActionPacket` action IDs;
- log item in hand, hotbar slot and selected slot.

## Expected findings

If `ACTION_CLICK_AIR` or `ReleaseItemTransactionData` is missing or malformed, throwable/projectile-like items will fail.

If `ItemStackRequestPacket` is rejected or decoded incorrectly, food consumption may visually happen client-side and then revert after server resync.

## Upstream contribution path

Before opening an upstream PocketMine-MP pull request, convert findings into clean source patches and avoid submitting a binary-only report.
