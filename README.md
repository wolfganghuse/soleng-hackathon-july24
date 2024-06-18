# DKP Custom Catalog Application: Kubeflow

1. Set the K8s context to the DKP management cluster.
2. Set the namespace to the relevant project as an environmental variable:

```bash
export NAMESPACE=[your_namespace]
````

3. Copy and paste the following manifest into the terminal to deploy to the DKP catalog:

```bash
kubectl apply -f - <<EOF
apiVersion: source.toolkit.fluxcd.io/v1beta1
kind: GitRepository
metadata:
  name: kubeflow-catalog
  namespace: ${NAMESPACE}
  labels:
    kommander.d2iq.io/gitapps-gitrepository-type: catalog
    kommander.d2iq.io/gitrepository-type: catalog
spec:
  interval: 1m0s
  ref:
    branch: master
  timeout: 1m0s
  url: https://github.com/d2iq-ps/gs-kubeflow
EOF
```
