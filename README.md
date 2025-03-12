# My Web App - Helm Chart

This repository contains a Helm chart for deploying a simple Nginx-based web application using a custom Docker image: `belalelnady/simple-app`.

## Repository Structure

```
Simple-helm-chart/
├── charts/                # (Optional) Directory for dependencies or subcharts
├── Chart.yaml             # Helm chart metadata
├── templates/             # Kubernetes manifest templates
│   ├── deployment.yml     # Defines the Deployment resource
│   ├── service.yml        # Defines the Service resource
├── values.yaml            # Default values for the Helm chart
```

## Prerequisites

Ensure you have the following installed:
- [Helm](https://helm.sh/docs/intro/install/)
- [Kubernetes](https://kubernetes.io/) cluster (Minikube, DigitalOcean, AWS EKS, etc.)

## Installation

### Add and Update Dependencies
If your chart has dependencies, update them using:
```sh
helm dependency update Simple-helm-chart
```

### Install the Chart
To deploy the application using Helm, run:
```sh
helm install Simple-helm-chart ./Simple-helm-chart
```

This will create the necessary Kubernetes resources using the values defined in `values.yaml`.

## Configuration

Modify `values.yaml` to customize the deployment. Common configurations include:
- **Replica Count**: Adjust the number of application replicas.
- **Image Settings**: Change the image repository and tag if needed.
- **Service Type**: Set the service type to `ClusterIP`, `NodePort`, or `LoadBalancer`.

To override values at installation time:
```sh
helm install Simple-helm-chart ./Simple-helm-chart --set replicaCount=3
```

## Upgrading the Chart
To upgrade an existing release:
```sh
helm upgrade Simple-helm-chart ./Simple-helm-chart
```

## Uninstallation
To remove the deployed application:
```sh
helm uninstall Simple-helm-chart
```
