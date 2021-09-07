# Docker

#### View all containres

```bash
docker ps -a
```
[doc](https://docs.docker.com/engine/reference/commandline/ps/)


#### View all volumes or container

```bash
docker volume ls
docker container ls
```
[doc](https://docs.docker.com/engine/reference/commandline/container_ls/)

#### Creating a volume for a database
```bash
docker volume create --name vol_1
```
[doc](https://docs.docker.com/engine/reference/commandline/volume_create/)

#### Launch container

```bash
docker run --rm --name pg-docker -e POSTGRES_PASSWORD=abc_123** -d -p 5400:5432 -v vol_1:/var/lib/postgresql/data postgres
```
[doc](https://docs.docker.com/engine/reference/commandline/run/)

#### Stop container

```bash
docker container stop pg-docker
```
[doc](https://docs.docker.com/engine/reference/commandline/container_stop/)

#### Save data from volume locally

```bash
docker run --rm -v vol_1:/volume -v e:/backup:/backup busybox sh -c 'cp -r /volume /backup'
```
[doc](https://docs.docker.com/desktop/backup-and-restore/)

where
run - Launch container
--rm - automatically removes the container if it already exists
-v vol_1:/volume -v e:/backup:/backup - we make mapping of catalogs
busybox - docker image in which you can find many linux utilities
sh -c 'cp -r /volume /backup' - execute the data copy command


===

## Common

- [Базы данных в 2020 (введение, история, состояние)](https://www.youtube.com/watch?v=8RjT2VYBWNQ)
- [Слайды](https://www.slideshare.net/tshemsedinov/2020-228734914)

### Node and connecting to db
- [Работа с базами данных в Node.js на примере PostgreSQL](https://www.youtube.com/watch?v=2tDvHQCBt3w)
  2.1. [github](https://github.com/HowProgrammingWorks/Databases)
- [How to Connect PostgreSQL with NodeJs Application?](https://medium.com/@dannibla/connecting-nodejs-postgresql-f8967b9f5932)

### Install: Docker and Postgres
- Docker Desktop for Window
- [pgAdmin 4 v5.6](https://www.pgadmin.org/download/pgadmin-4-windows/)
- [Setup PostgreSQL on Windows with Docke](https://elanderson.net/2018/02/setup-postgresql-on-windows-with-docker/)
- [SPACE. ROCKETS. POSTGRESQL](https://bigmachine.io/products/a-curious-moon/)
- [Docker, Windows, PostgreSQL и как это поможет в разработке торговых роботов](https://www.youtube.com/watch?v=EPJV2JZd67s)
