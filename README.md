# Welcome to The Squad! 👋🏻

We are a group of passionate software engineers who are interested in building scalable and robust software systems.

Our mission is to simulate a microservices architecture e-commerce app.

## About the team

[@Abdelrahman Shaheen](https://github.com/AbdelrahmanShaheen)

[@Amr Al-Amassi](https://github.com/amro412)

[@Said Ahmed](https://github.com/said-ahmd)

[@Salma Ahmed](https://github.com/salmaahmed0)

[@Mustafa Moghazy](https://github.com/Mustafa-Moghazy)


Let's get started! and have a look at what we are trying to build! 🎉.

# E-Commerce Microservices Platform

we are simulating building an e-commerce platform using microservices architecture. We are building a platform that allows customers to browse products, add them to their cart, and purchase them. We are also building a platform that allows admins to manage products, categories, brands, stores, stocks and coupons.

## 1. Order Service
The Orders API microservice is an important component of our e-commerce platform, designed to efficiently handle the creation, management, and processing of our customers' orders. And it encapsulates order-related functionalities.

Check out the full details here 👉🏻 [Order Service API README file.](https://github.com/Fawry-Project/Order-Service-API)

and here is the ERD for the database used in this service:

```mermaid
erDiagram
ORDER ||--o{ ORDER_ITEM : "consists of"
ORDER{
    int id pk
    string coupon_code 
    string order_code
    string user_email
    double total_price
    double total_price_after_discount
    date creation_date
}

ORDER_ITEM{
    int id pk
    int order_id fk
    int product_code
    int quntity
}
```

## 2. Notification Service
The notification service is a Spring Boot application designed to handle notifications through email. It integrates with a Kafka topic to consume notification requests from an external source, processes these requests, and sends emails using JavaMailSender. Additionally, it features a retry mechanism to handle failed email delivery attempts, ensuring robustness and reliability in delivering notifications.

Check out the full details here 👉🏻 [Notification Service API README file.](https://github.com/Fawry-Project/notification-service-api)

and here is the ERD for the database used in this service:

```mermaid
erDiagram
notification{
    int id pk
    string destination
    string content
    date sent_at
    string subject
    string status(SENT-FAILED-RETRY_FAILED)
    int retry_amount
}
```

## 3. Product Catalog API Service

This is a RESTful API designed for managing products, their categories, and consumption history. It provides endpoints for creating, retrieving, updating, and deleting products and categories, as well as recording product consumption history.

Check out the full details here 👉🏻 [Product Catalog API README file.](https://github.com/Fawry-Project/Product-API)

and here is the ERD for the database used in this service:

```mermaid
erDiagram
PRODUCT {
    int id pk
    string code uk
    string category_id fk
    string brand_name
    string name
    string description
    double price
    string img_url
}
PRODUCT }o--|| CATEGORY : "has"
CATEGORY{
    int id pk
    string name
    string description
}

PRODUCT ||--o{ PRODUCT_CONSUMPTION :"has"
PRODUCT_CONSUMPTION{
    int id pk
    int product_code fk
    int order_code 
    int quantity_consumed
    date consumed_at
}
```

## 4. Coupons Service API
This RESTful API for managing coupons and their consumption history. It facilitates operations such as creating, retrieving, updating, and deleting coupons, as well as recording and managing coupon consumption.


Check out the [Coupons API README file.](https://github.com/Fawry-Project/Coupon-API)

and here is the ERD for the database used in this service:

```mermaid
erDiagram
COUPON ||--o{ COUPON_CONSUMPTION : "consumes"
COUPON {
    int id pk
    string code uk
    int max_number_of_usage
    int current_number_of_usage
    date expiry_date
    boolean active
    string value_type(fixed)(percentage)
    double value
}
COUPON_CONSUMPTION {
    int id pk
    string coupon_code fk
    string order_code  
    date consumed_at
}
```




---
