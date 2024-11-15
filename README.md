# ArgoCD
Setting up ArgoCD for kubernetes deployment.

# Getting started with argocd installation
```bash
helm install argocd -n argocd --create-namespace argo/argo-cd 
helm install argocd argo/argo-cd --version 5.13.8
# Make sure to update argocd-app.yaml to reflect version. 
# Change password and delete this secret after first login.
kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d
```

# Bootstrap argocd
```bash
apiVersion: argoproj.io/v1alpha1
kind: Application
metadata:
  name: 01-eks-common-apps
  finalizers:
    - resources-finalizer.argocd.argoproj.io
spec:
  destination:
    namespace: argocd
    server: https://kubernetes.default.svc
  project: default
  syncPolicy:
    # automated: {}
    syncOptions:
      - CreateNamespace=false
  sources:
    - repoURL: https://github.com/vettom/ArgoCD.git
      targetRevision: HEAD
      path: .
```