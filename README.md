# 🚀 Static Website Deployment on Kubernetes

![Kubernetes](https://img.shields.io/badge/Kubernetes-Deployment-blue)
![Docker](https://img.shields.io/badge/Docker-Containerization-blue)
![Minikube](https://img.shields.io/badge/Minikube-Local--Cluster-orange)
![Status](https://img.shields.io/badge/Project-Completed-brightgreen)

---

## 📌 Project Overview

This project demonstrates how to deploy a simple static HTML website on Kubernetes using core objects like **Pods, Deployments, and Services**.

It is designed as a beginner-friendly DevOps project to understand Kubernetes fundamentals.

---

## 🧱 Tech Stack

* **Frontend:** HTML, CSS
* **Containerization:** Docker
* **Orchestration:** Kubernetes (Minikube)

---

## 🎯 Objectives

* Understand Kubernetes architecture
* Learn how Pods and Deployments work
* Expose applications using Services (NodePort)
* Practice container-based deployment

---

## 🏗️ Architecture Diagram

```
        User (Browser)
              │
              ▼
     NodePort Service (30007)
              │
              ▼
        Deployment (2 Pods)
         │            │
         ▼            ▼
       Pod 1        Pod 2
         │            │
         ▼            ▼
      Nginx        Nginx
         │            │
         ▼            ▼
     Static HTML  Static HTML
```

---

## 📁 Project Structure

```
k8s-static-site/
│── index.html
│── Dockerfile
│── deployment.yaml
│── service.yaml
```

---

## ⚙️ Setup Instructions

### 🔹 1. Install Dependencies

* Docker
* Minikube
* kubectl

---

### 🔹 2. Start Minikube

```bash
minikube start --driver=docker
```

Verify:

```bash
kubectl get nodes
```

---

### 🔹 3. Build Docker Image

```bash
eval $(minikube docker-env)
docker build -t k8s-static-site .
```

---

### 🔹 4. Deploy Application

```bash
kubectl apply -f deployment.yaml
```

Check pods:

```bash
kubectl get pods
```

---

### 🔹 5. Expose Service

```bash
kubectl apply -f service.yaml
```

Check service:

```bash
kubectl get svc
```

---

### 🔹 6. Access Application

#### Option 1 (Local Minikube)

```bash
minikube service static-site-service
```

#### Option 2 (EC2 / Cloud)

```bash
kubectl port-forward service/static-site-service 8080:80 --address 0.0.0.0
```

Open in browser:

```
http://<EC2-PUBLIC-IP>:8080
```

---

## 📦 Kubernetes Resources Used

### 🔹 Pod

* Smallest unit in Kubernetes
* Runs containerized application

### 🔹 Deployment

* Manages multiple Pods
* Ensures high availability
* Supports scaling and updates

### 🔹 Service (NodePort)

* Exposes application externally
* Maps internal container port to external port

---

## 🧪 Useful Commands

```bash
kubectl get all
kubectl describe pod <pod-name>
kubectl logs <pod-name>
```

---

## 🔁 Scaling Application

```bash
kubectl scale deployment static-site-deployment --replicas=5
```

---

## 📸 Screenshots

* Pod running (`kubectl get pods`)
* Service output (`kubectl get svc`)

  <img width="1918" height="528" alt="image" src="https://github.com/user-attachments/assets/e955584b-9e13-4818-b587-70a964e4b5ee" />

  

---

##   Troubleshooting

### 🔹 Cluster not running

```bash
minikube start
```

### 🔹 Docker permission issue

```bash
sudo usermod -aG docker $USER
```

### 🔹 Connection timeout (EC2)

* Use port-forward instead of Minikube IP
* Open required ports in Security Group

---

## 📸 Output

After successful deployment, the browser displays:

```
Hello from Kubernetes 
```

<img width="1436" height="786" alt="image" src="https://github.com/user-attachments/assets/9a9bb8d5-6f5f-4aac-8855-6aa9e8e50a5b" />


##  Author

**Jeny**

---

##  Conclusion

This project provides a strong foundation in Kubernetes basics and prepares you for real-world DevOps workflows.
