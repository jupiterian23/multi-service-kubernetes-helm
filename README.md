# Multi-Service App on Kubernetes with Helm

A multi-service Flask application deployed on Kubernetes using Helm.

## Overview

This project demonstrates deploying and managing multiple containerized services on Kubernetes using Helm.

### Services

- Frontend Flask service on port 8080
- Backend Flask service on port 5000
- Kubernetes Deployments with multiple replicas
- Kubernetes ClusterIP Services
- Readiness and liveness probes
- Helm chart configuration
- Helm install and upgrade lifecycle
- Kubernetes service discovery

## Technologies

- Python
- Flask
- Docker
- Kubernetes
- Kind
- Helm
- kubectl
- Linux

## Architecture

```text
Kubernetes Cluster
        |
   +----+----+
   |         |
Frontend   Backend
Service    Service
 :8080      :5000
   |         |
 +---+---+ +---+---+
 |       | |       |
Pod     Pod Pod    Pod
