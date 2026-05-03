# AZ-104 Architecture & Certification Path

## 🏗️ Azure Administrator Architecture

```
┌──────────────────────────────────────────────────────────────┐
│                  IDENTITY & GOVERNANCE                        │
│  ┌────────────────────────────────────────────────────────┐  │
│  │ • Microsoft Entra ID (Azure AD)                        │  │
│  │ • Role-Based Access Control (RBAC)                    │  │
│  │ • Azure Policy & Blueprints                           │  │
│  │ • Subscriptions & Management Groups                   │  │
│  └────────────────────────────────────────────────────────┘  │
└──────────────────────────────────────────────────────────────┘
                            ↓
┌──────────────────────────────────────────────────────────────┐
│                  COMPUTE RESOURCES                            │
│  ┌─────────────────────────────────────────────────────┐    │
│  │ VIRTUAL MACHINES        │ APP SERVICES             │    │
│  │ • VM Creation           │ • Web Apps               │    │
│  │ • VM Sizing             │ • API Apps               │    │
│  │ • VM Extensions         │ • Function Apps          │    │
│  │ • Availability Sets     │ • App Service Plans      │    │
│  │ • Scale Sets            │ • Container Instances    │    │
│  └─────────────────────────────────────────────────────┘    │
└──────────────────────────────────────────────────────────────┘
                            ↓
┌──────────────────────────────────────────────────────────────┐
│                  STORAGE MANAGEMENT                           │
│  ┌────────────────────────────────────────────────────────┐  │
│  │ • Storage Accounts (Blob, File, Queue, Table)         │  │
│  │ • Storage Replication & Redundancy                    │  │
│  │ • Managed Disks & Snapshots                           │  │
│  │ • Backup & Recovery Services                          │  │
│  │ • Azure Files & File Sync                             │  │
│  └────────────────────────────────────────────────────────┘  │
└──────────────────────────────────────────────────────────────┘
                            ↓
┌──────────────────────────────────────────────────────────────┐
│                  NETWORKING                                   │
│  ┌────────────────────────────────────────────────────────┐  │
│  │ • Virtual Networks (VNets)                            │  │
│  │ • Subnets & IP Addressing                             │  │
│  │ • Network Security Groups (NSGs)                      │  │
│  │ • Load Balancers & Application Gateways               │  │
│  │ • VPN & ExpressRoute Connectivity                     │  │
│  └────────────────────────────────────────────────────────┘  │
└──────────────────────────────────────────────────────────────┘
                            ↓
┌──────────────────────────────────────────────────────────────┐
│            MONITORING & MAINTENANCE                           │
│  ┌────────────────────────────────────────────────────────┐  │
│  │ • Azure Monitor & Log Analytics                       │  │
│  │ • Alerts & Notifications                              │  │
│  │ • Update Management                                   │  │
│  │ • Azure Backup & Site Recovery                        │  │
│  │ • Cost Management & Optimization                      │  │
│  └────────────────────────────────────────────────────────┘  │
└──────────────────────────────────────────────────────────────┘
```

## 🎓 Certification Path

### Level 1: Fundamentals → Level 2: Associate
```
PREREQUISITES
    ↓
┌─────────────────────────┐
│    AZ-900              │
│ Azure Fundamentals     │
│ (Recommended)          │
└──────────┬──────────────┘
           ↓
┌─────────────────────────┐
│    AZ-104              │
│ Azure Administrator    │
│ (40-50 hours)          │
│ ✓ Identity & Gov.      │
│ ✓ Compute              │
│ ✓ Storage              │
│ ✓ Networking           │
│ ✓ Monitoring           │
└──────────┬──────────────┘
           ↓
    READY FOR
    Expert Level
```

### Specialization Paths After AZ-104
```
AZ-104 (Administrator)
    ↓
    ├─→ AZ-500 (Security Engineer)
    ├─→ AZ-700 (Network Engineer)
    ├─→ AZ-120 (SAP Administrator)
    ├─→ AZ-140 (Virtual Desktop Admin)
    └─→ AZ-305 (Solutions Architect)
```

## 📊 Administrator Responsibilities

```
DAILY TASKS
├─ Monitor Azure resources
├─ Manage user access & permissions
├─ Configure storage & backups
├─ Troubleshoot connectivity issues
└─ Optimize costs

WEEKLY TASKS
├─ Review security compliance
├─ Update VM patches
├─ Analyze performance metrics
├─ Plan capacity
└─ Document changes

MONTHLY TASKS
├─ Conduct disaster recovery drills
├─ Review and optimize costs
├─ Update security policies
├─ Plan infrastructure upgrades
└─ Audit access controls
```

## 🔄 Learning Flow

```
PHASE 1: IDENTITY & GOVERNANCE (Week 1-2)
├─ Microsoft Entra ID concepts
├─ RBAC implementation
├─ Azure Policy basics
└─ Subscription management

         ↓

PHASE 2: COMPUTE RESOURCES (Week 3-4)
├─ Virtual Machines
├─ App Services
├─ Scaling & Availability
└─ Monitoring

         ↓

PHASE 3: STORAGE & NETWORKING (Week 5-6)
├─ Storage accounts
├─ Virtual Networks
├─ Load Balancing
└─ Connectivity

         ↓

PHASE 4: MONITORING & MAINTENANCE (Week 7-8)
├─ Azure Monitor
├─ Backup & Recovery
├─ Update Management
└─ Cost Optimization

         ↓

PHASE 5: PRACTICE & EXAM (Week 9-10)
├─ Hands-on labs
├─ Practice tests
├─ Weak area review
└─ Exam preparation
```

## 📈 Skills Progression

```
BEGINNER
  ├─ Azure Portal Navigation
  ├─ Basic Resource Creation
  ├─ User Management
  └─ Simple Networking
         ↓
INTERMEDIATE
  ├─ VM Management
  ├─ Storage Configuration
  ├─ Network Design
  ├─ Monitoring Setup
  └─ Backup Implementation
         ↓
ADVANCED
  ├─ Complex Architectures
  ├─ High Availability Design
  ├─ Disaster Recovery
  ├─ Security Hardening
  └─ Cost Optimization
```

## 🎯 Exam Domains Breakdown

| Domain | Weight | Focus |
|--------|--------|-------|
| Identity & Governance | 20-25% | Entra ID, RBAC, Policy |
| Compute Resources | 20-25% | VMs, App Services, Scaling |
| Storage | 15-20% | Storage accounts, Disks, Backup |
| Networking | 20-25% | VNets, Load Balancing, Connectivity |
| Monitoring | 15-20% | Monitor, Alerts, Updates |

---

**Next Steps After AZ-104:**
- Specialize in Security (AZ-500)
- Specialize in Networking (AZ-700)
- Advance to Architecture (AZ-305)
- Pursue specialized workloads (AZ-120, AZ-140)
