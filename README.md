# 7.5 Webhooks

## Webhooks in Kubernetes

### Setup

This project is for setting up a basic Kubernetes validating Admission
Controller using python.

Steps to deploy and test this admission controller.

1. Deploy a KIND cluster with Admission Controller enabled

   ```bash
   kind create cluster --config kind.yaml
   ```

1. Install cert-manager

   ```bash
   # Add the Jetstack Helm repository
   helm repo add jetstack https://charts.jetstack.io

   # Update your local Helm chart repository cache
   helm repo update

   # Install the cert-manager Helm chart (including cert-manager CRDs)
   helm install cert-manager \
   --namespace cert-manager \
   --create-namespace \
   --set installCRDs=true \
   --version v1.6.1 \
   jetstack/cert-manager
   ```

### Validating Webhooks

### Mutating Webhooks