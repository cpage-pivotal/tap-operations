# Custom Supply Chain

Sample Carvel resource to sync this folder to the iterate cluster:

```
apiVersion: kappctrl.k14s.io/v1alpha1
kind: App
metadata:
  name: custom-supply-chain
  namespace: tap-install
spec:
  serviceAccountName: tap-install-sa
  fetch:
    - git:
        url: https://github.com/cpage-pivotal/tap-operations
        ref: origin/main
        subPath: custom-sc
  template:
    - ytt: {}
  deploy:
    - kapp:
        rawOptions: ["--dangerous-allow-empty-list-of-resources=true"]
```
