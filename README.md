# Ceph Rook

## Toolbox

```bash
kubectl -n rook-ceph exec -it deploy/rook-ceph-tools -- bash
```

## Dashboard

### Access dashboard

https://localhost:8443/

```bash
kubectl port-forward rook-ceph-mgr-a-7f85cd4cb-n2rpq -n rook-ceph 8443:8443
```

### Get login credentials

```bash
kubectl -n rook-ceph get secret rook-ceph-dashboard-password -o jsonpath="{['data']['password']}" | base64 --decode && echo
```
