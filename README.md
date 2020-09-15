Grab a recent qcow2 image with something like:

```
wget "https://cloud.centos.org/centos/7/images/CentOS-7-x86_64-GenericCloud.qcow2"
```

Grab a recent version of virtctl: 

```
wget -O /usr/local/bin/virtctl https://github.com/kubevirt/kubevirt/releases/download/v0.32.0/virtctl-v0.32.0-linux-x86_64
```

Create a project:

```
oc new-project cnv-tekton
```

Tasks:

```
> kubectl apply -f https://raw.githubusercontent.com/tektoncd/catalog/master/task/openshift-client/0.1/openshift-client.yaml

> kubectl apply -f https://raw.githubusercontent.com/tylerauerbeck/catalog/master/task/virtctl/0.1/virtctl.yaml
```
