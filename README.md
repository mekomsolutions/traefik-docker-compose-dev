# Traefik Dev Setup for Ozone
This is a simple Traefik setup for Ozone developers. It provides local development with `https` domains backed by https://traefik.me/

## Setup
First clone the project:
```bash
git clone https://github.com/mekomsolutions/traefik-docker-compose-dev
```
Then create the network that will be shared between Traefik and Ozone:
```bash
docker network create web
```
Finally, start the project:
```bash
docker compose up -d
```
