# Hotfix v4 summary

Latest tested playable build:

```text
PMMP_INTERACTIONS_ENTITYRENDER_HOTFIX_build2608_v4_NODEBUG.phar
```

SHA256:

```text
126A40DE6BBE3F08559F9FC74FBF10F9F5DB88D3A80BF2AA7D3061AEE0C05868
```

## Result

The v4 hotfix is the latest build marked as tested/playable in the BladeOfSteel environment.

It keeps the successful v3 interaction/entity-render fixes and removes a leftover disconnect debug warning from console output.

## Reported working

- login;
- world/chunk rendering;
- basic containers;
- block placement;
- food consumption;
- wind charges;
- bow and arrow;
- ender pearls;
- trident;
- potions;
- goat horns;
- other tested item interactions;
- projectile/entity trajectories and rendering.

## Changed from v3

Removed noisy warning printed when a client disconnects:

```text
[Blade 26.30 Debug] Client disconnected. Last outgoing packets: ...
```

This warning was diagnostic only and did not represent a server crash.

## Preserved v3 fixes

### 1. Protocol 1001 item use in air

`UseItemTransactionData::ACTION_BREAK_BLOCK` is treated like `ACTION_CLICK_AIR` in `InGamePacketHandler`.

### 2. Protocol 1001 entity attack action

`UseItemOnEntityTransactionData::ACTION_ITEM_INTERACT` is treated like `ACTION_ATTACK` in `InGamePacketHandler`.

### 3. Entity/projectile packet render restoration

The diagnostic global entity packet block in `NetworkSession` is removed so entity/projectile packets can reach clients.

## Stability note

This is still an unofficial experimental build. It is marked as tested/playable for the BladeOfSteel environment, not as an official stable PocketMine-MP release.

Recommended before wide production use:

- longer multiplayer testing;
- plugin compatibility testing;
- TPS/memory monitoring;
- source/diff publication.
