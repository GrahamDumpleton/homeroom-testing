To test, checkout this repository.

In the repository run:

```
grep -r nip.io .
```

For each file, change the `A.B.C.D.nip.io` part of the hostname and set
it to the cluster subdomain for your Kubernetes cluster. That is, the
host which inbound ingress router listens on. This might just be another
`nip.io` address or a proper FQDN if setup.

Once done, in the top level directory of the repository, and with cluster
admin access to the cluster run:

```
kustomize build | kubectl apply -f -
```

Then access:

```
http://homeroom.A.B.C.D.nip.io
```

with whatever sub domain you changed hosts to.

To delete everything when done, run:

```
kustomize build | kubectl delete -f -
```
