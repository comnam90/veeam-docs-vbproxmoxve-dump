---
title: "Performing Restore"
product: "vbproxmoxve"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbproxmoxve/userguide/data_recovery.html"
last_updated: "6/30/2025"
product_version: "13.3.0.237"
---

# Performing Restore


In various disaster recovery scenarios, Veeam Backup & Replication allows you to perform the following operations using backed-up data:

* [Entire VM restore](restore_entire_vm.md) — recover Proxmox VE VMs to the original location or to a new location.

* [Instant VM recovery](restore_instant.md) — instantly start an Proxmox VE VM directly from a backup.
* [Disk publishing](disk_publish.md) — mount specific disks of a backed-up Proxmox VE VMs to any server added to the backup infrastructure.
* [File-level restore](vm_guest_restore.md) — recover individual VM guest OS files and folders.

* [Application items restore](restore_app_items.md) — restore applications, such as Microsoft Active Directory, Microsoft Exchange, Microsoft SharePoint, and Microsoft SQL Server.

* [VM disk export](disk_export.md) — restore VM disks and convert them to disks of the VMDK, VHD or VHDX format.
* [VM restore to Amazon Web Services](restore_to_amazon_ec2.md) — restore Proxmox VE VMs to Amazon Web Services as EC2 instances.
* [VM restore to Microsoft Azure](restore_to_microsoft_azure.md) — restore Proxmox VE VMs to Microsoft Azure as Azure VMs.
* [VM restore to Google Cloud](restore_to_google.md) — restore Proxmox VE VMs to Google Cloud as VM instances.

You can restore VM data to the most recent state or to any available restore point.


