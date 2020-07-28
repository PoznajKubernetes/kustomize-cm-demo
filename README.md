Docker for Desktop ze starym kubectl

```
kubectl apply -k .
```

Inne (nowsze) trzeba zmienić kustomization.yaml z [env na envs](https://github.com/kubernetes-sigs/kustomize/issues/1069)

```
# Example configuration for the webserver
# at https://github.com/monopole/hello
apiVersion: kustomize.config.k8s.io/v1beta1
kind: Kustomization
commonLabels:
  app: hello
resources:
- deployment.yaml
- service.yaml
configMapGenerator:
- name: the-map
  envs:
    - cm.env
```