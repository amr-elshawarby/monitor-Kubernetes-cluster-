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
