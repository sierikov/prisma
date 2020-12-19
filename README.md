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
- npm
- Node.js

Clone the repo. Navigate to the project folder. And run following command:

### Database

```docker
docker-compose up -d
```

You can check that `Postgres` is now up by typing `docker ps` you'll see
something like below:

```text
CONTAINER ID        IMAGE               COMMAND                  CREATED
8547f8e007ba        postgres:10.3       "docker-entrypoint.s…"   3 seconds ago 
```

Use this info to specify database location in `.env` file if it differs.

### Queries

Use

```bash
npx prisma migrate dev --name "init" --preview-feature
```

To generate typesafe sql queries. They will be stored in `prisma/migrations` folder.
The schema can be predefined in `prisma/schema.prisma`.

- `--name "init"`: Specifies the name of the migration (will be used to name the migration folder that’s created on your filesystem).

### API Client

Then you can start Express client with:

```bash
npx ts-node src/index.ts
```

You'll see something like below:

```text
REST API server ready at: http://localhost:3000
```

So the rest enpoint is on `localhost` on `3000` port.

Go ahead and `post` somethin to the database. For example to create a new user via the `/user` route, you can send the following `POST` request with `curl`:

```curl
curl -X POST -H "Content-Type: application/json" -d '{"name":"Bob", "email":"bob@prisma.io"}' http://localhost:3000/user
```

You'll see output like this:

```text
{"id":2,"email":"bob@prisma.io","name":"Bob"}
```

Or to add a post as *draft* you can simply send:

```curl
curl -X POST -H "Content-Type: application/json" -d '{"title":"I am Bob", "authorEmail":"bob@prisma.io"}' http://localhost:3000/post
```

And then publish it with:

```curl
curl -X PUT http://localhost:3000/post/publish/2
```

Check out your posted article on `/feed`.

Finally you can delete your post by calling `DELETE` request like below:

```curl
curl -X DELETE http://localhost:3000/post/2
```

## Endpoints

Here is complete of all endpoints to test.

| HTTP Method   | Route               | Description                                     |
| ------------- |:------------------- | :---------------------------------------------- |
| `GET`         | `/feed`             | Fetches all *published* posts.                  |
| `GET`         | `/post/:id`         | Fetches a specific post by its ID.              |
| `POST`        | `/user`             | Creates a new user.                             |
| `POST`        | `/post`             | Creates a new post (*as a draft*).              |
| `PUT`         | `/post/publish/:id` | Sets the `published` field of a post to `true`. |
| `DELETE`      | `/post/:id`         | Deletes a post by its ID.                       |

## Technologies

- Prisma
- Postgres
- Typescript
- Express

## More

As next steps, you can implement additional API routes or extend your database schema using
Prisma Migrate. Be sure to visit the [Prisma documentation](https://www.prisma.io/docs)
to learn more about Prisma. And some pre-built projects.

## Meta

Sierikov Artem – [twitter](https://twitter.com/sierikov_)

## Contribute

1. Fork it (<https://github.com/sierikov/prisma/fork>)
1. Create your feature branch (`git checkout -b feature/fooBar`)
1. Commit your changes (`git commit -am 'Add some fooBar'`)
1. Push to the branch (`git push origin feature/fooBar`)
1. Create a new Pull Request
