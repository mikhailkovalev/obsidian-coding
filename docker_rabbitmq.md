#docker #docker_cli #rabbitmq #run_rabbitmq
## Запуск брокера
```bash
sudo docker run
    -d
	--hostname my-rabbit-host
	--name rabbit-from-docker
	rabbitmq:3.7.11-alpine
```

Через `create/start`
```bash
docker container create
    --hostname my-rabbit-host
	--name rabbit-from-docker
	-p 5672:5672
	rabbitmq:3.7.11-alpine

docker container start
    rabbit-from-docker
```