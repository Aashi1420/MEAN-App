# MEAN Stack CRUD Application - Deployment Guide

This project is a full-stack CRUD application built with MongoDB, Express, Angular 15, and Node.js. It has been containerized using Docker and is ready for automated deployment via CI/CD.

## 🚀 Features
- **Frontend**: Angular 15 with HttpClient for API interaction.
- **Backend**: Node.js & Express REST APIs.
- **Database**: MongoDB for persistent storage.
- **Containerization**: Docker & Docker Compose.
- **CI/CD**: GitHub Actions for automated build, push, and deploy.
- **Proxy**: Nginx as a reverse proxy on port 80.

---

## 🛠️ Local Development (Docker)

1. **Clone the repository** (or copy these files).
2. **Build and run** the stack:
   ```bash
   docker-compose up --build
   ```
3. **Access the application**:
   - Frontend: [http://localhost](http://localhost)
   - Backend API: [http://localhost/api/tutorials](http://localhost/api/tutorials)
   - MongoDB: `localhost:27017`

---

## ☁️ Deployment Instructions (Ubuntu VM)

### 1. VM Setup
1. Provision an Ubuntu VM (AWS EC2, Azure VM, etc.).
2. Install Docker and Docker Compose:
   ```bash
   sudo apt update
   sudo apt install docker.io docker-compose -y
   sudo systemctl start docker
   sudo systemctl enable docker
   ```
3. Create a directory for the app:
   ```bash
   mkdir ~/mean-app
   ```

### 2. GitHub Actions (CI/CD)
The pipeline is configured in `.github/workflows/deploy.yml`. You need to add the following **Repository Secrets** in GitHub:
- `DOCKERHUB_USERNAME`: Your Docker Hub username.
- `DOCKERHUB_TOKEN`: Your Docker Hub Access Token.
- `VM_IP`: Public IP of your Ubuntu VM.
- `VM_SSH_KEY`: Private SSH key to access the VM.

### 3. Nginx Reverse Proxy
Nginx is configured within the frontend container (`frontend/nginx.conf`) to:
- Serve Angular static files.
- Proxy `/api/*` requests to the backend service.

---

## 📦 Project Structure
- `/backend`: Node.js/Express server, models, and routes.
- `/frontend`: Angular 15 client-side application.
- `docker-compose.yml`: Orchestration for the whole stack.
- `.github/workflows`: CI/CD pipeline configuration.

## 📝 Deliverables Checklist
- [x] Dockerfiles for Frontend & Backend.
- [x] Docker Compose file.
- [x] CI/CD Configuration (GitHub Actions).
- [x] Nginx Reverse Proxy setup.
- [x] Deployment Guide (this README).
