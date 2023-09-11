# Terraform/Terragrunt Infrastructure Deployment Project

Welcome to our Terraform and Terragrunt project for deploying a comprehensive AWS infrastructure stack and Kubernetes cluster for your applications. This project automates the setup of essential components, including a Virtual Private Cloud (VPC), Amazon Elastic Container Registry (ECR), Amazon Elastic Kubernetes Service (EKS) cluster, Ingress controller, Argo CD, and an application with an image updater.

## Project Overview

In today's cloud-native world, managing infrastructure and deploying applications efficiently is crucial. This repository simplifies this process by providing infrastructure as code (IaC) templates using Terraform and Terragrunt. By following the step-by-step documentation in this README, you can easily create a well-structured, scalable, and reliable environment for your applications.

### Key Features

- **Modular Design**: We've organized our codebase into manageable modules, making it easier to understand, maintain, and scale your infrastructure.

- **GitOps Workflow**: Utilize Argo CD for GitOps automation, ensuring that your application deployments and updates are version-controlled and auditable.

- **Highly Customizable**: The Terraform variables and Terragrunt configurations allow you to adapt the infrastructure to your specific requirements.

- **Documentation**: This README provides detailed instructions on setting up and deploying your infrastructure and applications, ensuring a smooth onboarding process for your team.

## Getting Started

Before you begin, please review the prerequisites and ensure you have the necessary tools and access. Follow the step-by-step instructions to create your infrastructure and deploy your applications.

Let's get started!

## Prerequisites

Before you can deploy your infrastructure and applications using Terraform and Terragrunt, please ensure that you have the following prerequisites in place:

1. **AWS Account**: You must have access to an AWS (Amazon Web Services) account with the necessary permissions to create and manage resources such as VPCs, ECR, EKS clusters, and IAM roles. If you don't have an AWS account, you can sign up for one [here](https://aws.amazon.com/).

2. **Terraform Installation**: Terraform is used for defining and provisioning infrastructure as code. You should have Terraform installed on your local machine. You can download Terraform from the official website [here](https://www.terraform.io/downloads.html) and follow the installation instructions for your platform.

3. **Terragrunt Installation**: Terragrunt is a wrapper for Terraform that provides extra features like remote state management and configuration. You'll need Terragrunt installed as well. You can download Terragrunt from the official GitHub repository [here](https://github.com/gruntwork-io/terragrunt#install-terragrunt) and follow the installation instructions.

4. **AWS CLI (Command Line Interface)**: The AWS CLI is essential for configuring AWS credentials and interacting with your AWS account from the command line. If you haven't installed the AWS CLI, you can find installation instructions for various platforms [here](https://aws.amazon.com/cli/).

5. **Git**: You'll need Git to clone this repository and manage your project code. If Git is not already installed on your system, you can download it from the official website [here](https://git-scm.com/downloads) and follow the installation instructions.

Once you have these prerequisites in place, you'll be ready to set up your environment and deploy your infrastructure and applications following the instructions provided in this README.

## Configuration Steps

### Step 1: AWS CLI Configuration

Configure the AWS CLI by running `aws configure` in your terminal and providing your AWS Access Key ID, Secret Access Key, default region, and output format. These credentials are essential for interacting with your AWS account and are securely stored on your system, enabling you to deploy resources using Terraform and Terragrunt.

### Step 2: Clone the Git Repository
To clone this Git repository, run the following command:

```bash
git clone https://github.com/intern0001/intern.git






