To test this repository, you will need `kustomize` and `envsubst`.

First ensure you are logged in to your OpenShift/Kubernetes cluster
with cluster admin privileges.

Work out the cluster subdomain for ingress.

Then run:

```
kustomize build https://github.com/GrahamDumpleton/homeroom-testing | CLUSTER_SUBDOMAIN=A.B.C.D.nip.io envsubst CLUSTER_SUBDOMAIN |  kubectl apply -f -
```

Access:

```
http://homeroom.A.B.C.D.nip.io
```

with whatever sub domain you changed hosts to.

To delete everything when done, run:

```
kustomize build https://github.com/GrahamDumpleton/homeroom-testing | CLUSTER_SUBDOMAIN=A.B.C.D.nip.io envsubst CLUSTER_SUBDOMAIN |  kubectl delete -f -
```
