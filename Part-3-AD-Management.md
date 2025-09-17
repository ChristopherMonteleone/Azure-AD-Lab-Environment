# Part 3: Managing Active Directory Users & Groups

This section covers the fundamental day-to-day tasks of a System Administrator: creating and managing user accounts, organizing them with Organizational Units (OUs), and using security groups to apply permissions.

## Key Steps:

1.  **Create and Manage User Accounts:**
    *   In Active Directory Users and Computers, navigate to the `BranchOne\Users` OU.
    *   Right-click in the empty space → **New** → **User**.
    *   Fill in the user's details and set an initial password. It is best practice to check the box for **"User must change password at next logon"**.
    *   To reset a password, right-click the user object and select **Reset Password**. You can also **Unlock Account** if a user has been temporarily locked out from too many incorrect password attempts.

2.  **Create and Manage a Security Group:**
    *   Navigate to the `BranchOne\Groups` OU.
    *   Right-click → **New** → **Group**.
    *   **Group Types:** The two main types are **Security** (used to assign permissions) and **Distribution** (used for email lists). We will create a Security group to manage access.
    *   Add a user to the group by opening the group's properties, clicking the **"Members"** tab, and then **"Add"**.

3.  **Use Templates for Efficiency:**
    *   To quickly create multiple users with the same group memberships and properties, right-click an existing user and select **Copy**. This creates a new user object that inherits the same permissions, saving significant time.

4.  **Understanding Disabled vs. Locked Accounts:**
    *   A **Locked** account is usually temporary, caused by too many incorrect password attempts. It can be unlocked by an administrator.
    *   A **Disabled** account has been manually deactivated by an administrator and cannot be used until it is re-enabled.

5.  **Organize with OUs and Move Objects:**
    *   Create a new top-level OU called `BranchTwo` to represent a different department (e.g., HR or Network Engineers).
    *   Within each branch OU (`BranchOne`, `BranchTwo`), it is standard practice to create sub-OUs for **Computers**, **Groups**, and **Users**.
    *   To move a user from `BranchOne` to `BranchTwo`, you can simply click and drag the user object into the new OU.
    *   **Important:** Moving an object between OUs can automatically change the policies applied to it, as different **Group Policy Objects (GPOs)** are often linked to specific OUs.

6.  **Populate Comprehensive User Details:**
    *   A key sysadmin task is maintaining accurate user information. Open a user's properties to add important details like their **email address, phone number, job title, and department** under the appropriate tabs. This information is critical for creating accurate address books and distribution lists.

7.  **Advanced Configuration with Attribute Editor:**
    *   For more advanced settings, you must first enable "Advanced Features" in the "View" menu of Active Directory Users and Computers.
    *   Once enabled, a new **"Attribute Editor"** tab will appear in a user's properties.
    *   This menu allows for granular control over all user attributes. A common and important use case is adding a **proxyAddress** to give a user a secondary email alias.

8.  **Find Objects in Active Directory:**
    *   To quickly locate a user in a large environment, click the **"Find Objects"** icon (looks like a folder with a magnifying glass) in the toolbar.
    *   Change the "In:" dropdown to **"Entire Directory"** to ensure you are searching the whole domain, then type the user's name.
    *   To find the exact location (path) of a user, find them, open their properties, go to the **"Object"** tab, and view their "Canonical name of object".
