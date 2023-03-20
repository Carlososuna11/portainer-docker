# Portainer Docker Configuration

> Portainer Business Edition (BE) is our commercial offering. With features geared towards businesses and larger organizations such as Role-Based Access Control, registry management, and dedicated support, Portainer BE is a powerful toolset that allows you to easily build and manage containers in Docker, Docker Swarm, Kubernetes and Azure ACI. [Portainer.io](https://docs.portainer.io/#about-portainer)

This repository contains the configuration files for running portainer in Docker containers. It is based on the [Earthly](https://earthly.dev/blog/portainer-for-dcm/#installing-docker-compose) tutorial.

## Configuration

1. Set up a portainer docker container

   The Docker Compose file below will run everything for you via Docker.

```yml
version: "3.8"
services:
  portainer:
    container_name: portainer
    image: portainer/portainer-ce:latest
    ports:
      # Portainer Web UI SSL
      - 9443:9443
      # Portainer Web UI
      - 9000:9000
      # Portainer Agent
      - 9001:9001
    volumes:
      - portainer_data:/data
      - /var/run/docker.sock:/var/run/docker.sock
    restart: unless-stopped

volumes:
  portainer_data:
```

2. Start the portainer docker

   From a directory containing the `docker-compose.yml` file created in the previous step, run this command to start all services in the correct order.

```bash
docker-compose up -d
```
