---
title: "Synthetic Full Backup"
product: "vbproxmoxve"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbproxmoxve/userguide/synthetic_full_backup.html"
last_updated: "11/17/2025"
product_version: "13.3.0.237"
---

# Synthetic Full Backup


In some situations, running active full backups periodically may not be an option. Active full backups are resource-intensive and consume considerable amount of network bandwidth. As an alternative, you can create synthetic full backups that also produce VBK files and contain data of the whole VM. However, while creating synthetic full backups, Veeam Backup & Replication does not retrieve VM data from the cluster but processes the data that is already stored in the backup repository.

To create a synthetic full backup, Veeam Backup & Replication performs the following operations:

1. Veeam Backup & Replication creates a regular incremental backup and adds it to the backup chain.

![Synthetic Full Backup](images/vplugin_synthetic_fulls_how_1.webp)

1. Veeam Backup & Replication creates a new synthetic full backup using backup files that are already available in the backup chain, including the newly created incremental backup file.

![Synthetic Full Backup](images/vplugin_synthetic_fulls_how_2.webp)

1. Veeam Backup & Replication deletes the created incremental backup as its data is already incorporated in the synthetic full backup.

![Synthetic Full Backup](images/vplugin_synthetic_fulls_how_3.webp)

When creating a synthetic full backup, Veeam Backup & Replication starts a new backup chain for the VM. All further created incremental backups use the latest full backup file as a new starting point. The old full backup file from the old backup chain remains on disk until it is automatically deleted according to the retention policy.

|  |
| --- |
| Note |
| The synthetic full backup session starts only on the day when the backup job is scheduled. For example, if you schedule the backup job to run at 12:00 AM Sunday through Friday, and schedule synthetic full backup to be created on Saturday, Veeam Backup & Replication will never start a backup job session that will produce a synthetic full backup. |

If the backup job is not scheduled to run automatically or is disabled, Veeam Backup & Replication will not perform synthetic full backup. If a regular backup session and a synthetic full backup session are scheduled on the same day, Veeam Backup & Replication will produce a synthetic full backup — an incremental backup that should have been created by the regular backup session will not be added to the backup chain. However, if you run the backup job again on the same day manually, Veeam Backup & Replication will perform incremental backup in a regular manner.

Related Topics

[Creating Backup Jobs](backup_job_create_advanced.md#advanced_job_settings)


