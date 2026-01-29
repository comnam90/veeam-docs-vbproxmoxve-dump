---
title: "File-Level Recovery"
product: "vbproxmoxve"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbproxmoxve/userguide/restore_how_flr.html"
last_updated: "8/21/2025"
product_version: "13.3.0.237"
---

# File-Level Recovery


To recover VM files and folders from a backup, Veeam Backup & Replication performs the following steps:

1. Mounts disks of the backed-up VM to the [mount host](https://helpcenter.veeam.com/docs/vbr/userguide/guest_file_recovery.html?ver=13#mount-hosts) specified for the recovery operation.
2. Launches the Veeam Backup Browser.

The Veeam Backup Browser displays the directory structure of the backed-up VM. In the browser, you select the necessary files and folders to restore.

1. Restores the selected files and folders to the original location or to a new location.
2. Detaches the disks from the mount host.

To learn how to recover individual VM files and folders, see [Performing File-Level Restore](vm_guest_restore.md).


