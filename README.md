# BitAssure connector

The connector lets [BitAssure](https://bitassure.app) check websites that
only exist inside your own network: a staging site behind a VPN, an
intranet. You run it on a machine in that network. It opens the sites with
the browser already installed there (Chrome or Edge) and sends the results
back to BitAssure.

- **It only calls out.** Plain HTTPS to `api.bitassure.app` on port 443,
  through your proxy if you have one. Nothing listens on your side, so no
  firewall needs opening.
- **You decide what it may open.** `allowed.hosts` in its settings is
  checked on your machine before anything is opened; nobody at BitAssure can
  widen it.
- **Nothing else is downloaded.** It never fetches a browser.

## Download

Take the files from the [latest release](https://github.com/BitAssure/connector/releases/latest):

| File | For |
|---|---|
| `bitassure-connector-windows-x64.zip` | Windows, with its own Java |
| `bitassure-connector-linux-x64.tar.gz` | Linux, with its own Java |
| `bitassure-connector.jar` | Any machine that already has Java 21 |

Each release lists the SHA-256 of every file in `SHA256SUMS`. Check one
before you install it:

```
# Linux
sha256sum -c SHA256SUMS --ignore-missing
# Windows (PowerShell)
Get-FileHash .\bitassure-connector-windows-x64.zip -Algorithm SHA256
```

These are the same files BitAssure's own servers offer: each release is
checked against the checksums `api.bitassure.app` publishes before it is
put here.

## Setting it up

Add a connector in BitAssure under **Settings, Connectors**. The page there
gives every step as a command to paste, for a Windows server, a Linux server
or your own computer. The full guide is at
[bitassure.app/docs/connector](https://bitassure.app/docs/connector).

## Network

The machine needs to reach these, on port 443 only:

- `api.bitassure.app`
- `auth.bitassure.app`
- `github.com` and `objects.githubusercontent.com`, to download it

## Questions

support@bitassure.app
