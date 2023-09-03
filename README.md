## 🚀 Automated GitOps Workflow in Action

Welcome to the heart of our GitOps project, where automation unfolds like a well-orchestrated symphony. This section provides an insightful look into the mechanics of our automated GitOps workflow and the roles played by key components.

### 🛠️ Meet the Ensemble

Allow us to introduce the ensemble cast, each performing a crucial role in our automation masterpiece:

| Technology             | Role                                                            |
|------------------------|-----------------------------------------------------------------|
| ![Terragrunt Logo](images/terragrunt.png)       | **Terragrunt - The Infrastructure Maestro**<br/>Designs and provisions AWS resources, ensuring infrastructure aligns with code.        |
| ![GitHub Actions Logo](images/github-actions.png) | **GitHub Actions - The Composer of Containers**<br/>Creates Docker images with precision, translating code changes into containerized art.   |
| ![ECR Logo](images/ecr.png)               | **Amazon Elastic Container Registry (ECR) - The Gallery of Images**<br/>Safely stores Docker images, ready to shine on the Kubernetes stage. |
| ![Argo CD Logo](images/argo-cd.png)          | **Argo CD - The Deployment Conductor**<br/>Monitors ECR for new images and orchestrates their deployment to the Kubernetes cluster using Helm charts. |
| ![Helm Logo](images/helm.png)             | **Helm Charts - The Scriptwriters**<br/>Compose intricate deployment blueprints, dictating every aspect of configuration.  |
| ![Ingress Logo](images/ingress.png)          | **Ingress - The Stage Designers**<br/>Craft access points and routing rules, an integral part of Helm charts. |
| ![New Stack Logo](images/new-stack.png)      | **New Stack - The Innovator**<br/>Introducing our latest addition, the "New Stack," which further enhances our automation prowess. |

### 📜 How to Configure

To understand how each component works and configure them to suit your needs, explore the dedicated files within their respective folders. Detailed documentation for each component is available there.

**Terragrunt**: Explore the configuration files within the Terragrunt folder to learn how to design and provision your AWS resources.

**GitHub Actions**: Navigate to the GitHub Actions folder for insights into configuring automated Docker image creation.

**ECR**: Discover image storage and management in the ECR folder.

**Argo CD**: Find out how Argo CD monitors ECR and deploys using Helm charts in the Argo CD folder.

**Helm Charts**: Dive into the Helm Charts folder to understand how to craft deployment blueprints.

**Ingress**: Explore the Ingress folder for details on setting access points and routing rules.

**New Stack**: For information on configuring and utilizing our latest addition, the "New Stack," check the New Stack folder.

### 🚀 The Result? A Symphony of Automation

This synchronized orchestration guarantees that your infrastructure and applications stay in perfect harmony with your code. Updates and deployments unfold seamlessly, promising a dependable and awe-inspiring experience for your users.

For in-depth exploration, component-specific details, and advanced techniques, please consult our comprehensive [Documentation](link-to-documentation).

Now, prepare to be captivated by the symphony of automation and precision! 🎶🌟🚀
