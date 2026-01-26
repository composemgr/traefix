## 👋 Welcome to traefix 🚀

Self-hosted traefix application

## 📋 Description

Self-hosted traefix application

## 🚀 Services

- **proxy**: proxy:latest

## 📦 Installation

### Option 1: Quick Install
```bash
curl -q -LSsf "https://raw.githubusercontent.com/composemgr/traefix/main/docker-compose.yaml" -o compose.yml
```

### Option 2: Git Clone
```bash
git clone "https://github.com/composemgr/traefix" ~/.local/srv/docker/traefix
cd ~/.local/srv/docker/traefix
docker compose up -d
```

### Option 3: Using composemgr
```bash
composemgr install traefix
```

## 🔧 Configuration

### Environment Variables

```shell
TZ=America/New_York
```

See `docker-compose.yaml` for complete list of configurable options.

## 🌐 Access

- **Web Interface**: http://172.17.0.1:443

## 📂 Volumes

- `./rootfs/config/traefik/acme.json` - Data storage
- `./rootfs/config/traefik/config.yml` - Data storage
- `./rootfs/config/traefik/traefik.yml` - Data storage

## 🔍 Logging

```shell
docker compose logs -f proxy
```

## 🛠️ Management

```bash
# Start services
docker compose up -d

# Stop services
docker compose down

# Update to latest images
docker compose pull && docker compose up -d

# View logs
docker compose logs -f

# Restart services
docker compose restart
```

## 📋 Requirements

- Docker Engine 20.10+
- Docker Compose V2+

## 🤝 Author

🤖 casjay: [Github](https://github.com/casjay) 🤖  
🦄 composemgr: [Github](https://github.com/composemgr) 🦄
