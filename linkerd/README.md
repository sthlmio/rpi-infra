# Upgrade

```
brew upgrade linkerd

linkerd upgrade > linkerd/components.yaml
linkerd viz install > linkerd/viz.yaml
```

## Restart deployments

```
kubectl -n <namespace> rollout restart deploy
```
