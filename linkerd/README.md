# Upgrade

```
brew upgrade linkerd

linkerd install \
  --identity-external-issuer \
  --ha \
  --set policyValidator.externalSecret=true \
  --set-file policyValidator.caBundle=ca.crt \
  --set proxyInjector.externalSecret=true \
  --set-file proxyInjector.caBundle=ca.crt \
  --set profileValidator.externalSecret=true \
  --set-file profileValidator.caBundle=ca.crt \
  > components.yaml

linkerd upgrade > components.yaml
```

## Restart deployments

```
kubectl -n <namespace> rollout restart deploy
```
