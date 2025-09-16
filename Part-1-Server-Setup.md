# Part 1: Initial Server Setup & Configuration

This section covers the initial deployment of the Windows Server 2022 virtual machine in Azure, connecting to it, and installing the necessary roles and features.

## Key Steps:

1.  **Create an Azure Account:**
    *   Navigate to portal.azure.com.
    *   It is recommended to use a pay-as-you-go subscription over the free trial to access a wider range of VM sizes.

2.  **Deploy a Virtual Machine (VM):**
    *   Create a Resource → Create a Virtual Machine.
    *   **Image:** Windows Server 2022 Datacenter Azure Edition.
    *   **Size:** Standard_E2s_v3 (2 vCPU, 16 GiB memory).
    *   Create an administrator username and password.
    *   Set inbound ports to `None` since we will use Azure Bastion.

3.  **Connect with Azure Bastion & Set a Static IP:**
    *   In the VM's settings, navigate to Connect → Bastion and deploy it.
    *   Go to the Networking tab, click on the Network Interface, select `ipconfig1`, and change the Private IP address setting from Dynamic to **Static**. This is critical for a Domain Controller.

4.  **Install Roles and Features:**
    *   Once connected to the server, Server Manager will open.
    *   Click Manage → Add Roles and Features.
    *   Select and install the following:
        *   Active Directory Domain Services
        *   DHCP Server
        *   DNS Server
        *   Print and Document Services
        *   Web Server
    *   Group Policy Management is installed by default with Active Directory Domain Services.
    *   Reboot the server after installation.

5.  **Deallocating the VM to Save Costs:**
    *   To avoid unnecessary charges, **STOP** the VM in the Azure portal when not in use. This deallocates the CPU and memory resources.
    *   For long-term storage, you will still be charged for the disk. To eliminate all costs, delete the entire resource group.
