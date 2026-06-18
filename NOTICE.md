# Notice

This repository contains documentation and metadata for an **unofficial experimental PocketMine-MP build** targeting Minecraft Bedrock **1.26.30 / protocol 1001**.

## Not official

This repository is not affiliated with, endorsed by or maintained by the official PocketMine-MP team.

Do not present this build as an official PocketMine-MP release.

## Origin

This build was originally used and tested in the context of the **BladeOfSteel** Minecraft Bedrock server. Because of that, it may contain changes or debugging behavior that differs from upstream PocketMine-MP.

## Current local status

The latest local build tested/playable in the BladeOfSteel environment:

```text
PMMP_INTERACTIONS_ENTITYRENDER_HOTFIX_build2608_v4_NODEBUG.phar
```

SHA256:

```text
126A40DE6BBE3F08559F9FC74FBF10F9F5DB88D3A80BF2AA7D3061AEE0C05868
```

This does not make it an official or production-ready PMMP release. It only documents the latest local testing result.

## Purpose

The purpose of this repository is to help developers inspect and test protocol 1001 behavior, especially around:

- login/session initialization;
- chunk rendering;
- BedrockData compatibility;
- inventory packets;
- player item interactions;
- serverbound item use packets;
- entity/projectile rendering.

## License responsibility

PocketMine-MP is licensed under LGPL-3.0.

If distributing a modified binary build, the corresponding modified source code or patches should be made available whenever possible.

Do not upload Mojang proprietary server binaries, private debug symbols or any data obtained under NDA/private partner agreements.
