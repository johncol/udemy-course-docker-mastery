# Kubernetes commands

```
kubectl run <deployment_name> --image <image_name>
kubectl create deployment <deployment_name> --image=<image_name>
```

```
kubectl get pods
kubectl get services
kubectl get all
```

```
kubectl get pods -w
```

```
kubectl delete deployment <deployment_name>
```

```
kubectl scale deploy/<deployment_name> --replicas <number_of_replicas>
kubectl scale deployment <deployment_name> --replicas <number_of_replicas>
```

```
kubectl logs deployment/<deployment_name> --follow --tail 10
```

```
kubectl logs -l run=<deployment_name> --follow --tail 10
```

```
kubectl describe pods
kubectl describe pod/<pod_name>
```

```
kubectl expose deployment/<deployment_name> --port 8888
kubectl expose deployment/<deployment_name> --port 8888 --name httpenv-np --type NodePort
kubectl expose deployment/<deployment_name> --port 8888 --name httpenv-lb --type LoadBalancer
```

```
kubectl run --generator run-pod/v1 tmp-shell --rm -it --image bretfisher/netshoot -- bash
```

```
kubectl create deployment test --image nginx --dry-run -o yaml
```
