# 🧱 Spring Boot Containerization & Orchestration Playground

This project demonstrates how to **containerize** a Spring Boot Gradle application using multiple approaches and deploy it with **various orchestration platforms**.

---

## 🚀 Technologies Covered

### 🐳 Containerization Methods
- [x] Docker (`Dockerfile`)
- [x] Cloud Native Buildpacks (`bootBuildImage`)
- [x] Google Jib (no Dockerfile required)

### ☸️ Orchestration Platforms
- [x] Docker Compose
- [x] Kubernetes (K8s)
- [x] OpenShift
- [x] AWS ECS (Fargate)
- [x] Google Cloud Run
- [x] Azure Container Instances / Web App for Containers

---

## 📦 Containerization Guide

### 1. Docker
```bash
docker build -t spring-boot-app .
docker run -p 8080:8080 spring-boot-app
```

### 2. Buildpacks
```bash
./gradlew bootBuildImage --imageName=spring-boot-app:buildpacks
docker run -p 8080:8080 spring-boot-app:buildpacks
```

### 3. Jib
```bash
./gradlew jibDockerBuild
docker run -p 8080:8080 spring-boot-app
```

---

## ⚙️ Orchestration Guide

### Docker Compose
```bash
docker-compose up
```

### Kubernetes
```bash
kubectl apply -f k8s/deployment.yaml
kubectl get services
```

### OpenShift
```bash
oc apply -f openshift/deployment.yaml
```

### AWS ECS (Fargate)
1. Push image to Amazon ECR.
2. Register ECS Task using `ecs/task-definition.json`.
3. Launch service with Fargate.

### Google Cloud Run
```bash
gcloud run deploy --source .
```
Or:
```bash
gcloud run services replace cloudrun/service.yaml
```

### Azure Container Instance / Web App
1. Push image to Azure Container Registry or Docker Hub.
2. Deploy via Azure Portal or CLI using `azure/appsettings.json`.

---

## 🗂 Directory Structure

```
.
├── Dockerfile
├── docker-compose.yml
├── k8s/
│   └── deployment.yaml
├── openshift/
│   └── deployment.yaml
├── ecs/
│   └── task-definition.json
├── cloudrun/
│   └── service.yaml
├── azure/
│   └── appsettings.json
├── build.gradle
└── README.md
```

---

## ✅ Prerequisites

- Java 21+
- Docker
- Gradle
- Kubernetes CLI (`kubectl`)
- OpenShift CLI (`oc`)
- AWS CLI
- Google Cloud CLI (`gcloud`)
- Azure CLI

---

## 📢 Notes

- Replace `your-app:latest` and image names accordingly.
- These configurations are intended for demo purposes. For production, add TLS, secrets, autoscaling, etc.
- This repo does **not** include CI/CD integrations.

---

## 📜 License

MIT License