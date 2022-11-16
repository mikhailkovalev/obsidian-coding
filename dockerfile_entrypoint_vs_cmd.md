#docker #dockerfile #entrypoint #cmd
[Source](https://habr.com/ru/company/southbridge/blog/329138/)
- Для контейнера необходимо определить хотя бы одну из инструкций `ENTRYPOINT` или `CMD`
- Если определена только одна из них -- эффект будет один и тот же
- И для `ENTRYPOINT`, и для `CMD` есть режимы `shell` (не рекомендуемый) и `exec` (рекомендуемый)
- `exec`: `ENTRYPOINT ["executable", "param1", "param2"]`
- `shell`: `ENTRYPOINT command param1 param2`
- Для `shell`-режима переданная строка оборачивается в `/bin/sh -c`
- При использовании `shell`-режима возможны неочевидности: например, сигнал `SIGINT` (`Ctrl + C`) посланный в процесс `sh` не будет передан в дочерний процесс (если по какой-то причине нужно использовать именно `shell`-режим -- лучше использовать `exec`: `ENTRYPOINT exec ping google.com`)
- При использовании `exec`-режима нет доступа к переменным окружения (например `$PATH`)