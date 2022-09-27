#docker #docker_cli #docker_container #docker_container_create #docker_entrypoint
Создаёт, но не запускает контейнер. Для запуска созданного контейнера следует использовать [[docker_container_start|start]]
#### Создание контейнера из образа
```bash
docker container create my_repo/my_image:my_tag
```
Конструкция `my_repo/my_image:my_tag` может быть сокращена до `my_image`

#### Подключение контейнера к `stdin`, `stdout`, `stderr`
```bash
docker container create -a STDIN my_image
```


#### Взаимодействие с контейнером через терминал
Чтобы получить возможность взаимодействия с контейнером через терминал нужно совместно использовать флаги `-i` и `-t`.

+ `-i` (`--interactive`): Поддерживать поток STDIN даже, если контейнер не подключен к STDIN.

+ `-t` (`--tty`): Выделить псевдотерминал, который соединяет используемый терминал с потоками STDIN и STDOUT контейнера.

#### Переопределение entrypoint
```bash
docker container create -it --entrypoint /bin/bash my_image
```

#### Команда для запуска
Можно указать сво
```bash
docker create -p 8080:8080 --name my_container my_image python3 main.py
```

#### Открытие сетевого доступа
`-p`
```bash
docker container create -p 127.0.0.1:80:8000/tcp ubuntu bash
```
Эта команда привязывает TCP порт контейнера 8080 к порту 80 на 127.0.0.1