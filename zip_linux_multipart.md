### Распаковка многотомного архива
Нужно собрать тома в один файл через утилиту `cat` (файл с расширением `zip` должен быть последним):
```bash
cat big-archive.z01 big-archive.z02 big-archive.zip > merged-big-archive.zip
```

Далее -- извлечь с помощью `unzip`:
```bash
unzip merged-big-archive.zip
```