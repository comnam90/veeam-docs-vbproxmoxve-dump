---
title: "Managing Backups"
product: "vbproxmoxve"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbproxmoxve/userguide/backups_manage.html"
last_updated: "6/5/2025"
product_version: "13.3.0.237"
---

# Managing Backups


Veeam Backup & Replication stores information on all protected Proxmox VE VMs in the configuration database. Even if a VM is no longer protected by any configured backup job and even if the VM no longer exists in the Proxmox VE environment, records about created backups will not be deleted from the database until Veeam Backup & Replication automatically removes all restore points associated with this VM according to the retention settings saved in the backup metadata. You can manage Proxmox VE VM backups as long as their records are present in the configuration database.

In This Section

* [Viewing Backup Properties](backups_view_properties.md)
* [Verifying Backups](backups_verify.md)
* [Exporting Backups](backups_export.md)
* [Copying Backups](backups_copy.md)
* [Copying Backups to Tapes](backups_copy_tape.md)
* [Deleting Backups](backups_delete.md)


