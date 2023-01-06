Prisma Client is an auto-generated and type-safe query builder that's *tailored* to your data. The easiest way to get started with Prisma Client is by following the [[quickstart]].

The setup instructions [[#Set up|below]] provide a high-level overview of the steps needed to set up Prisma Client. If you want to get started using Prisma Client with your own database, follow one of these guides:

- [[start-prisma-from-scratch|SET UP A NEW PROJECT FROM SCRATCH]]
- [[add-prisma-to-an-existing-project|ADD PRISMA TO AN EXISTING PROJECT]]

## Set up

### 1. Prerequisites
In order to set up Prisma Client, you need a **Prisma schema file** with your database connection, the Prisma Client generator, and at least one model:

`schema.prisma`
```prisma
datasource db {
	url      = env("DATABASE_URL")
	provider = "postgresql"
}

generator client {
	provider = "prisma-client-js"
}

model User {
	id        Int      @id @default(autoincrement())
	createdAt DateTime @default(now())
	email     String   @unique
	name      String?
}
```

Also make sure to *install the Prisma CLI*:
```sh
yarn add prisma --save-dev
yarn prisma
```

### 2. Installation
Install Prisma Client in your project with the following command:
```sh
yarn add @prisma/client
```

### 3. Use Prisma Client to send queries to your database
```ts
import { PrismaClient } from '@prisma/client'

const prisma = new PrismaClient()
// use `prisma` in your application to read and write data in your DB
```

or 

```ts
import { PrismaClient } from '@prisma/client'

const prisma = new PrismaClient()
// use `prisma` in your application to read and write data in your DB
```

Once you have instantiated `PrismaClient`, you can start sending queries in your code:

```ts
// run inside `async` function
const newUser = await prisma.user.create({
	data: {
		name: 'Alice',
		email: 'alice@prisma.io',
	},
})

const user = await prisma.user.findMany()
```

> - Note that queries will only run if used with `await` or chained with `.then()`. When using `$transaction`, this makes it possible for the client to pass all the queries on to the query engine as a transaction.
> - The client methods are "thenable", they return a PrismaPromise which is implemented like a JavaScript Promise, except for the query to be executed they need to be awaited or chained with `.then()`.

### 4. Evolving your application
Whenever you make changes to your database that are reflected in the Prisma schema, you need to manually re-generate Prisma Client to update the generated code in the `node_modules/.prisma/client` directory:
```sh
prisma generate
```