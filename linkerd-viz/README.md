# Upgrade

```
brew upgrade linkerd

linkerd viz install \
  --set tap.externalSecret=true \
  --set-file tap.caBundle=ca.crt \
  --set tapInjector.externalSecret=true \
  --set-file tapInjector.caBundle=ca.crt \
  > components.yaml
```

## Restart deployments

```
kubectl -n <namespace> rollout restart deploy
```
