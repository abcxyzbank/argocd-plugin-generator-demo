### ArgoCD Plugin Generator Demo

- The plugin service source code is in `/app`.
- First, create the sample postgres service by running : 
```
kubectl apply -f postgres-manifests.yaml -n argocd
```
- Then, create the plugin service in k8s cluster by running : 
```
kubectl apply -f plugin-manifests.yaml -n argocd
```
- Finally, `/argocd` has the `applicationset.yaml` which can be applied ona k8s cluster that has ArgoCD installed by running : 
```
kubectl apply -f argocd/Applicationset.yaml -n argocd
```
---
Here's how the flow looks like : 
```
[Custom Generator Plugin] --> [ApplicationSet] --> [Argo CD Applications]
      ^                             |
      |                             v
[PostgreSQL Database]        [Kubernetes Cluster]
```
---

Reference : https://argo-cd.readthedocs.io/en/stable/operator-manual/applicationset/Generators-Plugin/