# elabftw

## Enable TLS certificates

- `Certbot` should be installed.

```env
# .env
DISABLE_HTTPS=false
ENABLE_LETSENCRYPT=true
```

```bash
# Select `Spin up a temporary webserver (standalone)`
sudo certbot certonly -d <domain> -m <email> --agree-tos
```

## Renew TLS certificates

```bash
docker-compose stop
```

```bash
certbot renew
```

```bash
docker-compose up -d --remove-orphans --no-recreate
```
