# Upgrade

```
brew upgrade linkerd

linkerd install -f config.yaml > components.yaml
linkerd upgrade > components.yaml

linkerd viz install -f config-viz.yaml > viz.yaml
```

## Restart deployments

```
kubectl -n <namespace> rollout restart deploy
```
