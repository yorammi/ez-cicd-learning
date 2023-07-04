# ez-argocd-demo
![ez logo](/resources/images/ez/ez-smiley-small-logo.png)

## Install ARGO-CD

Run the following commands to install ARGO-CD:
```
kubectl create namespace argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
```

Run the following command to set the argocd-server with external IP:
```
kubectl patch svc argocd-server -n argocd -p '{"spec": {"type": "LoadBalancer"}}'
```

In order to findout the 'admin' user password, run this command:
```
kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d; echo
```

