# PocketMine-MP 1.26.30 / Protocol 1001 Experimental Build

> Unofficial experimental PocketMine-MP build for Minecraft Bedrock 1.26.30 / protocol 1001.

This repository is intended to document and share an experimental PocketMine-MP build originally used and tested on the **BladeOfSteel** Minecraft Bedrock server.

The goal is to help developers inspect, test, compare and improve support for Minecraft Bedrock **1.26.30 / protocol 1001**.

## Important notice

This is **not an official PocketMine-MP release**.

This build was modified and tested for a private server environment first, so it may contain changes that are different from upstream PocketMine-MP. It should be treated as a community testing build, not as a production-ready official release.

Please do not report this repository as an official PocketMine-MP release. If useful technical findings are produced here, they should be converted into clean patches or pull requests for the upstream project.

## Download

Experimental build release:

https://github.com/3FPSs/pmmp-1.26.30-protocol1001-experimental/releases/tag/build2608-protocol1001

Recommended filename:

```text
PocketMine-MP_1.26.30_protocol1001_experimental_build2608.phar
```

Known SHA256 for the tested PHAR:

```text
ED8F8B735BE3934C3B3E85B87F20208FD69199F9680E00AAC1ECE982048DD0
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

Known issues still under investigation:

- Item use in air may not work correctly.
- Throwable items may not launch correctly.
- Bows, tridents, potions, wind charges and fireworks may have issues.
- Food consumption may visually update and then revert.
- Goat horn sound/use behavior may not work correctly.
- Some vanilla item interactions may still require protocol/handler fixes.

## Developer focus

The remaining issues appear to be related mainly to player interaction packets, especially:

- `InventoryTransactionPacket`
- `UseItemTransactionData`
- `ReleaseItemTransactionData`
- `ItemStackRequestPacket`
- `PlayerActionPacket`
- `PlayerAuthInputPacket`
- `InGamePacketHandler`

Chunk rendering and basic block placement appear to be mostly functional in current testing.

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
