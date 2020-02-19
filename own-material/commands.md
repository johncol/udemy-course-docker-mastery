# Some commands

Show info about docker installation

```
docker version
```

```
docker info
```

Run a nginx container locally at port `8080`

```
docker container run --publish 8080:80 nginx
```

Run a nginx container locally at port `8080` and detach

```
docker container run --publish 8080:80 --detach nginx
```

List running containers

```
docker container ls
```

Stop a container which DI uniquely starts with `ID-prefix`

```
docker container stop <ID-prefix>
```

List all containers, not just the ones that are currently running

```
docker container ls --all
```

Use `--name <name>` to explicitly define a name for your container

```
docker container run --publish 8080:80 --name <name> nginx
```

To see the logs of a container

```
docker container logs <name>
```

To see the processes inside a container with name `<name>`

```
docker container top <name>
```

To remove containers `n` container

```
docker container rm <name_1> <name_2> ... <name_n>
```

List images found locally

```
docker image ls
```

See info about a container

```
docker container inspect <name>
```

```
docker container stats
```

To execute a process in a running container, e.g. bash, interactively, run

```
docker container exec --tty --interactive <name> bash
```
