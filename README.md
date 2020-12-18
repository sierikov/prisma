# Prisma

## How to run

You'll need:

- Docker

Clone the repo. Navigate to the project folder. And run following command:

```docker
docker-compose up -d
```

You can check that `Postgres` is now up by typing `docker ps` you'll see
something like below:

```text
CONTAINER ID        IMAGE               COMMAND                  CREATED
8547f8e007ba        postgres:10.3       "docker-entrypoint.s…"   3 seconds ago 
```

This info is usefull to specify database location in `.env` location.
