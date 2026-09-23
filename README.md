# Warden — releases

Release binaries for [Warden](https://github.com/Abhishek-Mallick/Warden), a governed
data-access runtime for AI agents. **This repository holds no source code** — only
release archives and their checksums.

## Install

```bash
brew install abhishek-mallick/tap/warden
```

Or take an archive from the [releases](../../releases) page:

```bash
VERSION=0.1.0
PLATFORM=darwin_arm64        # or darwin_amd64, linux_amd64, linux_arm64

curl -LO https://github.com/Abhishek-Mallick/warden-dist/releases/download/v${VERSION}/warden_${VERSION}_${PLATFORM}.tar.gz
curl -LO https://github.com/Abhishek-Mallick/warden-dist/releases/download/v${VERSION}/checksums.txt
shasum -a 256 -c checksums.txt --ignore-missing     # sha256sum on Linux

tar -xzf warden_${VERSION}_${PLATFORM}.tar.gz
sudo install warden_${VERSION}_${PLATFORM}/warden /usr/local/bin/warden
sudo install warden_${VERSION}_${PLATFORM}/warden-mcp /usr/local/bin/warden-mcp
```

Each archive contains `warden` (the gateway and its CLI) and `warden-mcp` (the MCP
server that exposes a gateway to an agent).

## Configuration

Warden needs a configuration file naming your database, the agents allowed to use it,
and the policy governing it:

```bash
warden serve --config warden.yaml
```

## Verifying

Every release carries `checksums.txt`. Homebrew checks the checksum for your platform
automatically and refuses an archive that does not match.

## Issues

Report problems on the [issue tracker](https://github.com/Abhishek-Mallick/warden-dist/issues).
