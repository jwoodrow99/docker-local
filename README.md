# Docker Local

This is a small docker compose project to startup the 4 most popular databases (including redis) on your local system. Docker Compose is usually added to a project to set up its environment, but in some cases you simply need access to a database on your local system, that is what this project is designed for. Each containers port is mapped to the default port of the service on your local machine and has volumes mapped to the directory of the docker compose file.

## Usage

This is a guid of how to stop start and cleanup everything generated by the docker compose file.

### Start Services

``` bash
docker-compose up --detach
```

### Stop Services

``` bash
docker-compose down
```

### Remove Services

``` bash
docker system prune --all --volumes
rm -rf volumes
```

## Connection Information

This is list of all of the information required to connect to each service while running.

### Mysql

| Key | Value |
|--|--|
| Host | localhost |
| Port | 3306 |
| User | root |
| Password | password |

### Pgsql

| Key | Value |
|--|--|
| Host | localhost |
| Port | 5432 |
| User | root |
| Password | password |

### Mongo

| Key | Value |
|--|--|
| Host | localhost |
| Port | 27017 |
| User | root |
| Password | password |

### Redis

| Key | Value |
|--|--|
| Host | localhost |
| Port | 6379 |

## One Liners

Below explains how to build each service with a single line using docker, excluding the volume mounting.

``` bash
docker run --name mysql-local -p 3306:3306 -e MYSQL_ROOT_PASSWORD=password -d mysql:latest --default-authentication-plugin=mysql_native_password

docker run --name pgsql-local -p 5432:5432 -e POSTGRES_PASSWORD=password -d postgres:latest

docker run --name mongo-local -p 27017:27017 -e MONGO_INITDB_ROOT_USERNAME=root -e MONGO_INITDB_ROOT_PASSWORD=password -d mongo:latest

docker run --name redis-local -p 6379:6379 -d redis:latest
```
