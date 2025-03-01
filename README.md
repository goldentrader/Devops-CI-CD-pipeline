# Devops-CI-CD-pipeline
# DevOps Pipeline Project

This repository contains the configuration and automation scripts for a CI/CD pipeline that integrates multiple DevOps tools. The pipeline leverages Ansible, Terraform, GitHub webhooks, Jenkins, Docker, and Kubernetes to provision infrastructure, build and push container images, and deploy applications seamlessly.

---

## Overview

- **Local Environment**:  
  - **Ansible**: Manages configuration of local environments and remote systems.  
  - **Terraform**: Provisions and manages infrastructure as code.

- **CI/CD Integration**:  
  - **GitHub Webhook**: Triggers Jenkins jobs upon code commits and pull requests.  
  - **Jenkins**: Orchestrates the pipeline; installed natively on an Azure master machine.

- **Containerization & Deployment**:  
  - **Docker**: Used to build application images on the master node and push them to Docker Hub.  
  - **Kubernetes**: Worker nodes pull the Docker images from Docker Hub and deploy the application.

---

## Architecture & Workflow

1. **Code Commit & Webhook Trigger**  
   Developers push code to the GitHub repository. A GitHub webhook then notifies Jenkins of the new commits.

2. **Jenkins Build Process**  
   Jenkins (installed natively on an Azure master machine) triggers the build:
   - Executes Ansible playbooks for configuration management.
   - Runs Terraform scripts to provision required infrastructure.

3. **Docker Build & Push**  
   - Jenkins builds a Docker image for the application.
   - The built image is pushed to Docker Hub.

4. **Kubernetes Deployment**  
   - Worker nodes in the Kubernetes cluster automatically pull the latest image from Docker Hub.
   - The application is deployed or updated within the Kubernetes cluster.

---

## Prerequisites

- **Local Machine Requirements**:
  - Git, Ansible, and Terraform installed.
  - Docker installed for local builds and testing.

- **Azure Master Node**:
  - Jenkins installed natively (refer to the [Jenkins Installation Guide](https://www.jenkins.io/doc/book/installing/)).
  - Docker configured to build images and push them to Docker Hub.
  
- **Docker Hub**:
  - An active Docker Hub account to host the built images.

- **Kubernetes Cluster**:
  - At least one worker node configured to pull images and run deployments.
  - `kubectl` configured for interacting with your cluster.

---

## Project Structure

