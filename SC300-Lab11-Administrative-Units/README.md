# 🏢 SC300-Lab11-Administrative-Units

## Delegated Administration, Scoped Role Assignments, and Restricted Management Administrative Units using Microsoft Entra ID

---

# 📖 Project Overview

This project demonstrates the implementation of Administrative Units (AUs) and Restricted Management Administrative Units (RMAUs) in Microsoft Entra ID.

Large enterprises often operate across multiple regions, departments, subsidiaries, and business units. Granting tenant-wide administrative permissions creates security risks and violates the principle of least privilege.

Administrative Units provide administrative boundaries that allow organizations to delegate administrative permissions to regional or departmental administrators without granting full tenant access.

Restricted Management Administrative Units extend this capability by protecting highly sensitive users and groups from tenant-wide administrative inheritance, creating an additional authorization boundary.

This project demonstrates delegated administration, scoped role assignments, administrative isolation, and executive account protection using Microsoft Entra ID.

---

# 🎯 Project Objectives

* Create Administrative Units
* Configure Regional Administration
* Delegate Administrative Permissions
* Implement Scoped Role Assignments
* Enforce Least Privilege Administration
* Create Restricted Management Administrative Units
* Protect Executive and Privileged Accounts
* Validate Administrative Boundaries
* Monitor Administrative Activities

---

# 🏢 Business Scenario

ABC Technologies operates globally with offices in:

```text
Germany
India
United States
```

Each region has its own IT support team.

The organization wants:

```text
Germany IT Team
to manage only Germany users

India IT Team
to manage only India users
```

without granting:

```text
Global Administrator
```

permissions.

Additionally, the company wants to protect:

```text
CEO
CISO
Identity Administrators
Break Glass Accounts
```

from being managed by regional administrators and other tenant-level administrators.

To achieve this, Administrative Units and Restricted Management Administrative Units are implemented.

---

# 🏗️ Solution Architecture

```text
Microsoft Entra Tenant
│
├── Germany-AU
│     │
│     ├── Germany Users
│     ├── Germany Groups
│     └── Germany Administrator
│
├── India-AU
│     │
│     ├── India Users
│     ├── India Groups
│     └── India Administrator
│
├── Executive-RMAU
│     │
│     ├── CEO
│     ├── CISO
│     ├── Identity Admin
│     └── BreakGlass01
│
└── Global Administrators
```

---

# 🔑 Understanding Administrative Units

## What is an Administrative Unit?

An Administrative Unit is a Microsoft Entra container used to scope administrative permissions to specific users, groups, and devices.

Think of an Administrative Unit as:

```text
Administrative Boundary
Inside Microsoft Entra ID
```

Administrative Units do not create a separate tenant.

Instead, they create a scoped management boundary within the same tenant.

---

# Why Administrative Units Exist

Without Administrative Units:

```text
User Administrator
```

can manage:

```text
Every User
Inside Tenant
```

This creates excessive permissions.

---

With Administrative Units:

```text
User Administrator
+
Germany-AU
```

can manage:

```text
Germany Users Only
```

This follows the Zero Trust principle:

```text
Least Privilege Access
```

---

# Administrative Units vs Security Groups

This is one of the most common SC-300 interview questions.

---

## Security Groups

Used for:

```text
Application Access

Licensing

Conditional Access

Permissions
```

Example:

```text
HR Group
Finance Group
IT Group
```

---

## Administrative Units

Used for:

```text
Delegated Administration

Administrative Scoping

Role Boundaries
```

Example:

```text
Germany-AU
India-AU
```

---

# What Objects Can Be Added to Administrative Units?

Administrative Units support:

## Users

Example:

```text
john.germany
anna.germany
```

---

## Groups

Example:

```text
Germany-HR
Germany-IT
```

---

## Devices

Example:

```text
Germany-Laptop01
Germany-Laptop02
```

---

# Roles That Support Administrative Unit Scope

Examples:

```text
User Administrator

Groups Administrator

Helpdesk Administrator

Password Administrator

Authentication Administrator

License Administrator
```

---

# Understanding Scoped Role Assignments

Normally:

```text
User Administrator
```

has permissions across the entire tenant.

---

Scoped Assignment:

```text
User Administrator
+
Germany-AU
```

means:

```text
Manage Germany Users Only
```

---

# Administrative Flow

```text
Administrative Unit
        │
        ▼
Assign Users
        │
        ▼
Assign Scoped Role
        │
        ▼
Delegate Administration
        │
        ▼
Manage Specific Objects Only
```

---

# 🔑 Understanding Restricted Management Administrative Units

## What is Restricted Management?

Restricted Management Administrative Units provide an additional authorization boundary for highly sensitive users and groups.

When enabled:

```text
Administrative Unit
+
Restricted Management
```

creates enhanced protection.

---

# Why Restricted Management Exists

Many organizations have sensitive accounts:

```text
CEO
CFO
CISO
Break Glass Accounts
Identity Administrators
```

These accounts require stronger protection.

Without Restricted Management:

```text
Tenant-Level Administrators
```

may inherit permissions over sensitive objects.

---

With Restricted Management:

```text
Only Explicitly Assigned Administrators
```

can manage protected objects.

---

# Business Example

ABC Technologies wants to protect:

```text
CEO
CISO
BreakGlass01
```

from unauthorized administration.

The company creates:

```text
Executive-RMAU
```

and enables:

```text
Restricted Management
```

---

# Restricted Management Architecture

```text
Microsoft Entra Tenant
│
├── Germany-AU
│
├── India-AU
│
└── Executive-RMAU
      │
      ├── CEO
      ├── CISO
      ├── Identity Admin
      └── BreakGlass01
```

---

# Security Benefits

Restricted Management provides:

```text
Administrative Isolation

Executive Protection

Privileged Identity Protection

Additional Authorization Boundary

Least Privilege Administration
```

---

# ⚙️ Task 1 – Create Germany Administrative Unit

Navigate:

```text
Microsoft Entra Admin Center
→ Identity
→ Administrative Units
→ New Administrative Unit
```

Create:

```text
Germany-AU
```

Description:

```text
Administrative Unit for Germany Region
```

---

# Validation

Verify:

```text
Germany-AU
```

exists.

---

# ⚙️ Task 2 – Create India Administrative Unit

Create:

```text
India-AU
```

Description:

```text
Administrative Unit for India Region
```

---

# Validation

Verify:

```text
India-AU
```

exists.

---

# ⚙️ Task 3 – Create Regional Users

Create:

```text
john.germany
anna.germany
```

Department:

```text
Germany
```

---

Create:

```text
raj.india
priya.india
```

Department:

```text
India
```

---

# Validation

Verify all users exist.

---

# ⚙️ Task 4 – Add Users to Administrative Units

Add:

```text
john.germany
anna.germany
```

to:

```text
Germany-AU
```

---

Add:

```text
raj.india
priya.india
```

to:

```text
India-AU
```

---

# Validation

Verify memberships.

---

# ⚙️ Task 5 – Create Regional Administrators

Create:

```text
germany.admin
india.admin
```

Purpose:

Regional delegated administrators.

---

# Validation

Verify accounts exist.

---

# ⚙️ Task 6 – Assign Germany Scoped Administrator

Navigate:

```text
Germany-AU
→ Roles and Administrators
```

Assign:

```text
User Administrator
```

to:

```text
germany.admin
```

Scope:

```text
Germany-AU
```

---

# Validation

Verify role assignment.

---

# ⚙️ Task 7 – Assign India Scoped Administrator

Navigate:

```text
India-AU
→ Roles and Administrators
```

Assign:

```text
User Administrator
```

to:

```text
india.admin
```

Scope:

```text
India-AU
```

---

# Validation

Verify role assignment.

---

# ⚙️ Task 8 – Test Germany Administrator

Login:

```text
germany.admin
```

Attempt:

```text
Reset Password
```

for:

```text
john.germany
```

Expected:

```text
Success
```

---

Attempt:

```text
Reset Password
```

for:

```text
raj.india
```

Expected:

```text
Access Denied
```

---

# Validation

Administrative boundary enforced.

---

# ⚙️ Task 9 – Test India Administrator

Login:

```text
india.admin
```

Attempt:

```text
Reset Password
```

for:

```text
raj.india
```

Expected:

```text
Success
```

---

Attempt:

```text
Reset Password
```

for:

```text
john.germany
```

Expected:

```text
Access Denied
```

---

# Validation

Administrative boundary enforced.

---

# ⚙️ Task 10 – Create Executive Restricted Management Administrative Unit

Navigate:

```text
Microsoft Entra Admin Center
→ Identity
→ Administrative Units
→ New Administrative Unit
```

Create:

```text
Executive-RMAU
```

Description:

```text
Restricted Management Administrative Unit for Executive Users
```

---

# ⚙️ Task 11 – Enable Restricted Management

Enable:

```text
Restricted Management Administrative Unit
```

Purpose:

Protect highly privileged users.

---

# Validation

Verify:

```text
Restricted Management = Enabled
```

---

# ⚙️ Task 12 – Add Protected Accounts

Add:

```text
CEO
CISO
BreakGlass01
IdentityAdmin01
```

to:

```text
Executive-RMAU
```

---

# Validation

Verify membership.

---

# ⚙️ Task 13 – Create Executive Administrator

Create:

```text
executive.admin
```

---

Assign:

```text
User Administrator
```

Scope:

```text
Executive-RMAU
```

---

# Validation

Verify assignment.

---

# ⚙️ Task 14 – Test Restricted Management

Login:

```text
germany.admin
```

Attempt:

```text
Reset Password
```

for:

```text
CEO
```

Expected:

```text
Access Denied
```

---

Login:

```text
india.admin
```

Attempt:

```text
Reset Password
```

for:

```text
CISO
```

Expected:

```text
Access Denied
```

---

Login:

```text
executive.admin
```

Attempt:

```text
Reset Password
```

for:

```text
CEO
```

Expected:

```text
Success
```

---

# Why This Happens

Restricted Management creates an additional authorization boundary.

Only administrators explicitly assigned to the Restricted Management Administrative Unit can manage protected users.

---

# ⚙️ Task 15 – Dynamic Administrative Unit Membership (Concept)

Membership can be automated using rules.

Example:

```text
user.department -eq "Germany"
```

Automatically places users into:

```text
Germany-AU
```

---

Benefits:

```text
Automatic Membership

Reduced Administration

Improved Governance
```

---

# Administrative Lifecycle

```text
Create Administrative Unit
        │
        ▼
Add Users
        │
        ▼
Assign Scoped Role
        │
        ▼
Delegate Administration
        │
        ▼
Monitor Activities
```

---

# ✅ Validation Results

| Validation Item                | Status |
| ------------------------------ | ------ |
| Germany AU Created             | ✅      |
| India AU Created               | ✅      |
| Users Added to AUs             | ✅      |
| Scoped Administrators Assigned | ✅      |
| Germany Boundary Tested        | ✅      |
| India Boundary Tested          | ✅      |
| Executive-RMAU Created         | ✅      |
| Restricted Management Enabled  | ✅      |
| Executive Users Protected      | ✅      |
| Executive Admin Assigned       | ✅      |
| Unauthorized Access Blocked    | ✅      |
| Authorized Access Allowed      | ✅      |

---

# 🎓 SC-300 Skills Covered

## Implement Identity Management

* Administrative Units
* Delegated Administration
* Scoped Administration

### Implement Access Management

* Role Assignment Scoping
* Least Privilege Access
* Administrative Boundaries

### Implement Identity Governance

* Restricted Management Administrative Units
* Executive Account Protection
* Privileged Identity Protection

### Monitor Identity Environment

* Administrative Activity Monitoring
* Audit Logs

---

# 🚀 Key Learning Outcomes

Through this lab, I gained hands-on experience in:

* Creating Administrative Units
* Delegating Administrative Roles
* Implementing Scoped Administration
* Enforcing Least Privilege Access
* Protecting Executive Accounts
* Configuring Restricted Management Administrative Units
* Testing Administrative Isolation
* Managing Regional Administration Models

---

# 💼 Portfolio Project

**Project Name:** Administrative Units and Restricted Management Administrative Units using Microsoft Entra ID

This project demonstrates how Microsoft Entra Administrative Units and Restricted Management Administrative Units can be used to implement delegated administration, administrative scoping, executive account protection, and least-privilege governance within enterprise environments.

---

# 👨‍💻 Author

**Your Name**

Microsoft SC-300 Identity and Access Administrator Journey

Microsoft Entra ID Enterprise Identity & Governance Lab Series

---

# Next Lab

```text
SC300-Lab12-Entitlement-Management
```

Topics:

* Access Packages
* Approval Workflows
* Self-Service Access Requests
* Guest User Onboarding
* Access Expiration
* Access Reviews Integration
* Identity Governance Automation
