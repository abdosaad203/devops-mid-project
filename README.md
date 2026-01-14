# 🚀 DevOps End-to-End Deployment Project

![CI/CD Pipeline](https://github.com/abdosaad203/devops-mid-project/actions/workflows/pipeline.yml/badge.svg?branch=main)
![Railway Deployment](https://img.shields.io/badge/Railway-Deployed-success)
![Docker](https://img.shields.io/badge/Docker-Containers-blue)
![Ansible](https://img.shields.io/badge/Ansible-Configuration-red)

## 📖 Project Overview

This project demonstrates a complete **DevOps CI/CD pipeline** for a 3-tier web application (React Frontend, .NET Backend, MySQL Database). The goal was to automate the build, test, security scanning, and deployment processes across multiple environments (**Dev**, **Staging**, and **Production**).

The infrastructure utilizes **Docker** for containerization, **Ansible** for local self-hosted configuration, and **Railway** for cloud deployments, orchestrated entirely by **GitHub Actions**.

---

## 🏗️ Architecture & Workflow

1.  **Code Commit:** Developers push code to the `main` branch.
2.  **Continuous Integration (CI):**
    * **Reusable Workflows:** Leveraging a centralized repository for standardized build logic.
    * **Build & Test:** Compiling .NET and React applications.
    * **Security Scans:**
        * **GitLeaks:** Detecting hardcoded secrets.
        * **Trivy:** Scanning Docker images for vulnerabilities.
        * **CodeQL:** Static code analysis.
    * **Artifacts:** Pushing Docker images to **GitHub Container Registry (GHCR)**.
3.  **Continuous Deployment (CD):**
    * **Dev Environment:** Deployed to a **Self-Hosted Runner (CentOS)** using **Ansible Playbooks** and Docker Compose.
    * **Staging Environment:** Automated deployment to **Railway** (Cloud Platform) for QA.
    * **Production Environment:** Gated deployment to **Railway** requiring **Manual Approval** via GitHub Environments.

---

## 🛠️ Tech Stack

### Application
* **Frontend:** React (Vite) + TypeScript
* **Backend:** .NET 8 Web API
* **Database:** MySQL

### DevOps & Infrastructure
* **Containerization:** Docker & Docker Compose
* **CI/CD:** GitHub Actions (Pipelines & Reusable Workflows)
* **Configuration Management:** Ansible
* **Cloud Platform:** Railway
* **Package Registry:** GitHub Container Registry (GHCR)
* **OS:** CentOS Stream (Self-Hosted Runner)

### Security
* **Secret Scanning:** GitLeaks
* **Vulnerability Scanning:** Trivy
* **SAST:** CodeQL

---

## 🚀 Key Features implemented

### 1. Multi-Environment Deployment strategy
* **Dev:** Deployed locally on a self-hosted runner to simulate on-premise servers using Ansible.
* **Staging:** Cloud deployment on Railway with live URLs for testing.
* **Production:** Protected environment with **Approval Gates** to ensure stability before release.

### 2. Intelligent Automation
* **Dynamic Variable Injection:** Injecting API URLs and Database credentials at runtime/build time (e.g., `VITE_API_BASE_URL`).
* **Ansible Automation:** Automatically detecting OS (CentOS), installing Docker/dnf packages, and managing container orchestration.

### 3. Security-First Approach
* Pipeline fails immediately if secrets are detected (GitLeaks).
* Container images are scanned for high-severity vulnerabilities before deployment (Trivy).

---

## 📸 Project Screenshots

### 1. CI/CD Pipeline Success
*(Replace this text with a link to your pipeline summary screenshot)*
![Pipeline Success](./screenshots/pipeline-success.png)

### 2. Manual Approval for Production
The pipeline pauses and waits for admin approval before deploying to Production.
![Production Approval](./screenshots/approval-gate.png)

### 3. Application Running on Production
**Frontend:**
![Frontend](./screenshots/frontend-prod.png)

**Backend Swagger:**
![Swagger](./screenshots/backend-swagger.png)

### 4. Railway Dashboard (Staging & Prod)
![Railway Dashboard](./screenshots/railway-dashboard.png)

---

## 💻 How to Run Locally

If you want to run this project without the pipeline:

1.  **Clone the repository:**
    ```bash
    git clone [https://github.com/abdosaad203/devops-mid-project.git](https://github.com/abdosaad203/devops-mid-project.git)
    cd devops-mid-project
    ```

2.  **Start with Docker Compose:**
    ```bash
    docker compose up -d --build
    ```

3.  **Access the App:**
    * Frontend: `http://localhost:8081`
    * Backend: `http://localhost:8080/swagger`

---

## 👤 Author

**Abdo Saad**
* DevOps Engineer
* GitHub: [abdosaad203](https://github.com/abdosaad203)

---
*Built with ❤️ and a lot of YAML.*
