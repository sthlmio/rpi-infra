## OpenFaas

### Get login credentials

```bash
kubectl get secret -n openfaas basic-auth -o jsonpath="{.data.basic-auth-password}" | base64 --decode; echo
```

## Monitoring

### Prometheus

http://127.0.0.1:9090

```bash
kubectl port-forward statefulset/prometheus-server -n monitoring 9090:9090
```

### Grafana

http://192.168.2.2/

```bash
kubectl get secret --namespace monitoring grafana-credentials -o jsonpath="{.data.admin-user}" | base64 --decode ; echo


kubectl get secret --namespace monitoring grafana-credentials -o jsonpath="{.data.admin-password}" | base64 --decode ; echo

```

## Create a sealed secret

```
kubectl -n <namespace> create secret generic <secret name> --dry-run -o json \
  --from-literal=<key>=<value> \
  | kubeseal \
  --format=yaml \
  --controller-name=sealed-secrets --controller-namespace=sealed-secrets \
  --cert=cert.pem > sealed-secret.yaml
```
