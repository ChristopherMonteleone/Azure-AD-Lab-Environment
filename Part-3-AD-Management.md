# Part 3: Managing Active Directory Users & Groups

This section covers the fundamental day-to-day tasks of a System Administrator: managing user accounts, security groups, and organizing them within the OU structure we created.

## Key Steps:

1.  **Create and Manage a User Account:**
    *   In Active Directory Users and Computers, navigate to the `BranchOne\Users` OU.
    *   Right-click in the empty space → New → User.
    *   Fill in the user's details and set an initial password. It's best practice to check the box for **"User must change password at next logon"**.
    *   To reset a password, right-click the user object and select **"Reset Password"**.

2.  **Create and Manage a Security Group:**
    *   Navigate to the `BranchOne\Groups` OU.
    *   Right-click → New → Group.
    *   **Group Types:** The two main types are **Security** (used to assign permissions) and **Distribution** (used for email lists). We will create a Security group.
    *   Add a user to the group by opening the group's properties, clicking the **"Members"** tab, and then **"Add"**.

3.  **Use Templates for Efficiency:**
    *   To quickly create multiple users with the same group memberships and properties, right-click an existing user and select **Copy**. This creates a new user object with the same permissions, saving significant time.

4.  **Understanding Disabled vs. Locked Accounts:**
    *   A **Locked** account is usually temporary, caused by too many incorrect password attempts. It can be unlocked by an administrator.
    *   A **Disabled** account is one that has been manually turned off by an administrator and cannot be used until it is re-enabled.

5.  **Moving Objects Between OUs:**
    *   Create a new top-level OU called `BranchTwo`.
    *   To move a user from `BranchOne` to `BranchTwo`, you can simply click and drag the user object to the new OU.
    *   **Important:** Moving a user to a different OU can automatically change the permissions and settings applied to them, as different **Group Policy Objects (GPOs)** may be linked to the new OU.
