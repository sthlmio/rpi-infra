# rpi-infra

GitOps repo for infrastructure applications running on our Raspberry Pi Kubernetes cluster.

## Ceph Rook

### Toolbox

```bash
kubectl -n rook-ceph exec -it deploy/rook-ceph-tools -- bash
```

### Dashboard

#### Access dashboard

https://192.168.2.3:8443/

#### Get login credentials

```bash
kubectl -n rook-ceph get secret rook-ceph-dashboard-password -o jsonpath="{['data']['password']}" | base64 --decode && echo
```

## OpenFaas

### Get login credentials

```bash
kubectl get secret -n openfaas basic-auth -o jsonpath="{.data.basic-auth-password}" | base64 --decode; echo
```

## Monitoring

### Prometheus

http://127.0.0.1:9090

```bash
kubectl port-forward deploy/prometheus-server -n monitoring 9090:9090
```

### Grafana

http://192.168.2.3/

```bash
kubectl get secret --namespace monitoring grafana-credentials -o jsonpath="{.data.admin-user}" | base64 --decode ; echo


kubectl get secret --namespace monitoring grafana-credentials -o jsonpath="{.data.admin-password}" | base64 --decode ; echo

```

### Longhorn

http://192.168.2.2/

## Create a sealed secret

```
kubectl -n <namespace> create secret generic <secret name> --dry-run -o json \
  --from-literal=<key>=<value> \
  | kubeseal \
  --format=yaml \
  --controller-name=sealed-secrets --controller-namespace=sealed-secrets \
  --cert=cert.pem > sealed-secret.yaml
```
