# Stock Market Data API

A RESTful API for accessing and managing stock market data, symbols, and exchanges.

## 📊 Overview

This application allows users to view market data (price action, price movement dates) for stocks across various exchanges. The data is organized in a hierarchical structure:

- **Exchanges** contain multiple symbols
- **Symbols** represent individual stocks and contain multiple data entries
- **Data Entries** contain price information for a specific symbol on a specific date

---

## 📋 Data Relationships

- Each data entry relates to one symbol (many-to-one)
- Each symbol belongs to one exchange (many-to-one)
- Each symbol can have many data entries
- Each exchange can list many symbols

---

## 🔑 User Access Levels

### Authenticated Users Can:
- View all market data entries
- View all symbols and exchanges
- Retrieve data entries for specific symbols
- Search data entries by trading date
- List symbols on a specific exchange

### Admin Users Can Also:
- Add new symbols
- Update existing symbols
- Remove symbols
- Remove exchanges
---
## 🛣️ API Endpoints

| Endpoint | Method | Description | Success | Error | Authentication |
|----------|--------|-------------|---------|-------|----------------|
| `/data_entries` | GET | Get all data entries | 200 | 400 | Required |
| `/symbols` | GET | Get all symbols | 200 | 400 | Required |
| `/exchanges` | GET | Get all exchanges | 200 | 400 | Required |
| `/exchanges/{id}` | GET | Get a specific exchange | 200 | 400 | Required |
| `/symbols/{id}/data_entries` | GET | Get all data entries for a symbol | 200 | 400, 404 | Required |
| `/exchanges/{id}/symbols` | GET | Get all symbols for an exchange | 200 | 400 | Required |
| `/symbols` | POST | Create a new symbol | 201 | 400, 422 | ADMIN |
| `/symbols/{id}` | PUT | Update a specific symbol | 200 | 404, 409 | ADMIN |
| `/symbols/{id}` | DELETE | Delete a specific symbol | 204 | 404 | ADMIN |
| `/exchanges/{id}` | DELETE | Delete a specific exchange | 204 | 404 | ADMIN |


---

## 📋 Functional Requirements

### As an authenticated user, I can:
- View a list of all data entries
- View a list of all symbols
- View a list of all exchanges
- Get all data entries for a symbol
- Get a single entry for a symbol by searching by the trading date
- Get all symbols for an exchange

### As an admin, I can:
- Add a symbol
- Update a symbol
- Remove a symbol
- Remove an exchange
---

## Login Credentials:

- username: user 
- password: ROLE_USER
---
- username: admin
- password: ROLE_admin


---

## 🛠️ Tech Stack

- Language: Java
- Framework: Spring Boot
- Database: PostgreSQL
- Data Access: Spring JDBC with DAO pattern
- Testing: Postman
- Build Tool: Maven
- IDE: IntelliJ IDEA

---



## 📬 Example API Endpoints

| Endpoint | Method | Description |
|----------|--------|-------------|
| `/data_entries` | GET | Get all data entries |
| `/symbols` | GET | Get all symbols |
| `/exchanges` | GET | Get all exchanges |
| `/exchanges/{id}` | GET | Get a specific exchange |
| `/symbols/{id}/data_entries` | GET | Get all data entries for a symbol |
| `/exchanges/{id}/symbols` | GET | Get all symbols for an exchange |
| `/symbols` | POST | Create a new symbol |
| `/symbols/{id}` | PUT | Update a specific symbol |
| `/symbols/{id}` | DELETE | Delete a specific symbol |
| `/exchanges/{id}` | DELETE | Delete a specific exchange |

---

## 🧪 How to Run

1. **Clone the repository**

```bash
git clone https://github.com/jettlewisd/stock-watcher-backend.git
cd stock-watcher-backend
```

2. **Set up PostgreSQL**

Make sure PostgreSQL is installed and running on your system.  
Then create a database for the project:

```sql
CREATE DATABASE stock_watcher_db;
```

3. **Configure application properties**

Edit the `src/main/resources/application.properties` file to match your local PostgreSQL setup (use the values provided below):

```properties

# Database connection
spring.datasource.url=jdbc:postgresql://localhost:5432/stock_watcher_db
spring.datasource.name=stock_watcher_db
spring.datasource.username=postgres
spring.datasource.password=postgres1
spring.datasource.driver-class-name=org.postgresql.Driver

# Hibernate configuration (optional)
spring.sql.init.mode=always
```

4. **Populate the database**

Use the provided SQL file (`stock_watcher.sql`) to create the tables and add sample data. If no file is included, you will need to add your own data manually. (Check the resources folder for SQL files).

5. **Run the application**

Using IntelliJ IDEA or from the terminal:

```bash
./mvnw spring-boot:run
```

---

## 📄 License

This project is open source and available under the MIT License.