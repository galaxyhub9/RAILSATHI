# RailSathi (FastAPI + PostgreSQL + Docker)

### Prerequisites
- [Docker](https://docs.docker.com/get-docker/)
- [Docker Compose](https://docs.docker.com/compose/install/)

## ✅ Project Setup (Docker)
### Clone the Repo
```bash
git clone https://github.com/galaxyhub9/RAILSATHI.git
cd RailSathiBE
```
### Create .env file
```
cp .env.example .env
```
- Edit .env and provide values like DB credentials, mail settings, etc.

### Run Docker
```
docker-compose up --build
```
Visit Swagger docs: http://localhost:8000/rs_microservice/docs

### Health check
Check if the service is up and running.
- Endpoint: GET /health
- Response:
  ```
  {
  "status": "healthy"
  }
  ```

## 📌 API Endpoints

All endpoints are prefixed with `/rs_microservice`.

| Method     | Endpoint                                  | Description                             |
|------------|-------------------------------------------|-----------------------------------------|
| `POST`     | `/complaint/add/`                         | Add a new complaint                     |
| `GET`      | `/complaint/get/{id}`                     | Get complaint by ID                     |
| `GET`      | `/complaint/get/date/{date}`              | Get complaints by date & mobile number  |
| `PUT`/`PATCH` | `/complaint/update/{id}`              | Update or replace a complaint           |
| `DELETE`   | `/complaint/delete/{id}`                  | Delete a complaint                      |
| `DELETE`   | `/media/delete/{id}`                      | Delete complaint media                  |
| `GET`      | `/train_details/{train_no}`               | Get train, depot, and zone info         |
| `GET`      | `/health`                                 | Health check endpoint                   |
| `GET`      | `/docs`                                   | Swagger UI for interactive API docs     |

## Assumptions & Design Decisions

- Authentication and user management are not implemented; email alerts assume static war room users.
- Tables like `rail_sathi_railsathicomplain`, `rail_sathi_railsathicomplainmedia`, `trains_traindetails` must be manually created in PostgreSQL.
- PostgreSQL is used directly via `psycopg2`, no ORM is used.

## Key Features
- PostgreSQL integration with raw SQL queries.
- Swagger/OpenAPI documentation at `/docs`.
- Dockerized setup with PostgreSQL and FastAPI.

## Security & Best Practices
- Sensitive config (DB credentials) are stored in a `.env` file and not committed to Git.
- Docker environment uses isolated containers for DB and app.
  
