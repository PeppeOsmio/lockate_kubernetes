# Install cluster

## 1. Metrics API

```shell
kubectl apply -f components.yaml
kubectl get deployment metrics-server -n kube-system
kubectl logs -n kube-system -l k8s-app=metrics-server

# if ok
kubectl top nodes
```
