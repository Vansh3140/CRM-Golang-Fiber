# CRM Application with Golang and Fiber

This project is a simple CRM (Customer Relationship Management) application built with **Golang**, **Fiber**, and **GORM**. The application uses **SQLite** as the database. It provides RESTful API endpoints to manage leads, allowing users to create, retrieve, and delete leads.

---

## Features

- **Create a new lead**
- **Retrieve all leads**
- **Retrieve a specific lead by ID**
- **Delete a lead by ID**
- **Auto-database migration using GORM**

---

## Project Structure

```plaintext
.
├── main.go          # Entry point of the application
├── lead/
│   └── lead.go      # Contains lead-related models and handlers
└── database/
    └── database.go  # Database connection setup
```

---

## Installation

1. **Clone the Repository**:
   ```bash
   git clone https://github.com/Vansh3140/crm-golang-fiber.git
   cd crm-golang-fiber
   ```

2. **Install Dependencies**:
   Ensure you have [Go](https://golang.org/) installed. Run the following command to install the necessary dependencies:
   ```bash
   go mod tidy
   ```

3. **Run the Application**:
   ```bash
   go run main.go
   ```

4. The application will start and listen on `http://localhost:8080`.

---

## API Endpoints

| Method | Endpoint            | Description                |
|--------|---------------------|----------------------------|
| GET    | `/api/v1/lead`      | Fetch all leads            |
| GET    | `/api/v1/lead/:id`  | Fetch a specific lead by ID|
| POST   | `/api/v1/lead`      | Create a new lead          |
| DELETE | `/api/v1/lead/:id`  | Delete a lead by ID        |

---

## Example Requests

### 1. **Create a New Lead**
**Endpoint**: `POST /api/v1/lead`  
**Request Body** (JSON):
```json
{
    "name": "John Doe",
    "company": "Example Co.",
    "email": "john@example.com",
    "phone": 1234567890
}
```

### 2. **Fetch All Leads**
**Endpoint**: `GET /api/v1/lead`

**Response** (JSON):
```json
[
    {
        "ID": 1,
        "Name": "John Doe",
        "Company": "Example Co.",
        "Email": "john@example.com",
        "Phone": 1234567890,
        "CreatedAt": "2024-12-06T12:00:00Z",
        "UpdatedAt": "2024-12-06T12:00:00Z",
        "DeletedAt": null
    }
]
```

### 3. **Fetch a Lead by ID**
**Endpoint**: `GET /api/v1/lead/1`

**Response** (JSON):
```json
{
    "ID": 1,
    "Name": "John Doe",
    "Company": "Example Co.",
    "Email": "john@example.com",
    "Phone": 1234567890,
    "CreatedAt": "2024-12-06T12:00:00Z",
    "UpdatedAt": "2024-12-06T12:00:00Z",
    "DeletedAt": null
}
```

### 4. **Delete a Lead**
**Endpoint**: `DELETE /api/v1/lead/1`

**Response** (Text):
```
Lead successfully deleted
```

---

## Dependencies

- **Fiber**: Web framework for Golang ([Documentation](https://gofiber.io/))
- **GORM**: ORM library for Golang ([Documentation](https://gorm.io/))
- **SQLite**: Lightweight database

---

## How It Works

1. **Database Initialization**:
   The `initDatabase` function connects to an SQLite database and performs automatic migration of the `Lead` model.

2. **Routes Setup**:
   The `setupRoutes` function defines RESTful API endpoints to handle lead operations.

3. **Handlers**:
   - `GetLeads`: Fetches all leads.
   - `GetLead`: Fetches a specific lead by ID.
   - `NewLead`: Creates a new lead from the request body.
   - `DeleteLead`: Deletes a lead by ID.

4. **Fiber Application**:
   The Fiber app listens on port 8080 and serves the defined API endpoints.

---

## Notes

- Ensure you have **SQLite** installed on your machine or Docker if running this in a containerized environment.
- The database file `leads.db` will be created in the root directory upon running the application.

---

## License

This project is open-source and available under the [MIT License](LICENSE).
