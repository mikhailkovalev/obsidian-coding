#docker #docker_cli #mysql
Запуск клиента в отдельном контейнере ([[mysql_cli_run|без докера]])
```bash
docker container create --name <client-container-name> -it --network <network-name> mysql mysql -h some-mysql -u example-user -p
```