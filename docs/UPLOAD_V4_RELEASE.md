# Upload v4 NODEBUG release

The latest tested/playable build is:

```text
PMMP_INTERACTIONS_ENTITYRENDER_HOTFIX_build2608_v4_NODEBUG.phar
```

SHA256:

```text
126A40DE6BBE3F08559F9FC74FBF10F9F5DB88D3A80BF2AA7D3061AEE0C05868
```

## Recommended GitHub Release

Tag:

```text
build2608-protocol1001-v4-nodebug
```

Title:

```text
PocketMine-MP 1.26.30 Protocol 1001 Experimental Build 2608 - v4 NODEBUG
```

Upload asset:

```text
PMMP_INTERACTIONS_ENTITYRENDER_HOTFIX_build2608_v4_NODEBUG.phar
```

## Suggested release notes

```markdown
# PocketMine-MP 1.26.30 / Protocol 1001 Experimental Build 2608 - v4 NODEBUG

This is an **unofficial experimental PocketMine-MP build** targeting Minecraft Bedrock **1.26.30 / protocol 1001**.

This is **not an official PMMP release** and should be treated as a community testing build.

## SHA256

```text
126A40DE6BBE3F08559F9FC74FBF10F9F5DB88D3A80BF2AA7D3061AEE0C05868
```

## What changed from v3

- Removed leftover disconnect debug warning:
  `[Blade 26.30 Debug] Client disconnected. Last outgoing packets: ...`

## Fixes preserved from v3

- Fixed protocol 1001 item use in air behavior by treating `ACTION_BREAK_BLOCK` like `ACTION_CLICK_AIR`.
- Added protocol 1001 entity attack mapping by treating `ACTION_ITEM_INTERACT` like `ACTION_ATTACK`.
- Removed a local diagnostic global packet block that prevented entity/projectile packets from rendering client-side.

## Reported working in local tests

- login;
- chunks/maps;
- containers;
- block placement;
- food consumption;
- wind charges;
- bow and arrow;
- ender pearls;
- trident;
- potions;
- goat horns;
- projectile/entity trajectories and rendering.

## Stability note

This build is marked as tested/playable in the BladeOfSteel environment, but remains unofficial and experimental.
```
