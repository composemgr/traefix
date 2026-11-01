## 👋 Welcome to traefix 🚀

Cloud-native reverse proxy and load balancer

## 📋 Description

Cloud-native reverse proxy and load balancer

## 🚀 Services

- **proxy**: Cloud-native reverse proxy and load balancer



## 📦 Installation

### Option 1: Quick Install
```bash
curl -q -LSsf "https://raw.githubusercontent.com/composemgr/traefix/main/docker-compose.yaml" -o compose.yml
```

### Option 2: Git Clone
```bash
git clone "https://github.com/composemgr/traefix" ~/.local/srv/docker/traefix
cd ~/.local/srv/docker/traefix
cp default.env .env
docker compose --env-file .env up -d
```

### Option 3: Using composemgr
```bash
composemgr install traefix
```

## 🔧 Configuration

### Environment Variables

```shell
TZ=America/New_York
RFC2136_TSIG_KEY=replace-with-your-dns-tsig-key
RFC2136_NAMESERVER=127.0.0.1
RFC2136_TSIG_SECRET=replace-with-a-random-password
RFC2136_TSIG_ALGORITHM=hmac-sha256.
```

See `docker-compose.yaml` for complete list of configurable options.

### Environment Files

`default.env.sample` holds the full set of variables and is copied to `.env`
before starting the stack:

```bash
cp default.env .env
docker compose --env-file .env up -d
```

`app.env.sample` holds the app-specific overrides and is copied to `app.env`:

```bash
cp app.env.sample app.env
```

`composemgr up` applies `app.env` and `default.env` automatically. Raw
`docker compose` commands need `--env-file .env` to pick up the same values.

### Reverse Proxy

Three standalone compose files ship in this repo:

| File | Use |
|------|-----|
| `docker-compose.yaml` | Default, published on `172.17.0.1:64371` |
| `docker-compose.traefik.yaml` | Behind an existing external `traefik` network |
| `docker-compose.tunnel.yaml` | Behind an existing external `cloudflare` tunnel network |

```bash
docker compose -f docker-compose.traefik.yaml --env-file .env up -d
```

## 🌐 Access

- **Web Interface**: http://172.17.0.1:64371

## 📂 Volumes

- `./volumes/config/traefik/acme.json` - ACME certificate store
- `./volumes/config/traefik/config.yml` - Static Traefik configuration, read-only
- `./volumes/config/traefik/traefik.yml` - Dynamic Traefik configuration, read-only

## 🔐 Security

- Mount `/var/run/docker.sock` read-only so Traefik can discover containers
- Restrict dashboard access and never expose it to the public internet
- Store `acme.json` with restrictive permissions - it holds your TLS private keys

## 🔍 Logging

```shell
docker compose --env-file .env logs -f proxy
```

## 🛠️ Management

```bash
# Start services
docker compose --env-file .env up -d

# Stop services
docker compose --env-file .env down

# Update to latest images
docker compose --env-file .env pull && docker compose --env-file .env up -d

# View logs
docker compose --env-file .env logs -f

# Restart services
docker compose --env-file .env restart
```

## 📋 Requirements

- Docker Engine 20.10+
- Docker Compose V2+

## 🤝 Author

🤖 casjay: [Github](https://github.com/casjay) 🤖
🦄 composemgr: [Github](https://github.com/composemgr) 🦄
