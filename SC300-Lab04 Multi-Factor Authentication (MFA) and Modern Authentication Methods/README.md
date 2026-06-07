# 🔐 SC300-Lab04-MFA-Modern-Authentication

## Multi-Factor Authentication (MFA) and Modern Authentication Methods using Microsoft Entra ID

---

# 📖 Project Overview

This project demonstrates the implementation of Multi-Factor Authentication (MFA) and Modern Authentication Methods in Microsoft Entra ID.

The objective was to strengthen identity security by implementing additional authentication factors beyond passwords and enabling passwordless authentication technologies such as Microsoft Authenticator, Temporary Access Pass (TAP), and FIDO2 Security Keys.

This lab aligns with Microsoft SC-300 Identity and Access Administrator certification objectives and modern Zero Trust security principles.

---

# 🎯 Project Objectives

* Enable Multi-Factor Authentication (MFA)
* Configure Microsoft Authenticator
* Configure Temporary Access Pass (TAP)
* Configure FIDO2 Security Keys
* Enable Passwordless Authentication
* Test MFA Authentication Flow
* Monitor Authentication Activities
* Review Sign-In Logs and Reports

---

# 🏢 Business Scenario

ABC Technologies recently experienced multiple phishing attempts targeting employee accounts.

Management required the implementation of stronger authentication controls to:

* Protect user identities
* Reduce account compromise risk
* Improve authentication security
* Enable passwordless sign-in
* Support Zero Trust security initiatives

As the Identity Administrator, I was responsible for deploying and validating Microsoft Entra authentication controls.

---

# 🏗️ Solution Architecture

```text
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
├── SMS Authentication
├── Temporary Access Pass (TAP)
├── FIDO2 Security Keys
└── Passwordless Authentication

        ↓

Secure Sign-In Experience
```

---

# 🔑 Key Concepts

## Multi-Factor Authentication (MFA)

Multi-Factor Authentication requires users to provide multiple forms of identity verification before gaining access.

### Authentication Factors

```text
Something You Know
→ Password

Something You Have
→ Mobile Device

Something You Are
→ Fingerprint / Biometrics
```

### Benefits

* Protects against credential theft
* Reduces phishing risks
* Improves account security
* Supports Zero Trust architecture

---

## Microsoft Authenticator

Microsoft Authenticator is a mobile application used for:

* MFA approval notifications
* Passwordless sign-in
* Number matching authentication
* Identity verification

### Benefits

* More secure than SMS
* Fast sign-in experience
* Phishing-resistant authentication

---

## Temporary Access Pass (TAP)

Temporary Access Pass is a time-limited authentication method used for onboarding users into passwordless authentication.

### Use Case

```text
New Employee
      ↓
Administrator Creates TAP
      ↓
User Signs In
      ↓
Registers Authenticator
      ↓
Passwordless Authentication Enabled
```

### Benefits

* Simplifies onboarding
* Supports passwordless deployment
* Secure temporary access

---

## FIDO2 Security Keys

FIDO2 Security Keys are hardware-based authentication devices.

### Examples

* YubiKey
* Feitian Security Key

### Benefits

* Phishing-resistant authentication
* Passwordless access
* Strong security assurance

---

## Passwordless Authentication

Passwordless Authentication eliminates the need for traditional passwords.

### Traditional Sign-In

```text
Username
+
Password
+
MFA
```

### Passwordless Sign-In

```text
Username
+
Authenticator or FIDO2 Key
```

### Benefits

* Better user experience
* Reduced password attacks
* Stronger authentication security

---

# ⚙️ Lab Tasks Performed

## Task 1 – Review Authentication Methods Policy

Reviewed available authentication methods within Microsoft Entra ID.

### Methods Reviewed

* Microsoft Authenticator
* SMS Authentication
* Voice Call
* Temporary Access Pass
* FIDO2 Security Key

---

## Task 2 – Enable Microsoft Authenticator

Configured Microsoft Authenticator authentication method.

### Configuration

```text
Authentication Methods
→ Microsoft Authenticator
→ Enable
```

Target Users:

```text
All Users
```

---

## Task 3 – Register Microsoft Authenticator

Registered Microsoft Authenticator through Security Info.

### Registration Portal

```text
https://mysignins.microsoft.com/security-info
```

---

## Task 4 – Test MFA Authentication

Validated MFA sign-in process.

### Authentication Flow

```text
Password
      ↓
Authenticator Approval
      ↓
Access Granted
```

---

## Task 5 – Enable Temporary Access Pass (TAP)

Enabled Temporary Access Pass policy.

### Purpose

Provide temporary credentials for onboarding and passwordless registration.

---

## Task 6 – Generate Temporary Access Pass

Created Temporary Access Pass for test users.

### Configuration

```text
Lifetime: 8 Hours
```

---

## Task 7 – Enable FIDO2 Security Keys

Enabled FIDO2 authentication method.

### Configuration

```text
Authentication Methods
→ FIDO2 Security Key
→ Enable
```

---

## Task 8 – Register FIDO2 Security Key

Registered hardware security key for user authentication.

### Result

Successfully configured passwordless authentication using FIDO2.

---

## Task 9 – Enable Passwordless Authentication

Enabled passwordless sign-in through Microsoft Authenticator.

### Configuration

```text
Microsoft Authenticator
→ Passwordless Sign-In
→ Enable
```

---

## Task 10 – Test Passwordless Sign-In

Validated passwordless authentication flow.

### Authentication Flow

```text
Username
      ↓
Number Matching
      ↓
Access Granted
```

No password required.

---

## Task 11 – Review Authentication Reports

Reviewed Microsoft Entra authentication method reports.

### Reports Reviewed

* MFA Registration Status
* Passwordless Adoption
* Registered Authentication Methods

---

## Task 12 – Review Sign-In Logs

Reviewed sign-in logs to verify:

* MFA Events
* Passwordless Sign-Ins
* Authentication Methods Used
* User Login Activity

---

# ✅ Validation Results

| Validation Item                 | Status |
| ------------------------------- | ------ |
| MFA Enabled                     | ✅      |
| Authenticator Registered        | ✅      |
| MFA Tested                      | ✅      |
| TAP Enabled                     | ✅      |
| TAP Generated                   | ✅      |
| FIDO2 Enabled                   | ✅      |
| FIDO2 Registered                | ✅      |
| Passwordless Enabled            | ✅      |
| Passwordless Tested             | ✅      |
| Authentication Reports Reviewed | ✅      |
| Sign-In Logs Reviewed           | ✅      |

---



# 🎓 SC-300 Skills Covered

## Implement Authentication Methods

* Microsoft Authenticator
* Temporary Access Pass
* FIDO2 Security Keys

## Implement Authentication Management

* Multi-Factor Authentication
* Passwordless Authentication

## Implement Identity Security

* Strong Authentication Controls
* User Verification

## Monitor Authentication Activities

* Authentication Reports
* Sign-In Logs

---

# 🚀 Key Learning Outcomes

Through this lab, I gained hands-on experience in:

* Implementing Multi-Factor Authentication
* Deploying Passwordless Authentication
* Managing Authentication Methods
* Configuring Temporary Access Pass
* Implementing FIDO2 Security Keys
* Monitoring Authentication Events
* Strengthening Identity Security using Zero Trust principles

---

# 💼 Portfolio Project

**Project Name:** Multi-Factor Authentication (MFA) and Modern Authentication Methods using Microsoft Entra ID

This project demonstrates the implementation of enterprise-grade authentication controls using Microsoft Entra ID, including MFA, Temporary Access Pass, FIDO2 Security Keys, and Passwordless Authentication. The solution strengthens identity security and aligns with Microsoft SC-300 certification objectives and Zero Trust architecture principles.

---

# 👨‍💻 Author

**Your Name**

Microsoft SC-300 Identity and Access Administrator Journey

Microsoft Entra ID Enterprise Identity & Governance Lab Series
