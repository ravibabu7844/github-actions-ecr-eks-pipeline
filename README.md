# 🚀 GitHub Actions CI/CD with Amazon ECR & EKS

A hands-on DevOps project demonstrating automated CI/CD using GitHub Actions, Docker, Amazon ECR, and Amazon EKS.

## 📌 Project Overview

This project demonstrates a CI/CD workflow where application code is automatically:

- Checked out from GitHub
- Built as a Docker image
- Pushed to Amazon ECR
- Deployed to Amazon EKS
- Verified using Kubernetes commands

## 🛠️ Technologies Used

- GitHub Actions
- Docker
- AWS
- Amazon ECR
- Amazon EKS
- Kubernetes
- Nginx
- Git & GitHub

## 🔄 CI/CD Flow

Developer  
↓  
GitHub Push  
↓  
GitHub Actions  
↓  
Docker Build  
↓  
Amazon ECR  
↓  
Amazon EKS  
↓  
Kubernetes Deployment  
↓  
LoadBalancer Service  
↓  
Application

## 📁 Project Structure

    github-actions-ecr-eks-pipeline/
    ├── .github/
    │   └── workflows/
    │       └── deploy.yml
    ├── Dockerfile
    ├── index.html
    ├── k8s/
    │   ├── namespace.yaml
    │   ├── deployment.yaml
    │   └── service.yaml
    └── README.md

## ⚙️ GitHub Actions Workflow

The workflow is triggered automatically whenever code is pushed to the `main` branch.

Pipeline stages:

1. Checkout source code
2. Configure AWS credentials
3. Login to Amazon ECR
4. Build Docker image
5. Tag Docker image
6. Push Docker image to ECR
7. Update EKS kubeconfig
8. Create Kubernetes namespace
9. Deploy Kubernetes resources
10. Update deployment image
11. Verify Kubernetes rollout

## 🔐 GitHub Secrets

The following GitHub repository secrets are expected:

    AWS_ACCESS_KEY_ID
    AWS_SECRET_ACCESS_KEY

AWS credentials should never be hardcoded inside the workflow file.

## 🐳 Docker

Build image locally:

    docker build -t ravi-devops-app .

Run locally:

    docker run -d -p 8080:80 ravi-devops-app

## ☸️ Kubernetes

Create namespace:

    kubectl apply -f k8s/namespace.yaml

Deploy application:

    kubectl apply -f k8s/deployment.yaml

Create service:

    kubectl apply -f k8s/service.yaml

Verify:

    kubectl get pods -n ravi-devops
    kubectl get deployments -n ravi-devops
    kubectl get svc -n ravi-devops

## ☁️ AWS Resources Required

To run this pipeline against a live AWS environment, the following resources are required:

- Amazon ECR repository
- Amazon EKS cluster
- IAM permissions for GitHub Actions
- Kubernetes access to the EKS cluster

Configured project values:

    AWS Region: ap-south-1
    ECR Repository: ravi-devops-app
    EKS Cluster: ravi-eks-cluster
    Namespace: ravi-devops

## 🔐 Security Best Practices

- AWS credentials are stored using GitHub Secrets
- Secrets are not hardcoded in source code
- Docker images use unique Git commit SHA tags
- Kubernetes workloads use a dedicated namespace
- Deployment rollout is verified after each release

## 📌 Future Improvements

- GitHub OIDC authentication instead of long-lived AWS keys
- Helm deployment
- Amazon ECR image scanning
- SonarQube integration
- Trivy container scanning
- Terraform provisioning for EKS and ECR
- Automatic rollback
- Prometheus and Grafana monitoring
- Slack deployment notifications

## 👨‍💻 Author

**Ravi Babu**  
DevOps Engineer | AWS | Kubernetes | Terraform | CI/CD
