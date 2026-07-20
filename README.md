<div align="center">

# Warehouse & Inventory Management System

### Full-Stack Java Application for Small & Medium Business Inventory Management

[![Java](https://img.shields.io/badge/Java-21-ED8B00?style=for-the-badge&logo=openjdk&logoColor=white)](https://www.oracle.com/java/)
[![Spring Boot](https://img.shields.io/badge/Spring_Boot-3.3-6DB33F?style=for-the-badge&logo=springboot&logoColor=white)](https://spring.io/projects/spring-boot)
[![React](https://img.shields.io/badge/React-18-61DAFB?style=for-the-badge&logo=react&logoColor=black)](https://react.dev/)
[![Tailwind CSS](https://img.shields.io/badge/Tailwind_CSS-3.4-06B6D4?style=for-the-badge&logo=tailwindcss&logoColor=white)](https://tailwindcss.com/)
[![MySQL](https://img.shields.io/badge/MySQL-8-4479A1?style=for-the-badge&logo=mysql&logoColor=white)](https://www.mysql.com/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg?style=for-the-badge)](LICENSE)

---

A production-inspired **Warehouse & Inventory Management System** built as an **MCA Final Year Major Project**.
The application features JWT authentication, role-based access, and a clean responsive UI — designed to feel like real software used by a local business.

</div>

---

## Live Preview

| Dashboard | Products | Purchases |
|-----------|----------|-----------|
| ![Dashboard](screenshots/dashboard.png) | ![Products](screenshots/products.png) | ![Purchases](screenshots/purchases.png) |

| Login | Categories | Inventory |
|-------|-----------|-----------|
| ![Login](screenshots/login.png) | ![Categories](screenshots/categories.png) | ![Inventory](screenshots/inventory.png) |

> **Note:** Add your own screenshots in the `screenshots/` folder and they will appear here automatically.

---

## Features

### Role-Based Access

| Capability | Admin | Staff |
|------------|:-----:|:-----:|
| Dashboard Overview | ✅ | ✅ |
| Product Management (CRUD) | ✅ | ✅ |
| Category Management | ✅ | ✅ |
| Supplier Management | ✅ | ✅ |
| Create Purchases | ✅ | ✅ |
| Create Sales | ✅ | ✅ |
| Inventory History | ✅ | ✅ |
| User Management | ✅ | ❌ |
| Reports & Analytics | ✅ | ❌ |

### Core Modules

- **Authentication** — JWT-based login/register with secure password hashing (BCrypt)
- **Dashboard** — Real-time stats: total products, low stock alerts, revenue summary, recent transactions
- **Product Management** — Full CRUD with auto SKU generation, category & supplier linking
- **Category Management** — Organize products into logical groups
- **Supplier Management** — Track supplier details, contact info, GST numbers
- **Purchase Management** — Create purchase orders that auto-update stock levels
- **Sales Management** — Create sales that auto-reduce inventory with stock validation
- **Inventory Logs** — Complete history of every stock in/out movement
- **Responsive Design** — Works on desktop, tablet, and mobile

---

## Tech Stack

<div align="center">

| Layer | Technologies |
|-------|-------------|
| **Frontend** | React 18, Vite 5, Tailwind CSS, React Router 6, Axios, Lucide Icons |
| **Backend** | Java 21, Spring Boot 3.3, Spring Security, JWT (jjwt 0.12), Hibernate |
| **Database** | MySQL 8, Spring Data JPA, Flyway-ready schema |
| **API Docs** | SpringDoc OpenAPI (Swagger UI) |
| **Build Tools** | Maven (Backend), npm (Frontend) |
| **Version Control** | Git, GitHub |

</div>

---

## Architecture

```
┌──────────────────────────────────────────────────────────┐
│                    FRONTEND (React)                       │
│   Pages → Components → AuthContext → Axios API Client     │
└──────────────────────┬───────────────────────────────────┘
                       │ HTTP (REST)
┌──────────────────────▼───────────────────────────────────┐
│                  BACKEND (Spring Boot)                    │
│                                                          │
│   ┌─────────────┐    ┌──────────────┐    ┌───────────┐  │
│   │ Controller   │───▶│   Service    │───▶│Repository │  │
│   │ (REST API)   │    │ (Business)   │    │  (JPA)    │  │
│   └─────────────┘    └──────────────┘    └─────┬─────┘  │
│         │                  │                    │         │
│   ┌─────▼─────┐    ┌──────▼──────┐    ┌───────▼──────┐ │
│   │    DTO     │    │   Entity    │    │    MySQL     │ │
│   │ (Request/  │    │ (JPA Model) │    │  Database    │ │
│   │  Response) │    └─────────────┘    └──────────────┘ │
│   └───────────┘                                          │
│                                                          │
│   ┌──────────────────────────────────────────────────┐  │
│   │         Security Layer (JWT + RBAC)               │  │
│   └──────────────────────────────────────────────────┘  │
└──────────────────────────────────────────────────────────┘
```

### Backend Layered Architecture

| Layer | Responsibility | Location |
|-------|---------------|----------|
| Controller | Handle HTTP requests, validation, response | `controller/` |
| Service | Business logic, transaction management | `service/` + `service/impl/` |
| Repository | Database queries, JPA operations | `repository/` |
| Entity | Database table mappings | `entity/` |
| DTO | Data transfer between layers | `dto/` |
| Security | JWT auth, password hashing, filters | `security/` + `config/` |

---

## Database Schema

```
┌──────────┐    ┌──────────┐    ┌────────────┐
│  roles   │◀───│  users   │    │ categories │
└──────────┘    └──────────┘    └─────┬──────┘
                                      │
┌──────────┐    ┌──────────────┐    ┌─▼────────┐
│suppliers │◀───│   products   │◀───│          │
└──────────┘    └──────┬───────┘    └──────────┘
                       │
            ┌──────────┼──────────┐
            │          │          │
     ┌──────▼──┐  ┌───▼────┐  ┌──▼──────────┐
     │purchases│  │ sales  │  │inventory    │
     └────┬────┘  └───┬────┘  │_logs        │
          │           │       └─────────────┘
     ┌────▼────┐  ┌───▼────┐
     │purchase │  │ sale   │
     │_items   │  │_items  │
     └─────────┘  └────────┘
```

**10 normalized tables:**
`users` · `roles` · `categories` · `suppliers` · `products` · `purchases` · `purchase_items` · `sales` · `sale_items` · `inventory_logs`

---

## Getting Started

### Prerequisites

Make sure you have the following installed:

| Software | Version | Check Command |
|----------|---------|---------------|
| Java | 21+ | `java -version` |
| Maven | 3.8+ | `mvn -version` |
| Node.js | 18+ | `node -v` |
| MySQL | 8.0+ | `mysql --version` |

### Step 1 — Clone the Repository

```bash
git clone https://github.com/ansht120/warehouse-inventory-management-system.git
cd warehouse-inventory-management-system
```

### Step 2 — Setup Database

```bash
# Login to MySQL
mysql -u root -p

# Create the database
CREATE DATABASE warehouse_db;
EXIT;

# Import the schema
mysql -u root -p warehouse_db < database/schema.sql
```

### Step 3 — Configure Backend

Open `backend/src/main/resources/application.properties` and update your MySQL credentials:

```properties
spring.datasource.url=jdbc:mysql://localhost:3306/warehouse_db?useSSL=false&serverTimezone=UTC&allowPublicKeyRetrieval=true
spring.datasource.username=root
spring.datasource.password=your_mysql_password
```

### Step 4 — Start Backend Server

```bash
cd backend
mvn spring-boot:run
```

Backend runs at → `http://localhost:8080`

### Step 5 — Start Frontend

```bash
cd frontend
npm install
npm run dev
```

Frontend runs at → `http://localhost:5173`

### Step 6 — Login

Open `http://localhost:5173` in your browser and use these credentials:

| Role | Username | Password |
|------|----------|----------|
| **Admin** | `admin` | `admin123` |
| **Staff** | `staff` | `staff123` |

---

## API Documentation

Access the interactive Swagger UI at:

```
http://localhost:8080/swagger-ui.html
```

### Endpoints Overview

| Method | Endpoint | Description | Auth |
|--------|----------|-------------|------|
| `POST` | `/api/auth/login` | Login & get JWT token | Public |
| `POST` | `/api/auth/register` | Register new user | Public |
| `GET` | `/api/auth/me` | Get current user profile | Bearer |
| `PUT` | `/api/auth/change-password` | Change password | Bearer |
| `GET` | `/api/dashboard` | Dashboard summary data | Bearer |
| `GET` | `/api/products` | Get all products (paginated) | Bearer |
| `GET` | `/api/products/{id}` | Get product by ID | Bearer |
| `POST` | `/api/products` | Create new product | Bearer |
| `PUT` | `/api/products/{id}` | Update product | Bearer |
| `DELETE` | `/api/products/{id}` | Delete product (soft) | Bearer |
| `GET` | `/api/products/low-stock` | Get low stock items | Bearer |
| `GET` | `/api/categories` | Get all categories | Bearer |
| `POST` | `/api/categories` | Create category | Bearer |
| `PUT` | `/api/categories/{id}` | Update category | Bearer |
| `DELETE` | `/api/categories/{id}` | Delete category (soft) | Bearer |
| `GET` | `/api/suppliers` | Get all suppliers | Bearer |
| `POST` | `/api/suppliers` | Create supplier | Bearer |
| `PUT` | `/api/suppliers/{id}` | Update supplier | Bearer |
| `DELETE` | `/api/suppliers/{id}` | Delete supplier (soft) | Bearer |
| `GET` | `/api/purchases` | Get all purchases (paginated) | Bearer |
| `POST` | `/api/purchases` | Create purchase (auto-updates stock) | Bearer |
| `GET` | `/api/sales` | Get all sales (paginated) | Bearer |
| `POST` | `/api/sales` | Create sale (auto-reduces stock) | Bearer |
| `GET` | `/api/inventory` | Get inventory logs (paginated) | Bearer |

### Sample Request

```bash
# Login
curl -X POST http://localhost:8080/api/auth/login \
  -H "Content-Type: application/json" \
  -d '{"username": "admin", "password": "admin123"}'

# Response
{
  "token": "eyJhbGciOiJIUzI1NiJ9...",
  "type": "Bearer",
  "id": 1,
  "username": "admin",
  "fullName": "System Administrator",
  "role": "ADMIN"
}
```

---

## Project Structure

```
warehouse-inventory-management-system/
│
├── backend/                            # Spring Boot Application
│   ├── pom.xml                         # Maven dependencies
│   └── src/main/java/com/warehouse/
│       ├── WarehouseManagementApplication.java   # Entry point
│       ├── config/                     # Configuration
│       │   ├── SecurityConfig.java     # Spring Security + CORS
│       │   ├── SwaggerConfig.java      # OpenAPI/Swagger setup
│       │   └── DataInitializer.java    # Default roles & users
│       ├── controller/                 # REST Controllers (8)
│       │   ├── AuthController.java
│       │   ├── ProductController.java
│       │   ├── CategoryController.java
│       │   ├── SupplierController.java
│       │   ├── PurchaseController.java
│       │   ├── SaleController.java
│       │   ├── InventoryController.java
│       │   └── DashboardController.java
│       ├── dto/                        # Data Transfer Objects (10)
│       ├── entity/                     # JPA Entities (10)
│       ├── exception/                  # Global Exception Handler
│       ├── repository/                 # Spring Data Repositories (8)
│       ├── security/                   # JWT Provider + Filter
│       └── service/                    # Service Layer
│           ├── AuthService.java
│           ├── ProductService.java
│           ├── CategoryService.java
│           ├── SupplierService.java
│           ├── PurchaseService.java
│           ├── SaleService.java
│           ├── DashboardService.java
│           └── impl/                   # Service Implementations
│
├── frontend/                           # React Application
│   ├── package.json                    # npm dependencies
│   ├── vite.config.js                  # Vite + API proxy config
│   ├── tailwind.config.js              # Tailwind CSS config
│   └── src/
│       ├── App.jsx                     # Router setup
│       ├── main.jsx                    # Entry point
│       ├── api/axios.js                # Axios with JWT interceptor
│       ├── context/AuthContext.jsx     # Authentication state
│       ├── components/Layout.jsx       # Sidebar + Navbar layout
│       └── pages/                      # Page Components
│           ├── Login.jsx
│           ├── Dashboard.jsx
│           ├── Products.jsx
│           ├── Categories.jsx
│           ├── Suppliers.jsx
│           ├── Purchases.jsx
│           ├── Sales.jsx
│           └── Inventory.jsx
│
├── database/
│   └── schema.sql                      # MySQL schema + seed data
│
├── screenshots/                        # App screenshots for README
├── LICENSE                             # MIT License
└── README.md
```

---

## Skills Demonstrated

| Category | Skills |
|----------|--------|
| **Backend** | Java 21, Spring Boot, Spring Security, Spring Data JPA, Hibernate, Maven, REST API Design |
| **Frontend** | React 18, Vite, Tailwind CSS, React Router, Axios, Responsive Design |
| **Database** | MySQL, Normalized Schema Design, Foreign Keys, JPA Relationships |
| **Architecture** | MVC / Layered Architecture, DTO Pattern, Repository Pattern |
| **Security** | JWT Authentication, BCrypt Password Hashing, Role-Based Access Control (RBAC) |
| **Tools** | Git & GitHub, Swagger/OpenAPI, Postman, VS Code, IntelliJ IDEA |
| **Practices** | Input Validation, Global Exception Handling, Soft Delete, Auto SKU Generation |

---

## Future Improvements

- [ ] PDF invoice generation for sales
- [ ] Email notifications for low stock alerts
- [ ] Product image upload with cloud storage
- [ ] Advanced reporting with charts (Recharts)
- [ ] Multi-warehouse support
- [ ] Barcode generation and scanning
- [ ] Unit testing with JUnit 5 + Mockito
- [ ] Docker containerization
- [ ] CI/CD pipeline with GitHub Actions

---

## License

This project is licensed under the **MIT License** — see the [LICENSE](LICENSE) file for details.

---

<div align="center">

**Built by [Ansh Tandel](https://github.com/ansht120) — MCA Final Year Major Project**

If you found this project helpful, consider giving it a ⭐ on GitHub!

</div>
