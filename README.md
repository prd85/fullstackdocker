# Application Stack (Docker Compose)
## 📌 Overview

This project defines a multi-container application using Docker Compose. It consists of a frontend, backend, and a PostgreSQL database, all connected through a custom bridge network.

The setup is designed for local development and testing, providing a simple way to run a full-stack application with a single command.

## 🚀 Deployment
### Prerequisites
- Docker
- Docker Compose
### Run the application
docker-compose up --build
### Access services
- Frontend: http://localhost:3000
- Backend API: http://localhost:5001

To stop the application:

docker-compose down
## 🧩 Services
### Frontend
- Built from ./frontend
- Exposed on port 3000 (mapped to container port 80)
- Depends on the backend service
### Backend
- Built from ./backend
- Exposed on port 5001 (mapped to container port 5000)
- Connects to the database using environment variables:
DB_HOST=database
DB_USER=postgres
DB_PASS=password
DB_NAME=postgres
### Database
- Uses **PostgreSQL 16 (Alpine)**
- Persistent storage via Docker volume (pgdata)
- Automatically restarts unless stopped
## 🔗 Networking
- All services are connected via a custom bridge network: **my-custom-network**
- Services communicate using their service names (e.g., database)
## 💾 Volumes
- **pgdata:** Stores PostgreSQL data to persist across container restarts
## 📝 Notes
- This setup is intended for development purposes
- Default credentials are used; update them for use case
