# Setting up Prometheus and Grafana in Minikube Cluster

This guide will help you set up Prometheus and Grafana in your Minikube cluster using Helm.

## Prerequisites

Make sure you have the following prerequisites installed:
- Minikube
- Helm 3

## Steps

### 1. Remove Docker (Optional)

If you already have Docker installed and want to remove it, you can use the following commands:

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
### 2. install Docker
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
### 3. Install Minikube

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
### 4. Install Helm
```bash
curl -fsSL -o get_helm.sh https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3
chmod 700 get_helm.sh
./get_helm.sh
```
### 5. Install kubectl 

1.Download the latest release with the command:
```bash
    curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
```

2.Install kubectl
```bash
    sudo install -o root -g root -m 0755 kubectl /usr/local/bin/kubectl
```

### 6. Add Prometheus Helm Repository
```bash
helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
```
### 7. Install Prometheus
```bash
helm install prometheus prometheus-community/prometheus
```
### 8. Expose Prometheus Service
```bash
kubectl expose service prometheus-server --type=NodePort --target-port=9090 --name=prometheus-server-np
```
### 9. Add Grafana Helm Repository
```bash
helm repo add grafana https://grafana.github.io/helm-charts
```
### 10. Install Grafana
```bash
helm install grafana grafana/grafana
```
### 11. Expose Grafana Service
```bash
kubectl expose service grafana --type=NodePort --target-port=3000 --name=grafana-np
```
### Conclusion
![Screenshot 2024-05-02 021630](https://github.com/amr-elshawarby/monitor-Kubernetes-cluster-/assets/161210166/5270bf4a-d235-48f1-935c-0eec7100dec1)
![Screenshot 2024-05-02 021909](https://github.com/amr-elshawarby/monitor-Kubernetes-cluster-/assets/161210166/b856a07c-2bfc-4258-9d36-3e79458318ff)
![Screenshot 2024-05-02 023710](https://github.com/amr-elshawarby/monitor-Kubernetes-cluster-/assets/161210166/f11a7c52-77e8-4f51-aaa0-e2b1bfb44341)
![Screenshot 2024-05-02 024723](https://github.com/amr-elshawarby/monitor-Kubernetes-cluster-/assets/161210166/3dd534e9-d0b9-4776-aab6-cb22a0ccf28b)






