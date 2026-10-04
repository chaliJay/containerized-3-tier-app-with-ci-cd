# Cloud Services CI/CD Deployment Project
This project demonstrates a full CI/CD workflow for deploying a containerized multi‑service application (frontend, backend, cache, and database) to Rahti/OpenShift. The pipeline automatically builds Docker images, pushes them to Docker Hub, and triggers a new deployment in Rahti whenever code is committed to the main branch.

The project also includes Kubernetes readiness probes, basic observability practices, and documentation showing how deployments are verified.

# High‑Level Architecture Diagram

                ┌──────────────────────────┐
                │        Frontend          │
                │      (React Pod)         │
                └───────────┬──────────────┘
                            │ Route
                            ▼
                ┌──────────────────────────┐
                │        Backend           │
                │     (Node.js Pod)        │
                └───────┬─────────┬────────┘
                        │         │
                        ▼         ▼
        ┌──────────────────┐   ┌──────────────────┐
        │      Cache       │   │    Database      │
        │    (Redis Pod)   │   │  (Postgres Pod)  │
        └──────────────────┘   └──────────────────┘

                ┌──────────────────────────┐
                │       CI/CD Pipeline     │
                │     (GitHub Actions)     │
                └──────────────────────────┘


# CI/CD Pipeline
The GitHub Actions workflow:

1. Checks out repository code

2. Logs into Docker Hub using GitHub Secrets

3. Builds Docker images for backend and frontend

4. Pushes images to Docker Hub

5. Rahti pulls updated images and redeploys pods

# Secrets Used
- RAHTI_SERVER
- RAHTI_TOKEN
- DOCKER_USERNAME
- DOCKER_PASSWORD

These are stored securely in GitHub → Settings → Secrets and variables → Actions.