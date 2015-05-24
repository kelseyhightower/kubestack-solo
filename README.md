# kubestack-solo

This repo contains a Packer configuration template that can be used to create a Kubernetes VMware image for local testing.

## Build

```
packer build -var-file settings.json kubestack-solo.json
```

## Start Kubestack Solo VM

```
$ /Applications/VMware\ Fusion.app/Contents/Library/vmrun \
  start output-vmware-iso/kubestack-solo.vmx
```

## Configure kubectl

```
$ kubectl config set clusters.local.server http://$vm-ip-address:8080
```

You now have a single node ready for use.

```
$ kubectl get nodes
```
```
NAME        LABELS    STATUS
127.0.0.1   <none>    Ready
```

## Logging In

```
$ ssh -i files/kubestack_id_rsa core@$vm-ip-address
```
