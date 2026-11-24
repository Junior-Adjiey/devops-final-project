
# Task Management API

A REST API for task management, developed as part of the DevOps and Continuous Deployment final project at EFREI Paris.

## Tech Stack

- Java 21
- Spring Boot
- Spring Data JPA
- PostgreSQL 17
- Docker Compose
- Maven

## Features

- Create a task
- List all tasks
- Get a task by ID
- Update a task
- Delete a task
- Health check endpoint

## API Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/tasks` | List all tasks |
| GET | `/tasks/{id}` | Get a task by ID |
| POST | `/tasks` | Create a task |
| PUT | `/tasks/{id}` | Update a task |
| DELETE | `/tasks/{id}` | Delete a task |
| GET | `/health` | Health check |

## Getting Started

### Prerequisites

Make sure you have installed:

- Java JDK 21
- Docker Desktop
- Git

### 1. Clone the repository

```bash
git clone https://github.com/Junior-Adjiey/devops-final-project.git
cd devops-final-project
```

### 2. Configure environment variables

Create a `.env` file from the provided example.

On Windows PowerShell:

```powershell
Copy-Item .env.example .env
```

On Linux or macOS:

```bash
cp .env.example .env
```

Open `.env` and replace `change_me` with your own PostgreSQL password.

**Never commit the `.env` file.**

### 3. Start PostgreSQL

Make sure Docker Desktop is running.

From the project root, execute:

```bash
docker compose up -d
```

PostgreSQL will be available on `localhost:5434`.

### 4. Configure Spring Boot

Set the `POSTGRES_PASSWORD` environment variable to the same password used in `.env`.

For IntelliJ IDEA, add it in:

`Run → Edit Configurations → Environment variables`

Or, if running from Windows PowerShell:

```powershell
$env:POSTGRES_PASSWORD = "your_password"
```

On Linux or macOS:

```bash
export POSTGRES_PASSWORD="your_password"
```

Replace `your_password` with your actual PostgreSQL password.

### 5. Run the application

Navigate to the application directory:

```bash
cd app
```

On Windows PowerShell:

```powershell
.\mvnw.cmd spring-boot:run
```

On Linux or macOS:

```bash
./mvnw spring-boot:run
```

The API will be available at:

http://localhost:8080

### 6. Verify the application

Health check:

```http
GET http://localhost:8080/health
```

List tasks:

```http
GET http://localhost:8080/tasks
```

Create a task:

```http
POST http://localhost:8080/tasks
Content-Type: application/json

{
  "title": "Configure CI/CD",
  "description": "Create the GitHub Actions pipeline",
  "status": "TODO"
}
```

Available statuses: `TODO`, `IN_PROGRESS`, `DONE`.
