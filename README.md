<h1>Kubeflow-Iris-quickstart</h1>
<h2>Installation on macOS using homebrew</h2>
<ul><li>brew install minikube</li>
<li>brew install docker</li><ul>
</ul>
<h2>Installation on Windows</h2>
## Step 1: Install Docker Desktop

Download and install Docker Desktop from [here](https://docs.docker.com/desktop/install/windows-install/).

## Step 2: Install Minikube

Run the following commands in Command Prompt (Make sure to run command prompt as Administrator):

<ul><li>New-Item -Path 'c:\' -Name 'minikube' -ItemType Directory -Force
Invoke-WebRequest -OutFile 'c:\minikube\minikube.exe' -Uri 'https://github.com/kubernetes/minikube/releases/latest/download/minikube-windows-amd64.exe' -UseBasicParsing</li>
<li>$oldPath = [Environment]::GetEnvironmentVariable('Path', [EnvironmentVariableTarget]::Machine)
if ($oldPath.Split(';') -inotcontains 'C:\minikube'){
  [Environment]::SetEnvironmentVariable('Path', $('{0};C:\minikube' -f $oldPath), [EnvironmentVariableTarget]::Machine)
}</li>
<li>minikube start</li>
<li>kubectl get po -A
  </li>
</ul>





## Step 3: Local Deployment
<ul><li> set PIPELINE_VERSION=2.2.0</li>
<li>kubectl apply -k "github.com/kubeflow/pipelines/manifests/kustomize/cluster-scoped-resources?ref=$PIPELINE_VERSION"</li>
<li>kubectl wait --for condition=established --timeout=60s crd/applications.app.k8s.io</li>
<li>kubectl apply -k "github.com/kubeflow/pipelines/manifests/kustomize/env/platform-agnostic?ref=$PIPELINE_VERSION"</li>
<li>kubectl port-forward -n kubeflow svc/ml-pipeline-ui 8080:80</li>
</ul>

<h2>Basics of Kubeflow</h2>
<li>2 CPUs or more</li>
   <li>2GB of free memory</li>
<li>minikube start (to start minikube will create image from docker if doesn't exist)</li> 
<li>kubectl cluster-info (To verify that our cluster is up and running )</li>
<li>kubectl get pods -A </li>
<li>if all our running, kubectl port-forward -n kubeflow svc/ml-pipeline-ui 8080:80</li>
<li>If any pods are not running, wait or diagnose (Initially, some services, such as the storage-provisioner, may not yet be in a Running state. This is a normal condition during cluster bring-up and will resolve itself momentarily.)</li>
<li>to pause minikube , minikube pause</li>
<li>to stop minikube, minikube stop</li>
</ul>



**IRIS PIPELINE** <br> <br>
![image](https://github.com/Bhavleenk/Kubeflow-Iris-quickstart/assets/107846946/aafe3c90-fa3b-4188-a476-36307cc5c91b)






