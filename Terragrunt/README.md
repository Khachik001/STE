# Terraform/Terragrunt Infrastructure Deployment Project

Welcome to our Terraform and Terragrunt project for deploying a comprehensive AWS infrastructure stack and Kubernetes cluster for your applications. This project automates the setup of essential components, including a Virtual Private Cloud (VPC), Amazon Elastic Container Registry (ECR), Amazon Elastic Kubernetes Service (EKS), Ingress controller, Argo CD, and an application with an image updater.

## Getting Started

Before you begin, please review the prerequisites and ensure you have the necessary tools and access. Follow the step-by-step instructions to create your infrastructure and deploy your applications.

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
```
### Step 3: Define AWS Region

In this step, you'll specify the AWS region you intend to use for your project. We'll configure this in the Terragrunt configuration for the `dev` environment.

1. Navigate to the `project/environments/dev/` directory in your project.

2. Open the `region.hcl` file using a text editor.

3. In the `region.hcl` file, you'll see the following content:

   ```hcl
   locals {
     aws_region = "us-east-1" # Replace with your desired AWS region
   }
   ```
### Step 4: Configure Environment Variables for `us-east-1` (Dev Environment)

In this step, you will configure environment-specific variables for the `dev` environment in the `us-east-1` region using the `env.hcl` file.

1. Navigate to the `project/environments/dev/us-east-1/` directory in your project.

2. Locate the `env.hcl` file.

3. Open the `env.hcl` file using a text editor.

4. In the `env.hcl` file, define your environment-specific variables.
    
# Understanding Modules, Inputs, and Default Values
<br> 

## VPC Module 

The VPC (Virtual Private Cloud) module in this project provides a flexible and customizable way to define the network infrastructure for your AWS resources. This documentation outlines the key details and input variables for the VPC module.

### Module Details

| Detail           | Description                                       |
|------------------|---------------------------------------------------|
| **Module Name**  | `vpc`                                             |
| **Source**       | `./modules/vpc`                                  |
| **Purpose**      | Creates a Virtual Private Cloud (VPC) on AWS.    |
| **Dependencies** | None (standalone module).                        |

### Input Variables

The following table lists the input variables that you can customize when using the VPC module. These variables allow you to tailor the VPC configuration to your specific requirements:

| Variable Name          | Type     | Default Value       | Description                                                                                      |
|------------------------|----------|----------------------|--------------------------------------------------------------------------------------------------|
| `vpc_cidr`             | String   | "10.10.0.0/16"       | The IP address range for the VPC, specified in CIDR notation with a `/16` prefix. Please ensure that you define the value with the `/16` prefix. The VPC will automatically create 2 public and 2 private subnets, each with a `/24` CIDR range. Customize to your desired `/16` CIDR range.  |
| `vpc_name`             | String   | "intern_vpc"      | The name of the VPC. Provide a meaningful name for easy identification within your environment. |
| `enable_dns_support`   | Bool     | true               | Enable or disable DNS resolution support within the VPC.                                      |
| `enable_dns_hostnames` | Bool     | true               | Enable or disable DNS hostnames within the VPC.                                               |
| `enable_nat_gateway`   | Bool     | true               | Enable or disable the creation of NAT gateways for private subnets.                            |
| `single_nat_gateway`   | Bool     | true               | Use a single NAT gateway for all private subnets (when `enable_nat_gateway` is `true`).         |
| `one_nat_gateway_per_az`| Bool    | false              | Create one NAT gateway per availability zone (AZ) for private subnets (when `enable_nat_gateway` is `true`). |

### Outputs

The VPC module provides the following outputs:

| Output Name        | Description                                       |
|--------------------|---------------------------------------------------|
| `vpc_id`           | The ID of the created VPC.                       |
| `private_subnets`  | A list of private subnet IDs within the VPC.     |


<br> <br> <br>

## ECR Module 

The ECR (Elastic Container Registry) module in this project allows you to create and manage Docker container image repositories on AWS. This documentation outlines the key details and input variables for the ECR module.

### Module Details

| Detail           | Description                                       |
|------------------|---------------------------------------------------|
| **Module Name**  | `ecr`                                             |
| **Source**       | `./modules/ecr`                                  |
| **Purpose**      | Creates an Elastic Container Registry (ECR) repository on AWS. |
| **Dependencies** | None (standalone module).                        |

### Input Variables

| Variable Name    | Type   | Default Value | Description                                                                                   |
|------------------|--------|----------------|-----------------------------------------------------------------------------------------------|
| `ecr_repo_name`  | String | "test_ecr" | The name of the ECR repository. Customize this value to specify a unique name for your repository. |

<br> <br> <br>   

## EKS Module 

The EKS (Amazon Elastic Kubernetes Service) module in this project allows you to create and manage Kubernetes clusters on AWS. This documentation outlines the key details, input variables, and dependencies for the EKS module.

### Module Details

| Detail           | Description                                       |
|------------------|---------------------------------------------------|
| **Module Name**  | `eks`                                             |
| **Source**       | `./modules/eks`                                  |
| **Purpose**      | Creates an Amazon EKS cluster on AWS.            |
| **Dependencies** | Requires a VPC configuration as defined in the VPC module. |

### Input Variables

The following table lists the input variables that you can customize when using the EKS module. These variables allow you to configure the EKS cluster to suit your project's requirements:

| Variable Name    | Type             | Default Value | Description                                                                                   |
|------------------|------------------|----------------|-----------------------------------------------------------------------------------------------|
| `vpc_id`         | String           | - (Required)   | The ID of the VPC where the EKS cluster should be created.                                 |
| `private_subnets`| List of Strings  | - (Required)   | A list of private subnet IDs where the EKS worker nodes should be launched.                |
| `min_size`       | Number           | 2              | Minimum size of the worker node group.                                                        |
| `max_size`       | Number           | 3              | Maximum size of the worker node group.                                                        |
| `desired_size`   | Number           | 2              | Desired size of the worker node group.                                                        |
| `cluster_name`   | String           | "intern_eks"   | Name of the EKS Cluster. Must be between 1-100 characters in length and follow naming conventions. |
| `instance_types` | List of Strings  | ["t3.small"]   | List of instance types associated with the EKS Node Group.                                   |

### Output 

The EKS module provides the following output:

| Output Name    | Description                            |
|----------------|----------------------------------------|
| `cluster_name` | The name of the created EKS Cluster.  |

<br> <br> <br> 

## Ingress Controller Module 
The Ingress Controller module in this project simplifies the setup of an Ingress Controller within your Amazon EKS (Elastic Kubernetes Service) cluster. This documentation outlines the key details, input variables, and dependencies for the Ingress Controller module.

### Module Details

| Detail           | Description                                       |
|------------------|---------------------------------------------------|
| **Module Name**  | `ingress`                                         |
| **Source**       | `./modules/ingress`                              |
| **Purpose**      | Sets up an Ingress Controller within an EKS cluster to manage external traffic routing to services. |
| **Dependencies** | Depends on an existing EKS cluster as defined in the EKS module. |                       |

### Input Variables

The following table lists the input variables that you can customize when using the Ingress Controller module. These variables allow you to configure the Ingress Controller to work with your EKS cluster:

| Variable Name    | Type   |         Default Value                | Description                                                                                   |
|------------------|--------|---------------------------|-----------------------------------------------------------------------------------------------|
| `cluster_name`   | String |         - (Required)        |The name of the EKS Cluster where the Ingress Controller should be deployed.    |

<br><br><br>
## Argo CD Module

The Argo CD module in this project simplifies the setup of Argo CD, a GitOps continuous delivery tool, within your Amazon EKS (Elastic Kubernetes Service) cluster. This documentation outlines the key details, input variables, and dependencies for the Argo CD module.

### Module Details

| Detail           | Description                                       |
|------------------|---------------------------------------------------|
| **Module Name**  | `argocd`                                         |
| **Source**       | `./modules/argocd`                              |
| **Purpose**      | Sets up Argo CD within an EKS cluster to manage deployments using GitOps. |
| **Dependencies** | Depends on an existing EKS cluster as defined in the EKS module and an Ingress Controller as defined in the Ingress module. |
| **Compatibility**| Terraform 0.12 and later.                        |

### Input Variables

The following table lists the input variables that you can customize when using the Argo CD module. These variables allow you to configure Argo CD to work with your EKS cluster and deployment workflow:

| Variable Name    | Type   | Default Value   | Description                                                                                   |
|------------------|--------|------------------|-----------------------------------------------------------------------------------------------|
| `argo_version`   | String | "v2.8.0"        | The version of Argo CD to be installed.                                                      |
| `updater_version`| String | "v0.12.2"       | The version of the Argo CD Image Updater to be installed.                                     |
| `cluster_name`   | String | - (Required)    | The name of the EKS Cluster where Argo CD should be deployed.                                 |
| `host`           | String | "argocd.example.com" | The host/domain for Argo CD.                                                           |
| `account_id`     | String | - (Required)    | Your AWS account ID.                                                                         |
| `aws_region`     | String | - (Required)    | The AWS region where your resources are deployed.                                            |
| `argo_repo`      | String | - (Required)    | The Argo CD Git repository that will be used to deploy applications.                           |
| `github_token`   | String | -              | A GitHub personal access token with sufficient permissions to access the repository.          |
| `github_name`    | String | -              | The GitHub username or organization name that owns the repository.                             |


