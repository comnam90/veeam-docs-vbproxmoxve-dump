---
title: "Considerations and Limitations"
product: "vbproxmoxve"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbproxmoxve/userguide/limitations.html"
last_updated: "1/12/2026"
product_version: "13.3.0.237"
---

# Considerations and Limitations


When you plan to use Veeam Plug-in for Proxmox VE, keep in mind the following limitations and considerations.

Configuration

When configuring Veeam Plug-in for Proxmox VE, consider the following:

* Veeam Plug-in for Proxmox VE supports Proxmox Virtual Environment deployments created using the official ISO image provided by Proxmox only.
* Veeam Plug-in for Proxmox VE supports only the /bin/bash shell to perform management operations with the Proxmox VE server.
* Veeam Plug-in for Proxmox VE supports custom certificates installed on the Proxmox VE server if either of the following conditions is met:

* The full certificate chain has been uploaded to the Proxmox VE server.
* The backup infrastructure components, such as workers, are able to connect to the CA server and validate the certificate.

* Veeam Plug-in for Proxmox VE does not support Online Certificate Status Protocol (OCSP) certificates to access the Proxmox VE server.
* Veeam Plug-in for Proxmox VE does not support Proxmox Virtual Environment deployments with S3 buckets connected as storage.
* Veeam Plug-in for Proxmox VE does not support credentials of the [SSH Private Keys type](https://helpcenter.veeam.com/docs/vbr/userguide/credentials_manager_linux_pubkey.html?ver=13) to access the Proxmox VE server.
* Veeam Plug-in for Proxmox VE does not support user accounts with multi-factor authentication to access the Proxmox VE server.

* Veeam Plug-in for Proxmox VE does not support the IPv6 protocol.

* The Proxmox VE server must be able to establish a direct IP connection to the backup server. Connections through NAT gateways are not supported.

* Before you [add a Proxmox VE server](sever_add.md) to the backup infrastructure, ensure that it has been assigned a unique Proxmox VE system UUID and its name does not contain an FQDN.

* If you want to protect VMs that reside in a Proxmox VE cluster, all nodes of these cluster must be added to the backup infrastructure separately. Adding clusters as standalone entities is not supported.
* After you add nodes of a cluster to the backup infrastructure, you must not change the name of the cluster in the Proxmox VE administration portal.
* After you make changes to your Proxmox VE environment (for example, you migrate a VM between cluster nodes), these changes may not appear in Veeam Backup & Replication immediately — the data synchronization process between the backup server and the Proxmox VE server may take up to 15 minutes to complete. You can speed up the data synchronization process by [rescanning the Proxmox VE server](server_rescan.md).

Backup Repositories

When managing backup repositories, consider that Veeam Plug-in for Proxmox VE does not support storing backups in [HPE Cloud Bank Storage](https://helpcenter.veeam.com/docs/vbr/userguide/storeonce_supported_features.html?ver=13#cloud-bank-storage) repositories. However, you can use them for [storing copies of backups](backups_copy.md) created with Veeam Plug-in for Proxmox VE.

Workers

When configuring workers, consider the following:

* The default local storage must be enabled on all hosts where worker VMs will be deployed. If you cannot use the default storage in your environment, contact [Veeam Customer Support](export_logs.md).
* The storage where system files of workers will be stored must [support snapshots](https://pve.proxmox.com/wiki/Storage).
* For VLAN-tagged environments, the VLAN ID must be manually assigned to worker VMs after they are deployed or redeployed.
* When transferring VM data to and from backup repositories, workers rely on the Hot-Add and NBD transport modes.

Backup

When protecting Proxmox VE resources, consider the following:

* Veeam Plug-in for Proxmox VE does not support backup of LXC containers.

* Veeam Plug-in for Proxmox VE does not support backup of VM templates.
* Veeam Plug-in for Proxmox VE does not support backup of VMs created from [templates as linked clones](https://pve.proxmox.com/wiki/VM_Templates_and_Clones#Linked_Clone). Backup of full clones is supported.
* Veeam Plug-in for Proxmox VE does not support backup of VMs with the same BIOS UUID.

* Veeam Plug-in for Proxmox VE does not support backup of iSCSI disks. If iSCSI disks are attached to a VM included into a backup job, these disks will be skipped from processing.
* Veeam Plug-in for Proxmox VE does not support backup of directly attached (passthrough) disks. If such disks are attached to a VM included into a backup job, these disks will be skipped from processing.
* Veeam Plug-in for Proxmox VE does not support backup of VM permissions granted to users, user groups and API tokens.

* Veeam Plug-in for Proxmox VE does not support backup of VMs that store their disks in the BTRFS and custom storage. All other [Proxmox VE storage types](https://pve.proxmox.com/wiki/Storage) are supported.
* The number of concurrent backup operations performed in each storage is limited to 4 to avoid excessive load on the production environment. To change the limit, contact [Veeam Customer Support](export_logs.md).

* Veeam Plug-in for Proxmox VE does not support VM replication.

Restore

When restoring Proxmox VE resources, consider the following:

* Starting from version 9, Proxmox VE supports the [snapshot-as-volume-chain](https://pve.proxmox.com/wiki/Storage%3A_LVM) functionality for some storage types. Since this functionality is available for VMs using QEMU version 10 and later, Veeam Plug-in for Proxmox VE is not able to restore VMs using an earlier QEMU version to a storage with the Allow Snapshots as Volume-Chain setting enabled. To work around the issue, see [this Veeam KB article](https://www.veeam.com/kb4773).

* For backups stored in [HPE StoreOnce Cloud Bank Storage](https://helpcenter.veeam.com/docs/vbr/userguide/storeonce_supported_features.html?ver=13) repositories, Veeam Plug-in for Proxmox VE supports only file-level restore.
* Veeam Plug-in for Proxmox VE supports [Instant Recovery](restore_instant.md) of Proxmox VE VMs to the VMware environment with the following limitations:

* UEFI VMs with MBR cannot be restored.
* Restored VMs may have an incorrect number of cores per vCPU assigned.
* Static IP addresses are not restored for Windows VMs.

* Veeam Plug-in for Proxmox VE does not support restore of VMs to the BTRFS and custom storage.


