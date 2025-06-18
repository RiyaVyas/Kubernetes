To use kubernetes on your machine you need to install the following -
1. Minikube
2. Install Kubectl

| Feature              | **Minikube**                                                                      | **kubectl**                                                                                               |
| -------------------- | --------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------- |
| **Purpose**          | Creates and runs a local Kubernetes cluster                                       | Interacts with a Kubernetes cluster                                                                       |
| **Type**             | Kubernetes **cluster manager**                                                    | Kubernetes **command-line interface (CLI)**                                                               |
| **Use Case**         | To **start**, **stop**, and **manage** a Kubernetes cluster on your local machine | To **deploy**, **inspect**, and **manage** resources (pods, services, etc.) inside any Kubernetes cluster |
| **Typical Commands** | `minikube start`, `minikube stop`, `minikube dashboard`                           | `kubectl get pods`, `kubectl apply -f`, `kubectl logs`                                                    |
| **Dependency**       | Runs a Kubernetes cluster, often uses Docker or Hyper-V drivers                   | Requires a running Kubernetes cluster (can be Minikube, EKS, GKE, etc.)                                   |
| **Installation**     | Installed separately; sets up Kubernetes locally                                  | Installed separately; works with any cluster via kubeconfig                                               |
| **Platform**         | Local (primarily for testing/development)                                         | Local CLI, but connects to both local and cloud clusters                                                  |


To start your minikube cluser 
  minikube start

![image](https://github.com/user-attachments/assets/a546b523-aa7a-4058-ab29-694a1d11402f)



