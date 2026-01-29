---
title: "Viewing Backup Properties"
product: "vbproxmoxve"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbproxmoxve/userguide/backups_view_properties.html"
last_updated: "10/27/2025"
product_version: "13.3.0.237"
---

# Viewing Backup Properties


After a backup job successfully creates a VM backup according to the specified schedule, or after you create an active full VM backup manually, the backup is displayed under the Backups node in the Home view of the Veeam Backup & Replication console. Each backup and the collection of restore points created for this backup is represented with a set of properties, such as:

* Object Name — the name of a protected VM.
* Original Size — the total amount of disk space allocated to the VM.
* File Name — the name of a restore point.
* Data Size — the amount of processed VM data.
* Backup Size — the amount of backed-up VM data.
* Data Reduction — the ratio between the data size and backup size.
* Date — the date and time when the restore point was created.
* Immutable Until — the date when the immutability period for the restore point will expire.
* Status — the result of the most recent [malware scan](backups_verify.md) performed for the restore point.

|  |
| --- |
| Tip |
| If a restore point is marked as Infected but you know that this point is clean, you can change its status manually. To do that, select the restore point and click Malware > Mark as clean. To learn how to manage infected restore points, see Veeam Backup & Replication User Guide, section [Managing Malware Status](https://helpcenter.veeam.com/docs/vbr/userguide/malware_detection_managing_status.html?ver=13). |

To view backup properties, do the following:

1. Open the Home view.
2. In the inventory pane, select Backups.
3. In the working area, right-click the necessary backup job and select Properties.

Alternatively, select the backup job and click Properties on the ribbon.

[![Viewing Backup Properties](images/pve_backups_view_properties.webp)](images/pve_backups_view_properties.webp "Viewing Backup Properties")


