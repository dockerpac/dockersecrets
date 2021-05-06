# Docker secrets

## Locally

Secrets vars are set as env vars in docker-compose.override.yml

```sh
docker-compose up -d

# Check value of SECRET1
docker-compose logs
# --> SECRET1=secretdev

# cleanup
docker-compose down
````

## Swarm

Secrets vars are set as external swarm secrets

```sh
# First create docker secret
echo "secretprod" | docker secret create SECRET1 -
docker stack deploy -c docker-compose.yml mystack

# Check value of SECRET1
docker service logs mystack_alpine
# --> SECRET1=secretprod

# cleanup
docker stack rm mystack
```
