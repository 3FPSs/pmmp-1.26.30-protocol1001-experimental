# Known Issues

This file tracks issues observed in the current experimental build.

## Resolved in local hotfix test

The following issues were reported as working correctly after applying the interaction + entity render hotfix build:

- food consumption;
- ender pearl usage/trajectory;
- bow and arrow;
- trident;
- splash potions;
- wind charge;
- goat horn usage/sound;
- other item interactions tested by the BladeOfSteel environment.

The successful test indicates that two areas were important:

1. protocol 1001 item-use-in-air mapping;
2. allowing entity/projectile packets to render client-side.

## Previously observed issues

These were previously observed before the hotfix:

- item use in air did not work correctly;
- throwable items/projectiles did not launch/render correctly;
- food consumption visually updated and then reverted;
- goat horn/fireworks/trident/potions/wind charge had issues.

## Confirmed working

- Client login/session can complete.
- World rendering no longer instantly crashes in tested maps.
- Chunks with blocks can render.
- Basic container interfaces can open.
- Block placement works.
- Food and item interactions work in the latest local hotfix test.
- Projectile/entity visuals work in the latest local hotfix test.

## Needs more testing

- Longer multiplayer sessions.
- More maps and dimensions.
- Mobs/entities under load.
- Armor/equipment edge cases.
- Creative inventory.
- Crafting flows.
- Resource packs.
- Multi-player testing with 5+ clients.
- TPS/memory stability over time.
