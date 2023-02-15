# ArgoCD
Setting up ArgoCD for kubernetes deployment.

# Getting started with argocd installation
```bash
helm install argocd -n argocd --create-namespace argo/argo-cd
helm install argocd argo/argo-cd
# Change password and delete this secret after first login.
kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d
```

5lh4TsQosdzYBjeF

# Bootstrap argocd
```bash
kubectl apply -k bootstrap
```