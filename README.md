# ArgoCD
Projects in Argo CD 

# App of projects
```yaml
apiVersion: argoproj.io/v1alpha1
kind: Application
metadata:
  name: projects
spec:
  destination:
    name: ''
    namespace: argocd
    server: 'https://kubernetes.default.svc'
  source:
    path: argo-projects
    repoURL: 'https://github.com/vettom/ArgoCD'
    targetRevision: HEAD
  project: default
  syncPolicy:
    automated:
      prune: true
      selfHeal: false


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
    automated: {}
    syncOptions:
      - CreateNamespace=true
```