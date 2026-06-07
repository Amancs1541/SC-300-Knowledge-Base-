# 🌐 SC300-Lab08-External-Identities-B2B-Collaboration

## External Identities, Guest Access Governance, and B2B Collaboration using Microsoft Entra ID

---

# 📖 Project Overview

This project demonstrates the implementation of Microsoft Entra External Identities and B2B Collaboration to securely manage guest users, vendors, consultants, and partner organizations.

The solution enables external users to access organizational resources while maintaining security, governance, and compliance through guest access controls, cross-tenant collaboration, access reviews, and entitlement management.

---

# 🎯 Project Objectives

* Configure External Identities
* Invite and Manage Guest Users
* Implement B2B Collaboration
* Configure Guest User Restrictions
* Configure Cross-Tenant Access Settings
* Create Access Reviews for Guests
* Implement Guest Lifecycle Governance
* Monitor Guest User Activity

---

# 🏢 Business Scenario

ABC Technologies works with:

* External Vendors
* Consultants
* Contractors
* Business Partners

These users require access to:

* Microsoft Teams
* SharePoint Sites
* Enterprise Applications
* Project Documentation

Instead of creating internal employee accounts, Microsoft Entra External Identities is used to securely onboard and manage guest users.

As the Identity Administrator, I was responsible for implementing guest collaboration and governance controls.

---

# 🏗️ Solution Architecture

```text
ABC Technologies
        │
        ▼
Microsoft Entra ID
        │
        ▼
External Identities
        │
        ├── Guest Users
        ├── B2B Collaboration
        ├── Cross-Tenant Access
        ├── Access Reviews
        └── Entitlement Management
        │
        ▼
Secure External Collaboration
```

---

# 🔑 Understanding the Concepts

## What are External Identities?

External Identities allow people outside your organization to access internal resources securely.

Examples:

* Vendors
* Partners
* Consultants
* Contractors

---

## What is a Guest User?

A Guest User is an external identity invited into your Microsoft Entra tenant.

### Example

```text
ABC Technologies
      │
      ▼
Invite:
vendor@gmail.com
      │
      ▼
Guest Account Created
```

User Type:

```text
Guest
```

---

## Why Not Create Internal Accounts?

Creating employee accounts for external users creates:

* Licensing overhead
* Security risks
* Administrative complexity

Guest users provide secure collaboration without creating full employee identities.

---

## What is B2B Collaboration?

B2B (Business-to-Business) Collaboration allows external users to access resources using their own credentials.

### Example

```text
Vendor User
      │
Uses Existing Account
      │
Accesses Teams Site
      │
Accesses SharePoint
```

No separate password is required.

---

## What is Cross-Tenant Access?

Cross-Tenant Access enables secure collaboration between organizations.

### Example

```text
ABC Technologies
      ↔
Contoso Ltd
```

Users can collaborate more securely across trusted organizations.

---

## Why Use Cross-Tenant Access?

Benefits:

* Simplified collaboration
* Improved trust relationships
* Reduced administration
* Better user experience

---

## What are Guest Restrictions?

Guest restrictions limit what guest users can see inside the directory.

### Example

Guests should NOT be able to:

```text
View all users
View all groups
Browse directory data
```

---

## What are Access Reviews?

Access Reviews periodically verify whether users still need access.

### Example

```text
Project Ends
      ↓
Vendor Still Has Access
      ↓
Security Risk
```

Access Reviews help identify and remove unnecessary access.

---

## What is Entitlement Management?

Entitlement Management automates access requests and approvals.

### Example

```text
Guest Requests Access
      ↓
Manager Approval
      ↓
Access Granted
      ↓
Expiration Date
      ↓
Access Removed Automatically
```

---

# ⚙️ Task 1 – Configure External Identities

Navigate:

```text
Microsoft Entra Admin Center
→ External Identities
```

Review:

* External Collaboration Settings
* Guest Access Settings
* Cross-Tenant Access Settings

---

## Validation

Verify External Identities configuration is available and enabled.

---

# ⚙️ Task 2 – Invite Guest User

## Why This Task Exists

Organizations frequently collaborate with vendors and consultants.

Guest invitations provide secure access without creating employee accounts.

---

## Configuration Steps

Navigate:

```text
Users
→ New User
→ Invite External User
```

Invite:

```text
vendor.user@gmail.com
```

Provide:

```text
Display Name
Personal Message
```

Send Invitation.

---

## Validation

Verify:

```text
User Type = Guest
```

Guest appears in the Users list.

---

# ⚙️ Task 3 – Create Vendor Security Group

## Why This Task Exists

Guest access should be managed through groups rather than direct assignments.

---

## Configuration Steps

Navigate:

```text
Groups
→ New Group
```

Create:

```text
Vendor-Team
```

Add guest user as member.

---

## Validation

Verify guest user appears in the Vendor-Team group.

---

# ⚙️ Task 4 – Grant Microsoft Teams Access

## Why This Task Exists

External users frequently collaborate through Microsoft Teams.

---

## Configuration Steps

Assign Vendor-Team group to:

```text
Microsoft Teams
```

Provide:

```text
Channel Access
Project Collaboration
File Sharing
```

---

## Validation

Guest successfully accesses Teams resources.

---

# ⚙️ Task 5 – Configure Guest User Restrictions

## Why This Task Exists

Guests should only access resources required for collaboration.

---

## Configuration Steps

Navigate:

```text
External Identities
→ External Collaboration Settings
```

Configure:

```text
Guests have limited access
```

Restrict:

```text
Directory browsing
User enumeration
Group discovery
```

---

## Validation

Verify guest cannot browse directory information.

---

# ⚙️ Task 6 – Configure Cross-Tenant Access

## Why This Task Exists

Partner organizations may require recurring collaboration.

---

## Configuration Steps

Navigate:

```text
External Identities
→ Cross-Tenant Access Settings
```

Add partner tenant.

Configure:

```text
Inbound Access
Outbound Access
Trust Settings
```

---

## Validation

Verify cross-tenant relationship is established.

---

# ⚙️ Task 7 – Create Guest Access Review

## Why This Task Exists

Guest users often retain access longer than necessary.

---

## Configuration Steps

Navigate:

```text
Identity Governance
→ Access Reviews
→ New Access Review
```

Target:

```text
Vendor-Team Group
```

Reviewers:

```text
Group Owners
```

Frequency:

```text
Monthly
```

---

## Validation

Verify review schedule is created successfully.

---

# ⚙️ Task 8 – Configure Guest Access Expiration

## Why This Task Exists

Temporary access should expire automatically.

---

## Configuration Steps

Configure:

```text
Guest Access Expiration
```

Example:

```text
90 Days
```

---

## Validation

Verify expiration settings are applied.

---

# ⚙️ Task 9 – Monitor Guest Activity

Navigate:

```text
Monitoring
→ Sign-In Logs
```

Review:

* Guest Sign-Ins
* Access Attempts
* Authentication Methods
* Location Information

---

## Validation

Verify guest sign-in activity is recorded.

---

# 📊 Guest Lifecycle Example

```text
Guest Invited
      ↓
Invitation Accepted
      ↓
Added to Vendor-Team
      ↓
Access Granted
      ↓
Monthly Review
      ↓
Project Completed
      ↓
Access Removed
```

---


# ✅ Validation Results

| Validation Item                | Status |
| ------------------------------ | ------ |
| External Identities Configured | ✅      |
| Guest User Invited             | ✅      |
| Guest Group Created            | ✅      |
| Teams Access Assigned          | ✅      |
| Guest Restrictions Applied     | ✅      |
| Cross-Tenant Access Configured | ✅      |
| Access Review Created          | ✅      |
| Guest Activity Monitored       | ✅      |

---

# 🎓 SC-300 Skills Covered

## Implement Identity Management

* External Identities
* Guest User Administration
* B2B Collaboration

## Implement Identity Governance

* Access Reviews
* Guest Lifecycle Management
* Entitlement Management

## Implement Authentication and Access Management

* Cross-Tenant Access
* External Collaboration Settings

## Monitor Identity Environment

* Sign-In Logs
* Guest Activity Monitoring

---

# 🚀 Key Learning Outcomes

Through this lab, I gained hands-on experience in:

* Managing Guest Users
* Implementing B2B Collaboration
* Configuring Cross-Tenant Access
* Restricting Guest Permissions
* Automating Guest Governance
* Conducting Access Reviews
* Managing External Identity Lifecycles

---

# 💼 Portfolio Project

**Project Name:** External Identities, B2B Collaboration, and Guest Access Governance using Microsoft Entra ID

This project demonstrates the implementation of Microsoft Entra External Identities to securely manage guest users, partner collaboration, and access governance through guest restrictions, cross-tenant access settings, and lifecycle management controls.

---

# 👨‍💻 Author

**Aman Varma**

Microsoft SC-300 Identity and Access Administrator Journey

Microsoft Entra ID Enterprise Identity & Governance Lab Series
