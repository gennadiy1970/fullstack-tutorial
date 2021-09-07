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
