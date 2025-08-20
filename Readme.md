# Kubernetes Starter Project

A comprehensive starter project for learning and working with Kubernetes, featuring local development setup, dashboard access, and common deployment patterns.

## 🚀 Quick Start

### Prerequisites
- Docker Desktop (Windows) or Docker Engine (Linux/macOS)
- kubectl CLI tool
- minikube

### Installation & Setup

1. **Install Docker Desktop (Windows)**
   ```bash
   # Download from: https://www.docker.com/products/docker-desktop
   # Ensure WSL2 integration is enabled
   ```

2. **Install kubectl**
   ```bash
   # Windows (using chocolatey)
   choco install kubernetes-cli
   
   # Or download directly from:
   # https://kubernetes.io/docs/tasks/tools/install-kubectl/
   ```

3. **Install minikube**
   ```bash
   # Windows (using chocolatey)
   choco install minikube
   
   # Or download from:
   # https://minikube.sigs.k8s.io/docs/start/
   ```

### Starting the Cluster

```bash
# Start minikube with CORS enabled for boot.dev
minikube start --extra-config "apiserver.cors-allowed-origins=[\"http://boot.dev\"]"

# Verify cluster is running
kubectl cluster-info

# Check nodes
kubectl get nodes
```

### Accessing Kubernetes Dashboard

```bash
# Enable dashboard addon
minikube addons enable dashboard

# Start dashboard
minikube dashboard

# Or access via proxy
kubectl proxy --address='0.0.0.0' --port=8001 --accept-hosts='.*'
```

## 🔧 Troubleshooting

### Docker Permission Issues (Linux)

If you encounter Docker permission errors:

```bash
# Add user to docker group
sudo usermod -aG docker $USER

# Apply new group membership
newgrp docker

# Verify access
docker version
```

### Connection Refused Errors

If you get connection refused errors:

1. **Check if minikube is running:**
   ```bash
   minikube status
   ```

2. **Restart minikube if needed:**
   ```bash
   minikube stop
   minikube start
   ```

3. **Verify kubectl context:**
   ```bash
   kubectl config current-context
   kubectl config use-context minikube
   ```

### Port Forwarding Issues

For services that need external access:

```bash
# Port forward a service
kubectl port-forward service/service-name 8080:80

# Or use minikube service
minikube service service-name
```

## 📁 Project Structure

```
k8s-starter/
├── manifests/           # Kubernetes YAML files
│   ├── deployments/     # Deployment configurations
│   ├── services/        # Service definitions
│   ├── configmaps/      # Configuration data
│   └── secrets/         # Secret data (gitignored)
├── scripts/             # Helper scripts
├── examples/            # Example applications
└── docs/               # Documentation
```

## 🎯 Common Commands

```bash
# View all resources
kubectl get all

# View pods with labels
kubectl get pods --show-labels

# Describe a resource
kubectl describe pod <pod-name>

# View logs
kubectl logs <pod-name>

# Execute command in pod
kubectl exec -it <pod-name> -- /bin/bash

# View events
kubectl get events --sort-by='.lastTimestamp'
```

## 🌐 Useful URLs

- **Kubernetes Dashboard**: http://localhost:8001/api/v1/namespaces/kubernetes-dashboard/services/http:kubernetes-dashboard:/proxy/
- **Minikube IP**: `minikube ip`
- **Service URLs**: `minikube service <service-name> --url`

## 📚 Learning Resources

- [Kubernetes Official Documentation](https://kubernetes.io/docs/)
- [Minikube Documentation](https://minikube.sigs.k8s.io/docs/)
- [kubectl Cheat Sheet](https://kubernetes.io/docs/reference/kubectl/cheatsheet/)

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Submit a pull request

## 📄 License

This project is licensed under the MIT License.




