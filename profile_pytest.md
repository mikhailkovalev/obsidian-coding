#pytest #python #line_profiler #profile #kernprof

[Source](https://stackoverflow.com/a/23765051)

Чтобы выполнить профилирование `pytest`-тестов через `kernprof` следует написать отдельный скрипт, который запустит `pytest`:

```python
import pytest


if __name__ == '__main__':
	pytest.main([  # да-да, нужен именно список
		'tests',
		
		# Или запустить конкретный тест
		# 'tests/test_mytest.py::test_basic',
		
		# Далее могут следовать другие аргументы,
		# которые можно передавать в `pytest` в
		# командной строке
	])
```

Далее запускаем `kernprof` "как обычно":
```bash
kernprof -l /path/to/script.py
```

После этого результат выполнения должен записаться в файл `script.py.lprof`

Для "человекочитабельного" просмотра выполнить:
```bash
python -m line_profiler script.py.lprof
```
