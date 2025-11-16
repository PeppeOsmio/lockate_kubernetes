# Cloud Native Postgres

```shell
helm repo add cnpg https://cloudnative-pg.github.io/charts
helm upgrade --install cnpg \
  cnpg/cloudnative-pg \
  --namespace cnpg-system \
  --create-namespace \
  --values cnpg-values.yaml 
kubectl create namespace cnpg
kubectl apply -f cnpg-cluster.yaml
```
