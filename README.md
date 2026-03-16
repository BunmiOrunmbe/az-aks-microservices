## README.md File

# Containerized Microservices Deployment on Azure Kubernetes Service (AKS) Using Terraform

This project showcases a cloud-native microservices application deployed on Azure Kubernetes Service, built using containerization, Infrastructure-as-Code, and Kubernetes orchestration.

The environment is provisioned using Terraform, application services are packaged with Docker, and container images are stored in Azure Container Registry before being deployed to a managed Kubernetes cluster.

The architecture follows a modular microservices design where each service runs independently in Kubernetes, enabling scalability, resilience, and simplified service management.

Application Architecture

The system is structured as a three-tier microservices architecture, with each layer deployed as a containerized workload inside the Kubernetes cluster.

- **Frontend** –

A lightweight web interface served through an Nginx container, responsible for presenting the user interface and sending requests to backend services.

- **Backend** –

A Python-based REST API that handles application logic, processes requests from the frontend, and communicates with the database.

- **Database** – 

A PostgreSQL database deployed with persistent storage to maintain data durability across pod restarts and rescheduling.

## Infrastructure Components

Azure Kubernetes Service (AKS) for container orchestration
Azure Container Registry (ACR) for secure image storage
Terraform for declarative infrastructure provisioning
Docker for container build and packaging

## Deployment Guide

### Build Docker Images


docker build -t bunmiacr080.azurecr.io/frontend:v1

docker build -t bunmiacr080.azurecr.io/backend:v1

Built images
![docker image](docs/docker%20image.png)


## Push Images to Azure Container Registry


docker build -t bunmiacr080.azurecr.io/frontend:v1

docker build -t bunmiacr080.azurecr.io/backend:v1

Images in ACR
![image in acr1](docs/images%20in%20acr1.png)

![images in acr2](docs/images%20in%20acr2.png)


## Provisioned Azure Kubernetes Services (AKS) with Terraform

terraform plan
![terraform plan](docs/terraform%20plan.png)

terraform apply
![terraform apply](docs/terraform%20apply.png)

### Deploy to Kubernetes

- Apply the Kubernetes manifests in order:
- kubectl apply -f k8s/database/
- kubectl apply -f k8s/backend/
- kubectl apply -f k8s/frontend/


## AKS Nodes and Pods After deployment

kubectl get nodes and pods
![kubectl get nodes and pods](docs/kubectl-get-nodes-and-pods.png)


## Service Access

- Frontend: Exposed via LoadBalancer (External IP)
- Backend: Internal ClusterIP service
- Database: Internal ClusterIP service


Service IPs
![service ips](docs/service%20ips.png)

## Application Access

Browser image
![browser image](docs/browser%20image.png)

## Key Skills Demonstrated

- Azure Kubernetes Service (AKS)
- Azure Container Registry (ACR)
- Docker & Containerization
- Kubernetes (Deployments, Services, Namespaces)
- Infrastructure as Code with Terraform
- Microservices Architecture
- Cloud Networking & Load Balancing


## Repository Structure

```
azure-aks-microservices
├── README.md
├── backend
│   ├── Dockerfile
│   ├── app.py
│   └── requirements.txt
├── docs
│   ├── Browser image.png
│   ├── Images in ACR.png
│   ├── Screenshot 2026-02-13 113229.png
│   ├── Service IPs.png
│   ├── docker image.png
│   ├── kubectl get deployments.png
│   ├── kubectl get nodes.png
│   ├── kubectl get pods.png
│   ├── kubectl get svc.png
│   ├── terraform apply.png
│   ├── terraform plan.png
│   └── tree.png
├── frontend
│   ├── Dockerfile
│   ├── health.html
│   └── index.html
├── k8s
│   ├── backend
│   │   ├── backend-deployment.yaml
│   │   └── backend-service.yaml
│   ├── database
│   │   ├── postgres-deployment.yaml
│   │   ├── postgres-pvc.yaml
│   │   ├── postgres-secret.example.yaml
│   │   ├── postgres-secret.yaml
│   │   └── postgres-service.yaml
│   ├── frontend
│   │   ├── deployment.yaml
│   │   └── service.yaml
│   └── namespaces.yaml
└── terraform
    ├── acr.tf
    ├── main.tf
    ├── outputs.tf
    ├── provider.tf
    ├── terraform.tfstate
    ├── terraform.tfstate.backup
    ├── terraform.tfvars
    └── variables.tf


Author

Bunmi Orunmbe

Azure Cloud Engineer

Certifications

• AZ-104 – Microsoft Azure Administrator
=======
# az-aks-microservices
>>>>>>> 628ee9bde880314e2e7d77f59c9652e014b0e8b6
