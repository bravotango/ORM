# Object-Relational Mapping (ORM): E-Commerce Back End

## Task

Internet retail, also known as **e-commerce**, is the largest sector of the electronics industry, generating an estimated $29 trillion in 2019. E-commerce platforms like Shopify and WooCommerce provide a suite of services to businesses of all sizes. Due to their prevalence, understanding the fundamental architecture of these platforms will benefit you as a full-stack web developer.

The task is to build the back end for an e-commerce site by modifying starter code. Configure a working Express.js API to use Sequelize to interact with a MySQL database.

Because this application won’t be deployed, a link to a walkthrough video is provided that demonstrates its functionality and all of the acceptance criteria being met.

## User Story

```md
AS A manager at an internet retail company

I WANT a back end for my e-commerce website that uses the latest technologies
SO THAT my company can compete with other e-commerce companies
```

## Satisfied Acceptance Criteria

```md
GIVEN a functional Express.js API

WHEN I add my database name, MySQL username, and MySQL password to an environment variable file
THEN I am able to connect to a database using Sequelize

WHEN I enter schema and seed commands
THEN a development database is created and is seeded with test data

WHEN I enter the command to invoke the application
THEN my server is started and the Sequelize models are synced to the MySQL database

WHEN I open API GET routes in Insomnia for categories, products, or tags
THEN the data for each of these routes is displayed in formatted JSON

WHEN I test API POST, PUT, and DELETE routes in Insomnia
THEN I am able to successfully create, update, and delete data in my database
```

## Project packages

This project uses the [MySQL2](https://www.npmjs.com/package/mysql2) and [Sequelize](https://www.npmjs.com/package/sequelize) packages to connect the Express.js API to the MySQL database and the [dotenv](https://www.npmjs.com/package/dotenv) package to use environment variables that store sensitive data.

## Database Models

The database contains the following four models, including the requirements listed for each model:

- `Category`

  - `id`

    - Integer.
    - Doesn't allow null values.
    - Set as primary key.
    - Uses auto increment.

  - `category_name`
    - String.
    - Doesn't allow null values.

- `Product`

  - `id`

    - Integer.
    - Doesn't allow null values.
    - Set as primary key.
    - Uses auto increment.

  - `product_name`

    - String.
    - Doesn't allow null values.

  - `price`

    - Decimal.
    - Doesn't allow null values.
    - Validates that the value is a decimal.

  - `stock`

    - Integer.
    - Doesn't allow null values.
    - Set a default value of `10`.
    - Validates that the value is numeric.

  - `category_id`

    - Integer.
    - References the `Category` model's `id`.

- `Tag`

  - `id`

    - Integer.
    - Doesn't allow null values.
    - Set as primary key.
    - Uses auto increment.

  - `tag_name`
    - String.

- `ProductTag`

  - `id`

    - Integer.
    - Doesn't allow null values.
    - Set as primary key.
    - Uses auto increment.

  - `product_id`

    - Integer.
    - References the `Product` model's `id`.

  - `tag_id`

    - Integer.
    - References the `Tag` model's `id`.

## Associations

Association methods on Sequelize models create the following relationships between them:

- `Product` belongs to `Category`, and `Category` has many `Product` models, as a category can have multiple products but a product can only belong to one category.

- `Product` belongs to many `Tag` models, and `Tag` belongs to many `Product` models. Products have multiple tags and tags have many products by using the `ProductTag` through model.

## API Routes to Perform RESTful CRUD Operations

`product-routes.js`, `tag-routes.js`, and `category-routes.js` perform create, read, update, and delete operations using Sequelize models.

## How to Set up Project

### After cloning project, NPM Install

Clone the project then in the terminal run:

```
$ npm install
```

### Add your credentials to '.env.Template':

Add your database user name and password to the template:

```
DB_USER=''
DB_PW=''
DB_NAME='ecommerce_db'
```

### Rename '.env.Template' File to '.env':

```
- Remove the extension '.Template'
- Filename should be '.env'
```

### Set up Database

Create database with following commands in the terminal:

```
$ mysql -u root -p
Enter password: *******
mysql> source db/schema.sql
mysql> exit
```

### Seed Database

```
$ npm run seed
```

### Start server

```
$ npm start
```

### Sync Sequelize to the Database on Server Start

Code in `server.js` will sync the Sequelize models to the MySQL database on server start.

## Walkthrough Video:

Walkthrough video demonstrating the functionality of the e-commerce back end:

[https://watch.screencastify.com/v/vrHEd4Y7cpJMMGTTD2yK](https://watch.screencastify.com/v/vrHEd4Y7cpJMMGTTD2yK)

- This walkthrough video shows all of the technical acceptance criteria being met.

- This walkthrough video demonstrates how to create the schema from the MySQL shell.

- The walkthrough video demonstrates how to seed the database from the command line.

- The walkthrough video demonstrates how to start the application’s server.

- The walkthrough video demonstrates GET routes for all categories, all products, and all tags being tested in Insomnia.

- The walkthrough video demonstrates GET routes for a single category, a single product, and a single tag being tested in Insomnia.

- The walkthrough video demonstrates POST, PUT, and DELETE routes for categories, products, and tags being tested in Insomnia.
