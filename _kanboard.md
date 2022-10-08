[Source](https://docs.kanboard.org/en/latest/admin_guide/docker.html)

```bash
docker pull kanboard/kanboard:v1.2.23
```

### `docker-compose.yml` with SQLite
```yaml
version: '3.3'
services:
  kanboard:
    image: kanboard/kanboard:v1.2.23
    ports:
      - "80:80"
      - "443:443"
    volumes:
      - './data:/var/www/app/data'
      - './plugins:/var/www/app/plugins'
      - './ssl:/var/www/app/ssl'
```
