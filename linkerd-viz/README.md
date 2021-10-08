# Upgrade

```
brew upgrade linkerd

linkerd viz install -f config.yaml > components.yaml
```

## Restart deployments

```
kubectl -n <namespace> rollout restart deploy
```
