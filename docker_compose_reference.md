# 🐳 Docker Compose Cheatsheet

---

## Basic Example

```yaml
version: "3"
services:
  web:
    build:
      context: ./Path
      dockerfile: Dockerfile
    ports:
      - "5000:5000"
    volumes:
      - .:/code
  redis:
    image: redis
```

---

## Compose Commands

```bash
docker compose up         # Start all services
docker compose down       # Stop and remove containers
docker compose build      # Build images
docker compose logs       # View logs
docker compose ps         # List containers
docker compose exec web bash  # Exec into container
docker compose restart    # Restart services
docker compose stop       # Stop services
docker compose start      # Start services
docker compose images     # List images
docker compose config     # Validate config
```

---

## Service Reference

### Build

```yaml
build: .
build:
  context: ./dir
  dockerfile: Dockerfile.dev
args:
  APP_HOME: app
image: ubuntu:latest
```

### Ports

```yaml
ports:
  - "8000:80" # host:container
expose:
  - "3000" # expose to linked services only
```

### Commands

```yaml
command: bundle exec thin -p 3000
entrypoint: /app/start.sh
```

### Environment Variables

```yaml
environment:
  RACK_ENV: development
env_file:
  - .env
```

### Dependencies

```yaml
depends_on:
  - db
links:
  - db:database
```

### Healthcheck

```yaml
healthcheck:
  test: ["CMD", "curl", "-f", "http://localhost"]
  interval: 1m30s
  timeout: 10s
  retries: 3
  start_period: 40s
```

### Volumes

```yaml
volumes:
  - /var/lib/mysql
  - ./_data:/var/lib/mysql
```

### Networks

```yaml
networks:
  frontend:
    external: true
```

### User

```yaml
user: root
user: 1000:1000
```

### Labels

```yaml
labels:
  com.example.description: "Accounting web app"
```

### DNS

```yaml
dns:
  - 8.8.8.8
  - 8.8.4.4
```

### Devices

```yaml
devices:
  - "/dev/ttyUSB0:/dev/ttyUSB0"
```

### Extra Hosts

```yaml
extra_hosts:
  - "somehost:192.168.1.100"
```

---

## Advanced

- `extends`: Inherit service config from another file.
- `restart`: Control restart policy (`always`, `unless-stopped`, `on-failure`, `no`).
- `external_links`: Link to containers outside this compose file.

---

## Versioning

- Use `docker compose` (v2+) instead of `docker-compose` (v1).
- Most features are available in version 3 and above.

---
