<h1>Kubeflow-Iris-quickstart</h1>
<h2>Installation on macOS using homebrew</h2>
<ul><li>brew install minikube</li>
<li>brew install docker</li><ul>
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



**IRIS PIPELINE** <be> <be>
![image](https://github.com/Bhavleenk/Kubeflow-Iris-quickstart/assets/107846946/aafe3c90-fa3b-4188-a476-36307cc5c91b)






