# PocketMine-MP 1.26.30 / Protocol 1001 Experimental Build

> Unofficial experimental PocketMine-MP build for Minecraft Bedrock 1.26.30 / protocol 1001.

This repository is intended to document and share an experimental PocketMine-MP build originally used and tested on the **BladeOfSteel** Minecraft Bedrock server.

The goal is to help developers inspect, test, compare and improve support for Minecraft Bedrock **1.26.30 / protocol 1001**.

## Important notice

This is **not an official PocketMine-MP release**.

This build was modified and tested for a private server environment first, so it may contain changes that are different from upstream PocketMine-MP. It should be treated as a community testing build, not as a production-ready official release.

Please do not report this repository as an official PocketMine-MP release. If useful technical findings are produced here, they should be converted into clean patches or pull requests for the upstream project.

## Download

Original experimental build release:

https://github.com/3FPSs/pmmp-1.26.30-protocol1001-experimental/releases/tag/build2608-protocol1001

Original build SHA256:

```text
ED8F8B735BE3934C3B3E85B87F20208FD69199F9680E00AAC1ECE982048DD0
```

Latest tested playable build:

```text
PMMP_INTERACTIONS_ENTITYRENDER_HOTFIX_build2608_v4_NODEBUG.phar
```

Latest tested playable build SHA256:

```text
126A40DE6BBE3F08559F9FC74FBF10F9F5DB88D3A80BF2AA7D3061AEE0C05868
```

Previous v3 hotfix release:

https://github.com/3FPSs/pmmp-1.26.30-protocol1001-experimental/releases/tag/build2608-protocol1001-v3-hotfix

Previous v3 hotfix SHA256:

```text
37B4893FF0DF2A8F6D7219CB550B935792592FC353E74694E099CE583ADE936C
```

## Why this exists

Minecraft Bedrock protocol updates can break login, chunks, inventories, item interactions and world rendering in server software. This repository gathers test information around a working experimental build for protocol 1001.

This project exists so developers can:

- inspect behavior;
- reproduce issues;
- compare against upstream PocketMine-MP;
- identify missing packet handling;
- help prepare cleaner protocol support patches;
- document what works and what is still broken.

## Current tested status

Confirmed working in local BladeOfSteel tests:

- Minecraft Bedrock 1.26.30 client can connect.
- Client can stay in-world without the earlier render crash.
- Real maps can render.
- Chunks with blocks can load.
- Basic containers such as chests and anvils can open.
- Block placement works.
- Food consumption works in the latest hotfix test.
- Ender pearl, wind charge, bow/arrow, trident, potions, goat horn and other tested items work correctly in the latest hotfix test.
- Projectile/entity render and trajectory work correctly in the latest hotfix test.
- v4 removes the leftover disconnect debug warning from v3.

## Developer focus

The successful local hotfix suggests the important areas were:

- protocol 1001 item-use-in-air mapping;
- entity/projectile packet rendering;
- `InventoryTransactionPacket`;
- `UseItemTransactionData`;
- `UseItemOnEntityTransactionData`;
- `InGamePacketHandler`;
- `NetworkSession` packet filtering/debug code.

## Repository structure

```text
README.md
NOTICE.md
KNOWN_ISSUES.md
TEST_REPORT.md
CONTRIBUTING.md
builds/README.md
docs/TESTS.md
docs/DEVELOPER_NOTES.md
docs/EXTERNAL_FIXES.md
docs/SOURCE_EXTRACTION.md
docs/HOTFIX_V3_SUMMARY.md
docs/HOTFIX_V4_SUMMARY.md
docs/RELEASE_NOTES_V3.md
docs/RELEASE_NOTES_V4.md
docs/UPLOAD_V3_RELEASE.md
docs/UPLOAD_V4_RELEASE.md
```

## Upstream etiquette

This repository should not be used to bypass or pressure upstream PocketMine-MP maintainers.

Recommended path:

1. Document the experimental build here.
2. Let the community reproduce and inspect the remaining issues.
3. Convert useful findings into clean source patches.
4. Open upstream issues or pull requests only with technical details and source changes.

## License

PocketMine-MP is licensed under the GNU Lesser General Public License v3.0.

Any modified binary build should be accompanied by the corresponding modified source code or patches whenever possible.

See [`NOTICE.md`](NOTICE.md) for more details.
