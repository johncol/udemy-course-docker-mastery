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

See port configuration for container `<name>`

```
docker container port <name>
```

Find out the IP that my container has

```
docker container inspect --format '{{ .NetworkSettings.IPAddress }}' <name>
```

List all networks

```
docker network ls
```

See the current state and properties of a network called `<name>`

```
docker network inspect <name>
```

Creates a new network with the default driver `bridge`

```
docker network create <name>
```

Create a container attached to a specific network

```
docker container run -p 81:80 -d --network <network_name> --name <container_name> nginx
```

```
docker network create --driver
```

Add a container to a network (a container may be in several networks at a time)

```
docker network connect <network_name> <container_name>
```

Remove a container from a network

```
docker network disconnect <network_name> <container_name>
```
