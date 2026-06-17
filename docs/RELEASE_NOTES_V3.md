# Release notes - v3 local hotfix

## Build

```text
PMMP_INTERACTIONS_ENTITYRENDER_HOTFIX_build2608_v3.phar
```

SHA256:

```text
37B4893FF0DF2A8F6D7219CB550B935792592FC353E74694E099CE583ADE936C
```

## Summary

This local hotfix was reported as working correctly in the BladeOfSteel test environment.

## Fixes included

### Item use in air

Protocol 1001 item use in air can arrive as `UseItemTransactionData::ACTION_BREAK_BLOCK` instead of the legacy `ACTION_CLICK_AIR`.

The hotfix routes `ACTION_BREAK_BLOCK` through the same path as `ACTION_CLICK_AIR`.

### Entity attack mapping

Protocol 1001 entity attacks can arrive as `UseItemOnEntityTransactionData::ACTION_ITEM_INTERACT` instead of only `ACTION_ATTACK`.

The hotfix routes `ACTION_ITEM_INTERACT` through the same path as `ACTION_ATTACK`.

### Entity/projectile rendering

A diagnostic global packet block was removed from `NetworkSession`, allowing projectile/entity packets to reach the client again.

This restored projectile visuals and trajectories.

## Reported working

- food;
- wind charges;
- bow and arrow;
- ender pearls;
- trident;
- potions;
- goat horns;
- other tested item interactions;
- projectile/entity render and trajectory.

## Still recommended before public stable use

- source/diff publication;
- multiplayer testing;
- TPS and memory testing;
- plugin compatibility testing;
- upstream-compatible patch cleanup.
