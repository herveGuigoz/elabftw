# Elabftw with Caddy

Opinioned [elabftw](https://github.com/elabftw/elabftw) configuration with [caddy](https://caddyserver.com/docs/) server.

## Features

- Automatic HTTPS provisions TLS certificates for all your sites and keeps them renewed.
- Can serve static files or other services with caddy directives

## Getting started

### Configuration

Edit `.env` with your own configuration

### Build containers

```bash
docker-compose build --pull --no-cache
```

### Start containers

```bash
docker-compose up --detach
```

### Import the database structure

```bash
docker exec -it elab bin/install start
```

## Additional information

If you comme from default elab configuration:

- [Backup](https://doc.elabftw.net/backup.html#backup) your installation

```bash
elabctl backup
```

- Stop old container

```bash
elabctl stop
```

- Populate env file

```bash
echo "$(grep -o -m 1 "SERVER_NAME=.*" docker-compose.yml)\n$(grep -o -m 1 "MYSQL_ROOT_PASSWORD=.*" docker-compose.yml)\n$(grep -o -m 1 "DB_NAME=.*" docker-compose.yml)\n$(grep -o -m 1 "DB_USER=.*" docker-compose.yml)\n$(grep -o -m 1 "DB_PASSWORD=.*" docker-compose.yml)\n$(grep -o -m 1 "SECRET_KEY=.*" docker-compose.yml)" > .env
```

- Edit the volumes to bind the default directories.

```yaml
# elab service
volumes:
    - /var/elabftw/web:/elabftw/uploads
# database service
volumes:
    - /var/elabftw/mysql:/var/lib/mysql
```

