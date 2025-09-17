# Azure-AD-Lab-Environment
A hands-on lab environment for deploying and managing Windows Server and Active Directory in Microsoft Azure. This project covers the end-to-end process of provisioning a virtual machine, promoting it to a Domain Controller, and performing fundamental system administration tasks like managing users, groups, and OUs.

## Table of Contents

This project is broken down into multiple parts. Click the links below to navigate to each section.

*   ### [Part 1: Initial Server Setup & Configuration](./Part-1-Server-Setup.md)
    *   *Deploying a Windows Server 2022 VM, connecting via Bastion, setting a static IP, and installing AD DS, DNS, and DHCP roles.*
*   ### [Part 2: Promoting to a Domain Controller](./Part-2-Domain-Controller.md)
    *   *Promoting the server to a Domain Controller, creating a new Active Directory forest, and building the initial Organizational Unit (OU) structure for future management.*
*   ### [Part 3: Managing Active Directory Users & Groups](./Part-3-AD-Management.md)
    *   *Creating and managing user accounts and security groups, demonstrating password resets, and organizing objects by moving them between different Organizational Units.*
*   ### [Part 4: Joining a Client PC to the Domain](./Part-4-Joining-Client-to-Domain.md)
    *   *Deploying a second VM, configuring its DNS settings to find the domain, and successfully joining it to our Active Directory environment.*

## Summary

**Azure-Based Windows Server Active Directory Lab**
*   Built a complete Windows Server 2022 environment from the ground up within Microsoft Azure, configuring critical services including Active Directory Domain Services, DNS, and DHCP.
*   Established a functional domain, promoted a server to a Domain Controller, and managed users, groups, and Organizational Units (OUs) while implementing Group Policy Objects (GPOs).

## Tools, Skills, and Concepts Demonstrated

This project utilizes and demonstrates proficiency in the following areas:

### Cloud & Virtualization
*   **Microsoft Azure:** Provisioning and managing cloud resources using the Azure portal.
*   **Azure Virtual Machines:** Deploying, configuring, and managing Windows Server 2022 VMs.
*   **Cloud Cost Management:** Understanding pay-as-you-go principles, including stopping (deallocating) and deleting resources to manage costs.

### Windows Server & Active Directory
*   **Windows Server 2022:** Installation and management of a server operating system.
*   **Active Directory Domain Services (AD DS):** Installation, configuration, and promotion of a server to a Domain Controller.
*   **Active Directory Users and Computers (ADUC):** The primary tool for managing AD objects.
*   **User Account Management:** Creating users, enforcing password policies, resetting passwords, and understanding locked vs. disabled accounts.
*   **Group Management:** Creating security groups and managing group membership.
*   **Organizational Units (OUs):** Designing and implementing an OU structure to organize objects and delegate administration.
*   **Group Policy Objects (GPOs):** Understanding how GPOs are applied to OUs.

### Networking & Security
*   **Azure Virtual Networking:** Basic understanding of virtual networks (VNet) and network interfaces in Azure.
*   **Static IP Configuration:** Assigning a static private IP address, a critical step for servers like Domain Controllers.
*   **Azure Bastion:** Utilizing a secure, managed service for remote server access without exposing RDP ports to the public internet.
*   **DNS Server Role:** Installation and basic function of DNS within an Active Directory environment.
*   **DHCP Server Role:** Installation of the DHCP role for future network management.
