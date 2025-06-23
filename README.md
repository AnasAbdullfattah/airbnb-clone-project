# 🏡 Airbnb Clone Project

This project is a clone of **Airbnb**, one of the most famous property booking platforms, built to practice backend development. It replicates core functionalities such as user management, property listings, bookings, payments, and reviews — all while focusing on a smooth user experience, making the app a go-to choice for booking needs.

---

## 🏆 Project Goals

- **User Management**: Secure registration, login, and profile management.
- **Property Management**: Create, update, and display property listings.
- **Booking System**: Allow users to book and manage properties.
- **Payment Processing**: Handle and record transaction details.
- **Review System**: Enable users to leave reviews and ratings.
- **Data Optimization**: Optimize data retrieval and storage.

---

## 🛠️ Features Overview

### 1. API Documentation

- **OpenAPI Standard**: APIs documented for easy integration.
- **Django REST Framework (DRF)**: RESTful API for user/property operations.
- **GraphQL Support**: Flexible and efficient data queries.

### 2. User Authentication

- **Endpoints**: `/users/`, `/users/{user_id}/`
- **Features**: Register, login, and manage user profiles.

### 3. Property Management

- **Endpoints**: `/properties/`, `/properties/{property_id}/`
- **Features**: Full CRUD support for property listings.

### 4. Booking System

- **Endpoints**: `/bookings/`, `/bookings/{booking_id}/`
- **Features**: Manage bookings, including check-in and check-out details.

### 5. Payment Processing

- **Endpoints**: `/payments/`
- **Features**: Process and log booking payments.

### 6. Review System

- **Endpoints**: `/reviews/`, `/reviews/{review_id}/`
- **Features**: Post and manage reviews and ratings for properties.

### 7. Database Optimizations

- **Indexing**: Fast access to frequently queried data.
- **Caching**: Improve performance and reduce database load using Redis.

---

## ⚙️ Technology Stack

| Tool                  | Purpose                                    |
| --------------------- | ------------------------------------------ |
| Django                | Backend web framework                      |
| Django REST Framework | RESTful API creation                       |
| PostgreSQL            | Relational database for persistent storage |
| GraphQL               | Flexible API querying                      |
| Celery                | Asynchronous task queue (emails, payments) |
| Redis                 | Caching and session management             |
| Docker                | Containerized development and deployment   |
| CI/CD                 | Automated testing and deployment pipelines |

---

## 👥 Team Roles

- **Backend Developer**: Builds APIs, handles logic and architecture.
- **Database Admin**: Manages schema design and performance tuning.
- **DevOps Engineer**: Deploys, monitors, and scales infrastructure.
- **QA Engineer**: Tests features to ensure robustness and quality.

---

## 📈 API Documentation Overview

- **REST API**: Full OpenAPI documentation for users, properties, bookings, payments, and reviews.
- **GraphQL API**: Advanced querying interface for frontend integration.

---

## 📌 Endpoints Overview

### 👤 Users

- `GET /users/` – List users
- `POST /users/` – Register new user
- `GET /users/{user_id}/` – Retrieve user
- `PUT /users/{user_id}/` – Update user
- `DELETE /users/{user_id}/` – Delete user

### 🏠 Properties

- `GET /properties/` – List all properties
- `POST /properties/` – Create property
- `GET /properties/{property_id}/` – Retrieve property
- `PUT /properties/{property_id}/` – Update property
- `DELETE /properties/{property_id}/` – Delete property

### 📅 Bookings

- `GET /bookings/` – List all bookings
- `POST /bookings/` – Create booking
- `GET /bookings/{booking_id}/` – Retrieve booking
- `PUT /bookings/{booking_id}/` – Update booking
- `DELETE /bookings/{booking_id}/` – Cancel booking

### 💳 Payments

- `POST /payments/` – Process a payment

### ✍️ Reviews

- `GET /reviews/` – List all reviews
- `POST /reviews/` – Submit a review
- `GET /reviews/{review_id}/` – Get a specific review
- `PUT /reviews/{review_id}/` – Update a review
- `DELETE /reviews/{review_id}/` – Delete a review

---

## 🙌 Contributions

Feel free to fork this project and submit pull requests to improve functionality, fix bugs, or enhance the UI/UX!

---

## 📫 Contact

For inquiries or collaboration, please reach out via [LinkedIn](#) or [email](#).

---

🗃️ Database Design
This section outlines the core database entities and how they relate to each other.

👤 Users
Represents people using the platform (guests or hosts).

id (Primary Key)

name

email (unique)

password_hash

is_host (boolean: determines if user can list properties)

🧩 Relationships:

A user can create multiple properties.

A user can make multiple bookings.

A user can write multiple reviews.

🏠 Properties
Represents properties listed by hosts for booking.

id (Primary Key)

title

description

location

price_per_night

host_id (Foreign Key → Users)

🧩 Relationships:

A property is owned by a user (host).

A property can have many bookings.

A property can have many reviews.

📅 Bookings
Represents a reservation made by a guest for a property.

id (Primary Key)

property_id (Foreign Key → Properties)

user_id (Foreign Key → Users)

check_in_date

check_out_date

status (pending, confirmed, cancelled)

🧩 Relationships:

A booking belongs to a user (guest).

A booking belongs to a property.

A booking can have one payment.

💳 Payments
Represents a payment transaction related to a booking.

id (Primary Key)

booking_id (Foreign Key → Bookings)

amount

payment_method

payment_status (e.g., success, failed)

🧩 Relationships:

A payment belongs to a booking.

✍️ Reviews
Represents feedback left by users after a stay.

id (Primary Key)

property_id (Foreign Key → Properties)

user_id (Foreign Key → Users)

rating (1–5)

comment

🧩 Relationships:

A review belongs to a property.

A review is written by a user.

