# SSF - Full-Stack Freelancing Platform

SSF (Scalable Services for Freelancers) is a robust, production-ready web application designed to connect clients with freelancers. Built with a modern tech stack and containerized for seamless deployment, SSF offers a streamlined experience for posting projects, submitting proposals, and managing collaborations.

## 🚀 Tech Stack

### Backend
- **Framework**: [Django](https://www.djangoproject.com/) & [Django REST Framework](https://www.django-rest-framework.org/)
- **Authentication**: JWT (SimpleJWT)
- **Database**: PostgreSQL (v17)
- **Server**: Gunicorn
- **Language**: Python

### Frontend
- **Library**: [React (v18)](https://react.dev/)
- **Styling**: [Bootstrap (v5)](https://getbootstrap.com/)
- **API Client**: Axios
- **State/Routing**: React Router DOM (v6)

### Infrastructure
- **Containerization**: Docker & Docker Compose
- **CI/CD**: GitHub Actions

---

## ✨ Key Features

### For Clients
- **User Registration & Login**: Secure account management.
- **Project Posting**: Define project requirements, budget, and department.
- **Project Management**: View, update, and delete your project listings.
- **Proposal Review**: Browse and manage bids from freelancers.
- **Search & Filter**: Find the right talent or project easily.

### For Freelancers
- **Browse Projects**: View all open project requirements on the dashboard.
- **Apply for Projects**: Submit detailed proposals with bid amounts.
- **Track Applications**: Monitor all applied projects from a dedicated dashboard.
- **Search & Filter**: Discover projects based on specific criteria.

---

## 🏗️ Project Structure

```text
SSF/
├── backend/            # Django REST API
│   ├── api/            # Main application logic (Models, Views, Serializers)
│   ├── Freelancing_Project/ # Project settings and configuration
│   ├── Dockerfile      # Backend container definition
│   └── requirements.txt # Python dependencies
├── frontend/           # React Application
│   ├── src/            # React components and logic
│   ├── Dockerfile      # Frontend container definition
│   └── package.json    # Node.js dependencies
├── docker-compose.yml  # Multi-container orchestration
└── .github/workflows/  # CI/CD pipeline configurations
```

---

## 🛠️ Getting Started

### Prerequisites
- [Docker](https://docs.docker.com/get-docker/)
- [Docker Compose](https://docs.docker.com/compose/install/)

### Local Development (Docker)

1. **Clone the Repository**
   ```bash
   git clone <repository-url>
   cd SSF
   ```

2. **Configure Environment Variables**
   Create a `.env` file in the root directory (refer to `.env.example` if available).

3. **Start the Services**
   ```bash
   docker-compose up --build
   ```

4. **Access the Application**
   - **Frontend**: [http://localhost:3323](http://localhost:3323)
   - **Backend API**: [http://localhost:8829](http://localhost:8829)
   - **Database (Postgres)**: `localhost:5525`

---

## 🔐 API Endpoints

- `POST /api/sign-up/` - Register a new user.
- `POST /api/login/` - Authenticate user and receive JWT.
- `GET/POST /api/projects/` - List all projects or create a new one.
- `GET/PUT/DELETE /api/projects/<id>/` - Manage a specific project.
- `GET/POST /api/proposals/` - List or submit project proposals.
- `GET /api/getuser/` - Fetch current user profile details.

---

## 📜 License
This project is licensed under the MIT License.