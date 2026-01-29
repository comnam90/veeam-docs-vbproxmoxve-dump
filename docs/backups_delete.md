---
title: "Deleting Backups"
product: "vbproxmoxve"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbproxmoxve/userguide/backups_delete.html"
last_updated: "11/10/2025"
product_version: "13.3.0.237"
---

# Deleting Backups


By default, Veeam Backup & Replication maintains backups stored in backup repositories according to retention policy settings saved in the backup metadata. If Veeam Backup & Replication detects that the number of restore points in the backup chain exceeds the allowed number, it automatically removes obsolete backups. You can also delete backup files from backup repositories manually if you no longer need them.

To delete backup files created for a Proxmox VE VM, do the following:

1. Open the Home view.
2. In the inventory pane of the Home view, select Backups.
3. In the working area, expand the job that created the backup, right-click the VM whose backups you want to delete and select Remove from > Disk.

Alternatively, expand the job that created the backup, select the VM and click Remove from > Disk on the ribbon.

|  |
| --- |
| Note |
| If [4-eyes authorization](https://helpcenter.veeam.com/docs/vbr/userguide/four_eyes_authorization.html?ver=13) is enabled in Veeam Backup & Replication, deleting backup files will require additional approval from another user with the Veeam Backup Administrator role. |

[![Deleting Backups](images/pve_backups_delete.webp)](images/pve_backups_delete.webp "Deleting Backups")


