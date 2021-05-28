

```bash
# run mysql server in docker
docker run --name local-mysql  \
-p 3306:3306 \
-e MYSQL_ROOT_HOST='%' -e MYSQL_ROOT_PASSWORD='admin123'   \
-d mysql/mysql-server:latest

# connect to mysql server 
docker exec -it local-mysql sh 
mysql -uroot -padmin123

# create test database and grant to user
CREATE DATABASE `testdb` DEFAULT CHARACTER SET utf8mb4 COLLATE utf8mb4_general_ci;

# create user and grant permissions
CREATE USER 'springuser'@'%' IDENTIFIED BY 'test123' PASSWORD EXPIRE NEVER;
ALTER USER 'springuser'@'%' IDENTIFIED WITH mysql_native_password BY 'test123';
GRANT ALL ON testdb.* to 'springuser'@'%';

FLUSH PRIVILEGES;


# mysql command
show datbases;
use <database>
show tables;

```

Initialization SQL:
- src/main/resources/schema-${platform}.sql
- src/main/resources/data-${platform}.sql
- src/main/resources/import.sql





References
- [Table 'DBNAME.hibernate_sequence' doesn't exist](https://stackoverflow.com/questions/49813666/table-dbname-hibernate-sequence-doesnt-exist/49813851)