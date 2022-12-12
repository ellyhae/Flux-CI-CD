# Flux-CI-CD
Cloud Computing project using Flux for Kubernetes CI/CD

## Setup

### 1. Create Flux Files

```
set GITHUB_TOKEN=
set GITHUB_USER=

flux bootstrap github --components-extra=image-reflector-controller,image-automation-controller --owner=%GITHUB_USER% --repository=Flux-CI-CD --branch=main --path=cluster --read-write-key --personal
```

### Add automatic image updates

```
# {"$imagepolicy": "flux-system:demo"}
```