<img src="https://raw.githubusercontent.com/Abhishek-Mallick/warden-dist/main/warden-banner.png" alt="Warden" width="820">

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

## Licence

Warden is **proprietary software**, distributed as a compiled binary. You may install
and run it for your own internal purposes, including in production; you may not
redistribute it, offer it as a service, or reverse engineer it. The full terms are in
[LICENSE.md](LICENSE.md), and ship inside every release archive.

Warden links open-source libraries whose licences require their notices to travel with
it; those are in [THIRD-PARTY-NOTICES.md](THIRD-PARTY-NOTICES.md).

## Issues

Report problems on the [issue tracker](https://github.com/Abhishek-Mallick/warden-dist/issues).
