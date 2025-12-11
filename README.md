# DevOps CI/CD Pipelines

This repository contains the CI and CD pipeline configurations for our projects.  
The workflow is separated into two dedicated branches:

- **`ci` branch** — contains the Continuous Integration pipeline  
- **`cd` branch** — contains the Continuous Deployment pipeline

The `main` branch serves as documentation and a reference point for how the pipelines work.

---

## 📌 Branch Structure

### **1. `ci` Branch (Continuous Integration)**
This branch includes all automation related to **building Docker images**, **running tests**, and **pushing images** to the private registry.

Typical tasks handled in the CI pipeline:
- Building Docker images with BuildKit
- Tagging images using Git tags (e.g., `v1.2.3`)
- Logging into the private Docker registry
- Pushing the built images to the registry

CI is triggered when:
- A **semantic version tag** is created (`vX.Y.Z`)

---

### **2. `cd` Branch (Continuous Deployment)**
This branch manages deployment to servers using Docker Compose.  
The CD pipeline:

- Fetches the `docker-compose.yml` file from the `cd` branch  
- Pulls the new image created by CI  
- Updates the running service using `docker compose up -d`

CD is triggered when:
- The **gitlab-ci branch** receives a semantic version tag  
- Deployment requires updating the image tag dynamically

---

## 🚀 Workflow Summary

1. Developer merges code → creates a version tag (`v1.0.0`)
2. CI branch builds & pushes the image → registry
3. CD branch deploys the new version → server using Docker Compose

---

## 📁 Repository Structure

