# Traefik Dev Setup for Ozone
This is a simple setup Traefik used for Development of Ozone. It provides local development with proper https domains backed by https://traefik.me/

## Setup
Clone the project

```https://github.com/mekomsolutions/traefik-docker-compose-dev```

Create the network that will be shared between Traefik and Ozone.

```docker network create web```

Then start the project

```docker compose up -d```


