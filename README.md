# EKS and Monitoring with OpenTelemetry

## Overview
This project demonstrates the deployment of a scalable, fault-tolerant application on AWS Elastic Kubernetes Service (EKS) using modern DevOps practices. The project incorporates Docker, Kubernetes, Helm, Grafana dashboards, alerting services, and CI/CD pipelines to automate the software lifecycle and ensure robust application management.

## Table of Contents
- [Project Structure](#project-structure)
- [Technologies Used](#technologies-used)
- [Features](#features)
- [Phases](#phases)
  - [Phase 1: Environment and Initial Application Setup](#phase-1-environment-and-initial-application-setup)
  - [Phase 2: YAML Splitting and Modular Deployment](#phase-2-yaml-splitting-and-modular-deployment)
  - [Phase 3: Integrating Helm for Deployment](#phase-3-integrating-helm-for-deployment)
  - [Phase 4: Customizing Grafana Dashboards for EKS Monitoring](#phase-4-customizing-grafana-dashboards-for-eks-monitoring)
  - [Phase 5: Alerting Service and Notifications](#phase-5-alerting-service-and-notifications)
  - [Phase 6: CI/CD Integration](#phase-6-cicd-integration)
- [How to Run](#how-to-run)
- [References](#references)

---

## Project Structure
The repository is structured as follows:
```
project-root/
├── docker-compose.yaml    # Docker setup
├── kubernetes/            # Split YAML files for Kubernetes
│   ├── configmaps/
│   ├── deployments/
│   ├── secrets/
│   ├── services/
│   └── others/
├── helm/                  # Helm charts
├── monitoring/            # Grafana and Prometheus configurations
└── cicd/                  # CI/CD pipeline files
```

---

## Technologies Used
- **AWS EKS**: Elastic Kubernetes Service for managing Kubernetes clusters.
- **Docker**: Containerization platform for application packaging.
- **Kubernetes**: Orchestration of containerized applications.
- **Helm**: Package manager for Kubernetes resources.
- **Prometheus & Grafana**: Monitoring and alerting systems.
- **GitHub Actions**: CI/CD pipeline automation.
- **AWS SES**: Email notification service for alerts.

---

## Features
- Scalable Kubernetes deployments on AWS EKS.
- Modular YAML files for better resource management.
- Helm charts for simplified deployment and rollback.
- Customized Grafana dashboards for EKS monitoring.
- Alerting mechanisms for critical metrics.
- Fully automated CI/CD pipelines for builds, tests, and deployments.

---

## Phases

### Phase 1: Environment and Initial Application Setup
- **Docker Setup**: Deployed the OpenTelemetry demo application using `docker-compose.yaml` on a dedicated EC2 instance.
- **Kubernetes Setup**: Configured an EKS cluster with at least 2 worker nodes and deployed the application using the `opentelemetry-demo.yaml` manifest.
- **Deliverables**:
  - Docker and Kubernetes logs.
  - Screenshots of running services and accessible endpoints.

### Phase 2: YAML Splitting and Modular Deployment
- Split the monolithic YAML file into smaller, service-specific files (e.g., ConfigMaps, Deployments, Services).
- Applied the resources recursively for efficient deployment.
- **Deliverables**:
  - Organized YAML files in a clear folder structure.
  - A ZIP file containing the split YAML files.

### Phase 3: Integrating Helm for Deployment
- Deployed the application using pre-configured Helm charts from the OpenTelemetry Helm repository.
- Tested Helm's upgrade and rollback features to ensure application stability.
- **Deliverables**:
  - Screenshots of successful Helm deployments, upgrades, and rollbacks.

### Phase 4: Customizing Grafana Dashboards for EKS Monitoring
- Customized Grafana dashboards to monitor:
  - Cluster health (node status, CPU/memory usage).
  - Pod performance (restarts, memory consumption).
  - Network and storage metrics.
- Set up alerts for critical metrics and validated them with simulated traffic.
- **Deliverables**:
  - Grafana screenshots of dashboards and alerts.
  - JSON exports of custom dashboards (optional).

### Phase 5: Alerting Service and Notifications
- Configured Prometheus to monitor pod restart counts and trigger alerts.
- Integrated AWS SES to send email notifications for alerts.
- **Deliverables**:
  - Alerting rules and configurations.
  - Screenshots of email notifications.

### Phase 6: CI/CD Integration
- Automated build, test, and deployment processes using GitHub Actions.
- Integrated a rollback mechanism to ensure stability during deployment failures.
- **Deliverables**:
  - CI/CD pipeline configuration files.
  - Logs/screenshots of successful builds, tests, and deployments.

---

## How to Run
### Prerequisites
- AWS account with IAM permissions for EKS, EC2, and SES.
- Tools installed on the client machine:
  - AWS CLI
  - kubectl
  - Docker
  - eksctl

### Steps
1. **Clone the Repository**:
   ```bash
   git clone https://github.com/your-repo/eks-monitoring-opentelemetry.git
   cd eks-monitoring-opentelemetry
   ```
2. **Set Up the Environment**:
   - Create an EKS cluster using `eksctl` or AWS Management Console.
   - Configure Docker and Kubernetes as described in Phase 1.
3. **Deploy Using Helm**:
   ```bash
   helm repo add opentelemetry https://open-telemetry.github.io/opentelemetry-helm-charts
   helm install otel-app opentelemetry/opentelemetry-demo -n otel-demo
   ```
4. **Set Up Monitoring**:
   - Apply Prometheus and Grafana configurations from the `monitoring/` folder.
   - Access Grafana at `http://<grafana-endpoint>` and import custom dashboards.
5. **Run CI/CD Pipeline**:
   - Push code changes to trigger GitHub Actions.
   - Verify successful builds, tests, and deployments in the logs.

---

## References
- [AWS EKS Documentation](https://docs.aws.amazon.com/eks/)
- [OpenTelemetry Helm Charts](https://open-telemetry.github.io/opentelemetry-helm-charts)
- [Prometheus Documentation](https://prometheus.io/docs/)
- [Grafana Documentation](https://grafana.com/docs/)
- [GitHub Actions Documentation](https://docs.github.com/en/actions)

---

For more details, check the full project report in the repository.
