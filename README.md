# Containerized Application Deployment - App Repository

## Overview

This repository contains the application source code, Dockerfile, and Jenkins pipeline responsible for building and publishing Docker images.

The application itself is intentionally simple (static website) because the primary purpose of this repository is to demonstrate DevOps deployment strategies rather than application development.

---

# Project Status

✅ Application CI/CD Completed

✅ Infrastructure CI/CD Completed

✅ Docker Image Versioning

✅ Terraform Remote Backend

✅ Launch Template Versioning

✅ ASG Instance Refresh

✅ Rollback Strategy Tested

🚧 Next Phase: Amazon ECS

## CI Flow

```text
Developer Commit
↓
GitHub Webhook
↓
Jenkins Pipeline
↓
Docker Build
↓
Docker Image Versioning
↓
Docker Hub Push
```
---

## Repository Structure
```text
.
├── app/
│   └── index.html
├── Dockerfile
├── Jenkinsfile
└── README.md
```
---

## Docker Build

The Jenkins pipeline automatically:

- Pulls application source code
- Builds Docker image
- Tags image using Jenkins build number
- Pushes image to Docker Hub

Example:

containerized-app:1
containerized-app:2
containerized-app:3

---

## Deployment Strategy

Application deployment is separated from infrastructure deployment.

Application pipeline responsibilities:

- Build image
- Push image
- Version image

Infrastructure pipeline responsibilities:

- Select image version
- Deploy infrastructure changes
- Trigger ASG refresh

This separation allows controlled deployments and easy rollback.

---

## Rollback Strategy

If version 10 fails:

Infrastructure variable:

docker_image_version = "10"

can be reverted to:

docker_image_version = "9"

```text
Terraform Apply
↓
Launch Template Update
↓
ASG Instance Refresh
↓
Rollback Complete
```
---

## Technologies Used

- GitHub
- Jenkins
- Docker
- Docker Hub

---

## Project Objective

This repository is part of a larger DevOps platform project focused on:

- CI/CD
- Containerization
- Infrastructure Automation
- Deployment Strategies
- Rollback Mechanisms

---