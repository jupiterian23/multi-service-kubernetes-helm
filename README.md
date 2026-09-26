# 🚀 Multi-Service App on Kubernetes with Helm

A multi-service Flask application deployed and managed on Kubernetes using Helm. ☸️

## 📌 Overview

This project demonstrates deploying and managing multiple containerized services on Kubernetes using Helm.

### 🧩 Services

* 🌐 Frontend Flask service on port `8080`
* ⚙️ Backend Flask service on port `5000`
* ☸️ Kubernetes Deployments with multiple replicas
* 🔗 Kubernetes ClusterIP Services
* ❤️ Readiness and liveness probes
* ⛵ Helm chart configuration
* 🔄 Helm install and upgrade lifecycle
* 🔍 Kubernetes service discovery

## 🛠️ Technologies

* 🐍 Python
* 🌶️ Flask
* 🐳 Docker
* ☸️ Kubernetes
* 📦 Kind
* ⛵ Helm
* 🧰 kubectl
* 🐧 Linux

## 🏗️ Architecture

```text
                 ☸️ Kubernetes Cluster
                         |
                  +------+------+
                  |             |
              🌐 Frontend    ⚙️ Backend
                Service       Service
                 :8080         :5000
                   |             |
              +----+----+    +---+----+
              |         |    |        |
             Pod       Pod  Pod      Pod
```

## 🌐 Frontend

**Port:** `8080`

### Endpoints

* `/`
* `/health`

### Health Check

```bash
curl http://localhost:8080/health
```

Response:

```json
{"status":"healthy"}
```

## ⚙️ Backend

**Port:** `5000`

### Endpoints

* `/`
* `/health`

## ☸️ Kubernetes Deployment

Both services are deployed using Kubernetes Deployments.

### Initial Configuration

* 🌐 Frontend replicas: `2`
* ⚙️ Backend replicas: `2`

Both services use `ClusterIP` Services for internal Kubernetes networking.

## ❤️ Health Probes

Both applications use:

* 🟢 Readiness probes
* ❤️ Liveness probes

The probes use the `/health` endpoint to verify application health.

## 🔗 Kubernetes Service Discovery

Backend connectivity was tested from a temporary Kubernetes pod:

```bash
kubectl run test-client --rm -it --image=curlimages/curl --restart=Never -- curl http://backend:5000/health
```

The backend returned:

```json
{"status":"healthy"}
```

✅ This demonstrates Kubernetes DNS-based service discovery and internal service-to-service communication.

## ⛵ Helm

The Helm chart is located at:

```text
helm/multi-service-app/
```

### 🔍 Chart Validation

```bash
helm lint helm/multi-service-app
```

The chart passed Helm linting successfully. ✅

### 🚀 Helm Installation

The Helm release was installed using:

```bash
helm install multi-service-app helm/multi-service-app
```

## 🔄 Helm Upgrade

The backend was scaled from **2 replicas to 3 replicas** using Helm:

```bash
helm upgrade multi-service-app helm/multi-service-app --set backend.replicaCount=3
```

### 📜 Helm Revision History

```text
Revision 1 - Initial installation
Revision 2 - Upgrade with backend scaled to 3 replicas
```

### 📊 Final Configuration

* ⚙️ Backend: `3 replicas`
* 🌐 Frontend: `2 replicas`

## 📦 Helm Package

The Helm chart was successfully packaged as:

```text
multi-service-app-1.0.0.tgz
```

📌 The package is excluded from Git using `.gitignore`.

## 📁 Project Structure

```text
multi-service-kubernetes-helm/
├── app/
│   ├── backend/
│   │   ├── app.py
│   │   ├── requirements.txt
│   │   ├── Dockerfile
│   │   ├── deployment.yaml
│   │   └── service.yaml
│   │
│   └── frontend/
│       ├── app.py
│       ├── requirements.txt
│       ├── Dockerfile
│       ├── deployment.yaml
│       └── service.yaml
│
├── helm/
│   └── multi-service-app/
│       ├── Chart.yaml
│       ├── values.yaml
│       └── templates/
│           ├── backend-deployment.yaml
│           ├── backend-service.yaml
│           ├── frontend-deployment.yaml
│           └── frontend-service.yaml
│
├── .gitignore
└── README.md
```

## 🎯 Skills Demonstrated

* 🐳 Docker containerization
* ☸️ Kubernetes Deployments
* 🔗 Kubernetes Services
* 🔍 Kubernetes DNS
* 🔄 Service-to-service communication
* 🟢 Readiness probes
* ❤️ Liveness probes
* 📈 Replica scaling
* ⛵ Helm chart development
* ⚙️ Helm values
* 🧩 Helm templating
* 🚀 Helm releases
* 🔄 Helm upgrades
* 📜 Helm revision history
* 📦 Helm packaging
* 🖥️ Kind local Kubernetes clusters
* 🧰 kubectl administration

## 🧠 Learning Outcome

This project demonstrates the practical deployment and management of a multi-service containerized application using Kubernetes and Helm.

Through this project, I practiced:

* 🚀 Deploying containerized applications on Kubernetes
* 🔗 Kubernetes service discovery
* ❤️ Application health monitoring
* 📈 Scaling application replicas
* ⛵ Creating and managing Helm charts
* 🔄 Managing Helm releases and upgrades
* 🧩 Using Helm values and templates
* 🐳 Working with Docker containers
* ☸️ Administering a local Kubernetes cluster with Kind

## 🏆 Project Status

**✅ Completed**

This project is part of my hands-on **Cloud & DevOps learning journey**.
