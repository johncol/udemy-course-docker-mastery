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

Check that two containers can talk to each other through docker dns service

```
docker container exec --interactive --tty <container_name1> ping <container_name2>
```

Create a couple of `elasticsearch` containers, both using the dns alias `elastic`

```
docker container run -d --net sample_net3 --network-alias elastic --name elastic1 elasticsearch:6.4.0
docker container run -d --net sample_net3 --network-alias elastic --name elastic2 elasticsearch:6.4.0
```

Create container of image `alpine`, added to the network `sample_net3`, and execute `nslookup` to `elastic`. `--rm` is used to remove the container immediately after the command is run

```
docker container run --net sample_net3 --rm alpine nslookup elastic
```

Run `centos` container, added to network `sample_net3`, and executes `curl` to domain name `elastic` on port 9200, where elastic containers are listening

```
docker container run --rm --net sample_net3 centos curl -s elastic:9200
```

To see the layers of an image

```
docker image history <name>
```

To inspect the configuration and how to use an image

```
docker image inspect <name>
```

To create a new image tag from an existing one

```
docker image tag <name>:<tag> <new-name>:<new-tag>
```

To push an image

```
docker image push <name>:<tag>
```

To login/logout

```
docker login
docker logout
```

To create a new image from a dockerfile

```
docker image build --tag <image_name>:<version/tag> <path_to_dockerfile>
```

To clean all docker objects

```
docker system prune
```

To clean containers

```
docker container prune
```

To clean images

```
docker image prune
```

To manually create a volume

```
docker volume create <volume_name>
```

To specify a container which volume to use:

```
docker container run --volume <name>:<path> <image_name>
```

e.g. mysql image uses a volume in /var/lib/mysql (check https://github.com/docker-library/mysql/blob/69e4645ced5c687b861ce4a4e8aa3ca4600152b6/8.0/Dockerfile#L69), so it would be:

```
docker container run --volume mysql_volume:/var/lib/mysql mysql:latest
```

To create a bind mount, use a path instead of a name when running a container with a specific volume:

```
docker container run --volume /some/path/in/the/host:/path/in/the/container <image_name>
```

To list images filtered byt by repositories, e.g. `postgres`:

```
docker image ls --filter=reference=postgres
```
