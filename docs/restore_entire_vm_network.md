---
title: "Step 7. Configure Network Settings"
product: "vbproxmoxve"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbproxmoxve/userguide/restore_entire_vm_network.html"
last_updated: "10/24/2025"
product_version: "13.3.0.237"
---

# Step 7. Configure Network Settings


[This step applies only if you have selected the Restore to a new location, or with different settings option at the Restore Mode step of the wizard]

At the Network step of the wizard, choose a network to which the recovered VM will be connected. If you do not want to connect the VM to any virtual network, select the VM and click Disconnect.

For a network to be displayed in the list of available networks, it must be configured in the virtual environment as described in [Proxmox VE documentation](https://pve.proxmox.com/wiki/Network_Configuration).

![Step 7. Configure Network Settings](images/pve_restore_entire_vm_network.webp)


