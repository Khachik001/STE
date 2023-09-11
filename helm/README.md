# Helm Chart

## Introduction

This Helm chart deploys a Kubernetes Deployment, Service, and Nginx Ingress rule. It allows you to configure the number of replicas, container image details, container ports, service load balancer ports, and the desired hostname for the Ingress rule.

## Prerequisites

Before installing this Helm chart, ensure that you have the following prerequisites:

- Kubernetes cluster is set up and running.
- Helm is installed on your local machine.

# Configuration Options

This section provides detailed information about the configuration options available for the Helm chart. You can customize these options in the `values.yaml` file when installing the chart.

| Parameter               | Description                                      | Default Value   |
| ----------------------- | ------------------------------------------------ | --------------- |
| `replicaCount`          | Number of desired replicas                      | `3`             |
| `containers.image`      | Container image repository                       | `548844171305.dkr.ecr.us-east-1.amazonaws.com/private-example`         |
| `containers.tag`        | Container image tag                             | `v0.4.0`        |
| `ports.container_port`  | Container port exposed in the container         | `3000`            |
| `ports.lb_port`         | Load balancer port for the Service               | `80`            |
| `host`                  | Desired hostname for the Nginx Ingress rule     | `kub.am`   |

## Parameter Descriptions

Here are detailed descriptions of each configuration option:

### `replicaCount`

- **Description:** The number of desired replicas for the Kubernetes Deployment.

### `containers.image`

- **Description:** The container image repository for the application to be deployed.

### `containers.tag`

- **Description:** The container image tag, specifying the version of the image to be deployed.

### `ports.container_port`

- **Description:** The port exposed within the container for the application.

### `ports.lb_port`

- **Description:** The port used by the Service's load balancer to forward traffic to the containers.

### `host`

- **Description:** The desired hostname for the Nginx Ingress rule. This should be set to the domain or subdomain you want to associate with your application.

## Customizing Configuration

To customize the configuration options for this Helm chart, create a `values.yaml` file and override the default values according to your requirements. For example, to change the number of replicas and the container image, your `values.yaml` might look like this:

```yaml
replicaCount: 3
containers:
  image: my-custom-image-repo/my-app
  tag: v1.2.3

