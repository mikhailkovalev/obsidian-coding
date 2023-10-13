#python #venv #virtualenv 

### Очистить virtualenv
```bash
pip freeze | grep -v "^-e" | xargs pip uninstall -y
```
### Uninstall editable packages (installed with -e)
- Remove egg file in
```
{virtualenv}/lib/python<v>/site-packages/
{system_dir}/lib/python<v>/dist-packages/
```
- Remove corresponding line in `easy-install.pth`