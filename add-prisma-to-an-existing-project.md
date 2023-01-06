# Relational database
Learn how to add Prisma to an existing Node.js or TypeScript project by connecting it to your database and generating a Prisma Client for database access. The following tutorial introduces you to the **Prisma CLI**, **Prisma Client**, and **Prisma Introspection**.

## Prerequisites
In order to successfully complete this guide, you need:
- an existing Node.js project with a `package.json`
- Node.js installed on your machine
- a MySQL database server running and a database with at least one table

> Make sure you have a database connection URL (that includes your authentication credentials) at hand! If you don't have a database server running and just want to explore Prisma, check out the [[quickstart]].

## Set up Prisma
As a first step, navigate into your project directory that contains the `package.json` file.

Next, add the Prisma CLI as a development dependency to your project:
```sh
yarn add prisma --save-dev
```

You can now invoke the Prisma CLI by prefixing it with `yarn`:
```sh
yarn prisma
```

Next, set up your Prisma project by creating your **Prisma schema** file template with the following command:
```sh
yarn prisma init
```

This command does two things:
- creates a new directory called `prisma` that contains a file called `schema.prisma`, which contains the Prisma schema with your database connection variable and schema models
- creates the `.env` file in the root directory of the project, which is used for defining environment variables (such as your database connection)