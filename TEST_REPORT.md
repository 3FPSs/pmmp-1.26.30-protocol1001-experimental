# Test Report

This document summarizes the tests reported for the current experimental PMMP 1.26.30 / protocol 1001 build.

## Environment

- Server software: Modified PocketMine-MP experimental build.
- Target client: Minecraft Bedrock 1.26.30.
- Target protocol: 1001.
- Original private test context: BladeOfSteel server.

## Original build hash

Known SHA256 for the original tested PHAR:

```text
ED8F8B735BE3934C3B3E85B87F20208FD69199F9680E00AAC1ECE982048DD0
```

## Latest tested playable build

Latest build tested by BladeOfSteel:

```text
PMMP_INTERACTIONS_ENTITYRENDER_HOTFIX_build2608_v4_NODEBUG.phar
```

SHA256:

```text
126A40DE6BBE3F08559F9FC74FBF10F9F5DB88D3A80BF2AA7D3061AEE0C05868
```

v4 is based on the successful v3 hotfix and removes the leftover disconnect debug warning from console output.

## Previous v3 hotfix test

```text
PMMP_INTERACTIONS_ENTITYRENDER_HOTFIX_build2608_v3.phar
```

SHA256:

```text
37B4893FF0DF2A8F6D7219CB550B935792592FC353E74694E099CE583ADE936C
```

## Working tests

### Login

Status: working in tested environment.

The client can connect and reach the in-game state.

### World rendering

Status: working in tested environment.

Earlier render/chunk crash behavior appears fixed.

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

Block placement works.

### Item interactions

Status: working in latest local hotfix test.

Reported working:

- food consumption;
- wind charges;
- bow and arrow;
- ender pearls;
- trident;
- potions;
- goat horns;
- other tested items.

### Projectile/entity visuals

Status: working in latest local hotfix test.

Reported working:

- projectile trajectories;
- item/projectile render behavior;
- entity/projectile visual travel.

### Console output

Status: improved in v4.

The leftover v3 warning:

```text
[Blade 26.30 Debug] Client disconnected. Last outgoing packets: ...
```

was removed from the v4 build.

## Important fix notes

The latest successful test included:

1. item-use-in-air mapping for protocol 1001;
2. entity/projectile packet render restoration;
3. removal of noisy disconnect debug output.

The second point was important because a prior diagnostic build still blocked entity packets such as `AddActorPacket`, `SetActorDataPacket` and `MoveActorAbsolutePacket`, which prevented projectile visuals from rendering client-side.

## Next recommended tests

- Test longer multiplayer sessions.
- Test PvP with multiple players.
- Test mobs/entities under load.
- Test armor/equipment edge cases.
- Test crafting and creative inventory.
- Test resource packs.
- Monitor TPS/memory over time.
- Prepare clean source patch/diff before upstream discussion.
