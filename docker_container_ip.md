#docker #docker_cli 
## Получить ip контейнера
```bash
docker container inspect kanboard-kanboard-1 -f '{{.Name}} - {{range.NetworkSettings.Networks}}{{.IPAddress}}{{end}}'
```