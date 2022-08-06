#docker #docker_cli 
## Получить ip контейнера
```bash
docker container inspect my_container -f '{{.Name}} - {{range.NetworkSettings.Networks}}{{.IPAddress}}{{end}}'
```