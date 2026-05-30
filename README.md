# ⚙️ DevOps Java CI/CD Pipeline Project

A hands-on CI/CD pipeline practice project built with a **Spring Boot Java application**, automated through Jenkins, analyzed by SonarQube, containerized with Docker, and deployed to **AWS EKS** via Kubernetes.

> 🔗 GitHub: [https://github.com/yourusername/devops-java-cicd-project.git](https://github.com/yourusername/devops-java-cicd-project.git)

---

## 🛠️ Tech Stack

| Layer | Tool |
|---|---|
| Application | Java 17 · Spring Boot 3.1 |
| Build | Maven |
| CI/CD | Jenkins |
| Code Quality | SonarQube |
| Containerization | Docker · DockerHub |
| Orchestration | Kubernetes · AWS EKS |
| Cloud | AWS |

---

## 🏗️ Project Structure

```
devops-java-cicd-project/
│
├── src/                        # Spring Boot Java application source
├── k8s/                        # Kubernetes manifests (Deployment, Service)
├── Dockerfile                  # Docker image build instructions
├── Jenkinsfile                 # Jenkins declarative pipeline
└── pom.xml                     # Maven build configuration
```

---

## 🔄 CI/CD Pipeline Flow

```
GitHub → Jenkins → Maven Build → SonarQube → Docker Build → DockerHub → Kubernetes (EKS) → AWS LoadBalancer
```

### Pipeline Stages (Jenkinsfile)

| Stage | Description |
|---|---|
| **Clone Repo** | Pulls the latest code from GitHub |
| **Build Maven** | Runs `mvn clean package` to compile and package the JAR |
| **SonarQube Analysis** | Runs `mvn sonar:sonar` for static code quality analysis |
| **Docker Build** | Builds the Docker image using the `Dockerfile` |
| **Docker Push** | Pushes the image to DockerHub |
| **Deploy to Kubernetes** | Applies all manifests in `k8s/` to AWS EKS |

---

## 🐳 Docker

The application is containerized using **OpenJDK 17 (slim)** as the base image.

```dockerfile
FROM openjdk:17-jdk-slim
WORKDIR /app
COPY target/java-devops-app-1.0.jar app.jar
EXPOSE 8080
ENTRYPOINT ["java","-jar","app.jar"]
```

**Build & run locally:**

```bash
docker build -t java-devops-app .
docker run -p 8080:8080 java-devops-app
```

---

## ☸️ Kubernetes on AWS EKS

The application is deployed to **AWS EKS** using manifests inside the `k8s/` directory.

```bash
# Apply all Kubernetes manifests
kubectl apply -f k8s/

# Check deployment status
kubectl get pods
kubectl get svc
```

The service is exposed via an **AWS LoadBalancer** (`type: LoadBalancer`) to make the application publicly accessible.

---

## ⚙️ Application

- **Framework:** Spring Boot 3.1
- **Language:** Java 17
- **Artifact:** `java-devops-app-1.0.jar`
- **Port:** `8080`
- **Group ID:** `com.devops`

**Build the JAR:**

```bash
mvn clean package
```

---

## 🚀 Getting Started

### Prerequisites

- Java 17
- Maven
- Docker
- kubectl configured with AWS EKS
- Jenkins server with SonarQube integration

### Run the Pipeline

1. Push code to GitHub
2. Jenkins pipeline triggers automatically
3. Maven builds the JAR
4. SonarQube performs code quality analysis
5. Docker image is built and pushed to DockerHub
6. Kubernetes deploys the app to AWS EKS
7. Application is accessible via AWS LoadBalancer

---

## 📄 License

This is a practice project built for learning DevOps concepts. Open for reference and educational use.
