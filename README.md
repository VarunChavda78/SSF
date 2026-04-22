# Skill Spring Freelance (SSF) - DevOps & Infrastructure

This repository contains the full-stack **Skill Spring Freelance (SSF)** platform, engineered with a focus on containerization, automated CI/CD workflows, and scalable infrastructure.

---

## 🏗️ System Architecture

The SSF system is built on a containerized 3-tier architecture:

1.  **Frontend**: React-based SPA served through a Node.js environment.
2.  **Backend**: Django REST Framework (DRF) handling business logic and API endpoints.
3.  **Database**: PostgreSQL (v17) for persistent data storage.

All services communicate over a private Docker bridge network, with specific ports exposed for external access and monitoring.

---

## 🐳 Containerization

The project is fully dockerized to ensure environment parity across development, staging, and production.

### Docker Images
- **Backend**: Built using `python:3.9` base image. It handles API requests on port `8000`.
- **Frontend**: Built using `node:18` base image. It serves the React application on port `3000`.

### Orchestration (Docker Compose)
The services are managed via `docker-compose.yml`, which handles:
- **Service Dependencies**: Ensuring the database starts before the backend, and the backend before the frontend.
- **Persistent Storage**: Utilizing Docker volumes (`pg_data`) for PostgreSQL data persistence.
- **Port Mapping**:
    - **Frontend**: `3323:3000`
    - **Backend**: `8829:8000`
    - **PostgreSQL**: `5525:5432`

---

## 🚀 CI/CD Pipeline (GitHub Actions)

The repository includes a robust CI/CD pipeline defined in `.github/workflows/ci.yml`.

### Workflow Steps:
1.  **Build**: Automatically triggers on pushes to the `main` branch.
2.  **Docker Hub Integration**: Authenticates and pushes multi-service images to Docker Hub.
3.  **Automated Logging**: Captures build and push logs for both frontend and backend services.
4.  **MCP Webhook Integration**: On completion (success or failure), the pipeline aggregates logs and sends a comprehensive report to a custom MCP (Model Context Protocol) endpoint (`https://mcp.varunchavda.in/webhook`). This provides real-time visibility into the deployment status.

---

## 🛠️ Infrastructure Setup

### Prerequisites
- Docker & Docker Compose
- GitHub Secrets (for CI/CD):
    - `DOCKER_USERNAME`
    - `DOCKER_PASSWORD`

### Local Deployment
1.  **Clone and Configure**:
    ```bash
    git clone <repo-url>
    cd SSF
    ```
2.  **Environment Variables**: Create a `.env` in the root:
    ```env
    REACT_APP_API_URL=http://localhost:8829/api
    ```
3.  **Launch Services**:
    ```bash
    docker-compose up --build -d
    ```

---

## 📊 Monitoring & Maintenance
- **Logs**: Access service logs via `docker-compose logs -f`.
- **Database Backups**: Managed through persistent volumes in `pg_data`.
- **Pipeline Visibility**: Status and logs are pushed to the MCP dashboard for every commit on `main`.

---

## 📜 License
This project's infrastructure and code are licensed under the MIT License.