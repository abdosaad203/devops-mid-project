# 🚀 End-to-End DevOps CI/CD Project

![CI/CD Pipeline](https://github.com/abdosaad203/devops-mid-project/actions/workflows/pipeline.yml/badge.svg?branch=main)
![Railway Deployment](https://img.shields.io/badge/Railway-Production-success)
![Docker](https://img.shields.io/badge/Docker-Containers-blue)
![Ansible](https://img.shields.io/badge/Ansible-Configuration-red)
![Security](https://img.shields.io/badge/Security-GitLeaks%20%7C%20Trivy-orange)

## 📖 Project Overview

This project implements a robust, production-grade **DevOps CI/CD Pipeline** for a 3-tier web application (React Frontend, .NET 8 Backend, MySQL Database).

The goal was to automate the entire software delivery lifecycle, starting from code commit to deployment across three distinct environments:
1.  **Development:** Self-hosted on-premise simulation using **Ansible** & **Docker**.
2.  **Staging:** Automated cloud deployment to **Railway** for QA/Testing.
3.  **Production:** Protected cloud deployment to **Railway** with **Approval Gates**.

The project focuses on **Automation**, **Security**, and **Scalability**, utilizing modern DevOps practices like Infrastructure as Code (IaC), Containerization, and Secret Management.

---

## 🏗️ Architecture & Workflow

The pipeline is orchestrated using **GitHub Actions** with a modular design (Reusable Workflows).

```mermaid
graph TD;
    User-->|Push Code| GitHub_Repo;
    GitHub_Repo-->|Trigger| CI_Pipeline;
    CI_Pipeline-->|Build & Test| Dotnet_React;
    CI_Pipeline-->|Security Scan| Trivy_GitLeaks;
    CI_Pipeline-->|Push Images| GHCR_Registry;
    GHCR_Registry-->|Deploy| Dev_Env[Dev: Ansible/Local];
    GHCR_Registry-->|Deploy| Staging_Env[Staging: Railway];
    GHCR_Registry-->|Wait for Approval| Prod_Gate{Manual Approval};
    Prod_Gate-->|Approved| Prod_Env[Production: Railway];
```
    📸 Project Showcase (Verification)
1. 🛡️ Security & Governance: Production Approval Gate
To ensure stability, the Production environment is protected. The pipeline pauses and waits for manual admin approval before deploying.

Proof of Protection Rules: <img width="1251" height="408" alt="1-approval-gate" src="https://github.com/user-attachments/assets/c9920b86-c577-4c89-9072-d030587d8363" />


2. ✅ CI/CD Pipeline Success
A fully green pipeline indicating successful Build, Test, Security Scans, and Deployments to all environments.

Full Pipeline Execution: <img width="1258" height="411" alt="2-pipeline-success" src="https://github.com/user-attachments/assets/8d18b448-cced-41e6-868e-23e48e5823dc" />


3. 🚀 Live Production Application
The application running live on the Production domain, connected to the database, serving real traffic.

Frontend & Backend Connectivity: <img width="1280" height="767" alt="3-production-live" src="https://github.com/user-attachments/assets/d34dd5cc-d73f-485f-9193-6eb20f5360b9" />


4. 🚆 Infrastructure Dashboard
Railway dashboard showing the healthy status of the 3-tier architecture (Frontend, Backend, Database) in the Production environment.

Service Status: <img width="1280" height="701" alt="4-railway-dashboard" src="https://github.com/user-attachments/assets/c21be76c-05e4-4362-872d-a1fac1a78ac4" />

---

## 🛠️ Technologies & Tools

### 🔹 Application Stack
* **Frontend:** React (Vite) + TypeScript
* **Backend:** .NET 8 Web API
* **Database:** MySQL 8.0

### 🔹 DevOps Infrastructure
* **Containerization:** Docker & Docker Compose
* **Orchestration:** Ansible (Playbooks & Inventory management)
* **Cloud Platform:** Railway (PaaS)
* **Artifact Registry:** GitHub Container Registry (GHCR)

### 🔹 CI/CD & Automation
* **GitHub Actions:** Primary CI/CD tool.
* **Reusable Workflows:** Centralized logic for maintainability.
* **Self-Hosted Runners:** Used for deploying to the Dev environment (CentOS).

### 🔹 Security Tools
* **GitLeaks:** Scans code for hardcoded secrets/passwords.
* **Trivy:** Scans Docker images for CVEs (Common Vulnerabilities).
* **CodeQL:** Static Application Security Testing (SAST).

---

## ⚙️ Key Features Implemented

### 1. Multi-Environment Deployment Strategy
* **Dev:** Deployed using **Ansible** on a local runner to simulate an on-premise data center. It installs Docker, authenticates with GHCR, and runs containers via Compose.
* **Staging:** Automatically deployed to **Railway** for immediate feedback.
* **Production:** Deployed to **Railway** but gated behind a "Required Reviewer" rule to prevent accidental breaking changes.

### 2. Intelligent Variable Injection
* The pipeline dynamically injects environment variables (Database URLs, API Endpoints) at runtime.
* Example: The Frontend connects to the Staging API in Staging, and the Production API in Production automatically.

### 3. "Fix & Secure" Approach
* **Dockerfile Optimization:** Fixed pathing issues for .NET build artifacts.
* **Secret Management:** All sensitive data (Tokens, Passwords) are stored in GitHub Secrets, never in the code.
* **Railway CLI Integration:** Automated the CLI authentication and deployment commands within the pipeline.

---

## 💻 How to Run Locally

If you wish to run the project on your local machine without the pipeline:

1.  **Clone the Repository:**
    ```bash
    git clone [https://github.com/abdosaad203/devops-mid-project.git](https://github.com/abdosaad203/devops-mid-project.git)
    cd devops-mid-project
    ```

2.  **Run with Docker Compose:**
    ```bash
    docker compose up -d --build
    ```

3.  **Access the Application:**
    * Frontend: `http://localhost:8081`
    * Backend Swagger: `http://localhost:8080/swagger`

---

## 👤 Author

**Abdo Saad**
* **Role:** DevOps Engineer
* **GitHub:** [abdosaad203](https://github.com/abdosaad203)

---
*Built with ❤️, YAML, and Docker.*
