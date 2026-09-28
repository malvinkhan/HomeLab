# HomeLab

Personal homelab for media, home automation, local AI and self-hosted infrastructure. Progress is logged in [CHANGELOG.md](CHANGELOG.md).

## Architecture

```mermaid
flowchart TB
  NET["Home network + Tailscale"]
  subgraph MS["MediaServer: Acer laptop (Debian + Docker)"]
    M1["Jellyfin, Sonarr, Radarr, Prowlarr, Seerr"]
  end
  subgraph NB["Nebula PC (Ryzen 7 7800X3D, RTX 5070 Ti)"]
    N1["Ollama, Open WebUI, n8n"]
  end
  NAS["NAS server: cloud storage (planned)"]
  NET --- MS
  NET --- NB
  NET -.- NAS
  style NAS stroke-dasharray: 5 5
```

| Host | Hardware | Role | Status |
|---|---|---|---|
| MediaServer | Acer laptop | Media stack | 🟢 Live |
| Nebula PC | Ryzen 7 7800X3D, RTX 5070 Ti | Local AI and automation | 🟢 Live |
| NAS server | To be decided | Cloud storage | 🟡 Planned |

## Hardware

### MediaServer
- Hardware: Acer laptop (model and specs to add)
- OS: Debian, running Docker
- Role: media stack (Jellyfin, Sonarr, Radarr, Prowlarr, Seerr)
- Managed remotely over SSH from the Nebula PC

### Nebula PC
- CPU: Ryzen 7 7800X3D
- GPU: RTX 5070 Ti
- RAM: 32 GB
- Storage: 1 TB SSD
- OS: (to add)
- Role: local AI (Ollama, Open WebUI) and n8n

### NAS server (planned)
- Purpose: cloud storage
- Status: to be added
- Hardware and OS: to be decided

## Services

**Media**
- Jellyfin
- Sonarr
- Radarr
- Prowlarr
- qBittorrent
- Seerr

**Home automation**
- Home Assistant, with Tapo cameras and Google Calendar integration
- n8n: Telegram webhook pipeline for receipt tracking

**Infrastructure**
- Vaultwarden
- Tailscale
- Uptime Kuma
- Portainer
- Watchtower
- Homepage dashboard

**AI**
- Ollama
- Open WebUI

**Finance**
- Notion tracker with Transactions and Warranties databases

## Current status and roadmap

- [ ] Add NAS server (cloud storage)
- [ ] Set up backups (no solution in place yet)
- [ ] Document Acer laptop specs, Nebula PC OS and network layout
- [ ] Add docker-compose files to this repo (secrets excluded)
- [ ] Move Seerr into docker-compose (currently run with `docker run`)
- [ ] Exclude Jellyfin and Seerr from Watchtower auto-updates
- [ ] Re-enable the Jellyfin widget in Homepage once it supports Jellyfin 12

## Skills demonstrated

- Linux (Debian) administration and Docker
- Self-hosting and secure remote access (Tailscale, Vaultwarden)
- Workflow automation (n8n, Telegram webhooks)
- Local LLM hosting (Ollama, Open WebUI)
- Monitoring and maintenance (Uptime Kuma, Watchtower, Portainer)
- Troubleshooting: diagnosing breakages from major-version updates (see the changelog)
