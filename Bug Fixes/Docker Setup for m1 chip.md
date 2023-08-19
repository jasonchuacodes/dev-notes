#### Problem
docker won't run properly on m1 chip as it is incompatible with default configuration.

#### Solution
Update Dockerfile - add linux/amd64 platform.
```php
// from php>Dockerfile
FROM --platform=linux/amd64 php:8.1-fpm
```

Update docker-compose.yml - change sql server.
```php
// from docker-compose.yml
# SQL Service
database:
    # image: mcr.microsoft.com/mssql/server:2022-latest
    image: mcr.microsoft.com/azure-sql-edge:latest
```