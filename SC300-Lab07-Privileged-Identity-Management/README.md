# 🔐 SC300-Lab07-Privileged-Identity-Management

## Privileged Identity Management (PIM) and Just-In-Time Administration using Microsoft Entra ID

---

# 📖 Project Overview

This project demonstrates the implementation of Microsoft Entra Privileged Identity Management (PIM) to secure privileged accounts through Just-In-Time (JIT) access, approval workflows, MFA enforcement, and time-bound role activation.

Instead of assigning permanent administrator roles, users receive eligible assignments and activate privileges only when needed.

This significantly reduces the organization's attack surface and supports Zero Trust security principles.

---

# 🎯 Project Objectives

* Enable Privileged Identity Management (PIM)
* Configure Eligible Role Assignments
* Configure Just-In-Time (JIT) Access
* Implement Approval Workflows
* Enforce MFA for Role Activation
* Configure Activation Duration
* Review PIM Audit Logs
* Monitor Privileged Access Activities

---

# 🏢 Business Scenario

ABC Technologies has several IT administrators with permanent Global Administrator access.

Security assessments identified the following concerns:

* Excessive administrative privileges
* Permanent privileged access
* Lack of approval process
* Limited auditing of privileged activities

To reduce these risks, Microsoft Entra Privileged Identity Management (PIM) was implemented.

As the Identity Administrator, I was responsible for securing privileged roles using JIT access and governance controls.

---

# 🏗️ Solution Architecture

```text
Administrator
      │
      ▼
Eligible Role Assignment
      │
      ▼
Role Activation Request
      │
      ├── MFA Verification
      ├── Business Justification
      ├── Approval Workflow
      └── Time Restriction
      │
      ▼
Temporary Privileged Access
      │
      ▼
Role Automatically Removed
```

---

# 🔑 Understanding the Concepts

## What is Privileged Identity Management (PIM)?

PIM is a Microsoft Entra service that controls, monitors, and secures privileged access.

Instead of permanent administrator permissions, users receive access only when required.

---

## Why is PIM Important?

Traditional Administration:

```text
User
      ↓
Global Administrator
      ↓
24x7 Permanent Access
```

Risk:

* Account compromise
* Insider threats
* Privilege abuse

---

## What is Just-In-Time (JIT) Access?

JIT grants privileged access only for a limited period.

### Example

Without PIM:

```text
John
Global Administrator
24 Hours a Day
```

With PIM:

```text
John
Eligible Global Administrator

Needs Access?
      ↓
Activate Role
      ↓
2 Hours Access
      ↓
Role Automatically Removed
```

---

## What is an Eligible Assignment?

An Eligible Assignment means the user can activate a role when required but does not permanently hold that role.

### Example

```text
John
Eligible Global Administrator
```

John is not an administrator until activation occurs.

---

## What is an Active Assignment?

An Active Assignment means the user currently holds the role.

### Example

```text
John
Global Administrator
Status: Active
```

Privileges are immediately available.

---

## Why Use Eligible Instead of Active?

Benefits:

* Reduced attack surface
* Better governance
* Improved auditing
* Stronger security

---

# ⚙️ Task 1 – Enable Privileged Identity Management

Navigate:

```text
Microsoft Entra Admin Center
→ Identity Governance
→ Privileged Identity Management
```

Enable PIM for:

* Microsoft Entra Roles

Verify successful activation.

---

# ⚙️ Task 2 – Discover Existing Administrators

Navigate:

```text
PIM
→ Microsoft Entra Roles
→ Discover Resources
```

Review:

* Global Administrators
* User Administrators
* Authentication Administrators
* Security Administrators

---

# ⚙️ Task 3 – Assign Eligible Global Administrator Role

## Why This Task Exists

Reduce permanent administrative access.

---

## Configuration Steps

Navigate:

```text
PIM
→ Roles
→ Global Administrator
→ Add Assignments
```

Configure:

```text
Assignment Type:
Eligible
```

Assign:

```text
John IT
```

Save.

---

## Validation

Verify:

```text
Role Status:
Eligible
```

Not Active.

---

# ⚙️ Task 4 – Configure Role Activation Settings

Navigate:

```text
PIM
→ Roles
→ Global Administrator
→ Settings
```

Configure:

### Activation Duration

```text
Maximum Duration:
2 Hours
```

### Require MFA

```text
Enabled
```

### Require Justification

```text
Enabled
```

---

# Why Require MFA?

Even if credentials are stolen:

```text
Password Stolen
      ↓
MFA Required
      ↓
Access Blocked
```

---

# Why Require Justification?

Administrators must explain why privileged access is required.

Example:

```text
Reset Executive User Account
```

This improves accountability.

---

# ⚙️ Task 5 – Configure Approval Workflow

Navigate:

```text
PIM
→ Role Settings
→ Activation
```

Enable:

```text
Require Approval
```

Approver:

```text
Security Administrator
```

---

## Example Workflow

```text
John Requests Activation
      ↓
Approval Required
      ↓
Security Team Reviews
      ↓
Approved
      ↓
Access Granted
```

---

# ⚙️ Task 6 – Activate Eligible Role

Login as:

```text
John IT
```

Navigate:

```text
My Roles
→ Activate
```

Provide:

```text
Business Justification
```

Complete:

```text
MFA Challenge
```

Submit request.

---

## Validation

Expected Result:

```text
Role Status:
Active
```

Duration:

```text
2 Hours
```

---

# ⚙️ Task 7 – Review Activation History

Navigate:

```text
PIM
→ Audit History
```

Review:

* Activation Requests
* Approvals
* Denials
* Expirations

---

# ⚙️ Task 8 – Review Alerts

Navigate:

```text
PIM
→ Alerts
```

Review:

* Excessive Administrators
* Permanent Assignments
* Unused Privileged Accounts

---

## Why Are Alerts Important?

PIM alerts help identify:

* Security risks
* Misconfigurations
* Governance violations

---

# ⚙️ Task 9 – Convert Active Assignments to Eligible

Identify permanent administrators.

Convert:

```text
Active
```

to:

```text
Eligible
```

Where possible.

---

## Benefit

Reduced standing privileges.

---

# ⚙️ Task 10 – Review Audit Logs

Navigate:

```text
Monitoring
→ Audit Logs
```

Review:

* Role Assignments
* Role Activations
* Approval Events
* Privileged Activities

---

# 📊 PIM Security Benefits

## Before PIM

```text
Global Administrator
24/7 Access
365 Days a Year
```

Risk:

```text
High
```

---

## After PIM

```text
Eligible Assignment
      ↓
Approval
      ↓
MFA
      ↓
2 Hour Activation
      ↓
Automatic Removal
```

Risk:

```text
Significantly Reduced
```

-
---

# ✅ Validation Results

| Validation Item              | Status |
| ---------------------------- | ------ |
| PIM Enabled                  | ✅      |
| Eligible Assignment Created  | ✅      |
| MFA for Activation Enabled   | ✅      |
| Justification Required       | ✅      |
| Approval Workflow Configured | ✅      |
| Role Activation Tested       | ✅      |
| Alerts Reviewed              | ✅      |
| Audit Logs Reviewed          | ✅      |

---

# 🎓 SC-300 Skills Covered

### Implement Identity Governance

* Privileged Identity Management
* Role Governance
* Access Reviews

### Implement Identity Security

* Just-In-Time Administration
* MFA Enforcement
* Approval Workflows

### Monitor Identity Environment

* Privileged Activity Monitoring
* Audit Logs
* Security Alerts

---

# 🚀 Key Learning Outcomes

Through this lab, I gained hands-on experience in:

* Implementing Just-In-Time Administration
* Reducing privileged access risks
* Configuring approval workflows
* Enforcing MFA for privileged roles
* Monitoring administrator activities
* Applying Zero Trust principles to privileged access

---

# 💼 Portfolio Project

**Project Name:** Privileged Identity Management (PIM) and Just-In-Time Administration using Microsoft Entra ID

This project demonstrates implementation of Microsoft Entra Privileged Identity Management to secure administrative roles through eligible assignments, approval workflows, MFA enforcement, and temporary privileged access activation.

---

# 👨‍💻 Author

**Your Name**

Microsoft SC-300 Identity and Access Administrator Journey

Microsoft Entra ID Enterprise Identity & Governance Lab Series
