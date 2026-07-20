# Warehouse & Inventory Management System

A production-inspired full-stack web application for managing warehouse operations, inventory, purchases, and sales — built as an **MCA Final Year Major Project**.

---

## Features

### Admin
- Full access to all modules
- Manage Products, Categories, Suppliers
- View Dashboard with real-time statistics
- Manage Users

### Staff
- Create Purchases and Sales
- View Products and Inventory
- Stock In / Stock Out tracking

### Core Modules
- **Authentication** — JWT-based login/register with role-based access
- **Dashboard** — Total products, low stock alerts, revenue summary, recent transactions
- **Product Management** — CRUD with SKU generation, category & supplier linking
- **Category Management** — Organize products into categories
- **Supplier Management** — Track suppliers and their details
- **Purchase Management** — Create purchases, auto-update stock levels
- **Sales Management** — Create sales, auto-reduce inventory, invoice-ready
- **Inventory Logs** — Full history of all stock in/out movements

---

## Technology Stack

| Layer | Technology |
|-------|-----------|
| Frontend | React 18, Vite, Tailwind CSS, React Router, Axios |
| Backend | Java 21, Spring Boot 3.3, Spring Security, JWT |
| Database | MySQL 8, Hibernate / Spring Data JPA |
| API Docs | Swagger / OpenAPI (SpringDoc) |
| Build | Maven (Backend), npm (Frontend) |
| Version Control | Git & GitHub |

---

## Project Structure

```
warehouse-inventory-management-system/
├── backend/
│   ├── src/main/java/com/warehouse/
│   │   ├── config/           # Security, Swagger, Data Initializer
│   │   ├── controller/       # REST API controllers
│   │   ├── dto/              # Data Transfer Objects
│   │   ├── entity/           # JPA Entities
│   │   ├── exception/        # Global exception handling
│   │   ├── repository/       # Spring Data repositories
│   │   ├── security/         # JWT token provider & filter
│   │   └── service/          # Business logic layer
│   └── pom.xml
├── frontend/
│   ├── src/
│   │   ├── api/              # Axios configuration
│   │   ├── components/       # Reusable UI components
│   │   ├── context/          # Auth context
│   │   └── pages/            # Page components
│   └── package.json
├── database/
│   └── schema.sql            # Complete database schema
├── screenshots/              # Application screenshots
├── LICENSE
└── README.md
```

---

## Database Schema

- **users** — User accounts with role references
- **roles** — ADMIN / STAFF roles
- **categories** — Product categories
- **suppliers** — Supplier information
- **products** — Products with SKU, price, stock levels
- **purchases** — Purchase orders with supplier reference
- **purchase_items** — Individual items in a purchase
- **sales** — Sales transactions with customer info
- **sale_items** — Individual items in a sale
- **inventory_logs** — Complete stock movement history

---

## Installation & Setup

### Prerequisites
- Java 21
- Node.js 18+
- MySQL 8
- Maven

### 1. Database Setup

```sql
-- Create database and run schema
mysql -u root -p < database/schema.sql
```

Or create the database manually:
```sql
CREATE DATABASE warehouse_db;
```

### 2. Backend Setup

```bash
cd backend

# Update database credentials in src/main/resources/application.properties
# spring.datasource.username=root
# spring.datasource.password=your_password

# Build and run
mvn spring-boot:run
```

Backend runs on: `http://localhost:8080`

### 3. Frontend Setup

```bash
cd frontend

npm install
npm run dev
```

Frontend runs on: `http://localhost:5173`

### 4. Default Login

| Role | Username | Password |
|------|----------|----------|
| Admin | admin | admin123 |
| Staff | staff | staff123 |

---

## API Documentation

Once the backend is running, access Swagger UI at:

```
http://localhost:8080/swagger-ui.html
```

### API Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | `/api/auth/login` | Login and get JWT token |
| POST | `/api/auth/register` | Register new user |
| GET | `/api/auth/me` | Get current user profile |
| GET | `/api/dashboard` | Get dashboard summary |
| GET/POST | `/api/products` | List / Create products |
| PUT/DELETE | `/api/products/{id}` | Update / Delete product |
| GET/POST | `/api/categories` | List / Create categories |
| GET/POST | `/api/suppliers` | List / Create suppliers |
| GET/POST | `/api/purchases` | List / Create purchases |
| GET/POST | `/api/sales` | List / Create sales |
| GET | `/api/inventory` | Get inventory logs |

---

## Key Skills Demonstrated

- Object-Oriented Programming (OOP)
- MVC / Layered Architecture (Controller → Service → Repository → Entity)
- CRUD Operations with validation
- Role-Based Access Control (RBAC)
- JWT Authentication & Authorization
- Spring Security integration
- DTO Pattern for API communication
- Global Exception Handling
- Input Validation with annotations
- Responsive Web Design with Tailwind CSS
- Git & GitHub version control
- RESTful API design
- Swagger / OpenAPI documentation
- Database normalization

---

## Future Improvements

- [ ] PDF invoice generation for sales
- [ ] Email notifications for low stock alerts
- [ ] Product image upload with cloud storage
- [ ] Advanced reporting with charts (Chart.js / Recharts)
- [ ] Multi-warehouse support
- [ ] Barcode generation and scanning
- [ ] Unit testing with JUnit and Mockito
- [ ] Docker containerization
- [ ] CI/CD pipeline with GitHub Actions

---

## License

This project is licensed under the MIT License — see [LICENSE](LICENSE) for details.

---

## Author

**Ansh Tandel** — MCA Final Year Student
GitHub: [ansht120](https://github.com/ansht120)
