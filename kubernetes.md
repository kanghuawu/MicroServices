# Kubernetes

### Resource

```
Awesome-Kubernetes
https://ramitsurana.gitbooks.io/awesome-kubernetes/content/index.html

Kubernetes: Up and Running
http://proquest.safaribooksonline.com.libaccess.sjlibrary.org/book/networking/9781491935668

https://courses.edx.org/courses/course-v1:LinuxFoundationX+LFS158x+2T2017/course/

Google Container Engine
https://cloud.google.com/container-engine/docs/tutorials/hello-app
```

### Command

```
minikube start

minikube stop

minikube delete

https://kubernetes.io/docs/user-guide/kubectl-cheatsheet/

kubectl version

https://your-k8s.com/api/v1/namespaces/default/pods/my-pod

kubectl get <resource-name>

kubectl get <resource-name> <object-name>

kubectl get componentstatuses                  

kubectl get nodes

kubectl describe <resource-name> <obj-name>

kubectl describe nodes 

kubectl edit <resource-name> <obj-name>

kubectl logs <pod-name>

kubectl exec -it <pod-name> -- bash

kubectl cp <pod-name>:/path/to/remote/file /path/to/local/file

kubectl help

kubectl run <pod name> --image=<image name>:<version>

kubectl apply -f <yaml>

kubectl port-forward <pod name> 8080:8080

kubectl cp <pod name>:/dir/file.txt ./file.txt

kubectl cp ./file.txt <pod name>:/dir/file.txt

// switching between minikube and gcloud kubernetes

kubectl config get-contexts

kubectl config use-context CONTEXT_NAME
```
