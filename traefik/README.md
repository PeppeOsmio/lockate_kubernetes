# Traefik

## 1. OVH application setup

Create an application token here <https://ca.ovh.com/auth/api/createToken> with the following rights:

- POST /domain/zone/*
- DELETE /domain/zone/*
- PUT /domain/zone/*
- GET /domain/zone/*

https://go-acme.github.io/lego/dns/ovh/


## 1. Install Traefik

```shell
helm repo add traefik https://traefik.github.io/charts
helm repo update
kubectl create namespace traefik1
kubectl apply -f ovh-credentials.yaml
kubectl apply -f auth-secret.yaml
helm upgrade --install traefik traefik/traefik --namespace traefik1 --values traefik-values.yaml
```


## 2. Install Cert Manager

```shell
kubectl create namespace cert-manager
helm install \
  cert-manager oci://quay.io/jetstack/charts/cert-manager \
  --version v1.19.1 \
  --namespace cert-manager \
  --create-namespace \
  --set crds.enabled=true
```

## 3. Install Cert Manger OVH webhook

```shell
helm repo add cert-manager-webhook-ovh-charts https://aureq.github.io/cert-manager-webhook-ovh/
helm repo update
kubectl
helm upgrade --install --namespace cert-manager -f cert-manager-webhook-ovh-values.yaml cm-webhook-ovh cert-manager-webhook-ovh-charts/cert-manager-webhook-ovh
```
