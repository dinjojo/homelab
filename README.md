# Homelab

My personal homelab configuration repository.

This repository houses configuration files I use to run core services on my home server.  
It’s intended for self-hosting tools that improve home network experience, automation, and service availability.

---

## 📁 Repository Contents

| File | Purpose |
|------|---------|
| `adguardhome.yaml` | Configuration for **AdGuard Home** DNS and network ad blocking service. AdGuard Home runs as a DNS resolver on your homelab network and blocks ads, trackers, and malware domains. See AdGuard Home docs for YAML format details. :contentReference[oaicite:0]{index=0} |
| `arr_services.yaml` | Definitions/configuration for **ARR services** (e.g., Sonarr, Radarr, Lidarr, etc.) which automate media management tasks like downloading and organizing TV shows, movies, and music. |

> If this repository grows with more configs (e.g., Docker compose files, service definitions), this table will be expanded accordingly.

---

## 🛠 How to Use These Configs

These YAML files are not standalone applications; they are meant to be used with:

- Docker / Docker Compose
- Container orchestrators (if applicable)
- Service runners you use in your homelab

For example, if using Docker Compose:

1. Place service definitions in a Docker Compose file.
2. Reference these YAML configs via `volumes:` and service options.
3. Start services.

Example (conceptual):

```yaml
services:
  adguard:
    image: adguard/adguardhome
    volumes:
      - ./adguardhome.yaml:/opt/adguardhome/AdGuardHome.yaml
    ports:
      - "53:53/tcp"
      - "53:53/udp"
      - "3000:3000"
