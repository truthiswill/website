---
title: Scaledown
menu:
  docs_v2020.08.26-rc.1:
    identifier: stash-scaledown
    name: Scaledown
    parent: reference-operator
menu_name: docs_v2020.08.26-rc.1
section_menu_id: reference
info:
  catalog: v2020.08.26-rc.1
  cli: v0.10.0-rc.1
  version: v2020.08.26-rc.1
---

## stash scaledown

Scale down workload

### Synopsis

Scale down workload

```
stash scaledown [flags]
```

### Options

```
  -h, --help                help for scaledown
      --kubeconfig string   Path to kubeconfig file with authorization information (the master location is set by the master flag).
      --master string       The address of the Kubernetes API server (overrides any value in kubeconfig)
      --selector string     Label used to select Restic's workload
```

### Options inherited from parent commands

```
      --alsologtostderr                  log to standard error as well as files
      --bypass-validating-webhook-xray   if true, bypasses validating webhook xray checks
      --enable-analytics                 Send analytical events to Google Analytics (default true)
      --log-flush-frequency duration     Maximum number of seconds between log flushes (default 5s)
      --log_backtrace_at traceLocation   when logging hits line file:N, emit a stack trace (default :0)
      --log_dir string                   If non-empty, write log files in this directory
      --logtostderr                      log to standard error instead of files (default true)
      --service-name string              Stash service name. (default "stash-operator")
      --stderrthreshold severity         logs at or above this threshold go to stderr
      --use-kubeapiserver-fqdn-for-aks   if true, uses kube-apiserver FQDN for AKS cluster to workaround https://github.com/Azure/AKS/issues/522 (default true)
  -v, --v Level                          log level for V logs
      --vmodule moduleSpec               comma-separated list of pattern=N settings for file-filtered logging
```

### SEE ALSO

* [stash](/docs/v2020.08.26-rc.1/reference/operator/stash)	 - Stash by AppsCode - Backup your Kubernetes Volumes

