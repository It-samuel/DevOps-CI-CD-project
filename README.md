# DevOps-CI-CD-project
Welcome to the Azure DevOps project repository! This project showcases the deployment of a microservices-based application through an end-to-end CI/CD pipeline, from scratch. Whether you're new to DevOps or have some experience, this guide will help you understand how to automate your deployments with Azure DevOps.




## Project Overview

This project involves the creation of a CI/CD pipeline for a 10-microservice application. Using Azure DevOps, we'll implement continuous integration (CI) and continuous delivery (CD) pipelines to automate building, testing, and deploying these microservices to separate development (dev) and production (prod) Kubernetes clusters.

### Key Components

- **CI/CD Pipelines**: Automate the build, test, and deployment processes for each microservice.
- **Kubernetes Clusters**: Separate clusters for dev and prod environments to manage different stages of deployment.
- **SonarQube Integration**: Quality analysis integrated into the pipeline for code quality checks.
- **Docker**: Microservices are containerized and managed through Docker, enabling consistent deployments.

## Architecture

This project uses a single CI/CD pipeline with stages that include:
1. Code Quality Check using SonarQube
2. Docker Image Build for each microservice
3. Push Docker Images to DockerHub
4. Deployment to Kubernetes Clusters (Dev and Prod)

The architecture is designed for ease of deployment, where a single pipeline deploys the application across both development and production environments.

## Prerequisites

Before you start, ensure that you have the following:

- **Azure DevOps Account**: Set up a free Azure DevOps account [here](https://azure.microsoft.com/en-us/services/devops/).
- **Azure Virtual Machine**: Used for SonarQube setup with minimum 8 GiB RAM.
- **DockerHub Account**: For pushing Docker images.
- **Kubernetes Cluster**: Two clusters (Dev and Prod) in Azure Kubernetes Service (AKS).

## Setup and Configuration

### Step 1: Set up SonarQube on an Azure VM

1. Create an Azure VM with 8 GiB RAM and install SonarQube. Use this VM as an agent in Azure DevOps.
2. Install the required plugins, such as the Community Branch Plugin, on SonarQube.

### Step 2: Configure Kubernetes Clusters

1. Create two Kubernetes clusters (Dev and Prod) on Azure Kubernetes Service (AKS).
2. These clusters will host the microservices for their respective environments.

### Step 3: Push Code to Azure Repos

1. Initialize a Git repository in Azure Repos.
2. Push the source code for the 10-microservice application to this repository.

### Step 4: Write the CI Pipeline

1. The CI pipeline includes stages to:
   - Perform code quality checks using SonarQube.
   - Build Docker images for each microservice.
   - Push the Docker images to DockerHub.

### Step 5: Write the CD Pipeline

1. Create a release pipeline in Azure DevOps.
2. Deploy the microservices to the dev Kubernetes cluster first. If successful, deploy to the prod cluster.
3. Monitor the pipeline for logs to ensure each stage completes successfully.

## Deployment Instructions

### Deploy to Development Environment

To deploy to the development environment:
1. Trigger the CI/CD pipeline.
2. Review the logs for any issues in the pipeline.

### Deploy to Production Environment

After successful deployment to the dev environment:
1. Manually promote the release to the production environment.
2. Confirm that the microservices are up and running on the prod Kubernetes cluster.

## Project Structure

```plaintext
|-- src/
|   |-- add-service/
|   |-- email-service/
|   |-- frontend-service/
|   |-- recommendation-service/
|   |-- catalog-service/
|-- Dockerfiles/
|-- deployment/
|   |-- dev/
|   |-- prod/
|-- README.md
```

- `src/`: Contains source code for each microservice.
- `Dockerfiles/`: Docker configuration files for building images.
- `deployment/`: YAML files for Kubernetes deployments, separated by environment (dev/prod).

## Pipeline Configuration

### CI Pipeline

The CI pipeline performs the following actions:
- **Code Quality Check**: Runs SonarQube analysis on the code.
- **Docker Build and Push**: Builds Docker images for each microservice and pushes them to DockerHub.

### CD Pipeline

The CD pipeline performs the following actions:
- **Dev Deployment**: Deploys the Docker images to the dev Kubernetes cluster.
- **Prod Deployment**: If the dev deployment succeeds, promotes the release to the prod cluster.

## Tools Used

- **Azure DevOps**: For CI/CD pipeline creation.
- **Kubernetes**: For container orchestration and deployment management.
- **SonarQube**: For code quality checks.
- **Docker**: For containerizing microservices.
- **DockerHub**: For storing Docker images.

## Conclusion

This project demonstrates a comprehensive setup of a DevOps CI/CD pipeline on Azure DevOps for a microservices-based application. By following the steps, you’ll be able to automate deployment across environments, ensuring code quality and consistent, scalable deployments.

Feel free to contribute to this project or reach out with any questions!
