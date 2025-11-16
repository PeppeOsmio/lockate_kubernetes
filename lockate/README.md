# Lockate

```shell
kubectl -n lockate create secret docker-registry harbor-credentials \
    --docker-server=harbor.kubernetes.giuseppebosa.eu \
    "--docker-username=robot\$lockate+pull" \
    --docker-password=*** \
    --docker-email=none
```
