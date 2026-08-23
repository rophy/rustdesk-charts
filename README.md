# rustdesk-charts

Helm charts for deploying RustDesk OSS server components, using forked images that enable web client and WebSocket support.

## Components

| Component | Container Image | Source Repo | Description |
|-----------|----------------|-------------|-------------|
| hbbs | `ghcr.io/rophy/rustdesk-server` | [rophy/rustdesk-server](https://github.com/rophy/rustdesk-server) | Rendezvous server |
| hbbr | `ghcr.io/rophy/rustdesk-server` | [rophy/rustdesk-server](https://github.com/rophy/rustdesk-server) | Relay server |
| web-client | `ghcr.io/rophy/rustdesk/web-client` | [rophy/rustdesk](https://github.com/rophy/rustdesk) | Browser-based remote desktop client |

## Why forked images?

The RustDesk web client and WebSocket-based peer registration were [removed from the upstream OSS builds](https://github.com/rustdesk/rustdesk) and are now only available in RustDesk Server Pro. The forked repos restore these features for the OSS server:

- [rophy/rustdesk](https://github.com/rophy/rustdesk) — restores the web client with OSS server compatibility patches
- [rophy/rustdesk-server](https://github.com/rophy/rustdesk-server) — enables WebSocket peer registration for web client connectivity

## Usage

```bash
helm install rustdesk ./charts -f values-override.yaml
```

Create a `values-override.yaml` with your deployment-specific settings (keypair secret, relay address, image tags, etc.).
