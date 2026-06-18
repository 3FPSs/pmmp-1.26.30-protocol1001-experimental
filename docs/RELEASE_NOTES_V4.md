# Release notes - v4 NODEBUG

## Release

https://github.com/3FPSs/pmmp-1.26.30-protocol1001-experimental/releases/tag/build2608-protocol1001-v4-nodebug

## Build

```text
PMMP_INTERACTIONS_ENTITYRENDER_HOTFIX_build2608_v4_NODEBUG.phar
```

SHA256:

```text
126A40DE6BBE3F08559F9FC74FBF10F9F5DB88D3A80BF2AA7D3061AEE0C05868
```

## Summary

This is the latest tested/playable experimental build for the BladeOfSteel 1.26.30 / protocol 1001 environment.

It preserves the successful v3 item interaction and entity/projectile render fixes, and removes a leftover debug warning from console output when clients disconnect.

## Changes from v3

- Removed noisy disconnect debug warning:

```text
[Blade 26.30 Debug] Client disconnected. Last outgoing packets: ...
```

## Fixes preserved from v3

- Protocol 1001 item use in air: `ACTION_BREAK_BLOCK` is handled like `ACTION_CLICK_AIR`.
- Protocol 1001 entity attack mapping: `ACTION_ITEM_INTERACT` is handled like `ACTION_ATTACK`.
- Entity/projectile packets are allowed to reach clients, restoring projectile visuals and trajectories.

## Reported working

- login;
- world/chunk rendering;
- basic containers;
- block placement;
- food;
- wind charges;
- bow and arrow;
- ender pearls;
- trident;
- potions;
- goat horns;
- other tested item interactions;
- projectile/entity rendering and trajectory.

## Stability status

This build is marked as:

```text
tested/playable in the BladeOfSteel environment
```

It should still be considered:

```text
unofficial experimental / community testing build
```

## Still recommended

- longer multiplayer testing;
- plugin compatibility testing;
- TPS and memory testing;
- source/diff publication before upstream review.
