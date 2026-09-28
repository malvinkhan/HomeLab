# Changelog

Newest entries first.

## 2026-09-28
- Started formal documentation of the homelab (this repo)
- Documented: the Acer laptop is currently serving as the MediaServer
- Planned: NAS server for cloud storage

## 2026-09-25
- **Fixed:** Jellyseerr login failure ("Something went wrong while trying to sign in"). Jellyfin had moved to 12.1.0 (likely via a Watchtower auto-update) while Jellyseerr was on 2.7.3, and the two were incompatible. Logs showed constant 401 errors from Jellyfin, and a freshly generated API key tested directly against Jellyfin still returned 401, which ruled out the key and the network.
- **Changed:** replaced Jellyseerr with Seerr 3.4.1 (`ghcr.io/seerr-team/seerr:latest`), run with `docker run` using the existing config, port 5055 and the `mediaserver_default` network. Settings migrated automatically.
- **Lesson:** auto-updates can break paired apps when one side jumps a major version. Pin or exclude version-sensitive containers from Watchtower.

## 2026-09-08
- **Fixed:** Homepage Jellyfin widget error ("Unexpected end of JSON input"). Homepage was calling Jellyfin's old `/emby/` API endpoints, which Jellyfin 12.0.0 removed, so every widget call returned a 404. Jellyfin itself, the API key and Tailscale connectivity were all confirmed working.
- **Changed:** commented out the Jellyfin widget block in `services.yaml` (app link kept) until Homepage supports Jellyfin 12.
- **Next:** pull the latest Homepage and uncomment the widget once a fix ships.

## Earlier work (mid 2026)
- Built the Nebula PC (Ryzen 7 7800X3D, RTX 5070 Ti) running Ollama and n8n, after selling the previous i5-9400F + RTX 2060 PC
- Re-purposed an old Acer laptop as the MediaServer, installing Debian Linux and managing it over SSH from the Nebula PC
- Built an automated media request pipeline (Radarr, Sonarr, qBittorrent) connected via API keys
- Added Tailscale for secure remote access, so the media library works on the go
- Added Vaultwarden and Home Assistant (Tapo cameras, Google Calendar integration)
- Added an n8n Telegram webhook pipeline for receipt tracking
- Added a Notion finance tracker (Transactions and Warranties databases)
- Added automated notification webhooks for new movies/shows added. User will be aware of completed requests
- Fixed the Jellyfin/Sonarr season folder structure
