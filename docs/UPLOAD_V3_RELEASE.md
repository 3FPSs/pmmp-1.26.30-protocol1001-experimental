# Upload v3 hotfix release

Status: completed.

Release:

https://github.com/3FPSs/pmmp-1.26.30-protocol1001-experimental/releases/tag/build2608-protocol1001-v3-hotfix

The latest local test succeeded with:

```text
PMMP_INTERACTIONS_ENTITYRENDER_HOTFIX_build2608_v3.phar
```

SHA256:

```text
37B4893FF0DF2A8F6D7219CB550B935792592FC353E74694E099CE583ADE936C
```

## Release information

Tag:

```text
build2608-protocol1001-v3-hotfix
```

Title:

```text
PocketMine-MP 1.26.30 Protocol 1001 Experimental Build 2608 - v3 Hotfix
```

Asset:

```text
PMMP_INTERACTIONS_ENTITYRENDER_HOTFIX_build2608_v3.phar
```

## Summary

This is an **unofficial experimental PocketMine-MP build** targeting Minecraft Bedrock **1.26.30 / protocol 1001**.

This is **not an official PMMP release** and should be treated as a community testing build.

## What changed from the previous build

- Fixed protocol 1001 item use in air behavior by treating `ACTION_BREAK_BLOCK` like `ACTION_CLICK_AIR`.
- Added protocol 1001 entity attack mapping by treating `ACTION_ITEM_INTERACT` like `ACTION_ATTACK`.
- Removed a local diagnostic global packet block that prevented entity/projectile packets from rendering client-side.

## Reported working in local tests

- food consumption;
- wind charges;
- bow and arrow;
- ender pearls;
- trident;
- potions;
- goat horns;
- projectile/entity trajectories and rendering;
- chunks/maps/containers/block placement.

## Still recommended

- multiplayer stress testing;
- plugin compatibility testing;
- source/diff publication before upstream review;
- TPS and memory testing.
