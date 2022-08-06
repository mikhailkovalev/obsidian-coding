#docker #docker_cli #mysql #run_mysql
## Запуск сервера
```bash
docker run
    --name <server-container-name>
	-e MYSQL_ROOT_PASSWORD=<root-password>
	-d
	mysql:tag
```

Через `create/start`
```bash
docker container create
    --name <server-container-name>
	-e MYSQL_ROOT_PASSWORD=<root-password>
	mysql:tag

docker container start <server-container-name>
```