# 🛡️ SC300-Lab05-Conditional-Access-Zero-Trust

## Conditional Access and Zero Trust Security using Microsoft Entra ID

---

# 📖 Project Overview

This project demonstrates the implementation of Microsoft Entra Conditional Access policies using Zero Trust security principles.

The objective is to protect identities, applications, and organizational resources by evaluating multiple signals during authentication and enforcing appropriate access controls.

Conditional Access serves as Microsoft's policy engine for implementing Zero Trust security and protecting enterprise identities.

---

# 🎯 Project Objectives

* Configure Conditional Access Policies
* Require MFA for Administrators
* Block Legacy Authentication
* Configure Trusted Locations
* Require MFA Outside Trusted Locations
* Configure Device-Based Access Controls
* Implement Authentication Strengths
* Review Conditional Access Reports
* Validate Security Controls through Sign-In Logs

---

# 🏢 Business Scenario

ABC Technologies is expanding its remote workforce and adopting cloud-first security practices.

Recent security assessments identified several risks:

* Password-based attacks
* Legacy authentication usage
* Unmanaged devices
* Remote access from unknown locations
* Privileged account compromise

To address these risks, Microsoft Entra Conditional Access policies were implemented using Zero Trust principles.

As the Identity Administrator, I was responsible for designing, implementing, testing, and validating these access controls.

---

# 🏗️ Solution Architecture

```text
User Sign-In
      │
      ▼
Microsoft Entra ID
      │
      ▼
Conditional Access Engine
      │
      ├── User Evaluation
      ├── Location Evaluation
      ├── Device Evaluation
      ├── Risk Evaluation
      └── Authentication Evaluation
      │
      ▼
Access Decision
      │
      ├── Allow Access
      ├── Require MFA
      ├── Require Compliant Device
      └── Block Access
```

---

# 🔑 Understanding the Concepts

## What is Conditional Access?

Conditional Access is Microsoft's policy engine that evaluates sign-in conditions and determines whether access should be granted.

Think of Conditional Access as:

```text
IF
(User + Device + Location + Risk)

THEN

Allow Access
Require MFA
Require Compliant Device
Block Access
```

### Real-World Example

When John signs in:

Microsoft checks:

```text
Who is the user?
Where is the user connecting from?
Which device is being used?
Is the sign-in risky?
```

Then Microsoft decides whether access should be granted or blocked.

---

## Why Conditional Access Exists

Traditional authentication:

```text
Username
+
Password
=
Access
```

Problem:

```text
If password is stolen
Attacker gets access
```

Conditional Access adds additional verification:

```text
Username
+
Password
+
MFA
+
Trusted Device
+
Safe Location
=
Access
```

This significantly reduces identity-related attacks.

---

## What is Zero Trust?

Zero Trust is a security model based on the principle:

```text
Never Trust
Always Verify
```

No user, device, application, or network is trusted automatically.

Every access request must be continuously verified.

### Zero Trust Principles

#### Verify Explicitly

Always verify:

* Identity
* Device
* Location
* Risk

#### Use Least Privilege

Users should only receive permissions required for their role.

#### Assume Breach

Design security controls as though attackers may already be inside the environment.

---

# ⚙️ Policy 1 – Require MFA for Administrators

## Why This Policy Exists

Administrative accounts are high-value targets.

Examples:

* Global Administrator
* Authentication Administrator
* User Administrator

If compromised, attackers can:

* Create new administrators
* Reset passwords
* Disable security controls
* Access sensitive resources

---

## Real-World Scenario

Without MFA:

```text
Attacker steals password
      ↓
Login Successful
```

With MFA:

```text
Attacker steals password
      ↓
MFA Prompt Appears
      ↓
Attacker Cannot Approve
      ↓
Access Blocked
```

---

## Configuration Steps

Navigate:

```text
Microsoft Entra Admin Center
→ Protection
→ Conditional Access
→ New Policy
```

Users:

```text
Global Administrators
Authentication Administrators
User Administrators
```

Grant Controls:

```text
Require Multi-Factor Authentication
```

Enable Policy.

---

## Validation

Sign in using an administrator account.

Expected Result:

```text
Password
      ↓
MFA Challenge
      ↓
Access Granted
```

---

# ⚙️ Policy 2 – Block Legacy Authentication

## What is Legacy Authentication?

Legacy authentication protocols include:

* POP3
* IMAP
* SMTP AUTH
* Exchange ActiveSync

These protocols only support:

```text
Username
+
Password
```

They do not support:

* MFA
* Conditional Access
* Authentication Strengths

---

## Why This Policy Exists

Attackers frequently use password spraying against legacy protocols.

Example:

```text
Summer2025!
Welcome123!
Company2025!
```

These attacks attempt common passwords against thousands of users.

---

## Configuration Steps

Navigate:

```text
Conditional Access
→ New Policy
```

Users:

```text
All Users
```

Condition:

```text
Client Apps
→ Legacy Authentication Clients
```

Grant Control:

```text
Block Access
```

Enable Policy.

---

## Validation

Attempt sign-in using a legacy protocol.

Expected Result:

```text
Access Blocked
```

---

# ⚙️ Policy 3 – Configure Trusted Locations

## What is a Trusted Location?

A Trusted Location is an approved corporate network or IP address range.

Example:

```text
Berlin Headquarters

203.0.113.10
```

---

## Why This Policy Exists

Benefits:

* Reduced MFA prompts
* Improved user experience
* Stronger location-based security

---

## Configuration Steps

Navigate:

```text
Protection
→ Conditional Access
→ Named Locations
```

Create:

```text
Berlin Office
```

Add corporate public IP address.

Mark as:

```text
Trusted Location
```

Save.

---

## Validation

Sign in from the office network.

Expected Result:

```text
Trusted Location Recognized
```

---

# ⚙️ Policy 4 – Require MFA Outside Trusted Locations

## Why This Policy Exists

Remote access introduces additional risk.

Users connecting from:

* Home networks
* Hotels
* Airports
* Public Wi-Fi

should be required to perform MFA.

---

## Configuration Logic

```text
Location ≠ Trusted Location
```

Then:

```text
Require MFA
```

---

## Configuration Steps

Navigate:

```text
Conditional Access
→ New Policy
```

Users:

```text
All Users
```

Locations:

```text
Exclude Trusted Locations
```

Grant Controls:

```text
Require MFA
```

Enable Policy.

---

## Validation

Sign in from an external network.

Expected Result:

```text
Password
      ↓
MFA Prompt
      ↓
Access Granted
```

---

# ⚙️ Policy 5 – Require Compliant Device

## What is a Compliant Device?

A compliant device meets organizational security requirements.

Examples:

* Device encrypted
* Antivirus installed
* Operating system updated
* Managed through Intune

---

## Why This Policy Exists

Even legitimate users may use insecure devices.

Example:

```text
Personal Laptop
No Antivirus
Outdated OS
```

This increases organizational risk.

---

## Configuration Steps

Navigate:

```text
Conditional Access
→ New Policy
```

Users:

```text
All Users
```

Grant Controls:

```text
Require Device to be Marked as Compliant
```

Enable Policy.

---

## Validation

### Compliant Device

```text
Access Granted
```

### Non-Compliant Device

```text
Access Blocked
```

---

# ⚙️ Policy 6 – Authentication Strengths

## What are Authentication Strengths?

Authentication Strengths define how strong authentication must be before access is granted.

---

## Examples

### Basic MFA

```text
Password
+
Microsoft Authenticator
```

### Strong MFA

```text
Password
+
FIDO2 Security Key
```

### Phishing Resistant MFA

```text
FIDO2 Security Key
```

---

## Why This Policy Exists

Not all MFA methods provide the same protection.

Example:

```text
SMS MFA
```

may be vulnerable to SIM-swapping attacks.

Whereas:

```text
FIDO2 Security Key
```

is phishing resistant.

---

## Configuration Steps

Navigate:

```text
Conditional Access
→ New Policy
```

Applications:

```text
Microsoft Entra Admin Center
Azure Portal
```

Grant Controls:

```text
Require Authentication Strength
```

Select:

```text
Phishing Resistant MFA
```

Enable Policy.

---

## Validation

Attempt to access Azure Portal.

Expected Result:

```text
FIDO2 Security Key Required
```

---

# 📊 Monitoring and Reporting

## Sign-In Logs

Navigate:

```text
Monitoring
→ Sign-In Logs
```

Review:

* Authentication Method Used
* Conditional Access Evaluation
* Policy Results
* Sign-In Success/Failure

---

## Conditional Access Insights

Review:

```text
Protection
→ Conditional Access
→ Insights and Reporting
```

Validate:

* MFA Enforcement
* Blocked Sign-Ins
* Device Compliance Decisions
* Authentication Strength Enforcement

---

# ✅ Validation Results

| Validation Item                           | Status |
| ----------------------------------------- | ------ |
| MFA for Administrators Configured         | ✅      |
| Legacy Authentication Blocked             | ✅      |
| Trusted Locations Configured              | ✅      |
| MFA Outside Trusted Locations Configured  | ✅      |
| Device Compliance Policy Configured       | ✅      |
| Authentication Strength Policy Configured | ✅      |
| Policy Testing Completed                  | ✅      |
| Sign-In Logs Reviewed                     | ✅      |
| Conditional Access Reports Reviewed       | ✅      |

---

# 📸 Screenshots



# 🎓 SC-300 Skills Covered

### Implement Authentication and Access Management

* Conditional Access
* Multi-Factor Authentication
* Authentication Strengths

### Implement Identity Security

* Zero Trust Security
* Device Compliance
* Risk-Based Access Control

### Monitor Identity Environment

* Conditional Access Reporting
* Sign-In Logs
* Authentication Monitoring

---

# 🚀 Key Learning Outcomes

Through this lab, I gained hands-on experience in:

* Designing Conditional Access Policies
* Applying Zero Trust Security Principles
* Protecting Administrative Accounts
* Blocking Legacy Authentication
* Implementing Location-Based Access Controls
* Enforcing Device Compliance
* Deploying Authentication Strengths
* Monitoring Identity Security Events

---

# 💼 Portfolio Project

**Project Name:** Conditional Access and Zero Trust Security using Microsoft Entra ID

This project demonstrates the implementation of enterprise-grade access control policies using Microsoft Entra Conditional Access. The solution applies Zero Trust principles to protect users, devices, and applications while reducing the organization's attack surface and improving identity security.

---

# 👨‍💻 Author

Aman Varma 

Microsoft SC-300 Identity and Access Administrator Journey

Microsoft Entra ID Enterprise Identity & Governance Lab Series
