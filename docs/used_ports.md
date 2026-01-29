---
title: "Ports"
product: "vbproxmoxve"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbproxmoxve/userguide/used_ports.html"
last_updated: "12/4/2025"
product_version: "13.3.0.237"
---

# Ports


Veeam Backup & Replication automatically creates firewall rules for the ports required to allow communication between the Proxmox VE server, workers and the backup server.

Workers

The following table describes network ports that must be open to ensure proper communication of workers with other backup infrastructure components.

| From | To | Protocol | Port | Notes |
| --- | --- | --- | --- | --- |
| Worker | Proxmox VE server | TCP/HTTPS | 8006 | Used to communicate with the REST API service running on the Proxmox VE server. |
| Proxmox VE server | SSH | 22 | Used to communicate with Proxmox VE server. |
| Backup server | TCP | 10006 | Used to communicate with the backup server. |
| Backup server | TCP | 2500 to 3300 | Default range of ports used for malware detection metadata transfer. |
| Veeam backup repository or [gateway server](https://helpcenter.veeam.com/docs/vbr/userguide/gateway_server.html?ver=13) | TCP | 2500 to 3300 | Default range of ports used as transmission channels for jobs and restore sessions. For each TCP connection that a job uses, one port from this range is assigned. |
| TCP | 6162 | Default port used by Veeam Transport Service (on Linux  servers) or Veeam Data Mover Service (on Windows servers). |
| Veeam Update Repository  [Amazon CloudFront](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/Introduction.html) | TCP/HTTPS | 443 | Used to download worker deployment packages.  Note: Veeam Update Repository uses the Amazon CloudFront service to distribute traffic when downloading product updates. |

Backup Server

The following table describes network ports that must be open to ensure proper communication of the backup server with other backup infrastructure components.

| From | To | Protocol | Port | Notes |
| --- | --- | --- | --- | --- |
| Backup server | Worker | TCP | 19000 | Used to communicate with workers. |
| Worker | TCP/HTTPS | 443 | Used by the Platform Service to enable communication with the Veeam Updater service on the worker. |
| Backup server | TCP/HTTPS | 6172 | Used by the Platform Service to enable communication with the Veeam Backup & Replication database. |
| Proxmox VE server | TCP/HTTPS | 8006 | Used to communicate with the REST API service running on the Proxmox VE server. |
| Proxmox VE server | SSH | 22 | Used to communicate with the Proxmox VE server. |
| FLR helper appliance | TCP | 22 | Used to connect to the helper appliance during file-level restore. |

|  |
| --- |
| Note |
| For the list of ports used by the backup server to communicate with backup repositories, see the Veeam Backup & Replication User Guide, section [Used Ports](https://helpcenter.veeam.com/docs/vbr/userguide/used_ports.html?ver=13#backup-repositories). |

Guest Processing Components

Connections with Non-Persistent Runtime Components

The following tables describe network ports that must be opened to ensure proper communication of the backup server and backup infrastructure components with the non-persistent runtime components deployed inside the VM guest OS for application-aware processing and indexing.

| From | To | Protocol | Port | Notes |
| --- | --- | --- | --- | --- |
| Backup server | VM guest OS (Linux) | TCP | 22 | Default SSH port used as a control channel. |
| TCP | 2500 to 3300 | Default range of ports used as transmission channels for log shipping. |
| VM guest OS (Microsoft Windows) | TCP | 445 135 | Required to deploy the runtime coordination process on the VM guest OS. |
| TCP | 2500 to 3300 | Default range of ports used as transmission channels for log shipping. |
| TCP | 49152 to 65535 | Dynamic RPC port range for Microsoft Windows 2008 and later. For more information, see [this Microsoft KB article](https://support.microsoft.com/kb/929851/en-us).  Used by the runtime process deployed inside the VM for guest OS interaction.  Note: If you use default Microsoft Windows firewall settings, you do not need to configure dynamic RPC ports. During setup, Veeam Backup & Replication automatically creates a firewall rule for the runtime process. If you use firewall settings other than default ones or application-aware processing fails with the "RPC function call failed" error, you need to configure dynamic RPC ports. For more information on how to configure RPC dynamic port allocation to work with firewalls, see [this Microsoft KB article](https://support.microsoft.com/en-us/help/154596/how-to-configure-rpc-dynamic-port-allocation-to-work-with-firewalls). |
| Guest interaction proxy | TCP | 6190 | Used for communication with the guest interaction proxy. |
| TCP | 6290 | Used as a control channel for communication with the guest interaction proxy. |
| TCP | 445 | Port used as a transmission channel. |
| Guest interaction proxy | VM guest OS (Linux) | TCP | 22 | Default SSH port used as a control channel. |
| TCP | 2500 to 3300 | Default range of ports used as transmission channels for log shipping. |
| VM guest OS (Microsoft Windows) | TCP | 445 135 | Required to deploy the runtime coordination process on the VM guest OS. |
| TCP | 2500 to 3300 | Default range of ports used as transmission channels for log shipping. |
| TCP | 49152 to 65535 | Dynamic RPC port range for Microsoft Windows 2008 and later. For more information, see [this Microsoft KB article](https://support.microsoft.com/kb/929851/en-us).  Used by the runtime process deployed inside the VM for guest OS interaction.  Note: If you use default Microsoft Windows firewall settings, you do not need to configure dynamic RPC ports. During setup, Veeam Backup & Replication automatically creates a firewall rule for the runtime process. If you use firewall settings other than default ones or application-aware processing fails with the "RPC function call failed" error, you need to configure dynamic RPC ports. For more information on how to configure RPC dynamic port allocation to work with firewalls, see [this Microsoft KB article](https://support.microsoft.com/en-us/help/154596/how-to-configure-rpc-dynamic-port-allocation-to-work-with-firewalls). |
| VM guest OS | Guest interaction proxy or backup server | TCP | 2500 to 3300 | Default range of ports used as transmission channels for log shipping.  Note: This range of ports applies to newly installed Veeam Backup & Replication starting from version 10.0, without upgrade from previous versions. If you have upgraded from an earlier version of the product, the range of ports from 2500 to 5000 applies to the already added components. |
| TCP | 6162 | Default port used by Veeam Transport Service (on Linux  servers) or Veeam Data Mover Service (on Windows servers). |

Connections with Persistent Agent Components

The following table describes network ports that must be opened to ensure proper communication of the guest interaction with the persistent agent components deployed inside the VM guest OS for application-aware processing and indexing.

| From | To | Protocol | Port | Notes |
| --- | --- | --- | --- | --- |
| Backup server (Windows-based) or Guest interaction proxy (Windows-based) | VM guest OS (Microsoft Windows) | TCP | 6160 11731 | Default port and failover port used by Veeam Installer Service. |
| TCP | 6173 2500 | Used by the Veeam Guest Helper for guest OS processing and file-level restore. |

Log Shipping Components

The following tables describe network ports that must be opened to ensure proper communication between log shipping components.

* [Log Shipping Server Connections](#log_shipping_server_connections)
* [MS SQL Guest OS Connections](#sql_guest_os_connections)
* [Oracle Guest OS Connections](#oracle_guest_os_connections)
* [PostgreSQL Guest OS Connections](#postgresql_guest_os_connections)

Log Shipping Server Connections

| From | To | Protocol | Port | Notes |
| --- | --- | --- | --- | --- |
| Backup server | Log shipping server | TCP | 445 135 | Required for deploying Veeam Backup & Replication components. |
| TCP | 6160 | Default port used by Veeam Installer Service. |
| TCP | 6162 | Default port used by Veeam Transport Service (on Linux  servers) or Veeam Data Mover Service (on Windows servers). |
| TCP | 49152 to 65535 | Dynamic RPC port range for Microsoft Windows 2008 and later. For more information, see [this Microsoft KB article](https://support.microsoft.com/kb/929851/en-us).  Note: If you use default Microsoft Windows firewall settings, you do not need to configure dynamic RPC ports. During setup, Veeam Backup & Replication automatically creates a firewall rule for the runtime process. If you use firewall settings other than default ones or application-aware processing fails with the "RPC function call failed" error, you need to configure dynamic RPC ports. For more information on how to configure RPC dynamic port allocation to work with firewalls, see [this Microsoft KB article](https://support.microsoft.com/en-us/help/154596/how-to-configure-rpc-dynamic-port-allocation-to-work-with-firewalls). |
| Log shipping server | Backup repository or gateway server | TCP | 2500 to 3300 | Default range of ports used for communication with a backup repository and transfer log backups.  By default, the log shipping server connects to the backup repository. However, if the target repository uses a gateway server, the connection will be established with that instead.For more information, see the Veeam Backup & Replication User Guide, section [Gateway Servers](https://helpcenter.veeam.com/docs/vbr/userguide/gateway_server.html?ver=13).  Note: This range of ports applies to newly installed Veeam Backup & Replication starting from version 10.0, without upgrade from previous versions. If you have upgraded from an earlier version of the product, the range of ports from 2500 to 5000 applies to the already added components. |
| TCP | 6162 | Default port used by Veeam Transport Service (on Linux  servers) or Veeam Data Mover Service (on Windows servers). |

MS SQL Guest OS Connections

| From | To | Protocol | Port | Notes |
| --- | --- | --- | --- | --- |
| Guest interaction proxy | MS SQL VM guest OS | TCP | 445 135 | [Applies to non-persistent runtime components only] Required for deploying Veeam Backup & Replication components including Veeam Log Shipper runtime component. |
| TCP | 6160, 11737 | [Applies to persistent agent components only] Default port and failover port used by Veeam Installer Service. |
| TCP | 2500 to 3300 | Default range of ports used for communication with a guest OS.  Note: This range of ports applies to newly installed Veeam Backup & Replication starting from version 10.0, without upgrade from previous versions. If you have upgraded from an earlier version of the product, the range of ports from 2500 to 5000 applies to the already added components. |
| TCP | 49152 to 65535 | Dynamic RPC port range for Microsoft Windows 2008 and later. For more information, see [this Microsoft KB article](https://support.microsoft.com/kb/929851/en-us).  Note: If you use default Microsoft Windows firewall settings, you do not need to configure dynamic RPC ports. During setup, Veeam Backup & Replication automatically creates a firewall rule for the runtime process. If you use firewall settings other than default ones or application-aware processing fails with the "RPC function call failed" error, you need to configure dynamic RPC ports. For more information on how to configure RPC dynamic port allocation to work with firewalls, see [this Microsoft KB article](https://support.microsoft.com/en-us/help/154596/how-to-configure-rpc-dynamic-port-allocation-to-work-with-firewalls). |
| TCP | 6167 | Used by the Veeam Log Shipping Service for preparing the database and taking logs. |
| MS SQL VM guest OS | Guest interaction proxy | TCP | 2500 to 3300 | Default range of ports used for communication with a guest interaction proxy.  Note: This range of ports applies to newly installed Veeam Backup & Replication starting from version 10.0, without upgrade from previous versions. If you have upgraded from an earlier version of the product, the range of ports from 2500 to 5000 applies to the already added components. |
| TCP | 6162 | Default port used by Veeam Transport Service (on Linux  servers) or Veeam Data Mover Service (on Windows servers). |
| Backup repository | TCP | 2500 to 3300 | Default range of ports used for communication with a backup repository and transfer log backups. Should be opened if log shipping servers are not used in the infrastructure and the MS SQL server has a direct connection to the backup repository.  Note: This range of ports applies to newly installed Veeam Backup & Replication starting from version 10.0, without upgrade from previous versions. If you have upgraded from an earlier version of the product, the range of ports from 2500 to 5000 applies to the already added components. |
| TCP | 6162 | Default port used by Veeam Transport Service (on Linux  servers) or Veeam Data Mover Service (on Windows servers). |
| Log shipping server | TCP | 2500 to 3300 | Default range of ports used for communication with a log shipping server and transfer log backups.  Note: This range of ports applies to newly installed Veeam Backup & Replication starting from version 10.0, without upgrade from previous versions. If you have upgraded from an earlier version of the product, the range of ports from 2500 to 5000 applies to the already added components. |

Oracle Guest OS Connections

| From | To | Protocol | Port | Notes |
| --- | --- | --- | --- | --- |
| Backup server or Guest interaction proxy | Oracle VM guest OS (Microsoft Windows) | TCP | 135 445 | [Applies to non-persistent runtime components only] Required for deploying Veeam Backup & Replication components including Veeam Log Shipper runtime component. |
| TCP | 6160, 11737 | [Applies to persistent agent components only] Default port and failover port used by Veeam Installer Service. |
| TCP | 2500 to 3300 | Default range of ports used for communication with a guest OS.  Note: This range of ports applies to newly installed Veeam Backup & Replication starting from version 10.0, without upgrade from previous versions. If you have upgraded from an earlier version of the product, the range of ports from 2500 to 5000 applies to the already added components. |
| TCP | 49152 to 65535 | [Applies to non-persistent runtime components only] Dynamic RPC port range for Microsoft Windows 2008 and later. For more information, see [this Microsoft KB article](https://support.microsoft.com/kb/929851/en-us).  Note: If you use default Microsoft Windows firewall settings, you do not need to configure dynamic RPC ports. During setup, Veeam Backup & Replication automatically creates a firewall rule for the runtime process. If you use firewall settings other than default ones or application-aware processing fails with the "RPC function call failed" error, you need to configure dynamic RPC ports. For more information on how to configure RPC dynamic port allocation to work with firewalls, see [this Microsoft KB article](https://support.microsoft.com/en-us/help/154596/how-to-configure-rpc-dynamic-port-allocation-to-work-with-firewalls). |
| TCP | 6167 | Used by the Veeam Log Shipping Service for preparing the database and taking logs. |
| Oracle VM guest OS (Linux) | TCP | 22 | Default SSH port used as a control channel. |
| TCP | 2500 to 3300 | Default range of ports used for communication with a guest OS.  Note: This range of ports applies to newly installed Veeam Backup & Replication starting from version 10.0, without upgrade from previous versions. If you have upgraded from an earlier version of the product, the range of ports from 2500 to 5000 applies to the already added components. |
| TCP | 6162 | [Applies to persistent agent components only] Default Management Agent port. Required if it is used as a control channel instead of SSH. |
| Oracle VM guest OS | Guest interaction proxy or backup server | TCP | 2500 to 3300 | Default range of ports used for communication with a guest interaction proxy.  Note: This range of ports applies to newly installed Veeam Backup & Replication starting from version 10.0, without upgrade from previous versions. If you have upgraded from an earlier version of the product, the range of ports from 2500 to 5000 applies to the already added components. |
| TCP | 6162 | Default port used by Veeam Transport Service (on Linux  servers) or Veeam Data Mover Service (on Windows servers). |
| Backup repository | TCP | 2500 to 3300 | Default range of ports used for communication with a backup repository and transfer log backups. Should be opened if log shipping servers are not used in the infrastructure and the Oracle server has a direct connection to the backup repository.  Note: This range of ports applies to newly installed Veeam Backup & Replication starting from version 10.0, without upgrade from previous versions. If you have upgraded from an earlier version of the product, the range of ports from 2500 to 5000 applies to the already added components. |
| TCP | 6162 | Default port used by Veeam Transport Service (on Linux  servers) or Veeam Data Mover Service (on Windows servers). |
| Log shipping server | TCP | 2500 to 3300 | Default range of ports used for communication with a log shipping server and transfer log backups.  Note: This range of ports applies to newly installed Veeam Backup & Replication starting from version 10.0, without upgrade from previous versions. If you have upgraded from an earlier version of the product, the range of ports from 2500 to 5000 applies to the already added components. |

PostgreSQL Guest OS Connections

| From | To | Protocol | Port | Notes |
| --- | --- | --- | --- | --- |
| Backup server | PostgreSQL VM guest OS | TCP | 22 | [Applies to non-persistent runtime components only] Default SSH port used as a control channel. |
| TCP | 2500 to 3300 | Default range of ports used for communication with a guest OS. |
| TCP | 6162 | [Applies to persistent agent components only] Default Management Agent port. Required if it is used as a control channel instead of SSH. |
| PostgreSQL VM guest OS | Backup server | TCP | 2500 to 3300 | Default range of ports used for communication with a guest interaction proxy.  Note: This range of ports applies to newly installed Veeam Backup & Replication starting from version 10.0, without upgrade from previous versions. If you have upgraded from an earlier version of the product, the range of ports from 2500 to 5000 applies to the already added components. |
| TCP | 6162 | Default port used by Veeam Transport Service (on Linux  servers) or Veeam Data Mover Service (on Windows servers). |
| Backup repository | TCP | 2500 to 3300 | Default range of ports used for communication with a backup repository and transfer log backups. Should be opened if log shipping servers are not used in the infrastructure and the PostgreSQL server has a direct connection to the backup repository.  Note: This range of ports applies to newly installed Veeam Backup & Replication starting from version 10.0, without upgrade from previous versions. If you have upgraded from an earlier version of the product, the range of ports from 2500 to 5000 applies to the already added components. |
| TCP | 6162 | Default port used by Veeam Transport Service (on Linux  servers) or Veeam Data Mover Service (on Windows servers). |
| Log shipping server | TCP | 2500 to 3300 | Default range of ports used for communication with a log shipping server and transfer log backups.  Note: This range of ports applies to newly installed Veeam Backup & Replication starting from version 10.0, without upgrade from previous versions. If you have upgraded from an earlier version of the product, the range of ports from 2500 to 5000 applies to the already added components. |


