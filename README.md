## Prerequisites

Before you begin, ensure you have the following:

- A Kubernetes cluster running (local or cloud-based).
- Helm 3.x installed on your local machine.
- `kubectl` configured to access your Kubernetes cluster.

## Installation

Follow these steps to install and deploy the Cosmocloud application using Helm:

1. Clone the repository:

    ```bash
    git clone https://github.com/your-repository.git
    cd your-repository
    ```

2. Install the Helm chart:

    ```bash
    helm install cosmocloud ./cosmocloud-deploy
    ```

3. Monitor the status of the deployment:

    ```bash
    kubectl get pods
    ```

4. Once the pods are running, access the frontend using the NodePort service.

    - Find the Node IP address:

    ```bash
    kubectl get nodes -o wide
    ```

    - Access the frontend by navigating to `http://<NODE_IP>:<NODE_PORT>`.

## Configuration

You can configure various parameters in the `values.yaml` file. Some key options include:

- **Frontend**: Configuration for the frontend service (Docker image, NodePort, etc.)
- **Backend**: Configuration for the backend service (Docker image, NodePort, etc.)
- **Redis**: Configuration for the Redis service (image, port, etc.)

Example configuration:

```yaml
frontend:
  image: "shreybatra/sample-frontend"
  service:
    type: NodePort
    port: 5173
    nodePort: 31000

backend:
  image: "shreybatra/sample-backend"
  service:
    type: NodePort
    port: 8080
    nodePort: 31001

redis:
  image: "redis:latest"
  service:
    type: ClusterIP
    port: 6379
