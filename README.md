```markdown
# Task 6.2c - Node.js App Deployment using Docker, Kubernetes, and Minikube

## 📦 Project Overview

This project demonstrates the deployment of a simple Node.js application on a Kubernetes cluster using Minikube. It includes Dockerization of the app, pushing the image to Docker Hub, and running it in a Kubernetes Pod.

---

## 🚀 Prerequisites

- Node.js and npm
- Docker
- Minikube
- kubectl (Kubernetes CLI)
- A Docker Hub account

---

## 🛠️ Project Structure

```

├── app.js              # Node.js application entry point
├── Dockerfile          # Docker image definition
├── package.json        # Node.js dependencies and metadata
├── deployment.yml      # Kubernetes Deployment and Service configuration
└── README.md           # Project instructions

````

---

## 📥 Step-by-Step Instructions

### 1️⃣ Start Minikube

```bash
minikube start
````

---

### 2️⃣ Build Docker Image

```bash
docker build -t chandrakanth00/task6.2c:latest .
```

---

### 3️⃣ Push Image to Docker Hub

```bash
docker push chandrakanth00/task6.2c:latest
```

> ✅ Make sure you are logged in using `docker login` and the image name matches your Docker Hub username.

---

### 4️⃣ Deploy to Kubernetes

```bash
kubectl apply -f deployment.yml
```

Check the pods:

```bash
kubectl get pods
```

Check the services:

```bash
kubectl get services
```

---

### 5️⃣ Access the Application

Use port forwarding:

```bash
kubectl port-forward service/node-app-service 3000:3000
```

Then open your browser:

```
http://localhost:3000
```

---

## 🔄 Updating the Application

1. Make changes in `app.js` or other files.
2. Rebuild the image with a new tag:

```bash
docker build -t chandrakanth00/task6.2cupdated:latest .
docker push chandrakanth00/task6.2cupdated:latest
```

3. Update the deployment:

```bash
kubectl set image deployment/node-app-deployment node-app=chandrakanth00/task6.2cupdated:latest
```

---

## 🧹 Cleanup

To delete the deployment and services:

```bash
kubectl delete -f deployment.yml
minikube stop
```

---

## 📌 Author

**Chandrakanth**


