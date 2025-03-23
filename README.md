# K8s-MongoDB

## Overview

This project demonstrates how to deploy a MongoDB database and a Mongo Express web-based MongoDB admin interface on a Kubernetes cluster. It uses Kubernetes resources such as Secrets, ConfigMaps, Deployments, and Services to manage the application.

## Prerequisites

- A Kubernetes cluster (e.g., Minikube, GKE, EKS, etc.)
- `kubectl` CLI installed and configured
- `minikube` CLI (if using Minikube)

## Files in the Repository

- **mongo-secret.yaml**: Contains the Kubernetes Secret for MongoDB credentials.
- **mongo.yaml**: Defines the MongoDB Deployment and Service.
- **mongo-configmap.yaml**: Contains the ConfigMap for MongoDB configuration.
- **mongo-express.yaml**: Defines the Mongo Express Deployment and Service.

## Deployment Steps

1. Clone the repository:
    ```bash
    git clone https://github.com/your-repo/K8s-MongoDB.git
    cd K8s-MongoDB
    ```

2. Apply the Kubernetes manifests in the specified order:
    ```bash
    kubectl apply -f mongo-secret.yaml
    kubectl apply -f mongo.yaml
    kubectl apply -f mongo-configmap.yaml
    kubectl apply -f mongo-express.yaml
    ```

3. Verify the resources:
    ```bash
    kubectl get all
    ```

4. Access the Mongo Express interface:
    - If using Minikube, run:
        ```bash
        minikube service mongo-express-service
        ```
    - For other environments, expose the service externally and use the provided URL.

## Notes

- Ensure the `mongo-secret.yaml` file contains the correct MongoDB username and password.
- Modify the `mongo-configmap.yaml` file to customize MongoDB configurations as needed.
- The `mongo-express.yaml` file is configured to connect to the MongoDB service using the credentials stored in the Secret.

## Cleanup

To delete all resources created by this project, run:
```bash
kubectl delete -f mongo-express.yaml
kubectl delete -f mongo-configmap.yaml
kubectl delete -f mongo.yaml
kubectl delete -f mongo-secret.yaml
```