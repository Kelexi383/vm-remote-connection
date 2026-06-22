# Azure Virtual Machine Setup and Remote Connection Learning Program

## Project Overview
This project documents the fundamental process of deploying, securing, and remotely accessing a cloud-based Linux virtual machine using Microsoft Azure. 

## Learning Program Details
* **Training Program:** 3MTT Cloud Computing Training Program
* **Platform:** Darey.io / 3mtt-darey
* **Environment:** Microsoft Azure & Windows Local Client

---

## Task 1 & 6: Configure Networking and Secure the Environment
During the deployment of the `Standard_B2ats_v2` Ubuntu Linux virtual machine, inbound Network Security Group (NSG) firewall rules were configured. 

To implement security best practices and prevent unauthorized access, the inbound rule for **SSH (Port 22)** was restricted from *Any* to my specific local network public IP address only. This blocks any unauthorized connections from outside my designated physical location.

* **Inbound Protocol:** TCP
* **Destination Port:** 22 (SSH)
* **Action:** Allow
* **Source Restriction:** Restricted to local Admin Public IP

---

## Task 2: Identify Connection Endpoints
The virtual machine was successfully provisioned with a dedicated Azure public endpoint:
* **VM Operating System:** Ubuntu Server 24.04 LTS
* **Virtual Machine Size:** Standard_B2ats_v2
* **Target Connection Endpoint (Public IP):** [INSERT_YOUR_VM_PUBLIC_IP_HERE]

---

## Task 4 & 5: Establish Linux Connection & Verify System Access
Using the native Windows Command Prompt client, a secure connection was initialized using standard SSH password authentication protocols:

```bash
ssh Darey3mttAzure@[INSERT_YOUR_VM_PUBLIC_IP_HERE]
System administrative capabilities were successfully verified within the cloud environment by executing the following commands:

whoami - Confirmed system identity as the administrative user Darey3mttAzure.

uptime - Monitored host server health and uptime tracking.```

_##Task 7: Manage Remote Sessions_
To enforce proper capacity management and cloud resource security, the remote interactive terminal connection was terminated cleanly using the native Linux exit command rather than abruptly terminating the window terminal client.
