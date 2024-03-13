# Docker CheatSheet

### List container

```shell
$ docker ps                                                               
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES
```

```shell
$ docker-compose ps
```

### Kill containers
Forces running containers to stop by sending a `SIGKILL` signal. Optionally the signal can be passed, for example:

```shell
docker-compose kill -s SIGINT
```

### Removes stopped service containers.

By default, anonymous volumes attached to containers are not removed. You can override this with `-v`. To list all volumes, use `docker volume ls`.

Any data which is not in a volume is lost.

Running the command with no options also removes one-off containers created by `docker-compose up` or `docker-compose run`:

```shell
$ docker-compose rm
Going to remove djangoquickstart_web_run_1
Are you sure? [yN] y
Removing djangoquickstart_web_run_1 ... done
```

### Remove images 
Remove one or more images

```shell
$ docker rmi [OPTIONS] IMAGE [IMAGE...]
```

### Remove containers

```shell
$ docker rm [OPTIONS] CONTAINER [CONTAINER...]
```

![[Capture d’écran 2022-05-17 à 13.40.05.png]]