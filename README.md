# Ceph Rook

## Toolbox

```bash
kubectl -n rook-ceph exec -it deploy/rook-ceph-tools -- bash
```

## Dashboard

### Access dashboard

https://localhost:8443/

```bash
kubectl port-forward deploy/rook-ceph-mgr-a -n rook-ceph 8443:8443
```

### Get login credentials

```bash
kubectl -n rook-ceph get secret rook-ceph-dashboard-password -o jsonpath="{['data']['password']}" | base64 --decode && echo
```

# OpenFaas

## Get login credentials

```bash
kubectl get secret -n openfaas basic-auth -o jsonpath="{.data.basic-auth-password}" | base64 --decode; echo
```

# Monitoring

## Grafana

http://192.168.2.2/

```bash
kubectl get secret --namespace monitoring grafana -o jsonpath="{.data.admin-user}" | base64 --decode ; echo


kubectl get secret --namespace monitoring grafana -o jsonpath="{.data.admin-password}" | base64 --decode ; echo

```
