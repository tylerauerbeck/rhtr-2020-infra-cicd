Grab a recent RHEL qcow2 image from somewhere like: https://access.redhat.com/downloads/content/69/ver=/rhel---7/7.8/x86_64/product-downloads

Grab a recent version of virtctl: 

```
wget -O /usr/local/bin/virtctl https://github.com/kubevirt/kubevirt/releases/download/v0.32.0/virtctl-v0.32.0-linux-x86_64
```

Create a project:

```
oc new-project cnv-tekton
```

Upload your base image to your project:

```
virtctl image-upload --pvc-name rhel7-vm-disk --pvc-size=20Gi --image-path=/path/to/rhel-server-7.8-x86_64-kvm.qcow2 --uploadproxy-url=https://cdi-uploadproxy-openshift-cnv.apps.s45.core.rht-labs.com
```

The uploadproxy above can be found with:

```
oc get route -n openshift-cnv
```

Create your VM definition:

```
oc apply -f rhel7-base-vm.yaml
```

Start your VM:

```
virtctl start XYZ
```

