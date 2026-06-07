# 🛡️ SC300-Lab06-Identity-Protection

## Microsoft Entra Identity Protection: User Risk, Sign-In Risk, and Risk-Based Policies

---

# 📖 Project Overview

This project demonstrates the implementation of Microsoft Entra Identity Protection to detect, investigate, and automatically respond to identity-based threats.

The solution uses machine learning and Microsoft's global threat intelligence to identify risky users and risky sign-ins and automatically enforce security controls.

Identity Protection is a key component of a Zero Trust security architecture.

---

# 🎯 Project Objectives

* Understand User Risk and Sign-In Risk
* Configure User Risk Policy
* Configure Sign-In Risk Policy
* Investigate Risk Detections
* Configure Risk-Based Conditional Access
* Monitor Risk Events
* Review Identity Protection Reports
* Validate Automated Remediation

---

# 🏢 Business Scenario

ABC Technologies has enabled MFA and Conditional Access.

However, security teams need protection against:

* Leaked credentials
* Password spray attacks
* Anonymous IP sign-ins
* Impossible travel events
* Suspicious sign-in behavior

To address these threats, Microsoft Entra Identity Protection was deployed.

As the Identity Administrator, I was responsible for implementing risk detection and automated response policies.

---

# 🏗️ Solution Architecture

```text
User Sign-In
      │
      ▼
Microsoft Entra ID
      │
      ▼
Identity Protection
      │
      ├── Risk Detection
      ├── User Risk Analysis
      ├── Sign-In Risk Analysis
      └── Threat Intelligence
      │
      ▼
Risk Policy Evaluation
      │
      ├── Require MFA
      ├── Require Password Change
      └── Block Access
      │
      ▼
Secure Access Decision
```

---

# 🔑 Understanding the Concepts

## What is Identity Protection?

Identity Protection is a Microsoft Entra security feature that continuously analyzes user and sign-in activity for suspicious behavior.

It helps answer:

```text
Is this sign-in risky?
Is this user compromised?
Should access be allowed?
```

---

## What is User Risk?

User Risk represents the probability that a user's identity has been compromised.

### Example Risk Signals

* Credentials found on the dark web
* Leaked passwords
* Malware-related activity
* Suspicious account behavior

### Real Example

```text
John's password appears in a breach.

Microsoft detects leaked credentials.

User Risk = High
```

---

## What is Sign-In Risk?

Sign-In Risk represents the likelihood that a specific authentication attempt is suspicious.

### Example Risk Signals

* Anonymous IP address
* TOR network usage
* Impossible travel
* Malware-linked IP address

### Real Example

```text
John signs in from Germany.

Five minutes later,
another sign-in appears from Brazil.

Microsoft detects:

Impossible Travel

Sign-In Risk = High
```

---

## What is Impossible Travel?

Impossible Travel occurs when a user signs in from two locations that are geographically impossible to travel between within the observed timeframe.

### Example

```text
09:00 AM
Berlin

09:10 AM
New York

Impossible Travel Detected
```

---

## What are Leaked Credentials?

Microsoft compares user credentials against known breach datasets.

### Example

```text
john.it@abctech.com

Password found in breach database

User Risk Generated
```

---

# ⚙️ Task 1 – Review Identity Protection Dashboard

Navigate:

```text
Microsoft Entra Admin Center
→ Protection
→ Identity Protection
```

Review:

* Risky Users
* Risky Sign-Ins
* Risk Detections

---

# ⚙️ Task 2 – Configure User Risk Policy

## Why This Policy Exists

If a user's credentials are compromised, they should be forced to secure their account.

---

## Configuration Steps

Navigate:

```text
Protection
→ Identity Protection
→ User Risk Policy
```

Users:

```text
All Users
```

Risk Level:

```text
Medium and Above
```

Control:

```text
Require Password Change
```

Enable Policy.

---

## Validation

Expected Result:

```text
User Risk Detected
      ↓
Password Change Required
      ↓
Access Restored
```

---

# ⚙️ Task 3 – Configure Sign-In Risk Policy

## Why This Policy Exists

Suspicious authentication attempts should require additional verification.

---

## Configuration Steps

Navigate:

```text
Protection
→ Identity Protection
→ Sign-In Risk Policy
```

Users:

```text
All Users
```

Risk Level:

```text
Medium and Above
```

Grant Control:

```text
Require MFA
```

Enable Policy.

---

## Validation

Expected Result:

```text
Risky Sign-In
      ↓
MFA Challenge
      ↓
Access Granted
```

---

# ⚙️ Task 4 – Investigate Risky Users

Navigate:

```text
Protection
→ Risky Users
```

Review:

* Risk Level
* Detection Type
* Risk State
* User Details

---

## Risk States

### At Risk

```text
Potential compromise detected
```

### Confirmed Compromised

```text
Administrator confirms compromise
```

### Remediated

```text
Risk resolved
```

---

# ⚙️ Task 5 – Investigate Risky Sign-Ins

Navigate:

```text
Protection
→ Risky Sign-Ins
```

Review:

* Anonymous IP Detection
* Impossible Travel
* Malware-linked Activity
* Suspicious Browser Activity

---

# ⚙️ Task 6 – Review Risk Detections

Navigate:

```text
Protection
→ Risk Detections
```

Review:

* Detection Type
* Risk Level
* Detection Date
* User Impact

---

# ⚙️ Task 7 – Dismiss or Confirm Risk

As an administrator:

```text
Risky User
→ Confirm Compromised
```

or

```text
Risky User
→ Dismiss Risk
```

---

## Why This Matters

Identity Protection improves accuracy through administrator feedback.

---

# ⚙️ Task 8 – Review Identity Protection Reports

Review:

* Risk Trends
* Detection History
* High-Risk Users
* High-Risk Sign-Ins

---

# ⚙️ Task 9 – Review Sign-In Logs

Navigate:

```text
Monitoring
→ Sign-In Logs
```

Verify:

* Risk Level
* Conditional Access Decisions
* MFA Challenges
* Authentication Methods

---

# 📊 Risk Levels Explained

## Low Risk

Minor suspicious activity.

Example:

```text
Unknown browser
```

---

## Medium Risk

Potential compromise.

Example:

```text
Anonymous IP
```

---

## High Risk

Strong compromise indicators.

Example:

```text
Leaked Credentials
Impossible Travel
```




# ✅ Validation Results

| Validation Item                | Status |
| ------------------------------ | ------ |
| Identity Protection Enabled    | ✅      |
| User Risk Policy Configured    | ✅      |
| Sign-In Risk Policy Configured | ✅      |
| Risky Users Reviewed           | ✅      |
| Risky Sign-Ins Reviewed        | ✅      |
| Risk Detections Investigated   | ✅      |
| Reports Reviewed               | ✅      |
| Sign-In Logs Reviewed          | ✅      |

---

# 🎓 SC-300 Skills Covered

### Implement Identity Security

* Identity Protection
* User Risk Policies
* Sign-In Risk Policies

### Implement Authentication and Access Management

* Risk-Based Conditional Access
* MFA Enforcement

### Monitor Identity Environment

* Risk Investigations
* Threat Monitoring
* Security Reporting

---

# 🚀 Key Learning Outcomes

Through this lab, I gained hands-on experience in:

* Detecting compromised identities
* Investigating risky sign-ins
* Implementing risk-based policies
* Automating remediation workflows
* Monitoring identity threats
* Applying Zero Trust security principles

---

# 💼 Portfolio Project

**Project Name:** Microsoft Entra Identity Protection and Risk-Based Access Control

This project demonstrates the implementation of Microsoft Entra Identity Protection to detect identity threats, investigate risky sign-ins, enforce risk-based policies, and automate security responses using Microsoft's threat intelligence platform.

---

# 👨‍💻 Author

**Your Name**

Microsoft SC-300 Identity and Access Administrator Journey

Microsoft Entra ID Enterprise Identity & Governance Lab Series
s