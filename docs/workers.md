---
title: "Managing Workers"
product: "vbproxmoxve"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbproxmoxve/userguide/workers.html"
last_updated: "8/27/2025"
product_version: "13.3.0.237"
---

# Managing Workers


To perform most data protection and disaster recovery operations, Veeam Backup & Replication uses workers. Workers are Linux-based VMs that process backup workload and distribute backup traffic when transferring data to backup repositories. Each worker is launched on a specific host for the duration of a backup or restore operation. As soon as a backup or restore session starts, Veeam Backup & Replication launches a worker, tests its configuration and installs system updates (if available). When the backup or restore session completes, Veeam Backup & Replication shuts down the worker VM so that it can be used for other sessions later.

|  |
| --- |
| Important |
| To modify the worker settings, use the Veeam Backup & Replication console as described in section [Editing Workers](workers_edit.md). Making any configuration changes to VMs running as workers manually in the Proxmox VE administration portal may cause technical issues. |

Worker Lifecycle

When you add a worker to the backup infrastructure, its configuration is saved to the Veeam Backup & Replication configuration database, but no VM is actually deployed on the host unless you choose to test the configuration. In the latter case, a VM (worker VM) is deployed and shut down after the test operation completes.

As soon as a backup or restore session starts, Veeam Backup & Replication tries to launch the worker and test its configuration. If no worker VM has been previously deployed, Veeam Backup & Replication deploys the VM using the worker configuration saved to the configuration database. Then, Veeam Plug-in for Proxmox VE powers on the worker VM and installs system updates (if available). When the backup or restore session completes, Veeam Backup & Replication shuts down the worker VM so that it can be used for other sessions later.

During the lifecycle, a worker can obtain one of the following statuses:

* Configured — the worker configuration is added to the Veeam Backup & Replication configuration database.
* Testing — the worker configuration is being updated and tested.
* Working — the worker is processing a backup or restore operation.
* Shut Down — the worker is powered off.

In This Section

* [Adding Workers](workers_add.md)
* [Testing Workers](workers_test.md)
* [Enabling and Disabling Workers](workers_disable.md)
* [Editing Workers](workers_edit.md)
* [Disabling Automatic Worker Updates](workers_update.md)
* [Removing Workers](workers_remove.md)


