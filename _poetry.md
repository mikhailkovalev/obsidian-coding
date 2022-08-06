#python #poetry #install #uninstal
https://realpython.com/dependency-management-python-poetry/
Пока что всё будет кидаться сюда, потом рассортирую

### Poetry installation
```bash
curl https://raw.githubusercontent.com/python-poetry/poetry/master/install-poetry.py | python3 -
```

По дефолту на маке установилось в `/Users/kovalev_m/Library/Python/3.9/bin/poetry`

### Poetry uninstallation
Использовать тот же скрипт с опцией `--uninstall`

### Create new project
```bash
poetry new rp-poetry
```
Здесь `rp-poetry` -- имя папки проекта и имя проекта:
```
rp-poetry/
+-- rp_poetry/
|   +-- __init__.py
+-- tests/
|   +-- __init__.py
|   +-- test_rp_poetry.py
+-- README.rst
+-- pyproject.toml
```


#### Задать разные имена для папки и для проекта:
```bash
poetry new --name realpoetry rp-poetry
```

```
rp-poetry/
+-- realpoetry/
|   +-- __init__.py
+-- tests/
|   +-- __init__.py
|   +-- test_realpoetry.py
+-- README.rst
+-- pyproject.toml
```

#### Поместить сгенеренный пакет в папку `src/`:
```bash
poetry new --src rp-poetry
```
Результат:
```
rp-poetry/
+-- src/
|   +-- realpoetry/
|       +-- __init__.py
+-- tests/
|   +-- __init__.py
|   +-- test_rp_poetry.py
+-- README.rst
+-- pyproject.toml
```

### Структура файла `pyproject.toml`
Стандарт описан в PEP 518: https://www.python.org/dev/peps/pep-0518/#abstract

Секции выделяемые  квадратными скобками называются таблицами. Можно выделять под-таблицы:
```
[table]
foo = "bar"

[table.subtable]
buzz = "bump"
```

Если таблица специфична для инструмента, то имя таблицы должно содержать префикс `tool`:
```
[tool.poetry]
...

[tool.poetry.dependencies]
...

# пример таблицы не для `poetry`:
[tool.pytest.ini_options]
...
```

Справка по доступным атрибутам
https://python-poetry.org/docs/pyproject/

### Проверка валидности `pyproject.toml`
```bash
poetry check
```
### Виртуальные окружения
По умолчанию окружения не создаются.

Посмотреть имеющиеся окружения:
```bash
poetry env list
```

Создать новое окружение:
```bash
poetry env use /path/to/python
```

Место создания окружения зависит от ОС

Можно переопределить это место изменив конфиг `poetry`.
https://python-poetry.org/docs/configuration

Текущие настройки можно посмотреть через 
```bash
poetry config --list
```

### Установка зависимостей
```bash
poetry install
```
Устанавливает зависимости из `pyproject.toml`, если отсутствует файл `poetry.lock`

Если в `pyproject.toml` добавить новые зависимости вручную, то запуск `poetry install` приведёт к ошибке.

Чтобы закрепить зависимости, добавленные вручную в `pyproject.toml`, нужно выполнить 
```bash
poetry lock
```

Запуск `poetry lock` обрабатывает все зависимости из `pyproject.toml` и фиксирует их в файле `poetry.lock`. Кроме непосредственных зависимостей проекта, так же фиксируются зависимости зависимостей.

```bash
poetry lock --no-update
```
Чтобы обновить в `poetry.lock` только новые зависимости, старые оставить как были

### Запуск тестов
```bash
poetry run pytest
```

### Описание версий зависимостей в `pyproject.toml`
Подробно здесь:
https://python-poetry.org/docs/dependency-specification/#version-constraints

### Установка новых пакетов
```bash
poetry add requests
```
Установит последнюю версию `requests`

```bash
poetry add black -D
```
Установит последнюю версию `black` пометив её как `dev`-зависимость

### Список установленных пакетов
```bash
poetry show
```

### Обновление зависимостей
Можно обновить в пределах указанных ограничений (например, накатить минорную версию или патч) и ли выйти за ограничения

```bash
poetry update
```
Обновляет зависимости в пределах указанных ограничений.

Можно указать только конкретные пакеты:
```bash
poetry update requests beautifulsoup4
```

Чтобы выйти за пределы ограничений надо либо скорректировать `pyproject.toml`, либо использовать команду `add` с новым ограничением версий или с тэгом `latest`:
```bash
poetry add pytest@latest --dev
```

Если не использовать указание новой версии или тэг `latest`, то упадёт ошибка а-ля "зависимость уже присутствует"

После добавления новой версии нужно запустить `poetry install` чтобы обновления были отражены в `poetry.lock`

### Добавление poetry в существующий проект
```bash
poetry init
```
Эта команда стартует интерактивную сессию чтобы создать `pyproject.toml`. 

После создания `pyproject.toml` можно использовать `poetry` в проекте

#### Если присутствует `requirements.txt`
Просто использовать команду `add`, в которую прокинуть все зависимости из `requirements.txt`:
```bash
poetry add `cat requirements.txt`
```

В случае если `requirements.txt` содержит сложные вещи, можно добавить зависимости в `pyproject.toml` вручную.

#### Как восстановить `requirements.txt` из `poetry.lock`
```bash
poetry export --output requirements.txt
```