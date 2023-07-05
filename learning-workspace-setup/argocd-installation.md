# ArgoCD installation
![ez logo](/resources/images/ez/ez-smiley-small-logo.png)

## install ArgoCD instance on Kubernetes
(based on this page: https://argo-cd.readthedocs.io/en/stable/getting_started/)

### Requirements
- Installed kubectl command-line tool.
- Connected to a Kubernetes cluster - Have a kubeconfig file (default location is ~/.kube/config).
 
### Install Argo CD
```
kubectl create namespace argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
```
This will create a new namespace, argocd, where Argo CD services and application resources will live.
