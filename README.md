# Kubernetes Cluster Monitoring with Prometheus and Grafana

This project sets up monitoring for a Kubernetes cluster using Prometheus and Grafana.

## Prerequisites

- Docker
- Minikube
- Kubectl
- Helm

## Installation

### Docker

Remove any old versions:

```bash
sudo yum remove docker \
                  docker-client \
                  docker-client-latest \
                  docker-common \
                  docker-latest \
                  docker-latest-logrotate \
                  docker-logrotate \
                  docker-engine
```
# Install Docker

## Prerequisites

- **Operating System**: CentOS
- **Package Manager**: yum

## Installation Steps

1. Install `yum-utils` package:
    ```bash
    sudo yum install -y yum-utils
    ```

2. Add Docker repository:
    ```bash
    sudo yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo
    ```

3. Install Docker packages:
    ```bash
    sudo yum install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
    ```

4. Start Docker service:
    ```bash
    sudo systemctl start docker
    ```

# Install Minikube

## Installation Steps

1. Download Minikube binary:
    ```bash
    curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-latest.x86_64.rpm
    ```

2. Install Minikube:
    ```bash
    sudo rpm -Uvh minikube-latest.x86_64.rpm
    ```

3. Start Minikube cluster:
    ```bash
    minikube start
    ```
![Screenshot 2024-04-29 223759](https://github.com/AbdElrahmanSaaad/Kubernetes-Cluster-Monitoring-with-Prometheus-and-Grafana/assets/60901149/bf5c1fb6-f25d-4852-bc83-446bb1c57418)

# Install and Set Up kubectl

## Install kubectl binary with curl on Linux

1.Download the latest release with the command:
```bash
    curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
```

2.Install kubectl
```bash
    sudo install -o root -g root -m 0755 kubectl /usr/local/bin/kubectl
```

# Install Helm

## Installation Steps

1. Download Helm installation script:
    ```bash
    curl -fsSL -o get_helm.sh https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3
    ```

2. Provide execute permission to the script:
    ```bash
    chmod 700 get_helm.sh
    ```

3. Run the Helm installation script:
    ```bash
    ./get_helm.sh
    ```

# Deploying Prometheus and Grafana

## Deploy Prometheus

### Installation Steps

1. Add Prometheus Helm repository:
    ```bash
    helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
    ```

2. Update the Helm repositories:
    ```bash
    helm repo update
    ```

3. Install Prometheus using Helm:
    ```bash
    helm install prometheus prometheus-community/prometheus
    ```

4. Expose Prometheus service:
    ```bash
    kubectl expose service prometheus-server --type=NodePort --target-port=9090 --name=prometheus-np
    ```

## Deploy Grafana

### Installation Steps

1. Add Grafana Helm repository:
    ```bash
    helm repo add grafana https://grafana.github.io/helm-charts
    ```

2. Update the Helm repositories:
    ```bash
    helm repo update
    ```

3. Install Grafana using Helm:
    ```bash
    helm install grafana grafana/grafana
    ```

4. Expose Grafana service:
    ```bash
    kubectl expose service grafana --type=NodePort --target-port=3000 --name=grafana-np
    ```

Accessing the Services
You can access Prometheus and Grafana using the NodePort IP at ports 9090 and 3000 respectively.

"minikube ip":9090 # Prometheus

"minikube ip":3000 # Grafana

# Conclusion

Congratulations! You have successfully set up Prometheus and Grafana for monitoring your Kubernetes cluster. With Grafana deployed, you can now configure dashboards to visualize various cluster metrics and gain insights into the health and performance of your Kubernetes environment.

![Screenshot 2024-04-29 233814](https://github.com/AbdElrahmanSaaad/Kubernetes-Cluster-Monitoring-with-Prometheus-and-Grafana/assets/60901149/9e0ce84c-e9aa-4ee4-b489-6c4945287e2c)

![Screenshot 2024-04-29 234635](https://github.com/AbdElrahmanSaaad/Kubernetes-Cluster-Monitoring-with-Prometheus-and-Grafana/assets/60901149/3642d7c0-6ab8-49fe-905a-76a06141bafd)






