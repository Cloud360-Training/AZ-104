# Microsoft Entra Users and Groups

![Microsoft Entra Users and Groups](https://private-us-east-1.manuscdn.com/sessionFile/PELdhIFr8k4l8jvbPIIMbc/sandbox/eXDyN0VX4v4pZR0BYh4uyG-images_1777918154362_na1fn_L2hvbWUvdWJ1bnR1L2F6dXJlX3NlY3VyaXR5X2RpYWdyYW1zL2ltYWdlcy9taWNyb3NvZnQtZW50cmEtdXNlcnMtYW5kLWdyb3Vwcw.png?Policy=eyJTdGF0ZW1lbnQiOlt7IlJlc291cmNlIjoiaHR0cHM6Ly9wcml2YXRlLXVzLWVhc3QtMS5tYW51c2Nkbi5jb20vc2Vzc2lvbkZpbGUvUEVMZGhJRnI4azRsOGp2YlBJSU1iYy9zYW5kYm94L2VYRHlOMFZYNHY0cFpSMEJZaDR1eUctaW1hZ2VzXzE3Nzc5MTgxNTQzNjJfbmExZm5fTDJodmJXVXZkV0oxYm5SMUwyRjZkWEpsWDNObFkzVnlhWFI1WDJScFlXZHlZVzF6TDJsdFlXZGxjeTl0YVdOeWIzTnZablF0Wlc1MGNtRXRkWE5sY25NdFlXNWtMV2R5YjNWd2N3LnBuZyIsIkNvbmRpdGlvbiI6eyJEYXRlTGVzc1RoYW4iOnsiQVdTOkVwb2NoVGltZSI6MTc5ODc2MTYwMH19fV19&Key-Pair-Id=K2HSFNDJXOU9YS&Signature=ovlvW-jr-zIf8EZQAA~rdZf5oZec7niXyH6dPMOhQyUljGOg-VD9Q2KBEUdEf8xT622oSKpzVj9xCzPYhqDpalPdQu7jrz-YogNwBGgdaKKUDpWsyULCEx08pI7KtgvNspf4i-LVcUrOb0oEgc3oNupp6kv0eJh2EdgHtaNwLn6htc~qBHm3GHw7PCwK18wbRxj6nBrlhaHs5FoKc1kesNUKLIdE86F8z0YlEsT2MQKq0NNek-3onVKdqudJih06ad2e532qqXIXX5-oXZTHPFz8iQQxwnZJJYRA1VubRzXmWmxf7bdiggoEB0Mz1ygVT2QEbvN5lvJky3dEg-jJXw__)

## Overview

Microsoft Entra ID (formerly Azure Active Directory) provides a robust framework for managing identities and their access to resources. The core principle illustrated in this diagram is that **groups simplify access management**. Instead of assigning permissions, licenses, and roles to individual users one by one, administrators can manage access once for many users by assigning these outcomes to groups.

This approach allows organizations to manage access at scale, enforce the principle of least privilege, and adapt to organizational changes with ease.

---

## 1. User Types

Microsoft Entra ID supports different types of user identities, each serving a specific purpose within the organization.

### Internal Users
- **User**: Standard corporate users (e.g., Megan Bowen) who require access to enterprise applications, email, and internal resources.
- **Employee**: Similar to standard users but often categorized specifically for HR or departmental grouping (e.g., Alex Wilber).
- **Admin**: Users with elevated privileges (e.g., James Anderson) who manage the Entra ID environment, Azure resources, or Microsoft 365 services.

### External Users
- **Guest User**: External identities (e.g., Lidia Holloway from fabrikam.com) invited into the directory via Microsoft Entra B2B collaboration. They use their own credentials to access shared resources securely.

---

## 2. Group Types

Groups are the fundamental building blocks for scalable access management. Microsoft Entra ID offers several group types to accommodate different administrative needs.

### Security Group
- **Purpose**: Used primarily to manage access to applications, resources, and security principals.
- **Membership**: Can be assigned manually or dynamically.
- **Use Case**: Creating a "Sales Team" group to grant access to Salesforce and internal sales data.

### Microsoft 365 Group
- **Purpose**: Enables collaboration by providing a shared mailbox, calendar, files (SharePoint), and Microsoft Teams workspace.
- **Membership**: Can be assigned manually or dynamically.
- **Use Case**: Creating a project team workspace where members need to collaborate on documents and communicate via Teams.

### Dynamic Group
- **Purpose**: Automates group membership based on user attributes, eliminating manual administration.
- **Mechanism**: Uses rules (e.g., `user.department -eq "Sales"`) to automatically add or remove members as their HR data changes.
- **Use Case**: Automatically granting all users in the "Engineering" department access to development tools.

### Role-Assignable Group
- **Purpose**: A specialized security group used specifically to assign Microsoft Entra roles to a group instead of individual users.
- **Security**: Prevents privilege escalation by restricting who can modify the group's membership.
- **Use Case**: Assigning the "Helpdesk Administrator" role to a group, allowing IT managers to add/remove helpdesk staff simply by updating group membership.

---

## 3. Outcomes of Group Membership

The true power of groups lies in the outcomes that can be assigned to them. When a user is added to a group, they automatically inherit all the access, licenses, and roles associated with that group.

### Application Access
- **Function**: Grants access to enterprise applications and SaaS platforms (e.g., Salesforce, ServiceNow, Box).
- **Benefit**: Simplifies onboarding. When a new employee joins the Marketing group, they instantly get access to all marketing applications.

### Licenses
- **Function**: Automates the assignment of product licenses (e.g., Microsoft 365 E5, Windows 11 E3, Visio Plan 2).
- **Benefit**: Ensures compliance and cost control. When a user leaves a group, their license is automatically revoked and returned to the pool.

### Roles
- **Function**: Assigns directory roles (e.g., Global Administrator, User Administrator, Helpdesk Administrator) via Role-Assignable Groups.
- **Benefit**: Centralizes role management and simplifies auditing of privileged access.

### Resource Permissions
- **Function**: Grants access to Azure resources (e.g., Azure Subscriptions, Resource Groups, Storage Accounts, Key Vaults) using Azure Role-Based Access Control (RBAC).
- **Benefit**: Ensures developers and administrators have the exact permissions they need to manage cloud infrastructure.

---

## Key Management Principles

| Principle | Description |
|-----------|-------------|
| **Cumulative Access** | Users can belong to multiple groups. Access and permissions from all groups are combined (additive). |
| **Dynamic Automation** | Dynamic groups use rules based on user attributes (e.g., department, location, job title) to automatically manage membership. |
| **Manage Once** | Groups simplify access management by allowing administrators to configure access once for many users. |

---

## Exam Relevance (SC-300, AZ-104, AZ-500)

For Microsoft certification exams, focus on these critical distinctions:

- **Security Groups vs. Microsoft 365 Groups**: Know that M365 groups include collaboration tools (Teams, SharePoint), while Security groups are strictly for access control.
- **Dynamic Membership**: Understand the syntax and use cases for dynamic user and dynamic device groups. Remember that a group cannot have both dynamic users and dynamic devices.
- **Role-Assignable Groups**: Recognize that this feature requires Microsoft Entra ID P1/P2 licensing and must be enabled at the time of group creation.
- **License Assignment**: Understand group-based licensing and how conflicting license assignments are resolved.
