# GitOps source repo for AKS Automatic + Camel K + Flux verification

This repository is the **GitOps source of truth** synced by Flux v2 (`microsoft.flux`
extension) to an AKS Automatic cluster.

## Layout (monorepo + subdirectory)

```
clusters/
  aks-automatic/        # Flux Kustomization path (only this subtree is reconciled)
    namespace.yaml
    podinfo.yaml        # sample app, AKS Automatic safeguards-compliant
    kustomization.yaml
    integration/        # Camel K Integration (added after the operator is installed)
      timer-log.yaml
```

Flux reconciles only `clusters/aks-automatic`, demonstrating that a single repo can
serve multiple clusters/environments from subdirectories (i.e. GitOps is **not**
limited to monorepo-only or one-app-per-repo).
