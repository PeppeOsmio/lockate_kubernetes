## 1. Install

```shell
helm repo add harbor https://helm.goharbor.io
kubectl create namespace harbor
helm install harbor harbor/harbor --namespace --values harbor-values.yaml
```