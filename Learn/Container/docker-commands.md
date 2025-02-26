# Docker Commands Cheat Sheet

## Table of Contents

- [Docker Commands Cheat Sheet](#docker-commands-cheat-sheet)
  - [Table of Contents](#table-of-contents)
  - [Basic Docker Commands](#basic-docker-commands)
    - [Images](#images)
    - [Containers](#containers)
    - [Network](#network)
    - [Volumes](#volumes)
  - [Docker Compose](#docker-compose)
    - [Basic Operations](#basic-operations)
  - [Dockerfile Examples](#dockerfile-examples)
    - [Basic Web App](#basic-web-app)
    - [Multi-stage Build](#multi-stage-build)
    - [With Health Checks](#with-health-checks)
    - [Non-root User](#non-root-user)
  - [System Management](#system-management)
  - [Common Use Cases](#common-use-cases)
    - [Running a Web Server](#running-a-web-server)
    - [Running a Database](#running-a-database)
    - [Running with Restart Policies](#running-with-restart-policies)
    - [Running with Resource Limits](#running-with-resource-limits)
  - [Docker Swarm](#docker-swarm)
  - [Debugging Tips](#debugging-tips)
  - [Security Best Practices](#security-best-practices)
  - [Advanced Network Examples](#advanced-network-examples)
  - [Environment Management](#environment-management)

## Basic Docker Commands

### Images

```bash
# List all images
docker images

# Pull an image
docker pull ubuntu:20.04

# Remove an image
docker rmi ubuntu:20.04

# Build an image from Dockerfile
docker build -t myapp:1.0 .

# Build with build arguments
docker build --build-arg VERSION=1.0 -t myapp:1.0 .

# List dangling images (untagged)
docker images -f "dangling=true"

# Search Docker Hub for images
docker search nginx

# Show image history
docker history nginx:latest

# Tag an image
docker tag myapp:latest myapp:v1.2.3
```

### Containers

```bash
# Run a container -d (detached mode) --name (container name)
docker run -d --name webserver nginx

# Run with port mapping -p (host_port:container_port)
docker run -d -p 8080:80 nginx

# Run with environment variables -e (key=value)
docker run -d -e APP_ENV=production nginx

# Run with volume mount
docker run -v /host/path:/container/path nginx

# List running containers
docker ps

# List all containers (including stopped)
docker ps -a

# Stop a container
docker stop container_name

# Remove a container
docker rm container_name

# Remove image
docker rmi image_name

# Remove all images not used by any container
docker system prune -a

# Remove all stopped containers
docker container prune

# Inspect container
docker inspect container_name

# Access container shell
docker exec -it container_name bash

# Copy files between host and container
docker cp /path/to/file container_name:/path/in/container
docker cp container_name:/path/in/container /path/on/host

# Restart container
docker restart container_name

# Pause/unpause container
docker pause container_name
docker unpause container_name

# Rename container
docker rename old_name new_name

# Run container with memory limits
docker run -d --memory="512m" --memory-swap="1g" nginx

# Run container with CPU limits
docker run -d --cpus=0.5 nginx

# Check container resource usage
docker stats container_name
```

### Network

```bash
# List networks
docker network ls

# Create a network
docker network create mynetwork

# Create a network with custom subnet
docker network create --subnet=172.18.0.0/16 mynetwork

# Connect container to network
docker network connect mynetwork container_name

# Disconnect container from network
docker network disconnect mynetwork container_name

# Inspect network
docker network inspect mynetwork

# Remove network
docker network rm mynetwork

# Remove all unused networks
docker network prune
```

### Volumes

```bash
# Create a volume
docker volume create myvolume

# List volumes
docker volume ls

# Remove volume
docker volume rm myvolume

# Inspect volume
docker volume inspect myvolume

# Remove all unused volumes
docker volume prune

# Create named volume with driver
docker volume create --driver local \
  --opt type=none \
  --opt device=/path/on/host \
  --opt o=bind \
  myvolume
```

## Docker Compose

### Basic Operations

```bash
# Start services
docker-compose up -d

# Stop services and remove containers
docker-compose down

# View logs
docker-compose logs

# View logs for specific service and follow
docker-compose logs -f service_name

# View running services
docker-compose ps

# Restart service
docker-compose restart web

# Remove all containers
docker-compose rm -f

# Build and start services
docker-compose up --build

# Scale service
docker-compose up -d --scale web=3

# Run a one-off command in service
docker-compose exec web npm test

# Show environment variables
docker-compose config

# Validate and view the compose file
docker-compose config

# List containers
docker-compose ps

# Stop services without removing
docker-compose stop
```

## Dockerfile Examples

### Basic Web App

```dockerfile
FROM node:14
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
EXPOSE 3000
CMD ["npm", "start"]
```

### Multi-stage Build

```dockerfile
# Build stage
FROM node:14 AS builder
WORKDIR /app
COPY . .
RUN npm install && npm run build

# Production stage
FROM nginx:alpine
COPY --from=builder /app/build /usr/share/nginx/html
```

### With Health Checks

```dockerfile
FROM nginx:alpine
COPY ./site /usr/share/nginx/html
# Add health check
HEALTHCHECK --interval=30s --timeout=3s \
  CMD curl -f http://localhost/ || exit 1
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
```

### Non-root User

```dockerfile
FROM node:14-alpine
# Create app directory
WORKDIR /app
# Create non-root user
RUN addgroup -S appgroup && adduser -S appuser -G appgroup
COPY . .
RUN npm ci --only=production
# Use non-root user
USER appuser
EXPOSE 3000
CMD ["node", "index.js"]
```

## System Management

```bash
# System info
docker info

# Clean up system
docker system prune

# Detailed system prune (volumes, unused images)
docker system prune -a --volumes

# View container stats
docker stats

# View logs
docker logs container_name

# View logs with timestamps
docker logs --timestamps container_name

# Follow logs (like tail -f)
docker logs -f container_name

# Show last N lines
docker logs --tail 100 container_name

# Show disk usage
docker system df

# Show detailed disk usage
docker system df -v

# Monitor events
docker events
```

## Common Use Cases

### Running a Web Server

```bash
# Nginx with custom port and volume
docker run -d \
  --name mynginx \
  -p 8080:80 \
  -v /local/content:/usr/share/nginx/html \
  nginx
```

### Running a Database

```bash
# PostgreSQL with environment variables
docker run -d \
  --name postgres \
  -e POSTGRES_PASSWORD=mysecretpassword \
  -p 5432:5432 \
  postgres
```

### Running with Restart Policies

```bash
# Always restart container
docker run -d --restart always nginx

# Restart on failure
docker run -d --restart on-failure:5 nginx
```

### Running with Resource Limits

```bash
# Memory and CPU limits
docker run -d \
  --name limited_container \
  --memory="256m" \
  --memory-swap="512m" \
  --cpus="0.5" \
  nginx
```

## Docker Swarm

```bash
# Initialize swarm
docker swarm init --advertise-addr <MANAGER-IP>

# Join as worker
docker swarm join --token <TOKEN> <MANAGER-IP>:<PORT>

# List nodes
docker node ls

# Deploy stack from compose file
docker stack deploy -c docker-compose.yml myapp

# List stacks
docker stack ls

# List services in stack
docker stack services myapp

# Remove stack
docker stack rm myapp

# Create service
docker service create --name web --replicas 3 -p 80:80 nginx

# Scale service
docker service scale web=5

# Update service
docker service update --image nginx:latest web
```

## Debugging Tips

```bash
# Show container logs
docker logs container_name

# Follow logs in real time
docker logs -f container_name

# Show processes running inside container
docker top container_name

# Show container resource usage statistics
docker stats container_name

# Run interactive debugging tools
docker exec -it container_name /bin/bash

# Inspect container details (JSON format)
docker inspect container_name

# Check container networking
docker exec container_name ping another_container

# Get IP address of container
docker inspect -f '{{range .NetworkSettings.Networks}}{{.IPAddress}}{{end}}' container_name

# Find containers by label
docker ps --filter "label=app=web"
```

## Security Best Practices

```bash
# Scan image for vulnerabilities
docker scan myimage:latest

# Run container with read-only filesystem
docker run --read-only nginx

# Run container with dropped capabilities
docker run --cap-drop=ALL --cap-add=NET_BIND_SERVICE nginx

# Run container with no privileges
docker run --security-opt=no-new-privileges nginx

# Use non-root user in container
docker run -u 1000:1000 nginx
```

## Advanced Network Examples

```bash
# Create an overlay network for Swarm
docker network create --driver overlay --attachable mynetwork

# Create a macvlan network
docker network create -d macvlan \
  --subnet=192.168.0.0/24 \
  --gateway=192.168.0.1 \
  -o parent=eth0 macvlan_net

# Connect container to multiple networks
docker network connect network2 container_name
```

## Environment Management

```bash
# Set environment variables from file
docker run --env-file ./env.list nginx

# Pass all host environment variables
docker run --env-file ./env.list -e VAR1 -e VAR2 nginx

# Override entrypoint
docker run --entrypoint /bin/bash nginx -c "echo hello"
```
