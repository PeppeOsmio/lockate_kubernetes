## 1. Creation

https://rook.io/docs/rook/latest-release/Getting-Started/quickstart

```shell
kubectl create namespace rook-ceph
kubectl apply -f crds.yaml -f common.yaml -f csi-operator.yaml -f operator.yaml
kubectl -n rook-ceph get pod

# customize storage class here!
# also set portable: false
kubectl apply -f cluster-on-pvc.yaml
```

## 2. Install toolbox

https://rook.io/docs/rook/latest-release/Troubleshooting/ceph-toolbox/

```shell
kubectl apply -f toolbox.yaml
kubectl -n rook-ceph rollout status deploy/rook-ceph-tools
kubectl -n rook-ceph exec -it deploy/rook-ceph-tools -- bash
```

Then in toolbox

```shell
ceph status
```


## Delete everything

https://rook.io/docs/rook/v1.11/Getting-Started/ceph-teardown/