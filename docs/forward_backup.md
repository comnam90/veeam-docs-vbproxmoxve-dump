---
title: "Forward Incremental Backup"
product: "vbproxmoxve"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbproxmoxve/userguide/forward_backup.html"
last_updated: "10/24/2025"
product_version: "13.3.0.237"
---

# Forward Incremental Backup


To create a backup chain for a VM protected by a backup job that is configured to produce full backups, Veeam Backup & Replication implements the forward incremental backup method:

1. During the first (full) backup session, Veeam Backup & Replication copies the full VM image and creates a full backup file in the backup repository. The full backup file becomes a starting point in the backup chain.
2. During subsequent backup sessions, Veeam Backup & Replication copies only those data blocks that have changed since the previous backup session, and stores these data blocks to incremental backup files in the backup repository. The content of each incremental backup file depends on the content of the full backup file and the preceding incremental backup files in the backup chain.

![Forward Incremental Backup](images/vplugin_backup_chain.webp)

1. On a day when the [synthetic full](synthetic_full_backup.md) or [active full](active_full_backup.md) backup is scheduled, Veeam Backup & Replication creates a full backup file and adds it to the backup chain. Incremental restore points produced after this full backup file use it as a new starting point.

![Forward Incremental Backup](images/vplugin_forward_incremental_chain.webp)


