---
title: Stash
menu:
  docs_0.7.0:
    identifier: stash
    name: Stash
    parent: reference
    weight: 0
product_name: stash
menu_name: docs_0.7.0
section_menu_id: reference
aliases:
- /docs/0.7.0/reference/
info:
  version: 0.7.0
---

## stash

Stash by AppsCode - Backup your Kubernetes Volumes

### Synopsis

Stash is a Kubernetes operator for restic. For more information, visit here: https://appscode.com/products/stash

### Options

```
      --alsologtostderr                  log to standard error as well as files
      --enable-analytics                 Send analytical events to Google Analytics (default true)
  -h, --help                             help for stash
      --log_backtrace_at traceLocation   when logging hits line file:N, emit a stack trace (default :0)
      --log_dir string                   If non-empty, write log files in this directory
      --logtostderr                      log to standard error instead of files
      --stderrthreshold severity         logs at or above this threshold go to stderr
  -v, --v Level                          log level for V logs
      --vmodule moduleSpec               comma-separated list of pattern=N settings for file-filtered logging
```

### SEE ALSO

* [stash backup](/docs/0.7.0/reference/stash_backup)	 - Run Stash Backup
* [stash check](/docs/0.7.0/reference/stash_check)	 - Check restic backup
* [stash forget](/docs/0.7.0/reference/stash_forget)	 - Delete snapshots from a restic repository
* [stash recover](/docs/0.7.0/reference/stash_recover)	 - Recover restic backup
* [stash run](/docs/0.7.0/reference/stash_run)	 - Launch Stash Controller
* [stash scaledown](/docs/0.7.0/reference/stash_scaledown)	 - Scale down workload
* [stash snapshots](/docs/0.7.0/reference/stash_snapshots)	 - Get snapshots of restic repo
* [stash version](/docs/0.7.0/reference/stash_version)	 - Prints binary version number.

