# Contributing

Thanks for helping test this experimental build.

## Important

This repository is not an official PocketMine-MP repository. Contributions should be focused on investigation, documentation and clean patches that may later be proposed upstream.

## Current focus after v3

The v3 local hotfix was reported to restore item interactions and projectile/entity rendering.

Useful next contributions include:

- longer multiplayer testing;
- performance/TPS reports;
- plugin compatibility reports;
- source patches or diffs;
- review of the `NetworkSession` diagnostic packet block removal;
- review of protocol 1001 item-use/action mappings.

## Good contributions

Useful contributions include:

- reproducible test logs;
- packet debug output;
- source patches;
- comparisons against upstream PocketMine-MP;
- comparisons against upstream BedrockProtocol;
- documentation of working/broken behavior;
- minimal reproduction steps.

## Please avoid

Please avoid:

- presenting this build as official;
- uploading Mojang proprietary binaries;
- uploading private debug symbols;
- submitting random binary-only builds without source or patch notes;
- pressuring upstream maintainers with incomplete reports.

## Suggested report format

```markdown
## Environment

- Minecraft Bedrock version:
- Protocol:
- OS:
- PHP version:
- Build hash:

## What works

## What breaks

## Steps to reproduce

1.
2.
3.

## Logs

```text
paste logs here
```

## Suspected files/classes

```
InventoryTransactionPacket
ItemStackRequestPacket
InGamePacketHandler
NetworkSession
```
```

## Upstream path

If a fix is identified, it should be cleaned into a source-level patch before being proposed to PocketMine-MP or related upstream repositories.
