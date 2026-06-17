# Known Issues

This file tracks issues observed in the current experimental build.

## Confirmed / observed

### Item use in air

Using items in air may not work correctly.

Affected examples:

- throwable items;
- splash potions;
- wind charge;
- fireworks;
- goat horn usage/sound.

Likely area:

- `UseItemTransactionData`
- `ReleaseItemTransactionData`
- `ItemStackRequestPacket`
- `PlayerActionPacket`
- `PlayerAuthInputPacket`
- `InGamePacketHandler`

### Food consumption desync

Food can visually regenerate the hunger bar client-side, but the hunger state may revert afterward.

This suggests client prediction is occurring, but the server may not be confirming the action correctly.

Likely area:

- `ItemStackRequestPacket`
- item consume handling;
- inventory/food state synchronization.

### Projectile-like behavior

Items that should spawn or release entities may fail to do so.

Affected examples:

- bow/arrow;
- trident;
- splash potion;
- fireworks;
- wind charge.

Likely area:

- release item transaction handling;
- item use-in-air action handling;
- projectile entity creation.

## Confirmed working

- Client login/session can complete.
- World rendering no longer instantly crashes in tested maps.
- Chunks with blocks can render.
- Basic container interfaces can open.
- Block placement works.

## Needs more testing

- Breaking blocks.
- Teleporting long distances.
- Nether/End or additional dimensions if used.
- Mobs/entities.
- Armor/equipment.
- Creative inventory.
- Crafting flows.
- Resource packs.
- Multi-player testing with 5+ clients.
