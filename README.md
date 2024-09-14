# Product Catalog API Service

[![License](https://img.shields.io/badge/license-Apache%202.0-blue.svg)](https://www.apache.org/licenses/LICENSE-2.0)

A **Flask-based Product Catalog API** that allows CRUD operations for managing products, querying by availability, name, and category. This service is optimized for scalability and testing, ensuring reliability in production environments.

## Table of Contents

* [Features](#features)
* [Tech Stack](#tech-stack)
* [Installation](#installation)
* [Usage](#usage)
* [API Endpoints](#api-endpoints)
* [Running Tests](#running-tests)
* [License](#license)

---

## Features

* **Create, Read, Update, Delete (CRUD)** operations on products
* **Query products** by availability, category, or name
* **Unit and integration testing** for reliability
* **SQLAlchemy ORM** for database interactions
* **PostgreSQL** as the primary database
* **Scalable architecture** with Docker support
* **Health check endpoint** for monitoring service status

## Tech Stack

* **Framework**: Flask (Python)
* **Database**: PostgreSQL
* **ORM**: SQLAlchemy
* **Testing**: unittest, factories for data generation
* **Containerization**: Docker
* **Version Control**: GitHub

## Installation

### Prerequisites
Ensure you have the following installed:
- Python 3.x
- PostgreSQL
- Docker (optional, for containerized setup)

### Step-by-Step Guide

1. Clone the repository:

    ```bash
    git clone https://github.com/InfectedDuck/ProductHub-API-Scalable-Product-Management-with-Flask.git
    cd ProductHub-API-Scalable-Product-Management-with-Flask
    ```

2. Set up a virtual environment and install dependencies:

    ```bash
    python3 -m venv venv
    source venv/bin/activate
    pip install -r requirements.txt
    ```

3. Set up the environment variables and database:

    ```bash
    export DATABASE_URI="postgresql://username:password@localhost:5432/products_db"
    ```

4. Initialize the database:

    ```bash
    flask db-create
    ```

5. Run the application:

    ```bash
    flask run
    ```

## Usage

Once the application is running, you can access the API at `http://localhost:5000/products`.

### Example: Creating a New Product

```bash
curl -X POST http://localhost:5000/products \
-H "Content-Type: application/json" \
-d '{"name": "Shirt", "description": "A cotton shirt", "price": 19.99, "available": true, "category": "CLOTHS"}'
```
### Example: Querying by Availability
```bash
curl -X GET http://localhost:5000/products?available=true
```
## API Endpoints

#### `GET /products`
- **Description**: List all products.

### `GET /products/{id}`
- **Description**: Retrieve a product by its ID.
- **Path Parameters**:
  - `id` (string): The unique ID of the product.

#### `POST /products`
- **Description**: Create a new product.
- **Request Body**: Product details.

#### `PUT /products/{id}`
- **Description**: Update an existing product.
- **Path Parameters**:
  - `id` (string): The unique ID of the product.
- **Request Body**: Updated product details.

#### `DELETE /products/{id}`
- **Description**: Delete a product by its ID.
- **Path Parameters**:
  - `id` (string): The unique ID of the product.

#### `GET /products?available=true`
- **Description**: Query products by availability.
- **Query Parameters**:
  - `available` (boolean): Whether the product is available (`true`/`false`).

#### `GET /products?name=Shirt`
- **Description**: Query products by name.
- **Query Parameters**:
  - `name` (string): The name of the product.

#### `GET /products?category=CLOTHS`
- **Description**: Query products by category.
- **Query Parameters**:
  - `category` (string): The category of the product.

#### `GET /health`
- **Description**: Health check endpoint to ensure the service is running.

## Running Tests

### To run the complete test suite, use:
```bash
nosetests --with-coverage --cover-package=service --cover-html --cover-eras
```
### You can also run individual test cases for debugging:
```bash
nosetests --stop tests/test_service.py:TestProductRoutes
```
### For checking code coverage:
```bash
coverage report -m
```

## Docker Setup
### To build and run the service using Docker:
#### Build the Docker image:
```bash
docker build -t product-catalog-api .
```

#### Run the container:
```bash
docker run -d -p 5000:5000 product-catalog-api
```

#### Access the service:
```bash
curl http://localhost:5000/products
```

## License
This project is licensed under the Apache License 2.0. See the [LICENSE](LICENSE) file for details. <br>
This project is made as a part of IBM Course.
