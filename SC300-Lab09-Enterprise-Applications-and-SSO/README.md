# 🔐 SC300-Lab09-Enterprise-Applications-and-SSO

## Enterprise Applications, Single Sign-On (SSO), SAML, OAuth 2.0, OpenID Connect, and Application Provisioning using Microsoft Entra ID

---

# 📖 Project Overview

This project demonstrates how Microsoft Entra ID integrates with enterprise applications to provide secure authentication, authorization, Single Sign-On (SSO), and lifecycle management.

The goal is to enable users to access multiple applications using a single identity while improving security, user experience, and governance.

This lab covers:

* Enterprise Applications
* Single Sign-On (SSO)
* SAML Authentication
* OAuth 2.0
* OpenID Connect (OIDC)
* Application Assignments
* Application Owners
* Application Provisioning
* Sign-In Monitoring

---

# 🎯 Project Objectives

* Add Enterprise Applications
* Configure Single Sign-On (SSO)
* Understand Authentication Protocols
* Configure SAML-Based Authentication
* Understand OAuth 2.0 and OIDC
* Assign Users and Groups
* Configure Application Owners
* Monitor Application Sign-ins
* Understand SCIM Provisioning

---

# 🏢 Business Scenario

ABC Technologies uses multiple cloud applications:

* Salesforce
* ServiceNow
* Jira
* Workday
* Confluence

Users currently maintain separate credentials for every application.

Problems:

* Password fatigue
* Password reuse
* Increased helpdesk tickets
* Poor user experience

Management wants a centralized authentication solution using Microsoft Entra ID.

As the Identity Administrator, I was responsible for implementing Single Sign-On (SSO) and application governance.

---

# 🏗️ Solution Architecture

```text
User
 │
 ▼
Microsoft Entra ID
 │
 ├── Authentication
 ├── MFA
 ├── Conditional Access
 └── Identity Protection
 │
 ▼
Enterprise Application
 │
 ├── Salesforce
 ├── ServiceNow
 ├── Workday
 ├── Jira
 └── Custom Applications
```

---

# 🔑 Understanding Enterprise Applications

## What is an Enterprise Application?

An Enterprise Application is any application integrated with Microsoft Entra ID.

Examples:

* Salesforce
* ServiceNow
* SAP
* Workday
* Jira
* Confluence

Microsoft Entra acts as the Identity Provider (IdP).

---

## What is an Identity Provider (IdP)?

The system responsible for authenticating users.

Example:

```text
Microsoft Entra ID
```

---

## What is a Service Provider (SP)?

The application that trusts the Identity Provider.

Examples:

```text
Salesforce
ServiceNow
Workday
```

---

# 🔑 Understanding Single Sign-On (SSO)

## What is SSO?

Single Sign-On allows users to authenticate once and access multiple applications.

Without SSO:

```text
User
│
├── Salesforce Password
├── Jira Password
├── Workday Password
└── ServiceNow Password
```

---

With SSO:

```text
User
 │
 ▼
Microsoft Entra ID
 │
 ▼
Access All Applications
```

One login.

Multiple applications.

---

## Benefits of SSO

* Better user experience
* Fewer passwords
* Reduced helpdesk tickets
* Improved security
* Centralized authentication

---

# 🔑 Understanding SAML

## What is SAML?

SAML stands for:

```text
Security Assertion Markup Language
```

It is the most common enterprise SSO protocol.

---

## Why SAML Exists

Instead of every application maintaining passwords:

```text
Salesforce
Maintains Password

ServiceNow
Maintains Password
```

Applications trust Microsoft Entra.

---

## SAML Authentication Flow

```text
User
 │
 ▼
Salesforce
 │
 ▼
Redirect to Microsoft Entra
 │
 ▼
Authentication
 │
 ▼
SAML Token Issued
 │
 ▼
Salesforce
 │
 ▼
Access Granted
```

---

## What is a SAML Assertion?

A SAML Assertion is a security token.

Contains:

```text
Username
Email
Groups
Claims
Authentication Status
```

The application trusts the assertion.

---

## Real Example

John accesses Salesforce.

Salesforce asks:

```text
Did Microsoft authenticate John?
```

Microsoft responds:

```text
Yes
Here's the SAML Assertion
```

Access granted.

---

# 🔑 Understanding OAuth 2.0

## What is OAuth 2.0?

OAuth 2.0 is an authorization protocol.

Important:

```text
OAuth ≠ Authentication
```

OAuth provides:

```text
Authorization
```

---

## Why OAuth Exists

Example:

A Calendar App wants access to:

```text
Microsoft Graph
```

Instead of sharing your password:

```text
User Grants Permission
```

OAuth issues a token.

---

## OAuth Flow

```text
User
 │
 ▼
Application
 │
 ▼
Microsoft Entra
 │
 ▼
Access Token
 │
 ▼
Microsoft Graph
```

---

## OAuth Tokens

### Access Token

Used to access resources.

Example:

```text
Read User Profile
Read Mail
Read Calendar
```

---

# 🔑 Understanding OpenID Connect (OIDC)

## What is OIDC?

OpenID Connect adds authentication to OAuth.

Think:

```text
OAuth
+
Authentication
=
OIDC
```

---

## Why OIDC Exists

OAuth answers:

```text
What can user access?
```

OIDC answers:

```text
Who is the user?
```

---

## OIDC Flow

```text
User
 │
 ▼
Application
 │
 ▼
Microsoft Entra
 │
 ▼
ID Token
 │
 ▼
Application
```

---

## ID Token Contains

```text
Username
Name
Email
Tenant Information
```

---

## Modern Applications Use OIDC

Examples:

* React Applications
* Angular Applications
* Mobile Apps
* Cloud Applications

---

# 🔑 Understanding SCIM Provisioning

## What is SCIM?

SCIM stands for:

```text
System for Cross-domain Identity Management
```

---

## Purpose

Automatically create users in applications.

Without SCIM:

```text
Create User in Entra
Create User in Salesforce
Create User in Workday
```

Manual work.

---

With SCIM:

```text
Create User in Entra
      ↓
Automatically Created Everywhere
```

---

## Benefits

* Automated onboarding
* Automated offboarding
* Reduced administration
* Better governance

---

# ⚙️ Task 1 – Add Enterprise Application

Navigate:

```text
Microsoft Entra Admin Center
→ Enterprise Applications
→ New Application
```

Add:

```text
Salesforce
```

or

```text
ServiceNow
```

---

# Validation

Verify application appears in Enterprise Applications.

---

# ⚙️ Task 2 – Configure Single Sign-On

Navigate:

```text
Enterprise Applications
→ Salesforce
→ Single Sign-On
```

Select:

```text
SAML
```

---

# Why SAML?

Most enterprise SaaS applications support SAML.

---

# Validation

Verify SSO configuration page loads successfully.

---

# ⚙️ Task 3 – Configure SAML Settings

Configure:

```text
Identifier (Entity ID)

Reply URL (ACS URL)

Sign-On URL
```

Download:

```text
Federation Metadata XML
```

Upload to Salesforce.

---

# Validation

Verify SAML configuration completes.

---

# ⚙️ Task 4 – Assign Users

Navigate:

```text
Users and Groups
→ Add Assignment
```

Assign:

```text
John IT
Sarah IT
```

---

# Validation

Users can access application.

---

# ⚙️ Task 5 – Assign Dynamic Groups

Assign:

```text
DG_IT
```

instead of individual users.

---

# Why?

Group-based assignment simplifies administration.

---

# ⚙️ Task 6 – Configure Application Owner

Navigate:

```text
Enterprise Application
→ Owners
```

Assign:

```text
John IT
```

---

# Why?

Application owners manage application configuration.

---

# ⚙️ Task 7 – Test SSO

Access:

```text
My Apps Portal
```

Launch:

```text
Salesforce
```

Expected Result:

```text
No Password Prompt
```

User automatically signs in.

---

# ⚙️ Task 8 – Review Sign-In Logs

Navigate:

```text
Monitoring
→ Sign-In Logs
```

Review:

* User
* Application
* Authentication Method
* Conditional Access Result

---

# ⚙️ Task 9 – Configure SCIM Provisioning (Optional)

Navigate:

```text
Enterprise Application
→ Provisioning
```

Configure:

```text
Automatic Provisioning
```

---

# Validation

New users automatically created in application.

---



# ✅ Validation Results

| Validation Item              | Status |
| ---------------------------- | ------ |
| Enterprise Application Added | ✅      |
| SAML Configured              | ✅      |
| Users Assigned               | ✅      |
| Groups Assigned              | ✅      |
| Application Owner Assigned   | ✅      |
| SSO Tested                   | ✅      |
| Sign-In Logs Reviewed        | ✅      |
| Provisioning Configured      | ✅      |

---

# 🎓 SC-300 Skills Covered

### Implement Authentication and Access Management

* Enterprise Applications
* Single Sign-On
* SAML

### Implement Identity Security

* Centralized Authentication
* Application Governance

### Manage Applications

* User Assignments
* Group Assignments
* Application Ownership

### Monitor Identity Environment

* Sign-In Logs
* Application Activity

---

# 🚀 Key Learning Outcomes

Through this lab, I gained hands-on experience in:

* Integrating Enterprise Applications
* Implementing Single Sign-On
* Understanding SAML Authentication
* Understanding OAuth 2.0
* Understanding OpenID Connect
* Managing Application Access
* Monitoring Application Authentication

---

# 💼 Portfolio Project

**Project Name:** Enterprise Applications and Single Sign-On using Microsoft Entra ID

This project demonstrates implementation of enterprise-grade application authentication using Microsoft Entra ID, including SAML-based Single Sign-On, user and group assignments, application governance, and authentication monitoring.

---

# 👨‍💻 Author

**Your Name**

Microsoft SC-300 Identity and Access Administrator Journey

Microsoft Entra ID Enterprise Identity & Governance Lab Series
