# 🏠 My Homelab Infrastructure

This repository contains the **Docker Compose** files and configurations used to run my self-hosted services. These stacks are deployed automatically using **Portainer** via Git polling.

## 📂 Repository Structure

Each service has its own dedicated directory containing its compose file and environment configuration:

Example:
- `/jellyfin` - Media Server
- `/speedtest-tracker` - Network monitoring
- `/nextjs-apps` - Web development projects

## 🚀 Deployment Workflow

1. Update `docker-compose.yml` or `.env` in this repository.
2. Push changes to the `main` branch.
3. Portainer detects the change (Polling set to 5 min).
4. Stack is automatically updated and redeployed.

## ⚠️ Note on Security
This repository is **Private** because it contains `.env` files with sensitive configuration details.
