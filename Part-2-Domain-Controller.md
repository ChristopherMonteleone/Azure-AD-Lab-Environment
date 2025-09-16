# Part 2: Promoting the Server to a Domain Controller

With the necessary roles installed, we now promote our server to become the Domain Controller (DC) for our new domain. The DC is the heart of Active Directory, managing authentication and security for the entire domain.

## Key Steps:

1.  **Start the Promotion Process:**
    *   Start the VM, connect via Bastion, and open Server Manager.
    *   Click the notifications flag (a yellow triangle) in the top right and select **"Promote this server to a domain controller"**.

2.  **Configure the Domain:**
    *   In the deployment configuration wizard, select **"Add a new forest"**.
    *   Enter a **Root domain name**. A common practice for internal labs is to use a `.local` suffix (e.g., `lab.local`).
    *   Set a Directory Services Restore Mode (DSRM) password. This is a crucial password for recovery scenarios, so be sure to save it.
    *   Proceed through the wizard with the default options and click **Install**.

3.  **Server Reboot:**
    *   The server will automatically reboot to complete the promotion process. Once it is back online, it will be a fully functional Domain Controller for the `lab.local` domain.

4.  **Exploring Active Directory Users and Computers (ADUC):**
    *   From the Start Menu, search for and open "Active Directory Users and Computers".
    *   You will see your domain (`lab.local`). The folders inside are called **Organizational Units (OUs)**. Users, computers, and groups are referred to as **Objects**.

5.  **Creating the Initial OU Structure:**
    *   Right-click the domain (`lab.local`) → New → Organizational Unit.
    *   Create a top-level OU named `BranchOne`.
    *   Inside the `BranchOne` OU, create three more OUs: `Users`, `Computers`, and `Groups`. This is a best practice for organizing objects and applying specific policies.
