# Relational database
Learn how to create a new Node.js or TypeScript project from scratch by connecting Prisma to your database and generating a Prisma Client for database access. The following tutorial introduces you to the **Prisma CLI**, **Prisma Client**, and **Prisma Migrate**.

## Prerequisites
In order to successfully complete this guide, you need:
- **Node.js** installed on your machine
- a **MySQL** database server running

> Make sure you have your database connection URL at hand. If you don't have a database server running and just want to explore Prisma, check out the [[quickstart]].

## Create a project setup
As a first step, create a project directory and navigate into it:
```sh
mkdir hello-prisma
cd hello-prisma
```

Next, initialize a TypeScript project and add the Prisma CLI as a development dependency to it:

```sh
yarn init -y
yarn add prisma typescript ts-node @types/node --save-dev
```

This creates a `package.json` with an initial setup for your TypeScript app.

Next, initialize TypeScript:
```sh
yarn tsc --init
```

You can now invoke the Prisma CLI by prefixing it with `yarn`:
```sh
yarn prisma
```

Next, set up your Prisma project by creating your **Prisma schema** file with the following command:
```sh
yarn prisma init
```

This command does two things:
- creates a new directory called `prisma` that contains a file called `schema.prisma`, which contains the Prisma schema with your database connection variable and schema models
- creates the `.env` file in the root directory of the project, which is used for defining environment variable (such as your database connection)