## Automated GitOps Workflow

Our GitOps project is designed to automate the entire development and deployment process. Here's a simplified overview of how it works:

1. **Infrastructure as Code (IaC) with Terragrunt:** Our infrastructure is defined and managed as code using Terragrunt. GitHub Actions triggers Terragrunt to provision, update, or scale AWS resources automatically whenever changes are pushed to the repository.

2. **Docker Image Builds:** Whenever there are changes in the application code, a new Docker image is automatically built using GitHub Actions. This ensures that our application is always up to date.

3. **Amazon Elastic Container Registry (ECR):** The newly built Docker image is pushed to Amazon Elastic Container Registry (ECR). ECR provides secure and scalable storage for container images, making them readily available for deployment.

4. **Argo CD Deployment:** Argo CD, our GitOps continuous delivery tool, continuously monitors the Git repository for changes. When changes are detected, Argo CD ensures that the Kubernetes cluster matches the desired state defined in the Git repository.

5. **Helm Chart for Deployment:** We use Helm charts to define our application deployments. Argo CD leverages Helm to create deployments, manage replica sets, and handle updates seamlessly.

6. **Ingress Configuration:** Helm charts also include Ingress definitions. Argo CD deploys these Ingress resources to set up routing rules for incoming traffic, making the application accessible.

This streamlined workflow allows for automatic infrastructure provisioning, application updates, and deployment management, ensuring your system is always in the desired state and up to date.

For detailed configuration and customization options, refer to our [Documentation](link-to-documentation).
