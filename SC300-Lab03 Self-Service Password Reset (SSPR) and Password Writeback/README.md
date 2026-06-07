# 🔐 SC300-Lab03-SSPR-Password-Reset

## Self-Service Password Reset (SSPR) and Password Writeback using Microsoft Entra ID


\

---

# 📖 Project Overview

This project demonstrates the implementation of **Microsoft Entra Self-Service Password Reset (SSPR)**, enabling users to securely reset forgotten passwords and unlock accounts without requiring assistance from the IT Helpdesk.

The solution improves security, reduces operational costs, and enhances user productivity by providing a secure self-service password recovery experience.

---

# 🎯 Project Objectives

* Configure Self-Service Password Reset (SSPR)
* Configure Authentication Methods
* Enable Registration Campaign
* Test Password Reset Workflow
* Test Account Unlock Workflow
* Review Audit Logs
* Review Sign-In Logs
* Configure Password Writeback (Hybrid Environment)

---

# 🏢 Business Scenario

ABC Technologies receives a large number of password-related support requests each month.

### Common Challenges

* Forgotten passwords
* Locked user accounts
* Delayed productivity
* Increased Helpdesk workload

To solve these challenges, Microsoft Entra Self-Service Password Reset (SSPR) was implemented.

---

# 🏗️ Solution Architecture

```text
ABC Technologies

Users
│
├── John IT
├── Sarah IT
├── Mike HR
├── Emma HR
├── David Finance
└── Lisa Finance

        ↓

Microsoft Entra ID

        ↓

Authentication Methods

├── Microsoft Authenticator
├── Mobile Phone
├── Email Verification
└── Security Questions

        ↓

Self-Service Password Reset

        ↓

Password Reset / Account Unlock
```

---

# 🔑 Key Concepts

## Self-Service Password Reset (SSPR)

Self-Service Password Reset allows users to reset forgotten passwords or unlock their accounts without contacting IT support.

### Benefits

* Reduced Helpdesk tickets
* Faster password recovery
* Improved user productivity
* Enhanced user experience

---

## Authentication Methods

Authentication methods are used to verify a user's identity before a password reset can occur.

### Configured Methods

* Microsoft Authenticator
* Mobile Phone (SMS)
* Email Verification
* Security Questions (Optional)

### Security Configuration

```text
Required Authentication Methods: 2
```

This ensures stronger identity verification before password reset.

---

## Registration Campaign

A Registration Campaign prompts users to register authentication methods during sign-in.

### Why It Is Important

Users cannot use SSPR unless they have registered authentication methods.

### Example

```text
User signs in
       ↓
Prompt appears
       ↓
Register Microsoft Authenticator
       ↓
SSPR becomes available
```

### Benefits

* Increases MFA adoption
* Improves security posture
* Simplifies onboarding

---

## Password Writeback

Password Writeback synchronizes password changes made in Microsoft Entra ID back to on-premises Active Directory.

### Hybrid Identity Flow

```text
User resets password
       ↓
Microsoft Entra ID
       ↓
Microsoft Entra Connect
       ↓
On-Premises Active Directory
```

### Benefits

* Single password across environments
* Reduced synchronization issues
* Improved hybrid identity experience

---

# ⚙️ Lab Tasks Performed

## Task 1 – Enable Self-Service Password Reset

Configured SSPR for selected users/groups.

### Configuration

```text
Protection
→ Password Reset
→ Enable SSPR
```

---

## Task 2 – Configure Authentication Methods

Enabled:

* Microsoft Authenticator
* Mobile Phone
* Email Verification

Configured:

```text
Require 2 Authentication Methods
```

---

## Task 3 – Configure Registration Settings

Enabled user registration requirements.

### Configuration

```text
Require Registration: Yes
Reconfirmation Interval: 180 Days
```

---

## Task 4 – Enable Registration Campaign

Configured Microsoft-managed registration campaign.

### Purpose

Prompt users to register authentication methods during sign-in.

---

## Task 5 – Register Authentication Methods

Tested registration process using:

* Mobile Number
* Microsoft Authenticator

---

## Task 6 – Perform Password Reset

Validated successful password recovery through the SSPR portal.

---

## Task 7 – Test Account Unlock

Validated account unlock process using registered authentication methods.

---

## Task 8 – Review Audit Logs

Reviewed:

* Password Reset Events
* Registration Events
* Authentication Method Changes

---

## Task 9 – Configure Password Writeback

Enabled Password Writeback using Microsoft Entra Connect.

---

## Task 10 – Review Sign-In Logs

Verified:

* Successful Password Reset Events
* Authentication Methods Used
* User Sign-In Activity

---

# ✅ Validation Results

| Validation Item                   | Status |
| --------------------------------- | ------ |
| SSPR Enabled                      | ✅      |
| Authentication Methods Configured | ✅      |
| Registration Campaign Enabled     | ✅      |
| Password Reset Tested             | ✅      |
| Account Unlock Tested             | ✅      |
| Audit Logs Verified               | ✅      |
| Sign-In Logs Verified             | ✅      |
| Password Writeback Enabled        | ✅      |

---



---

# 🎓 SC-300 Skills Covered

### Implement Identity Management

* User Identity Management
* Authentication Methods

### Implement Authentication and Access Management

* Self-Service Password Reset
* Authentication Verification

### Implement Identity Governance

* Registration Campaign
* User Lifecycle Security

### Monitor and Maintain Identity Environment

* Audit Logs
* Sign-In Logs

---

# 🚀 Key Learning Outcomes

Through this lab, I gained hands-on experience in:

* Implementing Self-Service Password Reset
* Managing Authentication Methods
* Configuring Registration Campaigns
* Monitoring Identity Activities
* Supporting Hybrid Identity Environments
* Improving Security and User Experience

---

# 💼 Portfolio Project

**Project Name:** Self-Service Password Reset (SSPR) and Password Writeback using Microsoft Entra ID

This project demonstrates practical implementation of identity security controls and self-service identity management capabilities aligned with Microsoft SC-300 certification objectives and enterprise identity governance best practices.

---

# 👨‍💻 Author

Aman Varma

Microsoft SC-300 Identity and Access Administrator Journey

Microsoft Entra ID Enterprise Identity & Governance Lab Series
