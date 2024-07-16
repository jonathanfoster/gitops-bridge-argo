# GitOps Bridge

## Getting Started

### 1. Create Local Cluster

```bash
kind create cluster --name=gitops-bridge
```

### 2. Install Argo CD

```bash
kubectl create namespace argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
```

### 3. Install Add-Ons

```bash
kubectl apply -n argocd -f clusters/local/add-ons.yaml
```

## Accessing the Argo CD Server

### 1. Expose the Argo CD Server

```bash
kubectl port-forward svc/argocd-server -n argocd 8080:443
```

The API server can be accessed at <https://localhost:8080>.

### 2. Login to the Argo CD Server

Get the admin password.

```bash
kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d && echo
```
