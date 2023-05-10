1. Update Dockerfile - add linux/amd64 platform.
```php
// from php>Dockerfile
FROM --platform=linux/amd64 php:8.1-fpm
```

2. Update docker-compose.yml - change sql server.
```php
// from docker-compose.yml
# SQL Service
database:
    # image: mcr.microsoft.com/mssql/server:2022-latest
    image: mcr.microsoft.com/azure-sql-edge:latest
```