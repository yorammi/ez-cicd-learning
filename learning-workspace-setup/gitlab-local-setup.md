# GitLab local installation & setup
![ez logo](/resources/images/ez/ez-smiley-small-logo.png)
## setup GitLab instance on Kubernetes
(based on this page: https://docs.gitlab.com/charts/installation/deployment.html)

```
helm repo add gitlab https://charts.gitlab.io/
helm repo update
```

```
helm upgrade --install gitlab gitlab/gitlab \
  --timeout 600s \
  --set global.edition=ce \
  --set global.hosts.domain=example.com \
  --set global.hosts.externalIP=10.10.10.10 \
  --set certmanager-issuer.email=me@example.com \
  --set postgresql.image.tag=13.6.0
```

```
kubectl get secret gitlab-gitlab-initial-root-password -ojsonpath='{.data.password}' | base64 --decode ; echo
```

