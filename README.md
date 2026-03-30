# CloudMart — AI-Integrated Multi-Cloud E-Commerce Platform

[![AWS](https://img.shields.io/badge/AWS-EKS%20%7C%20DynamoDB%20%7C%20Bedrock%20%7C%20Lambda-FF9900?logo=amazonaws&logoColor=white)](https://aws.amazon.com)
[![OpenAI](https://img.shields.io/badge/OpenAI-GPT--4o-412991?logo=openai&logoColor=white)](https://openai.com)
[![Azure](https://img.shields.io/badge/Azure-AI%20Language-0078D4?logo=microsoftazure&logoColor=white)](https://azure.microsoft.com)
[![Google Cloud](https://img.shields.io/badge/Google%20Cloud-BigQuery-4285F4?logo=googlecloud&logoColor=white)](https://cloud.google.com)
[![Terraform](https://img.shields.io/badge/Terraform-Infrastructure%20as%20Code-7B42BC?logo=terraform&logoColor=white)](https://terraform.io)
[![Kubernetes](https://img.shields.io/badge/Kubernetes-EKS-326CE5?logo=kubernetes&logoColor=white)](https://kubernetes.io)

CloudMart is a production-grade e-commerce prototype that demonstrates how modern AI capabilities and multi-cloud infrastructure work together in a single, unified application. Built during graduate research at the University of Maryland, it serves as a hands-on reference for integrating generative AI, automated CI/CD pipelines, and cross-cloud data engineering.

---

## Architecture Overview

cloudmart_architecture_diagram.svg

---

## Features

### AI Capabilities

| Feature | Provider | Model | Purpose |
|---|---|---|---|
| Product Recommendations | Amazon Bedrock | Claude 3 Sonnet | Conversational product discovery with live catalog queries |
| Customer Support | OpenAI | GPT-4o | Handles general customer service and platform questions |
| Sentiment Analysis | Microsoft Azure | Azure AI Language | Classifies customer conversations as positive, neutral, or negative |

### Infrastructure & DevOps

- **Kubernetes on EKS** — Frontend and backend deployed as separate containerized pods with LoadBalancer services
- **CI/CD Pipeline** — GitHub → CodePipeline → CodeBuild → ECR → EKS. Zero-touch deployments on every push
- **Infrastructure as Code** — All AWS resources (DynamoDB, Lambda, IAM roles, EKS configuration) defined in Terraform
- **Real-time Data Streaming** — DynamoDB Streams → Lambda → Google BigQuery for live order analytics

---

## Tech Stack

### AWS Services
- **EKS (Elastic Kubernetes Service)** — Container orchestration for frontend and backend
- **DynamoDB** — NoSQL database for products, orders, and support tickets
- **Lambda** — Serverless functions for product catalog queries (Bedrock agent) and BigQuery streaming
- **Bedrock** — Managed generative AI service hosting the Claude 3 Sonnet recommendation agent
- **ECR (Elastic Container Registry)** — Docker image storage
- **CodePipeline + CodeBuild** — CI/CD automation
- **S3** — Static asset storage
- **IAM** — Role-based access control for all services

### Application
- **Frontend** — React (Vite), served on port 5001
- **Backend** — Node.js (Express), running on port 5000
- **Containerization** — Docker, with multi-stage builds for the frontend

### AI & External Services
- **Amazon Bedrock** — Hosts the Claude 3 Sonnet recommendation agent with a custom action group connected to Lambda
- **OpenAI API** — GPT-4o assistant for customer support, configured with CloudMart-specific instructions
- **Azure AI Language** — Sentiment analysis API integrated into the support chat pipeline
- **Google BigQuery** — Serverless analytics warehouse receiving real-time order streams

### Infrastructure as Code
- **Terraform** — Provisions DynamoDB tables, Lambda functions, IAM roles, Lambda event source mappings, and Bedrock agent permissions

---

## Project Structure

```
cloudmart/
├── terraform-project/
│   └── main.tf                    # All AWS infrastructure
├── challenge-day2/
│   ├── backend/
│   │   ├── Dockerfile
│   │   ├── cloudmart-backend.yaml  # Kubernetes deployment
│   │   ├── .env                    # Runtime config (Bedrock, OpenAI, Azure)
│   │   └── src/
│   │       └── lambda/
│   │           ├── list_products/  # Lambda for Bedrock agent
│   │           └── addToBigQuery/  # Lambda for DynamoDB → BigQuery stream
│   └── frontend/
│       ├── Dockerfile
│       ├── cloudmart-frontend.yaml # Kubernetes deployment
│       └── .env                    # VITE_API_BASE_URL
```

---

## How It Works

### Product Recommendation Flow

1. Customer opens the recommendation chat on the CloudMart storefront
2. The frontend sends the message to the Node.js backend
3. The backend calls the Amazon Bedrock agent (Claude 3 Sonnet)
4. The Bedrock agent invokes a Lambda function to query DynamoDB for live product data
5. Claude synthesizes the results and returns a personalized recommendation
6. The customer sees a conversational, context-aware response

### CI/CD Deployment Flow

1. Developer pushes code to the `cloudmart` GitHub repository
2. AWS CodePipeline detects the change and triggers a build
3. CodeBuild builds a Docker image using the project Dockerfile
4. The image is tagged and pushed to Amazon ECR
5. CodeBuild runs `kubectl apply` to deploy the new image to EKS
6. Kubernetes performs a rolling update — zero downtime

### Real-time Order Streaming

1. A customer places an order, which is written to the DynamoDB `cloudmart-orders` table
2. DynamoDB Streams captures the new record and triggers the `dynamodb-to-bigquery` Lambda function
3. The Lambda function authenticates to Google Cloud using a service account and writes the record to BigQuery
4. The data is immediately available for analytics queries in BigQuery

---

## Environment Variables

### Backend (`.env`)

```env
PORT=5000
AWS_REGION=us-east-1
BEDROCK_AGENT_ID=<your-bedrock-agent-id>
BEDROCK_AGENT_ALIAS_ID=<your-bedrock-agent-alias-id>
OPENAI_API_KEY=<your-openai-api-key>
OPENAI_ASSISTANT_ID=<your-openai-assistant-id>
AZURE_ENDPOINT=<your-azure-endpoint>
AZURE_API_KEY=<your-azure-api-key>
```

### Frontend (`.env`)

```env
VITE_API_BASE_URL=http://<kubernetes-backend-loadbalancer-url>:5000/api
```

---

## Setup & Deployment

### Prerequisites

- AWS account with CLI configured
- Terraform installed
- Docker installed
- `kubectl` and `eksctl` installed
- Google Cloud project with BigQuery enabled
- Azure account with Text Analytics resource
- OpenAI account with API key

### 1. Provision Infrastructure with Terraform

```bash
cd terraform-project
terraform init
terraform apply
```

This creates DynamoDB tables, Lambda functions, IAM roles, and Lambda event source mappings.

### 2. Create the EKS Cluster

```bash
eksctl create cluster \
  --name cloudmart \
  --region us-east-1 \
  --nodegroup-name standard-workers \
  --node-type t3.medium \
  --nodes 1 \
  --with-oidc \
  --managed

aws eks update-kubeconfig --name cloudmart
```

### 3. Configure the Amazon Bedrock Agent

- Enable Claude 3 Sonnet model access in the Bedrock console
- Create an agent named `cloudmart-product-recommendation-agent`
- Attach the `Get-Product-Recommendations` action group connected to the `cloudmart-list-products` Lambda function
- Create an alias named `cloudmart-prod`
- Note the Agent ID and Alias ID for backend configuration

### 4. Configure OpenAI Assistant

- Create a new assistant in the OpenAI platform with model `gpt-4o`
- Name it `CloudMart Customer Support`
- Configure instructions to handle CloudMart-specific support scenarios
- Note the Assistant ID and generate an API key

### 5. Set Up Azure Sentiment Analysis

- Create a Text Analytics resource in Azure
- Note the endpoint URL and API key

### 6. Build and Deploy Backend

```bash
cd challenge-day2/backend

# Build and push to ECR (follow ECR push commands from AWS console)
docker build -t cloudmart-backend .
# tag and push...

# Update cloudmart-backend.yaml with your Bedrock, OpenAI, and Azure credentials
kubectl apply -f cloudmart-backend.yaml
kubectl get service cloudmart-backend-app-service  # note the external URL
```

### 7. Build and Deploy Frontend

```bash
cd challenge-day2/frontend

# Update .env with the backend service URL from step 6
echo "VITE_API_BASE_URL=http://<backend-url>:5000/api" > .env

# Build and push to ECR, then deploy
kubectl apply -f cloudmart-frontend.yaml
kubectl get service cloudmart-frontend-app-service  # your app URL
```

### 8. Set Up CI/CD Pipeline

- Push your code to a GitHub repository named `cloudmart`
- In AWS CodePipeline, create `cloudmart-cicd-pipeline` connected to your GitHub repo
- Create a CodeBuild project `cloudmartBuild` with the provided `buildspec.yml`
- Create a deployment CodeBuild project `cloudmartDeployToProduction` with deploy `buildspec.yml`

---

## Teardown

To avoid ongoing AWS charges:

```bash
# Delete Kubernetes resources
kubectl delete -f cloudmart-frontend.yaml
kubectl delete -f cloudmart-backend.yaml

# Delete EKS cluster
eksctl delete cluster --name cloudmart --region us-east-1

# Destroy Terraform-managed resources
cd terraform-project
terraform destroy
```

---

## Key Learnings

This project demonstrates several cross-domain concepts in a single working system:

- **Agentic AI** — How a Bedrock agent with an action group can query live data and make decisions within a conversation
- **Multi-cloud integration** — How AWS, Azure, Google Cloud, and OpenAI services can be composed into one application without vendor lock-in
- **Event-driven streaming** — How DynamoDB Streams and Lambda enable real-time data movement without batch jobs
- **GitOps / CI/CD** — How a single `git push` can trigger a complete build and deployment pipeline
- **Infrastructure as Code** — How Terraform enables reproducible, version-controlled cloud infrastructure

---

## Acknowledgements

Developed as part of graduate-level research and coursework at the **University of Maryland, College Park** (Master of Science in Information Systems). This project was designed to serve as a practical, production-grade reference for students learning cloud architecture, DevOps, and AI integration.

---

## License

MIT
