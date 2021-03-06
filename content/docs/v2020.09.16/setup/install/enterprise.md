---
title: Install Stash Enterprise Edition
description: Installation guide for Stash Enterprise edition
menu:
  docs_v2020.09.16:
    identifier: install-stash-enterprise
    name: Enterprise Edition
    parent: installation-guide
    weight: 20
product_name: stash
menu_name: docs_v2020.09.16
section_menu_id: setup
info:
  catalog: v2020.09.16
  cli: v0.11.0
  community: v0.11.0
  elasticsearch:
  - 5.6.4-v2
  - 6.2.4-v2
  - 6.3.0-v2
  - 6.4.0-v2
  - 6.5.3-v2
  - 6.8.0-v2
  - 7.2.0-v2
  - 7.3.2-v2
  enterprise: v0.11.0
  mongodb:
  - 3.4.17-v2
  - 3.4.22-v2
  - 3.6.13-v2
  - 3.6.8-v2
  - 4.0.11-v2
  - 4.0.3-v2
  - 4.0.5-v2
  - 4.1.13-v2
  - 4.1.4-v2
  - 4.1.7-v2
  - 4.2.3-v2
  mysql:
  - 5.7.25-v2
  - 8.0.14-v2
  - 8.0.3-v2
  percona-xtradb:
  - 5.7-v2
  postgres:
  - 10.14.0
  - 11.9.0
  - 12.4.0
  - 9.6.19
  version: v2020.09.16
---

# Install Stash Enterprise Edition

Stash Enterprise edition is the open core version of [Stash](https://github.com/stashed/stash). It comes with all the functionalities of Stash Community edition as well as some advanced features such as [Auto-Backup](/docs/v2020.09.16/guides/latest/auto-backup/overview), [Batch Backup](/docs/v2020.09.16/guides/latest/batch-backup/overview), and [Local Backend](/docs/v2020.09.16/guides/latest/backends/local) support, etc. A full features comparison between Stash Enterprise Edition and community version can be found [here](/docs/v2020.09.16/concepts/what-is-stash/overview).

If you are willing to try Stash Enterprise Edition, you can grab a **14 days trial** license from [here](https://license-issuer.appscode.com/).

## Get a Trial License

In this section, we are going to show you how you can get a **14 days trial** license for Stash Enterprise edition. You can get a license for your Kubernetes cluster by going through the following steps:

- At first, go to [AppsCode License Server](https://license-issuer.appscode.com/) and fill up the form. It will ask for your Name, Email, the product you want to install, and your cluster ID (UID of the `kube-system` namespace).
- Provide your name and email address. **You must provide your work email address**.
- Then, select `Stash Enterprise Edition` in the product field.
- Now, provide your cluster ID. You can get your cluster ID easily by running the following command:

```bash
kubectl get ns kube-system -o=jsonpath='{.metadata.uid}'
```

- Then, you have to agree with the terms and conditions. We recommend reading it before checking the box.
- Now, you can submit the form. After you submit the form, the AppsCode License server will send an email to the provided email address with a link to your license file.
- Navigate to the provided link and save the license into a file. Here, we save the license to a `license.txt` file.

Here is a screenshot of the license form.

<figure align="center">
  <img alt="Stash Backend Overview" src="/docs/v2020.09.16/images/setup/enterprise_license_form.png">
  <figcaption align="center">Fig: Stash License Form</figcaption>
</figure>

You can create licenses for as many clusters as you want. You can upgrade your license any time without re-installing Stash by following the upgrading guide from [here](/docs/v2020.09.16/setup/upgrade#upgrading-license).

>Stash licensing process has been designed to work with CI/CD workflow. You can automatically obtain a license from your CI/CD pipeline by following the guide from [here](https://github.com/appscode/offline-license-server#offline-license-server).

## Get an Enterprise License

If you are interested in purchasing Enterprise license, please contact us via sales@appscode.com for further discussion. You can also set up a meeting via our [calendly link](https://calendly.com/appscode/30min).

If you are willing to purchasing Enterprise license but need more time to test in your dev cluster, feel free to contact sales@appscode.com. We will be happy to extend your trial period.

## Install

Stash operator can be installed as a Helm chart or simply as Kubernetes manifests.

<ul class="nav nav-tabs" id="installerTab" role="tablist">
  <li class="nav-item">
    <a class="nav-link active" id="helm3-tab" data-toggle="tab" href="#helm3" role="tab" aria-controls="helm3" aria-selected="true">Helm 3 (Recommended)</a>
  </li>
  <li class="nav-item">
    <a class="nav-link" id="helm2-tab" data-toggle="tab" href="#helm2" role="tab" aria-controls="helm2" aria-selected="false">Helm 2</a>
  </li>
  <li class="nav-item">
    <a class="nav-link" id="script-tab" data-toggle="tab" href="#script" role="tab" aria-controls="script" aria-selected="false">YAML</a>
  </li>
</ul>
<div class="tab-content" id="installerTabContent">
  <div class="tab-pane fade show active" id="helm3" role="tabpanel" aria-labelledby="helm3-tab">

## Using Helm 3

Stash can be installed via [Helm](https://helm.sh/) using the [chart](https://github.com/stashed/installer/tree/{{< param "info.enterprise" >}}/charts/stash-enterprise) from [AppsCode Charts Repository](https://github.com/appscode/charts). To install the chart with the release name `stash-enterprise`:

```bash
$ helm repo add appscode https://charts.appscode.com/stable/
$ helm repo update
$ helm search repo appscode/stash-enterprise --version {{< param "info.enterprise" >}}
NAME                       CHART VERSION         APP VERSION         DESCRIPTION
appscode/stash-enterprise  {{< param "info.enterprise" >}}    {{< param "info.enterprise" >}}  Stash Enterprise by AppsCode - Enterprise features for Stash

$ helm install stash-enterprise appscode/stash-enterprise  \
  --version {{< param "info.enterprise" >}}                  \
  --namespace kube-system                       \
  --set-file license=/path/to/the/license.txt
```

To see the detailed configuration options, visit [here](https://github.com/stashed/installer/tree/{{< param "info.enterprise" >}}/charts/stash-enterprise).

</div>
<div class="tab-pane fade" id="helm2" role="tabpanel" aria-labelledby="helm2-tab">

## Using Helm 2

Stash can be installed via [Helm](https://helm.sh/) using the [chart](https://github.com/stashed/installer/tree/{{< param "info.enterprise" >}}/charts/stash-enterprise) from [AppsCode Charts Repository](https://github.com/appscode/charts). To install the chart with the release name `stash`:

```bash
$ helm repo add appscode https://charts.appscode.com/stable/
$ helm repo update
$ helm search appscode/stash-enterprise --version {{< param "info.enterprise" >}}
NAME                      CHART VERSION APP      VERSION             DESCRIPTION
appscode/stash-enterprise  {{< param "info.enterprise" >}}    {{< param "info.enterprise" >}}  Stash by AppsCode - Backup your Kubernetes Volumes

$ helm install appscode/stash-enterprise --name stash-enterprise   \
  --version {{< param "info.enterprise" >}}                          \
  --namespace kube-system                               \
  --set-file license=/path/to/the/license.txt
```

To see the detailed configuration options, visit [here](https://github.com/stashed/installer/tree/{{< param "info.enterprise" >}}/charts/stash-enterprise).

</div>
<div class="tab-pane fade" id="script" role="tabpanel" aria-labelledby="script-tab">

## Using YAML

If you prefer to not use Helm, you can generate YAMLs from Stash chart and deploy using `kubectl`. Here we are going to show the prodecure using Helm 3.

```bash
$ helm repo add appscode https://charts.appscode.com/stable/
$ helm repo update
$ helm search repo appscode/stash-enterprise --version {{< param "info.enterprise" >}}
NAME                       CHART VERSION         APP VERSION         DESCRIPTION
appscode/stash-enterprise  {{< param "info.enterprise" >}}    {{< param "info.enterprise" >}}  Stash by AppsCode - Backup your Kubernetes Volumes

$ helm template stash-enterprise appscode/stash-enterprise \
  --version {{< param "info.enterprise" >}}                  \
  --namespace kube-system                       \
  --set-file license=/path/to/the/license.txt   \
  --no-hooks | kubectl apply -f -
```

To see the detailed configuration options, visit [here](https://github.com/stashed/installer/tree/{{< param "info.enterprise" >}}/charts/stash-enterprise).

</div>
</div>

## Verify installation

To check if Stash operator pods have started, run the following command:

```bash
$ kubectl get pods --all-namespaces -l app.kubernetes.io/name=stash-enterprise --watch

NAMESPACE     NAME                                READY   STATUS    RESTARTS   AGE
kube-system   stash-enterprise-568c884795-hzbgg   2/2     Running   0          5h35m
```

Once the operator pod is running, you can cancel the above command by typing `Ctrl+C`.

Now, to confirm CRD groups have been registered by the operator, run the following command:
```bash
$ kubectl get crd -l app.kubernetes.io/name=stash

NAME                                      CREATED AT
backupbatches.stash.appscode.com          2020-08-24T08:20:54Z
backupblueprints.stash.appscode.com       2020-08-24T08:20:55Z
backupconfigurations.stash.appscode.com   2020-08-24T08:20:54Z
backupsessions.stash.appscode.com         2020-08-24T08:20:55Z
functions.stash.appscode.com              2020-08-24T08:20:55Z
recoveries.stash.appscode.com             2020-08-24T08:20:54Z
repositories.stash.appscode.com           2020-08-24T08:20:54Z
restics.stash.appscode.com                2020-08-24T08:20:54Z
restorebatches.stash.appscode.com         2020-08-24T08:20:55Z
restoresessions.stash.appscode.com        2020-08-24T08:20:55Z
tasks.stash.appscode.com                  2020-08-24T08:20:55Z
```

Now, you are ready to [take your first backup](/docs/v2020.09.16/guides/latest/README) using Stash.
