# E-Commerce REST API

This is a simple REST API for an e-commerce application built with Java and Spring Boot.

## Description

This project provides a backend service for managing products in an e-commerce system. It allows you to perform CRUD (Create, Read, Update, Delete) operations on products, as well as search for products and manage product images.

## Technologies Used

- **Java 21**
- **Spring Boot 3**
- **Spring Web**: For building RESTful web services.
- **Spring Data JPA**: For data persistence.
- **H2 Database**: An in-memory database.
- **Lombok**: To reduce boilerplate code.
- **Maven**: For dependency management.

## API Endpoints

The base URL for all endpoints is `/api`.

| Method | Endpoint                    | Description                                       |
|--------|-----------------------------|---------------------------------------------------|
| `GET`    | `/`                         | A simple greeting.                                |
| `GET`    | `/products`                 | Get a list of all products.                       |
| `GET`    | `/product/{id}`             | Get a single product by its ID.                   |
| `POST`   | `/product`                  | Add a new product (expects multipart form data). |
| `GET`    | `/product/{productId}/image`| Get the image for a specific product.             |
| `PUT`    | `/product/{id}`             | Update an existing product (expects multipart form data). |
| `DELETE` | `/product/{id}`             | Delete a product by its ID.                       |
| `GET`    | `/products/search?keyword={keyword}` | Search for products by a keyword.          |

### Product Model

```json
{
  "id": 0,
  "name": "string",
  "description": "string",
  "brand": "string",
  "price": 0.00,
  "category": "string",
  "releaseDate": "yyyy-MM-dd'T'HH:mm:ss.SSSZ",
  "productAvailable": true,
  "stockQuantity": 0,
  "imageName": "string",
  "imageType": "string",
  "imageDate": "base64-encoded-string"
}
```

### Adding/Updating a Product

When using `POST /product` or `PUT /product/{id}`, you need to send a `multipart/form-data` request with two parts:
1.  `product`: A JSON object with the product details.
2.  `imageFile`: The product image file.

## How to Run

1.  **Clone the repository:**
    ```bash
    git clone <repository-url>
    cd ecom-java
    ```

2.  **Run the application:**
    You can run the application using the Maven wrapper included in the project.

    On macOS/Linux:
    ```bash
    ./mvnw spring-boot:run
    ```

    On Windows:
    ```bash
    ./mvnw.cmd spring-boot:run
    ```

The application will start on port `8080`.

The application uses an in-memory H2 database, so no external database setup is required. The database is seeded with some initial data from `src/main/resources/data1.sql`. 