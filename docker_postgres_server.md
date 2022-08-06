#docker #docker_cli #postgres #run_postgres
## Запуск сервера
Создать контейнер с сохранением файлов на локальном хосте
```bash
docker container create
    --name <server-container-name>
	-e POSTGRES_PASSWORD=postgres
	-e PGDATA=/var/lib/postgresql/data/pgdata
	-v /mnt/hdd/postgres11_data:/var/lib/postgresql/data
    -v /mnt/hdd/backups:/backups
    postgres:11.10-alpine
```

Создать контейнер без сохранения файлов на локальном хосте
```bash
docker container create
    --name postgres14
	-e POSTGRES_PASSWORD=postgres
	-p 5432:5432/tcp
	postgres:14.4-alpine
```