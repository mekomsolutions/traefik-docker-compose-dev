# Traefik v2 HTTPS (SSL) on localhost

Minimal Traefik v2 setup for localhost with HTTPS. TLS is enabled by default for all routers on the **websecure** entrypoint, so services do not need `traefik.http.routers.<name>.tls=true`.

## Project layout

```
.
├── config/
│   ├── static.yml   # Traefik static config (entrypoints, providers, API)
│   └── dynamic.yml  # TLS certs, dashboard router
├── certs/           # Create this; put mkcert output here
├── docker-compose.yml
├── whoami.yml       # Example service
└── README.md
```

## Prerequisites

- [Docker](https://docs.docker.com/get-docker/) and Docker Compose
- [mkcert](https://github.com/FiloSottile/mkcert) (for local CA and certs)

## Setup

1. **Clone and go to the project root**

   ```bash
   cd traefik-v2-https-ssl-localhost
   ```

2. **Install mkcert and generate certificates** (first time only)

   ```bash
   mkcert -install
   mkdir -p certs
   mkcert -cert-file certs/local-cert.pem -key-file certs/local-key.pem \
     "docker.localhost" "*.docker.localhost" "domain.local" "*.domain.local"
   ```

   On macOS, mkcert may prompt for your password (Keychain + system trust).

3. **Create the Docker network**

   ```bash
   docker network create web
   ```

4. **Start Traefik**

   ```bash
   docker-compose up -d
   ```

5. **Start the whoami example** (optional)

   ```bash
   docker-compose -f whoami.yml up -d
   ```

## Access

- **Whoami:** https://whoami.docker.localhost  
- **Traefik dashboard:** https://traefik.docker.localhost  

HTTP (port 80) redirects to HTTPS (port 443).
