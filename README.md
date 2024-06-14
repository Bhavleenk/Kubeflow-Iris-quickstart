# Kubeflow Quick Start

## Installation on macOS using Homebrew:
- `brew install minikube`
- `brew install docker`

## Installation on Windows using Command Prompt: <br>
(Make sure to run Command Prompt as Administrator)
- Install [Docker for Desktop](https://docs.docker.com/desktop/install/windows-install/)
-  Install Minikube:
  ```powershell
  New-Item -Path 'c:\' -Name 'minikube' -ItemType Directory -Force
  Invoke-WebRequest -OutFile 'c:\minikube\minikube.exe' -Uri 'https://github.com/kubernetes/minikube/releases/latest/download/minikube-windows-amd64.exe' -UseBasicParsing
  $oldPath = [Environment]::GetEnvironmentVariable('Path', [EnvironmentVariableTarget]::Machine)
  if ($oldPath.Split(';') -inotcontains 'C:\minikube'){
    [Environment]::SetEnvironmentVariable('Path', $('{0};C:\minikube' -f $oldPath), [EnvironmentVariableTarget]::Machine)
  }
  minikube start
  kubectl get pod -A
```
- To deploy the Kubeflow Pipelines, run the following commands (run on Command Prompt):
  ```bash
  Set PIPELINE_VERSION=2.2.0
  kubectl apply -k "github.com/kubeflow/pipelines/manifests/kustomize/cluster-scoped-resources?ref=$PIPELINE_VERSION"
  kubectl wait --for=condition=established --timeout=60s crd/applications.app.k8s.io
  kubectl apply -k "github.com/kubeflow/pipelines/manifests/kustomize/env/platform-agnostic-pns?ref=$PIPELINE_VERSION"
  ```
- Verify that the Kubeflow Pipelines UI is accessible by port-forwarding:
```bash
kubectl port-forward -n kubeflow svc/ml-pipeline-ui 8080:80
```
