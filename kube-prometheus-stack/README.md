# Kube Prometheus Stack

## 1. Install

```shell
helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
helm upgrade --install kube-prometheus-stack \
    oci://ghcr.io/prometheus-community/charts/kube-prometheus-stack \
    --namespace kube-prometheus-stack --create-namespace \
    --version 79.7.1 --values kube-prometheus-values.yaml
```

## 2. Uninstall

```shell
helm uninstall -n kube-prometheus-stack kube-prometheus-stack

kubectl delete crd alertmanagerconfigs.monitoring.coreos.com
kubectl delete crd alertmanagers.monitoring.coreos.com
kubectl delete crd podmonitors.monitoring.coreos.com
kubectl delete crd probes.monitoring.coreos.com
kubectl delete crd prometheusagents.monitoring.coreos.com
kubectl delete crd prometheuses.monitoring.coreos.com
kubectl delete crd prometheusrules.monitoring.coreos.com
kubectl delete crd scrapeconfigs.monitoring.coreos.com
kubectl delete crd servicemonitors.monitoring.coreos.com
kubectl delete crd thanosrulers.monitoring.coreos.com

kubectl delete namespace kube-prometheus-stack
```
