# DevOps Java CI/CD Pipeline Project

Pipeline Stack:
GitHub → Jenkins → SonarQube → Docker → Kubernetes → AWS EKS → Prometheus

Steps:

1. Push code to GitHub
2. Jenkins pipeline triggers
3. Maven builds Java application
4. SonarQube performs code analysis
5. Docker image is built
6. Image pushed to DockerHub
7. Kubernetes deploys application to EKS
8. Service exposed via AWS LoadBalancer

Monitoring:
Prometheus + Grafana

Author: DevOps Practice Project