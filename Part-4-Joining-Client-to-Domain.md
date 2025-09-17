# Part 4: Joining a Client PC to the Active Directory Domain

This section covers the essential process of adding a new computer to your network and joining it to the Active Directory domain. This is a core task for any system administrator, as it allows the computer to be managed centrally by the Domain Controller. We will also cover the difference between local and domain accounts and how to recover deleted objects from Active Directory.

Before we begin, it's important to understand the difference between a PC in a **Workgroup** versus a **Domain**:
*   **Workgroup:** This is a peer-to-peer network where each computer manages its own user accounts and security. There is no central control. This is common for home networks.
*   **Domain:** This is a client-server network where user accounts, security, and policies are managed centrally by a Domain Controller. This allows for unified login credentials and the application of settings across the entire organization. Our goal is to move our new PC from a workgroup to our `lab.local` domain.

## Key Steps:

1.  **Create the Client Virtual Machine:**
    *   Navigate to the Azure portal and select **Create a resource** → **Virtual Machine**.
    *   **Resource Group:** Select the same resource group you created for your Domain Controller (`rg-labtest-1`).
    *   **Virtual machine name:** `LAB-PC`.
    *   **Image:** For consistency, we will use **Windows Server 2022 Datacenter: Azure Edition Hotpatch**, but in a real environment, this would typically be a client OS like Windows 11.
    *   **Subnet:** Ensure it is on the same subnet as your Domain Controller. The default should be correct.
    *   **Administrator Account:** Create a new local administrator username and password for this machine.
    *   **Inbound port rules:** Set "Public inbound ports" to **None**, as we will connect via Bastion.
    *   Review and create the VM.

2.  **Configure DNS for Domain Discovery:**
    *   This is the most critical step. For `LAB-PC` to find the `lab.local` domain, it must use our Domain Controller for DNS.
    *   Navigate to your new `LAB-PC` VM in Azure.
    *   In the left-hand menu, select **Networking**.
    *   Click on the **Network Interface** link.
    *   In the Network Interface menu, select **DNS servers**.
    *   Change the setting from "Inherit from virtual network" to **Custom**.
    *   In the "Add DNS server" field, enter the private IP address of your Domain Controller: **10.0.0.4**.
    *   Click **Save**. A restart of the network interface will be required.

    *   **Crucial Note:** In a traditional on-premises network, your DHCP server would automatically provide this DNS information to any new computer. Because we are in a simplified Azure VNet, we must manually tell the client PC where to find the domain's DNS server.

3.  **Join the PC to the Domain:**
    *   Connect to `LAB-PC` using Azure Bastion.
    *   Once logged in, search for and open the **Settings** app.
    *   Go to **System** → **About** → **Advanced system settings**.
    *   In the "Computer Name" tab, click the **Change...** button.
    *   Under "Member of," switch from "Workgroup" to **Domain:** and type `lab.local`.
    *   Click OK. You will be prompted for credentials with permission to join a computer to the domain. Use your domain administrator account (e.g., `LAB\Administrator`) and its password.
    *   You will receive a "Welcome to the lab.local domain" message. You must **restart the computer** for the changes to take effect.

4.  **Verify the Domain Join and Organize in AD:**
    *   After `LAB-PC` reboots, connect to it again.
    *   Open Command Prompt and test connectivity by pinging your Domain Controller *by name*:
        ```
        ping lab-vm
        ```
        If you get a reply, it means DNS is working and the join was successful.
    *   Now, switch back to your Domain Controller VM (`lab-vm`).
    *   Open **Active Directory Users and Computers**.
    *   Click on the **"Computers"** container. You should now see your `LAB-PC` object listed.
    *   To keep things organized, **drag the `LAB-PC` object** from the default "Computers" container into your `BranchOne\Computers` OU.

5.  **Bonus: Recovering a Deleted Computer with the AD Recycle Bin:**
    *   What if a computer is deleted from AD by mistake? First, you must enable the AD Recycle Bin (it is off by default).
    *   On your Domain Controller, search for and open the **Active Directory Administrative Center (ADAC)**.
    *   Right-click on your domain (`lab.local`) in the left pane and select **"Enable Recycle Bin"**. *Note: This action is irreversible.*
    *   Now, if you go back to ADUC and delete the `LAB-PC` object, you can recover it.
    *   In the **ADAC**, you will now see a **"Deleted Objects"** container. Open it, right-click the deleted computer, and select **Restore**. It will be restored to its original OU.
