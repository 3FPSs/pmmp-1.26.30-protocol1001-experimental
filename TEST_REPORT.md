# Test Report

This document summarizes the tests reported for the current experimental PMMP 1.26.30 / protocol 1001 build.

## Environment

- Server software: Modified PocketMine-MP experimental build.
- Target client: Minecraft Bedrock 1.26.30.
- Target protocol: 1001.
- Original private test context: BladeOfSteel server.

## Build hash

Known SHA256 for the tested PHAR:

```text
ED8F8B735BE3934C3B3E85B87F20208FD69199F9680E00AAC1ECE982048DD0
```

## Working tests

### Login

Status: working in tested environment.

The client can connect and reach the in-game state.

### World rendering

Status: working in tested environment.

Earlier render/chunk crash behavior appears fixed in the currently tested build.

### Maps with blocks

Status: working in tested environment.

Real maps can render and the client can remain in-world.

### Containers

Status: working in tested environment.

Examples tested:

- chests;
- anvils.

### Block placement

Status: working in tested environment.

Block placement works, suggesting item use on block / click block path is at least partially functional.

## Broken / incomplete tests

### Item use in air

Status: broken or incomplete.

Affected examples:

- throwable items;
- potions;
- fireworks;
- goat horn;
- wind charge.

### Food consumption

Status: broken or incomplete.

Observed behavior: hunger can update visually and then revert, suggesting a server/client state confirmation issue.

### Projectile release

Status: broken or incomplete.

Affected examples:

- arrows;
- trident;
- potion throws;
- fireworks.

## Next recommended tests

- Test block breaking.
- Test item use in air with debug logs.
- Log `InventoryTransactionPacket` transaction types.
- Log `ItemStackRequestPacket` request actions.
- Log `PlayerActionPacket` start/release/stop item use.
- Compare against upstream BedrockProtocol implementation for protocol 1001.
