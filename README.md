# Azure Virtual Machine Deployment & Secure Connectivity Lab

## Project Overview
This project demonstrates the deployment, configuration, and secure management of cross-region cloud infrastructure within Microsoft Azure. The environment consists of both Linux and Windows Server virtual instances managed via secure, modern remote connectivity standards.

## Infrastructure Architecture
*   **Linux Environment:** Ubuntu Server deployed in the `West US 2` region, configured within `3mtt-linux-vm-vnet`.
*   **Windows Environment:** Windows Server 2022 deployed in the `Australia East` region, configured within its local virtual network.
*   **Network Integration:** Established Global Virtual Network Peering (`windows-to-linux`) to link the North American and Australian infrastructures, enabling secure cross-region transit traffic.

---

## Remote Management & Connectivity Methods

### 1. Secure Shell (SSH)
*   **Target:** `3mtt-linux-vm` (Ubuntu)
*   **Protocol:** SSH (Port 22)
*   **Description:** Verified remote administration of the headless Linux environment by establishing a direct command-line session via terminal to execute core system operations.

### 2. Remote Desktop Protocol (RDP) via Azure Bastion
*   **Target:** `3mtt-windows-vm` (Windows Server)
*   **Protocol:** RDP (Port 3389) encapsulated inside HTTPS (Port 443)
*   **Description:** Utilized Azure Bastion to stream a full graphical user interface (GUI) desktop session securely inside a standard web browser interface. This eliminates the exposure of public RDP ports to the public internet.

---

## Lab Troubleshooting Guide (Real-World Resolutions)

During deployment, several architectural restrictions were encountered and successfully remediated:

### Issue 1: Bastion Host Provisioning Failure
*   **Symptom:** Initial deployment of the Bastion service resulted in a stuck `Provisioning State: Failed` error.
*   **Resolution:** Completely purged the corrupted Bastion resource, manually cleaned up the underlying virtual network placeholders, and re-executed a custom deployment template to successfully bring the host online.

### Issue 2: Cross-Region Resource Isolation
*   **Symptom:** The Windows VM was deployed to a different geographical region (`Australia East`) than the Linux VM (`West US 2`), preventing them from sharing a local virtual network.
*   **Resolution:** Configured **Global VNet Peering** between the two distinct networks. Adjusted the peering configuration flags to allow forwarded transit traffic, bridging the global distance and enabling unified network visibility.
