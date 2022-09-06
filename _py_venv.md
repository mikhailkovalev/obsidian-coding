#python #venv #virtualenv 

### Очистить virtualenv
```bash
pip freeze | grep -v "^-e" | xargs pip uninstall -y
```