#docker #docker_cli 
## Получить ip контейнера
```bash
docker container inspect kanboard_kanboard_1 -f '{{.Name}} - {{range.NetworkSettings.Networks}}{{.IPAddress}}{{end}}'
```