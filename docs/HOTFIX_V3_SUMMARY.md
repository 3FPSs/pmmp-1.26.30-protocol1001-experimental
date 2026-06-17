# Hotfix v3 summary

Local tested build:

```text
PMMP_INTERACTIONS_ENTITYRENDER_HOTFIX_build2608_v3.phar
```

SHA256:

```text
37B4893FF0DF2A8F6D7219CB550B935792592FC353E74694E099CE583ADE936C
```

## Result

The v3 hotfix was reported as working correctly in the BladeOfSteel test environment.

Reported working:

- food consumption;
- wind charges;
- bow and arrow;
- ender pearls;
- trident;
- potions;
- goat horns;
- other tested item interactions;
- projectile/entity trajectories and rendering.

## Applied concepts

### 1. Protocol 1001 item use in air

`UseItemTransactionData::ACTION_BREAK_BLOCK` was treated like `ACTION_CLICK_AIR` in `InGamePacketHandler`.

Reason: protocol 1001 clients may report right-click item use in air using `ACTION_BREAK_BLOCK` instead of the legacy `ACTION_CLICK_AIR`.

### 2. Protocol 1001 entity attack action

`UseItemOnEntityTransactionData::ACTION_ITEM_INTERACT` was treated like `ACTION_ATTACK` in `InGamePacketHandler`.

Reason: protocol 1001 clients may report entity attacks as `ACTION_ITEM_INTERACT`.

### 3. Entity/projectile packet render restoration

A diagnostic packet block in `NetworkSession` was removed so entity/projectile packets can reach clients again.

The diagnostic block skipped packets such as:

- `AddActorPacket`
- `AddPlayerPacket`
- `RemoveActorPacket`
- `SetActorDataPacket`
- `MobEquipmentPacket`
- `MobArmorEquipmentPacket`
- `MoveActorAbsolutePacket`
- `MovePlayerPacket`
- `PlayerListPacket`

This was preventing projectiles and item trajectories from rendering client-side.

## Next steps

- Publish v3 build as a release asset if desired.
- Extract and publish source or clean patch/diff.
- Continue longer multiplayer and performance testing.
- Do not propose upstream until source/diff is clean and reviewable.
