# ArgoCD
Projects in Argo CD 

# App of projects
```yaml
project: default
source:
  repoURL: 'https://github.com/vettom/ArgoCD'
  path: argo-projects
  targetRevision: HEAD
destination:
  server: 'https://kubernetes.default.svc'
  namespace: argocd
syncPolicy:
  automated: {}
  syncOptions:
    - CreateNamespace=true

```

# App of apps
```yaml
apiVersion: argoproj.io/v1alpha1
kind: Application
metadata:
  name: app-of-apps
spec:
  destination:
    name: ''
    namespace: argocd
    server: 'https://kubernetes.default.svc'
  source:
    path: apps
    repoURL: 'https://github.com/vettom/ArgoCD'
    targetRevision: HEAD
    directory:
      recurse: true
  project: argocd
  syncPolicy:
    syncOptions:
      - CreateNamespace=true
```