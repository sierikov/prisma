# Prisma

## About

Prisma Client is an auto-generated and type-safe query builder that you
can use to programmatically read and write data in a database from a
Node.js or TypeScript application. You will use it for database
access within your REST API routes, replacing traditional ORMs, plain
SQL queries, custom data access layers, or any other method of talking
to a database.

## How to run

You'll need:

- Docker
- Node.js

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

This info is usefull to specify database location in `.env` file.

Use

```bash
npx prisma migrate dev --name "init" --preview-feature
```

To generate typesafe sql queries. They will be stored in `prisma/migrations` folder.

- `--name "init"`: Specifies the name of the migration (will be used to name the migration folder that’s created on your filesystem).

## Technologies

- Prisma
- Postgres
- Typescript
- Express
