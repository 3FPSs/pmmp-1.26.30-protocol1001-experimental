# Source extraction guide

This guide explains how to extract source files from the experimental PHAR build so the community can inspect it and prepare cleaner patches.

## Why source is needed

A PHAR binary is useful for testing, but developers need source code or a patch/diff to review what changed.

Before asking upstream PocketMine-MP maintainers to review anything, the changes should be converted into readable source-level patches.

## Requirements

- PHP CLI installed.
- The tested PHAR file.
- Optional but recommended: Git.

## Recommended filename

```text
PocketMine-MP_1.26.30_protocol1001_experimental_build2608.phar
```

Known SHA256:

```text
ED8F8B735BE3934C3B3E85B87F20208FD69199F9680E00AAC1ECE982048DD0
```

## Extract using PHP

On Windows PowerShell:

```powershell
mkdir C:\BladePMMPSource
cd C:\BladePMMPSource
copy C:\path\to\PocketMine-MP_1.26.30_protocol1001_experimental_build2608.phar .\PocketMine-MP.phar
php -r "$p = new Phar('PocketMine-MP.phar'); $p->extractTo('PocketMine-MP_build2608_src', null, true);"
```

If PHP blocks PHAR operations, try:

```powershell
php -d phar.readonly=0 -r "$p = new Phar('PocketMine-MP.phar'); $p->extractTo('PocketMine-MP_build2608_src', null, true);"
```

## Create a source ZIP

```powershell
Compress-Archive .\PocketMine-MP_build2608_src\* .\PocketMine-MP_build2608_source.zip
Get-FileHash .\PocketMine-MP_build2608_source.zip -Algorithm SHA256
```

Upload the generated ZIP to the GitHub Release as an additional asset.

## Create a patch/diff

A clean patch is better than a source ZIP for upstream review.

If you know the exact upstream PocketMine-MP base commit, compare against that commit. If not, compare against the closest official stable version used as base.

Example using Git Bash or PowerShell:

```powershell
git clone https://github.com/pmmp/PocketMine-MP.git pmmp-upstream
git clone https://github.com/3FPSs/pmmp-1.26.30-protocol1001-experimental.git pmmp-build2608-docs
```

Then create a raw no-index diff between upstream source and extracted source:

```powershell
git diff --no-index .\pmmp-upstream .\PocketMine-MP_build2608_src > build2608.patch
```

Note: this can be noisy if vendor files, generated files or build metadata differ.

## Better patch workflow

For a cleaner review:

1. Identify the official PMMP version or commit used as the original base.
2. Clone that exact commit.
3. Copy the extracted source over it.
4. Run `git diff`.
5. Split changes into smaller commits:
   - protocol version/metadata;
   - BedrockProtocol packet changes;
   - BedrockData changes;
   - chunk/block mapping changes;
   - inventory/item interaction changes;
   - debug/test-only changes.

## Do not upload

Do not upload:

- Mojang BDS binaries;
- private debug symbols;
- files obtained under NDA/private partner access;
- secrets, tokens or authentication data;
- server-specific private data.

## Next review target

Current known remaining issue area:

```text
InventoryTransactionPacket
UseItemTransactionData
ReleaseItemTransactionData
ItemStackRequestPacket
PlayerActionPacket
PlayerAuthInputPacket
InGamePacketHandler
```
