#mysql
[[mysql_cli_run|Запуск консольного клиента]]
[[mysql_cli_single_query|Запуск одного запроса]]
[[mysql_whoami|Узнать текущего пользователя]]

#### Вывести все БД
```sql
show databases;
```

#### Как сделать дамп
https://serverfault.com/a/912677
```bash
mysqldump --column-statistics=0 -u mixon272 mixon272\$money -h mixon272.mysql.pythonanywhere-services.com -p 
```

#### Как восстановить дамп
https://phoenixnap.com/kb/how-to-backup-restore-a-mysql-database
```bash
mysql -u [username] -p [database-name] < dump.sql

gunzip -c dump.sql.gz | mysql -u [username] -p [database-name]
```