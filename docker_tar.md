#docker #tar #docker_save #docker_load
[Source](https://stackoverflow.com/a/23938978)

```bash
docker save -o /path/to/generated/tar/file.tar my_image:my_tag
```

```bash
docker load -i /path/to/existing/tar/file.tar
```