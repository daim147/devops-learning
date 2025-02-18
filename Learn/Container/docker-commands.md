# Docker Commands Cheat Sheet

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
```

### Containers

```bash
# Run a container
docker run -d --name webserver nginx

# Run with port mapping
docker run -d -p 8080:80 nginx

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

# Access container shell
docker exec -it container_name bash
```

### Network

```bash
# List networks
docker network ls

# Create a network
docker network create mynetwork

# Connect container to network
docker network connect mynetwork container_name
```

### Volumes

```bash
# Create a volume
docker volume create myvolume

# List volumes
docker volume ls

# Remove volume
docker volume rm myvolume
```

## Docker Compose

### Basic Operations

```bash
# Start services
docker-compose up -d

# Stop services
docker-compose down

# View logs
docker-compose logs

# Scale service
docker-compose up -d --scale web=3
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

## System Management

```bash
# System info
docker info

# Clean up system
docker system prune

# View container stats
docker stats

# View logs
docker logs container_name
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
