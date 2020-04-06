docker network create --driver overlay front
docker network create --driver overlay back

docker service create \
 --name vote \
 --network front \
 -p 80:80 \
 bretfisher/examplevotingapp_vote

docker service create \
 --name redis \
 --network front \
 redis:3.2

docker service create \
 --name worker \
 --network front \
 --network back \
 bretfisher/examplevotingapp_worker:java

docker service create \
 --name postgres \
 --network back \
 --mount type=volume,source=db-data,target=/var/lib/postgresql/data \
 --env POSTGRES_USER=root \
 --env POSTGRES_PASSWORD=root \
 postgres:9.4

docker service create \
 --name result \
 --network back \
 --publish 4000:80 \
 bretfisher/examplevotingapp_result
