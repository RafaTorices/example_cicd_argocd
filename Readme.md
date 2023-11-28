## Example Manifiest File for a ArgoCD project

### Author: RafaelTorices

This is a example of a ArgoCD project manifiest file. This file is used to create a ArgoCD project and link it to a Git repository.

![Alt text](images/image.png)

## Pre-requisites

- Kubernetes cluster installed and running
- Deploy ingress controller: https://kubernetes.github.io/ingress-nginx/deploy/ in the namespace ingress-nginx of the cluster
- ArgoCD installed and running: https://argo-cd.readthedocs.io/en/stable/
- Helm installed and running: https://helm.sh/docs/intro/install/

## How to use

1.  Clone this repository
2.  Install chart of ArgoCD project:
    ```
        helm repo add argo https://argoproj.github.io/argo-helm
    ```
3.  Install ArgoCD project:
    ```
        helm upgrade --install --wait --timeout 15m --atomic --namespace argocd --create-namespace \
        --repo https://argoproj.github.io/argo-helm argocd argo-cd --values values.yaml
    ```

> This command will install a ArgoCD project in the namespace argocd and will use the values.yaml file to configure the project.

4.  Check the ArgoCD project is running:

    ```
        kubectl get pods -n argocd
    ```

5.  Access to the ArgoCD UI:
    ```
        http://localhost/argocd
    ```
