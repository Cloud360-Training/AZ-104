# Azure Subscriptions and Governance

![Azure Subscriptions and Governance](https://private-us-east-1.manuscdn.com/sessionFile/PELdhIFr8k4l8jvbPIIMbc/sandbox/eXDyN0VX4v4pZR0BYh4uyG-images_1777918154453_na1fn_L2hvbWUvdWJ1bnR1L2F6dXJlX3NlY3VyaXR5X2RpYWdyYW1zL2ltYWdlcy9henVyZS1zdWJzY3JpcHRpb25zLWFuZC1nb3Zlcm5hbmNl.png?Policy=eyJTdGF0ZW1lbnQiOlt7IlJlc291cmNlIjoiaHR0cHM6Ly9wcml2YXRlLXVzLWVhc3QtMS5tYW51c2Nkbi5jb20vc2Vzc2lvbkZpbGUvUEVMZGhJRnI4azRsOGp2YlBJSU1iYy9zYW5kYm94L2VYRHlOMFZYNHY0cFpSMEJZaDR1eUctaW1hZ2VzXzE3Nzc5MTgxNTQ0NTNfbmExZm5fTDJodmJXVXZkV0oxYm5SMUwyRjZkWEpsWDNObFkzVnlhWFI1WDJScFlXZHlZVzF6TDJsdFlXZGxjeTloZW5WeVpTMXpkV0p6WTNKcGNIUnBiMjV6TFdGdVpDMW5iM1psY201aGJtTmwucG5nIiwiQ29uZGl0aW9uIjp7IkRhdGVMZXNzVGhhbiI6eyJBV1M6RXBvY2hUaW1lIjoxNzk4NzYxNjAwfX19XX0_&Key-Pair-Id=K2HSFNDJXOU9YS&Signature=NnvEGG-F36uS-laYPvrFkTi~jRjRZNjLHhwyzNpGHB9vEQpqXmbytxpLKmfbJEe0k0TZ14qn2aKpHAPM0wb5lUpx4cxZtWR4CYy8Q8Ps7YXyMcmShGRixjf1NwvvajOr5jlfmwrJle7avPwBaGcR6bIjuTNdr3ebErM2Yc6WmPCWAy47qoYFsegoNU6kO5W6rIMhyiupgyBEKNwS-4ytTua-eDgtPowS9BPEKFic1upA6j6LpRkbs~QOic8Ab7Sygyp2bVm1P5Bdc2wD2bTmzRG-LjCQAIvxCPCImLEpyCB5sEYEQPGs1FFcarZ65qldZqUtAzV6x0dN4ipvn8C9pw__)

## Overview

Azure Subscriptions and Governance provides the foundational architecture for enterprise-scale cloud management. This diagram illustrates how organizations can implement centralized control and policy enforcement across their entire Azure footprint.

The core concept is **centralized governance**, where policies and controls are defined at higher levels of the organizational hierarchy and automatically inherited downward to all underlying resources. This ensures consistent compliance, security, and cost management without requiring manual configuration for every new resource.

---

## 1. The Governance Hierarchy

Azure organizes resources into a strict hierarchy that dictates how access, policies, and costs are managed and inherited.

### Azure Tenant (Microsoft Entra ID)
- **Top Level**: The Azure Tenant (e.g., Contoso Corporation) represents the organization.
- **Identity Boundary**: It is backed by Microsoft Entra ID, which manages all Users, Groups, and Applications.
- **Trust Boundary**: All subscriptions within the hierarchy trust this single Entra ID tenant for authentication and authorization.

### Management Groups
- **Purpose**: Define governance scope and inheritance boundaries above the subscription level.
- **Structure**: Can be nested up to six levels deep to reflect organizational structure (e.g., Corporate → Business Units, Platform, Landing Zones, Custom).
- **Benefit**: Allows administrators to apply Azure Policy and Role-Based Access Control (RBAC) to multiple subscriptions simultaneously.

### Subscriptions
- **Purpose**: Serve as billing boundaries and administrative boundaries.
- **Environment Segmentation**: Best practice dictates separating workloads into different subscriptions based on environment or purpose:
  - **Production Subscription**: For live, customer-facing workloads.
  - **Development Subscription**: For building and testing applications.
  - **Sandbox Subscription**: For experimentation and learning with strict cost controls.

### Resource Groups
- **Purpose**: Logical containers for resources that share the same lifecycle.
- **Organization**: Typically grouped by application, environment, or tier (e.g., `rg-apps-prod`, `rg-data-prod`, `rg-network-prod`).

### Resources
- **Bottom Level**: The actual Azure services deployed (e.g., Virtual Machines, Storage Accounts, Azure SQL Databases, App Services, Virtual Networks).

---

## 2. Governance Controls

To manage this hierarchy effectively, Azure provides a suite of native governance controls that can be applied at various levels (Tenant, Management Group, Subscription, or Resource Group).

### Azure Policy
- **Function**: Defines and enforces rules across the environment.
- **Use Case**: Restricting resource deployments to specific regions (e.g., only allow deployments in "East US") or requiring specific tags on all resources.

### RBAC (Role-Based Access Control)
- **Function**: Standardizes access control using role-based permissions.
- **Use Case**: Granting the "Virtual Machine Contributor" role to the infrastructure team at the Management Group level, allowing them to manage VMs across all underlying subscriptions.

### Tags
- **Function**: Key-value pairs applied to resources for classification and organization.
- **Use Case**: Tagging resources with `CostCenter: Marketing` or `Environment: Production` for detailed billing reports.

### Budgets & Cost Management
- **Function**: Sets spending limits and analyzes costs across the environment.
- **Use Case**: Creating a $500/month budget on the Sandbox subscription that triggers an email alert when spending reaches 80%.

### Security & Compliance
- **Function**: Protects resources and ensures they meet regulatory requirements.
- **Use Case**: Using Microsoft Defender for Cloud to continuously assess the environment against industry standards like ISO 27001 or HIPAA.

### Monitoring
- **Function**: Tracks the health, performance, and availability of resources.
- **Use Case**: Centralizing logs from all subscriptions into a single Log Analytics workspace for enterprise-wide visibility.

### Resource Locks
- **Function**: Prevents accidental deletion or modification of critical assets.
- **Use Case**: Applying a "CanNotDelete" lock to the production database to ensure it cannot be removed, even by an administrator.

---

## 3. Governance Outcomes

Implementing this enterprise-scale governance architecture yields significant organizational benefits:

| Outcome | Description |
|---------|-------------|
| **Policy Enforcement** | Consistent compliance and guardrails at scale. Policies applied at the Management Group level automatically apply to all new and existing resources. |
| **Standardized Access** | Least privilege access enforced via RBAC, ensuring users only have the permissions necessary for their role. |
| **Cost Visibility** | Track, analyze, and optimize spend across all subscriptions using centralized Cost Management and tagging strategies. |
| **Stronger Security** | Protect resources and reduce risk across the enterprise by enforcing security best practices by default. |
| **Audit Readiness** | Meet internal policies, industry standards, and regulatory requirements continuously, simplifying the audit process. |

---

## Exam Relevance (AZ-104, AZ-305, AZ-900)

For Microsoft certification exams, focus on these architectural concepts:

- **Inheritance**: Understand that policies and RBAC assignments flow *downward*. An assignment at a Management Group affects all child Management Groups, Subscriptions, Resource Groups, and Resources.
- **Management Groups vs. Subscriptions**: Know that Management Groups are for applying governance across multiple subscriptions, while Subscriptions are primarily for billing and hard isolation.
- **Resource Locks**: Remember that Resource Locks override RBAC permissions. Even an Owner cannot delete a resource if a "CanNotDelete" lock is applied.
- **Azure Policy vs. RBAC**: Azure Policy focuses on resource properties (e.g., "Is this VM allowed in this region?"), while RBAC focuses on user actions (e.g., "Is this user allowed to create a VM?").
