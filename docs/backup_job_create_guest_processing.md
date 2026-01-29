---
title: "Step 5. Specify Guest Processing Options"
product: "vbproxmoxve"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbproxmoxve/userguide/backup_job_create_guest_processing.html"
last_updated: "10/21/2025"
product_version: "13.3.0.237"
---

# Step 5. Specify Guest Processing Options


At the Guest Processing step of the wizard, you can specify the following settings:

* [Enable application-aware processing](backup_job_create_gp_applications.md) — to create transactionally consistent backups that will guarantee proper recovery of VM applications, without data loss.

For VMs running Microsoft SQL Server, Oracle Server or PostgreSQL Server applications, you can also instruct Veeam Backup & Replication to periodically back up transaction logs. This will allow you to restore your databases to specific points in time as described in the Veeam Enterprise Manager User Guide, section [Restoring Point-in-Time State](https://helpcenter.veeam.com/docs/vbr/explorers/vesql_restoring_pit.html?ver=13).

* [Enable guest file system indexing and malware detection](backup_job_create_gp_indexing.md) — to create a catalog of guest OS files that will allow you to search for specific items during file-level restore. This will also allow you to receive reports about malware files and suspicious system activity detected on VMs included into the backup scope.
* [Choose guest interaction proxies](backup_job_create_gp_proxy.md) — to select specific servers that Veeam Backup & Replication will use when communicating with guest OSes of VMs included into the backup scope.
* [Manage VM guest OS credentials](backup_job_create_gp_credentials.md) — to specify credentials that Veeam Backup & Replication will use to access guest OSes of all VMs included into the backup scope.

Considerations and Limitations

If you enable application-aware processing or guest files system indexing, consider the following:

* Veeam Plug-in for Proxmox VE will not be able to [use Kerberos authentication](https://helpcenter.veeam.com/docs/vbr/userguide/kerberos_authentication.html?ver=13) while connecting to guest OSes of the processed VMs.

![Step 5. Specify Guest Processing Settings](images/pve_backup_job_create_guest_processing.webp)

Related Topics

* [Requirements and limitations for PostgreSQL WAL files backup](https://helpcenter.veeam.com/docs/vbr/userguide/postgresql_backup.html?ver=13)
* [Requirements and limitations for Oracle archived redo logs backup](https://helpcenter.veeam.com/docs/vbr/userguide/oracle_backup.html?ver=13)


