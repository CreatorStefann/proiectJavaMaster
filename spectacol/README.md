# 🎭 Reservation System

## 📌 Project Description

This project represents a Spring Boot application that manages show events and seat reservations within a performance hall.

The system allows:
- Managing halls and automatically generating seats
- Managing shows associated with a hall
- Registering clients
- Creating reservations for one or multiple seats
- Cancelling reservations
- Viewing available seats for a specific show

The application uses PostgreSQL for data persistence and Swagger for API documentation. All functionalities are tested using unit tests.

---

# 📋 Business Requirements

1. The system must allow creation and management of performance halls.
2. The system must automatically generate seats based on rows and seats per row.
3. The system must allow creation and management of shows associated with a hall.
4. The system must allow client registration.
5. A client can create a reservation for one or multiple seats.
6. The system must verify seat availability before creating a reservation.
7. A seat cannot be reserved twice for the same show.
8. The system must automatically calculate the total price of a reservation.
9. The system must allow reservation cancellation.
10. The system must allow viewing available seats for a show.

---

# 🚀 MVP Features (Minimum Viable Product)

## 1️⃣ Hall Management
- Create hall
- Automatically generate seats
- Persist data in database

## 2️⃣ Show Management
- Create show
- Associate show with a hall
- Retrieve all shows

## 3️⃣ Client Management
- Create client
- Unique email validation
- Retrieve client details

## 4️⃣ Reservation Management
- Create reservation for multiple seats
- Validate seat availability
- Automatically calculate total price
- Save reservation-seat relationship

## 5️⃣ Reservation Cancellation
- Change reservation status to `CANCELED`
- Preserve reservation history

---

# 🏗️ Application Architecture

The application follows a layered architecture:

- **Controller Layer** – Handles REST requests
- **Service Layer** – Contains business logic
- **Repository Layer** – Handles database operations
- **Model Layer** – JPA entities

---

# 🗄️ Persistent Entities

The system contains 6 entities:

1. `Sala`
2. `Loc`
3. `Client`
4. `Spectacol`
5. `Rezervare`
6. `RezervareLoc`

---

# 🔗 Entity Relationships

- Sala → OneToMany → Loc
- Sala → OneToMany → Spectacol
- Spectacol → ManyToOne → Sala
- Rezervare → ManyToOne → Client
- Rezervare → ManyToOne → Spectacol
- Rezervare → OneToMany → RezervareLoc
- RezervareLoc → ManyToOne → Loc

---

# 💾 Data Persistence

- Database: **PostgreSQL**
- ORM: **Spring Data JPA**
- Hibernate used for object-relational mapping
- `ddl-auto=update` used for schema generation

---

# ✅ Validation

The application uses Bean Validation annotations:

- `@NotBlank`
- `@NotNull`
- `@Email`
- `@Min`
- `@Future`

Validation is applied both at DTO and entity level.

---

# 🌐 REST API Endpoints

### Hall
- `POST /api/sali`

### Client
- `POST /api/clients`
- `GET /api/clients`
- `GET /api/clients/{id}`

### Show
- `POST /api/spectacole`
- `GET /api/spectacole`

### Reservation
- `POST /api/rezervari`
- `DELETE /api/rezervari/{id}`
- `GET /api/rezervari/spectacol/{id}/locuri-disponibile`

Swagger documentation available at:

http://localhost:8080/swagger-ui.html


---

# 🧪 Testing

The application includes:

- Unit tests for Service Layer
- Controller tests using MockMvc
- Mockito for mocking dependencies

All tests pass successfully.

---

Access Swagger UI:
   http://localhost:8080/swagger-ui.html