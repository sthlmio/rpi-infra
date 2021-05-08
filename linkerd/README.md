# Upgrade

```
brew upgrade linkerd

linkerd install -f linkerd/config.yaml > linkerd/components.yaml
linkerd upgrade > linkerd/components.yaml

linkerd viz install --config=linkerd/config-viz.yaml > linkerd/viz.yaml
```

## Restart deployments

```
kubectl -n <namespace> rollout restart deploy
```
