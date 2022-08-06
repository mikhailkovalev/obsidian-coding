#docker #docker-compose #mysql

```yaml
version: '3.3'  
  
services:  
  mysql:  
    image: "mysql:5.7.34"  
 environment:  
      MYSQL_RANDOM_ROOT_PASSWORD: "yes"  
 MYSQL_DATABASE: pocketbook  
      MYSQL_USER: pocketbook  
      MYSQL_PASSWORD: pocketbook  
    ports:  
      - "3306:3306"  
 volumes:  
      - './mysql-datadir:/var/lib/mysql'  
 command:  
      - "--character-set-server=utf8mb4"  
      - "--collation-server=utf8mb4_unicode_ci"
```