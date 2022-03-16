# Pod

```
## Imperative way to run a pod
$ kubectl run firstpod --image=nginx --restart=Never
```

```
## Display pod object events and details
$ kubectl describe pods firstpod
```

```
## Connect container stdout
## Note that if there are more than one container running, you need to give container name with -c option
$ kubectl logs firstpod
```

```
## Connect to container and run command
$ kubectl exec firstpod --printenv
```

```
## Open a shell in the container
$ kubectl exec -it firstpod -c container1 -- /bin/sh
```

```
## Delete the k8s pod object
$ kubectl delete pods firstpod
```

```
## Declarative way of creating a pod object
$kubectl apply -f pod.yaml
```

```
## Deleting the objects created with yaml declaration
$ kubectl delete -f pod.yaml
```

```
## Create a pod with label and pod values
$ kubectl run secondpod --image=nginx --port=80 --labels="app=front-end,team=developer" --restart=Never
```

```
## Opens an editor to edit k8s object
$ kubectl edit pods firstpod
```

```
## Creating a tunnel to pod's http (80) port
$ kubectl port-forward pod/firstpod 8080:80
```

# Deployment

```
## Imperative way to create a deployment
$ kubectl create deployment firstdeployment --image=nginx:latest --replicas=2
```

```
## List all deployment objects
$ kubectl get deployment
```

```
## Delete the deployment object
$ kubectl delete deployment firstdeployment
```

```
## Set a new container image on existing deployment
$ kubectl set image deployment/firstdeployment nginx=httpd:alpine
```

```
## Scale out replica number of deployment (updates scaleset)
$ kubectl scale deployment firstdeployment --replicas=3
```

# Service

```
## List all services
$ kubectl get service
```

```
## Only for internal cluster network
$ kubectl expose deployment nginx --type=ClusterIP --name=nginx

## Minikube exposing node ip for a NodePort type service
$ minikube service --url <service-name>

## Creating a tunnel to access LoadBalancer type service object
$ minikube tunnel
```

```
## Delete service object
$ kubectl delete service backend
```
