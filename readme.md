# Flyway by Gradle
## Environment
- OS : macOS Mojave(10.14.6)
- Gradle : 5.2.1
- Flyway : 6.2.2
- MySQL : 5.7.24

## MySQL Setup
```sql
-- CREATE DATABASE
CREATE DATABASE localdb DEFAULT CHARACTER SET utf8;
SHOW DATABASES;

-- CREATE USER
CREATE USER 'flywayuser'@'localhost' IDENTIFIED BY 'flywaypass';
SELECT user, host FROM mysql.user;

-- GRANT PRIVILEGES
GRANT ALL ON localdb.* TO 'flywayuser'@'localhost' IDENTIFIED BY 'flywaypass';
FLUSH PRIVILEGES;
SHOW GRANTS FOR 'flywayuser'@'localhost';
```

## SQL Location
`./src/main/resources/db/migration`

## Execute Flyway tasks
- Check status
  ```
  gradle flywayInfo
  ```
- Migration
  ```
  gradle flywayMigrate
  ```
- Repair
  ```
  gradle flywayRepair
  ```
- Delete
  ```
  gradle flywayClean
  ```

## Specify an environment identifier
- For Dev
  ```
  gradle flywayInfo -Penv=dev
  ```

## Connection information
`./gradle.properties`