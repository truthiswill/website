---
title: Install
description: Stash Install
menu:
  docs_v0.9.0-rc.2:
    identifier: install-stash
    name: Install
    parent: setup
    weight: 10
product_name: stash
menu_name: docs_v0.9.0-rc.2
section_menu_id: setup
info:
  catalog: v0.1.0
  cli: v0.2.0
  version: v0.9.0-rc.2
---

# Installation Guide

Stash operator can be installed via a script or as a Helm chart.

<ul class="nav nav-tabs" id="installerTab" role="tablist">
  <li class="nav-item">
    <a class="nav-link active" id="script-tab" data-toggle="tab" href="#script" role="tab" aria-controls="script" aria-selected="true">Script</a>
  </li>
  <li class="nav-item">
    <a class="nav-link" id="helm2-tab" data-toggle="tab" href="#helm2" role="tab" aria-controls="helm2" aria-selected="false">Helm 2</a>
  </li>
  <li class="nav-item">
    <a class="nav-link" id="helm3-tab" data-toggle="tab" href="#helm3" role="tab" aria-controls="helm3" aria-selected="false">Helm 3</a>
  </li>
</ul>
<div class="tab-content" id="installerTabContent">
  <div class="tab-pane fade show active" id="script" role="tabpanel" aria-labelledby="script-tab">

## Using Script

To install Stash in your Kubernetes cluster, run the following command:

```console
$ curl -fsSL https://github.com/stashed/installer/raw/{{< param "info.version" >}}/deploy/stash.sh | bash
```

After successful installation, you should have a `stash-operator-***` pod running in the `kube-system` namespace.

```console
$ kubectl get pods -n kube-system | grep stash-operator
stash-operator-846d47f489-jrb58       1/1       Running   0          48s
```

#### Customizing Installer

The installer script and associated yaml files can be found in the [/deploy](https://github.com/stashed/installer/tree/{{< param "info.version" >}}/deploy) folder. You can see the full list of flags available to installer using `-h` flag.

```console
$ curl -fsSL https://github.com/stashed/installer/raw/{{< param "info.version" >}}/deploy/stash.sh | bash -s -- -h

stash.sh - install stash operator

stash.sh [options]

options:
-h, --help                             show brief help
-n, --namespace=NAMESPACE              specify namespace (default: kube-system)
    --docker-registry                  docker registry used to pull stash images (default: appscode)
    --pushgateway-registry             docker registry used to pull Prometheus pushgateway image (default: prom)
    --image-pull-secret                name of secret used to pull stash operator images
    --run-on-master                    run stash operator on master
    --enable-mutating-webhook          enable/disable mutating webhooks for Kubernetes workloads
    --enable-validating-webhook        enable/disable validating webhooks for Stash crds
    --bypass-validating-webhook-xray   if true, bypasses validating webhook xray checks
    --enable-status-subresource        if enabled, uses status sub resource for crds
    --use-kubeapiserver-fqdn-for-aks   if true, uses kube-apiserver FQDN for AKS cluster to workaround https://github.com/Azure/AKS/issues/522 (default true)
    --enable-analytics                 send usage events to Google Analytics (default: true)
    --uninstall                        uninstall stash
    --purge                            purges stash crd objects and crds
    --monitoring-agent                 specify which monitoring agent to use (default: none)
    --monitoring-backup                specify whether to monitor stash backup and restore activity (default: false)
    --monitoring-operator              specify whether to monitor stash operator (default: false)
    --prometheus-namespace             specify the namespace where Prometheus server is running or will be deployed (default: same namespace as stash-operator)
    --servicemonitor-label             specify the label for ServiceMonitor crd. Prometheus crd will use this label to select the ServiceMonitor. (default: 'app: stash')
```

If you would like to run Stash operator pod in `master` instances, pass the `--run-on-master` flag:

```console
$ curl -fsSL https://github.com/stashed/installer/raw/{{< param "info.version" >}}/deploy/stash.sh \
    | bash -s -- --run-on-master
```

Stash operator will be installed in a `kube-system` namespace by default. If you would like to run Stash operator pod in `stash` namespace, pass the `--namespace=stash` flag:

```console
$ kubectl create namespace stash
$ curl -fsSL https://github.com/stashed/installer/raw/{{< param "info.version" >}}/deploy/stash.sh \
    | bash -s -- --namespace=stash [--run-on-master]
```

If you are using a private Docker registry, you need to pull the following image:

 - [appscode/stash](https://hub.docker.com/r/appscode/stash)

To pass the address of your private registry and optionally a image pull secret use flags `--docker-registry` and `--image-pull-secret` respectively.

```console
$ kubectl create namespace stash
$ curl -fsSL https://github.com/stashed/installer/raw/{{< param "info.version" >}}/deploy/stash.sh \
    | bash -s -- --docker-registry=MY_REGISTRY [--image-pull-secret=SECRET_NAME]
```

Stash implements [validating admission webhooks](https://kubernetes.io/docs/reference/access-authn-authz/admission-controllers/#validatingadmissionwebhook) to validate Stash CRDs and **mutating webhooks** for Kubernetes workload types. This is helpful when you create `Restic` before creating workload objects. This allows stash operator to initialize the target workloads by adding sidecar or, init-container before workload-pods are created. Thus stash operator does not need to delete workload pods for applying changes. This is particularly helpful for workload kind `StatefulSet`, since Kubernetes does not support adding sidecar / init containers to StatefulSets after they are created. This is enabled by default for Kubernetes 1.9.0 or later releases. To disable this feature, pass the `--enable-validating-webhook=false` and `--enable-mutating-webhook=false` flag respectively.

```console
$ curl -fsSL https://github.com/stashed/installer/raw/{{< param "info.version" >}}/deploy/stash.sh \
    | bash -s -- --enable-validating-webhook=false --enable-mutating-webhook=false
```

Stash {{< param "info.version" >}} or later releases can use status sub resource for CustomResourceDefintions. This is enabled by default for Kubernetes 1.11.0 or later releases. To disable this feature, pass the `--enable-status-subresource=false` flag.

</div>
<div class="tab-pane fade" id="helm2" role="tabpanel" aria-labelledby="helm2-tab">

## Using Helm 2
Stash can be installed via [Helm](https://helm.sh/) using the [chart](https://github.com/stashed/installer/tree/{{< param "info.version" >}}/charts/stash) from [AppsCode Charts Repository](https://github.com/appscode/charts). To install the chart with the release name `my-release`:

```console
$ helm repo add appscode https://charts.appscode.com/stable/
$ helm repo update
$ helm search appscode/stash
NAME            CHART VERSION APP VERSION DESCRIPTION
appscode/stash  {{< param "info.version" >}}    {{< param "info.version" >}}  Stash by AppsCode - Backup your Kubernetes Volumes

$ helm install appscode/stash --name stash-operator --version {{< param "info.version" >}} --namespace kube-system
```

To see the detailed configuration options, visit [here](https://github.com/stashed/installer/tree/{{< param "info.version" >}}/charts/stash).

</div>
<div class="tab-pane fade" id="helm3" role="tabpanel" aria-labelledby="helm3-tab">

## Using Helm 3
Stash can be installed via [Helm](https://helm.sh/) using the [chart](https://github.com/stashed/installer/tree/{{< param "info.version" >}}/charts/stash) from [AppsCode Charts Repository](https://github.com/appscode/charts). To install the chart with the release name `my-release`:

```console
$ helm repo add appscode https://charts.appscode.com/stable/
$ helm repo update
$ helm search repo appscode/stash
NAME            CHART VERSION APP VERSION DESCRIPTION
appscode/stash  {{< param "info.version" >}}    {{< param "info.version" >}}  Stash by AppsCode - Backup your Kubernetes Volumes

$ helm install stash-operator appscode/stash --version {{< param "info.version" >}} --namespace kube-system
```

To see the detailed configuration options, visit [here](https://github.com/stashed/installer/tree/{{< param "info.version" >}}/charts/stash).

</div>
</div>

### Installing in GKE Cluster

If you are installing Stash on a GKE cluster, you will need cluster admin permissions to install Stash operator. Run the following command to grant admin permision to the cluster.

```console
$ kubectl create clusterrolebinding "cluster-admin-$(whoami)" \
  --clusterrole=cluster-admin \
  --user="$(gcloud config get-value core/account)"
```

In addition, if your GKE cluster is a [private cluster](https://cloud.google.com/kubernetes-engine/docs/how-to/private-clusters), you will need to either add an additional firewall rule that allows master nodes access port `8443/tcp` on worker nodes, or change the existing rule that allows access to ports `443/tcp` and `10250/tcp` to also allow access to port `8443/tcp`. The procedure to add or modify firewall rules is described in the official GKE documentation for private clusters mentioned before.

## Verify installation
To check if Stash operator pods have started, run the following command:
```console
$ kubectl get pods --all-namespaces -l app=stash --watch

NAMESPACE     NAME                              READY     STATUS    RESTARTS   AGE
kube-system   stash-operator-859d6bdb56-m9br5   2/2       Running   2          5s
```

Once the operator pods are running, you can cancel the above command by typing `Ctrl+C`.

Now, to confirm CRD groups have been registered by the operator, run the following command:
```console
$ kubectl get crd -l app=stash

NAME                                 AGE
recoveries.stash.appscode.com        5s
repositories.stash.appscode.com      5s
restics.stash.appscode.com           5s
```

Now, you are ready to [take your first backup](/docs/v0.9.0-rc.2/guides/latest/README) using Stash.


## Configuring RBAC
Stash introduces resources, such as, `Restic`, `Repository`, `Recovery` and `Snapshot`. Stash installer will create 2 user facing cluster roles:

| ClusterRole         | Aggregates To | Desription                                                                                            |
| ------------------- | ------------- | ----------------------------------------------------------------------------------------------------- |
| appscode:stash:edit | admin, edit   | Allows edit access to Stash CRDs, intended to be granted within a namespace using a RoleBinding.      |
| appscode:stash:view | view          | Allows read-only access to Stash CRDs, intended to be granted within a namespace using a RoleBinding. |

These user facing roles supports [ClusterRole Aggregation](https://kubernetes.io/docs/admin/authorization/rbac/#aggregated-clusterroles) feature in Kubernetes 1.9 or later clusters.

## Install Stash kubectl plugin

Stash provides a CLI using kubectl plugin to work with the stash Objects quickly. Download pre-build binaries from [stashed/cli Githhub release]() and put the binary to some directory in your `PATH`. To install linux 64-bit you can run the following commands:

```console
# Linux amd 64-bit
wget -O kubectl-stash https://github.com/stashed/cli/releases/download/{{< param "info.cli" >}}/kubectl-stash-linux-amd64 \
  && chmod +x kubectl-stash \
  && sudo mv kubectl-stash /usr/local/bin/
```

If you prefer to install kubectl Stash cli from source code, you will need to set up a GO development environment following [these instructions](https://golang.org/doc/code.html). Then, install the CLI using `go get` from source code.

```console
go get github.com/stashed/cli/...
```

>Please note that this will install kubectl stash cli from master branch which might include breaking and/or undocumented changes.

## Detect Stash version

To detect Stash version, exec into the operator pod and run `stash version` command.

```console
$ POD_NAMESPACE=kube-system
$ POD_NAME=$(kubectl get pods -n $POD_NAMESPACE -l app=stash -o jsonpath={.items[0].metadata.name})
$ kubectl exec -it $POD_NAME -c operator -n $POD_NAMESPACE /stash version

Version = {{< param "info.version" >}}
VersionStrategy = tag
Os = alpine
Arch = amd64
CommitHash = 85b0f16ab1b915633e968aac0ee23f877808ef49
GitBranch = release-0.5
GitTag = {{< param "info.version" >}}
CommitTimestamp = 2017-10-10T05:24:23

$ kubectl exec -it $POD_NAME -c operator -n $POD_NAMESPACE restic version
restic 0.9.1
compiled with go1.9 on linux/amd64
```
