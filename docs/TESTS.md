# Suggested Test Plan

Use this checklist to test protocol 1001 behavior.

## Baseline

- Start server with no plugins.
- Join with Minecraft Bedrock 1.26.30.
- Confirm server reaches in-game state.
- Watch console for packet decode errors.

## World tests

- Join void world.
- Join flat world.
- Join a real map with blocks.
- Walk around spawn area.
- Teleport far away.
- Relog several times.

## Block tests

- Place common blocks.
- Break common blocks.
- Place blocks against different faces.
- Test blocks with tile entities.

## Container tests

- Open chest.
- Open anvil.
- Open furnace.
- Move items between inventory/container.

## Item interaction tests

- Eat apple/bread.
- Throw snowball/ender pearl.
- Use splash potion.
- Use bow and arrow.
- Use trident.
- Use fireworks.
- Use goat horn.
- Use wind charge if available.

## Debug targets

Log these packets/classes while testing item interaction:

- `InventoryTransactionPacket`
- `UseItemTransactionData`
- `ReleaseItemTransactionData`
- `ItemStackRequestPacket`
- `PlayerActionPacket`
- `PlayerAuthInputPacket`
- `InGamePacketHandler`

## Multiplayer tests

- 2 players join.
- 5 players join.
- Players move around each other.
- Players place/break blocks near each other.
- Players use projectiles near each other.

## Performance tests

- Monitor TPS.
- Monitor memory.
- Watch for increasing garbage collection time.
- Relog multiple times.
