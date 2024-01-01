# prometheus-thanos

POC for kube-prometheus-stack with thanos

## Local kind cluster prepwork


Start your local Kind cluster

```bash
kind create cluster --config kind/kind-cluster.yaml
```

Command will create a 3 node cluster, one control-plane node with taints, and three worker nodes simulating three availability zones.

After that apply the ingress and cert-manager

```bash
helmfile --file kind/helmfile.yaml apply --skip-needs=false
```

This will install and expose Haproxy ingress controller on port 80 and 443. Cert manager will be installed with local cert issuer.

## Install kube-prometheus-stack

```bash
helmfile --file prometheus/helmfile.yml apply --skip-needs=false
```
