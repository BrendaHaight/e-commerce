# e-commerce

## Description

This project is the back end for an e-commerce site built using Node.js, Express.js, Sequelize, and PostgreSQL. The application provides a RESTful API for managing products, categories, and tags in an e-commerce platform. The API supports CRUD operations and uses Sequelize to interact with a PostgreSQL database.

## Table of Contents

- Installation
- Usage
- Routes
- Models
- Associations
- Seeding the Database
- Testing with Insomnia
- Walkthrough Video
- License

## Installation

1. Clone the repository:

```bash

git clone https://github.com/your-username/e-commerce-backend.git
cd e-commerce-backend
```

2. Install dependencies:

```bash

npm install
```

3. Create a .env file in the root directory and add your database credentials:

```bash
DB_NAME='ecommerce_db'
DB_USER='your_db_user'
DB_PASSWORD='your_db_password'
DB_HOST='localhost'
PORT=3001
```

4. Set up the database by running the schema.sql file in your PostgreSQL client or by using the following command:

```bash
psql -U your_db_user -d ecommerce_db -f db/schema.sql
```

## Usage

1. Start the server:

```bash
node server.js
```

2. Seed the database with initial data:

```bash
node seeds/index.js
```

3. The server will be running on `http://localhost:3001`. You can test the API using Insomnia or any other API client.

## Routes

**Categories**

- GET `/api/categories`
- GET `/api/categories/:id`
- POST `/api/categories`
- PUT `/api/categories/:id`
- DELETE `/api/categories/:id`

**Products**

- GET `/api/products`
- GET `/api/products/:id`
- POST `/api/products`
- PUT `/api/products/:id`
- DELETE `/api/products/:id`

**Tags**

- GET `/api/tags`
- GET `/api/tags/:id`
- POST `/api/tags`
- PUT `/api/tags/:id`
- DELETE `/api/tags/:id`

## Models

**Category**

- `id`: Integer, primary key, auto increment
- `category_name`: String, not null

**Product**

- `id`: Integer, primary key, auto increment
- `product_name`: String, not null
- `price`: Decimal, not null
- `stock`: Integer, not null, default value of 10
- `category_id`: Integer, references Category

**Tag**

- `id`: Integer, primary key, auto increment
- `tag_name`: String

**ProductTag**

- `id`: Integer, primary key, auto increment
- `product_id`: Integer, references Product
- `tag_id`: Integer, references Tag

## Associations

- `Product` belongs to `Category`
- `Category` has many `Product`
- `Product` belongs to many `Tag` through `ProductTag`
- `Tag` belongs to many `Product` through `ProductTag`

## Seeding the Database

To seed the database with initial data, run:

```bash
node seeds/index.js
```

This will populate the database with sample categories, products, tags, and product-tag associations.

## Testing with Insomnia

You can test the API endpoints using Insomnia or any other API client. Here are some example requests:

**GET All Products**

- Method: GET
- URL: `http://localhost:3001/api/products`
- POST New Product
- Method: POST
- URL: `http://localhost:3001/api/products`
- Body: JSON

```json
{
  "product_name": "Basketball",
  "price": 200.0,
  "stock": 3,
  "category_id": 1,
  "tagIds": [1, 2, 3]
}
```

**PUT Update Product**

- Method: PUT
- URL: `http://localhost:3001/api/products/:id`
- Body: JSON

```json
{
  "product_name": "Updated Product",
  "price": 150.0,
  "stock": 10,
  "tagIds": [1, 2, 3, 4]
}
```

**DELETE Product**

- Method: DELETE
- URL: `http://localhost:3001/api/products/:id`

## Walkthrough Video

A walkthrough video demonstrating the functionality of the application and all of the acceptance criteria being met can be found here.
<video controls src="20240619-1818-03.3186635.mp4" title="Demonstration"></video>

## License

This project is licensed under the MIT License.
