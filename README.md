# ArgoCD
Setting up ArgoCD for kubernetes deployment.

# Getting started
```bash
helm install argocd -n argocd --create-namespace argo/argo-cd
helm install argocd argo/argo-cd
```
kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d
d4c606jSfqJ33M4M

