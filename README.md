# Liatrio Bootcamp - 7.5 Webhooks

## Webhooks in Kubernetes

### Setup

This project is for setting up a basic Kubernetes validating Admission
Controller using python.

Steps to deploy and test this admission controller.

1. Deploy a KIND cluster with Admission Controller enabled

   ```bash
   kind create cluster --config kind.yaml
   ```

2. Install cert-manager

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

3. Create the validation namespace, the root CA, and self signed certificate.
    ```
    kubectl apply -f certs.yaml
    ```

4. Get the base64 value of the ca.crt file in the secret
    ``` 
    CA=`kubectl -n validation get secret validation-ca-tls -o jsonpath='{.data.ca\.crt}'` 
    ```

### Validating Webhooks

### Mutating Webhooks