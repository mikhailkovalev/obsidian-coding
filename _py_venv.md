#python #venv #virtualenv 

### Очистить virtualenv
```bash
pip freeze | grep -v "^-e" | xargs pip uninstall -y
```
### Uninstall editable packages (installed with -e)
[Source](https://stackoverflow.com/a/18818891)
- Remove egg file in
```
{virtualenv}/lib/python<v>/site-packages/
{system_dir}/lib/python<v>/dist-packages/
```
- Remove corresponding line in `easy-install.pth`