# 🔐 SC300-Lab10-Employee-Portal-RBAC-EntraID

## Authentication and Authorization using Microsoft Entra ID, OpenID Connect, OAuth 2.0, App Roles, and Microsoft Graph

---

# Project Overview

This project demonstrates how to build a modern enterprise web application that uses Microsoft Entra ID for authentication and authorization.

The application implements:

* OpenID Connect (OIDC) Authentication
* OAuth 2.0 Authorization
* Microsoft Entra ID Integration
* App Registration
* Enterprise Application
* Service Principal
* Application Roles (RBAC)
* Microsoft Graph Integration
* ID Token and Access Token Inspection
* Role-Based UI Authorization

Instead of maintaining local usernames and passwords, the application relies entirely on Microsoft Entra ID as the Identity Provider (IdP).

---

# Business Scenario

ABC Technologies wants to build an internal Employee Portal.

Requirements:

### Authentication

All users must sign in using their Microsoft Entra ID account.

No local authentication should exist.

---

### Authorization

The application supports three business roles:

| Role     | Access                                |
| -------- | ------------------------------------- |
| Employee | View Profile                          |
| HR       | View Profile + Enter Employee Records |
| Admin    | View Profile + Manage Users           |

The portal must dynamically display UI elements based on the authenticated user's role.

---

# Solution Architecture

```text
User
 │
 ▼
Employee Portal
(ASP.NET Core)
 │
 ▼
Microsoft Entra ID
 │
 ├── OpenID Connect
 ├── OAuth 2.0
 ├── MFA
 ├── Conditional Access
 └── Token Issuance
 │
 ▼
ID Token
Access Token
Role Claims
 │
 ▼
Authorization Engine
 │
 ▼
Microsoft Graph API
 │
 ▼
User Information
```

---

# Identity Architecture

Microsoft Entra creates two directory objects:

```text
Application Object
        +
Service Principal
```

---

## Application Object

Stored under:

```text
App Registrations
```

Responsible for:

* Authentication Configuration
* Redirect URIs
* API Permissions
* OAuth Configuration
* OIDC Configuration
* Certificates
* Client Secrets
* Token Configuration

---

## Service Principal

Stored under:

```text
Enterprise Applications
```

Responsible for:

* User Assignment
* Group Assignment
* Conditional Access
* SSO Configuration
* Access Governance
* Monitoring
* Provisioning

---

# Application Roles

The application uses App Roles for authorization.

Three roles are configured:

## Employee

```text
Employee
```

Can:

* View Profile
* View Claims
* View Tokens
* Logout

---

## HR

```text
HR
```

Can:

* View Profile
* View Claims
* View Tokens
* Enter Employee Records
* Logout

---

## Admin

```text
Admin
```

Can:

* View Profile
* View Claims
* View Tokens
* Manage Users
* Logout

---

# Authentication Flow

The application uses OpenID Connect.

Authentication answers:

```text
Who is the user?
```

---

## Login Flow

```text
User
 │
 ▼
Employee Portal
 │
 ▼
Microsoft Entra ID
 │
 ▼
User Authentication
 │
 ▼
ID Token Issued
 │
 ▼
User Logged In
```

---

# OpenID Connect (OIDC)

OpenID Connect is an identity layer built on top of OAuth 2.0.

OIDC provides:

* Authentication
* Identity Claims
* User Information

OIDC returns an ID Token.

Example:

```json
{
  "name": "John Doe",
  "email": "john@contoso.com",
  "oid": "xxxxxxxx",
  "tid": "xxxxxxxx"
}
```

The application uses the ID Token to identify the user.

---

# Authorization Flow

Authorization answers:

```text
What is the user allowed to do?
```

The application uses OAuth 2.0 and App Roles.

---

## Authorization Process

```text
User Authenticated
 │
 ▼
Role Claim Retrieved
 │
 ▼
Application Evaluates Role
 │
 ▼
Display Authorized Features
```

---

# OAuth 2.0

OAuth 2.0 is an authorization framework.

OAuth issues:

```text
Access Token
```

Used for:

```text
Microsoft Graph
Protected APIs
Custom APIs
```

---

# Access Token Example

```json
{
  "aud": "Microsoft Graph",
  "scp": "User.Read",
  "roles": [
    "Admin"
  ]
}
```

The Access Token determines what resources the application can access.

---

# Application Roles

Application Roles are configured inside the App Registration.

Role Definitions:

```text
Employee
HR
Admin
```

When users authenticate, Microsoft Entra adds role claims into the token.

Example:

```json
{
  "roles": [
    "HR"
  ]
}
```

The application reads these claims and applies authorization rules.

---

# Role-Based Authorization Logic

Employee:

```text
Profile Page
Claims Viewer
Token Viewer
Logout
```

---

HR:

```text
Profile Page
Claims Viewer
Token Viewer
Enter Employee Records
Logout
```

---

Admin:

```text
Profile Page
Claims Viewer
Token Viewer
Manage Users
Logout
```

---

# Authorization Implementation

Example:

```csharp
[Authorize(Roles = "Admin")]
public IActionResult ManageUsers()
{
    return View();
}
```

---

HR Example:

```csharp
[Authorize(Roles = "HR")]
public IActionResult EmployeeEntry()
{
    return View();
}
```

---

Authenticated User Example:

```csharp
[Authorize]
public IActionResult Profile()
{
    return View();
}
```

---

# Microsoft Entra Configuration

## Step 1 - Create App Registration

Create:

```text
Employee Portal
```

Configure:

```text
Single Tenant
```

---

## Step 2 - Configure Redirect URI

```text
https://localhost:5001/signin-oidc
```

Purpose:

Microsoft Entra redirects authenticated users back to this location.

---

## Step 3 - Configure App Roles

Create:

```text
Employee
HR
Admin
```

These roles will be assigned through the Enterprise Application.

---

## Step 4 - Configure API Permissions

Microsoft Graph Permissions:

```text
User.Read
```

Purpose:

Read profile information of the signed-in user.

---

## Step 5 - Grant Admin Consent

Grant consent for Graph permissions.

---

## Step 6 - Create Client Secret

Generate:

```text
Client Secret
```

Used by the application to authenticate with Microsoft Entra.

---

# Enterprise Application Configuration

Navigate:

```text
Enterprise Applications
→ Employee Portal
```

---

## Assign Users

Assign users to roles.

Example:

```text
John Employee
→ Employee
```

```text
Sarah HR
→ HR
```

```text
Mike Admin
→ Admin
```

---

# User Experience

## Login Screen

```text
Sign In With Microsoft
```

---

## Employee Dashboard

Displays:

```text
Name
Email
Object ID
Tenant ID
Role
Claims
ID Token
Access Token

Logout
```

---

## HR Dashboard

Displays:

```text
Name
Email
Claims
Tokens

Enter Employee
Logout
```

---

## Admin Dashboard

Displays:

```text
Name
Email
Claims
Tokens

Manage Users
Logout
```

---

# Microsoft Graph Integration

The application calls:

```http
GET https://graph.microsoft.com/v1.0/me
```

Returns:

```json
{
  "displayName": "John Doe",
  "mail": "john@contoso.com"
}
```

Displayed on the profile page.

---

# Token Inspection Page

The application displays:

## ID Token

Contains:

```text
Name
Email
Object ID
Tenant ID
Authentication Details
```

---

## Access Token

Contains:

```text
Audience
Scopes
Roles
Expiration
Issuer
```

---

## Claims Viewer

Displays:

```text
name
email
preferred_username
oid
tid
roles
groups
aud
iss
exp
```

Useful for learning token-based authentication.

---

# Security Controls

The application supports:

* Microsoft Entra Authentication
* MFA
* Conditional Access
* Role-Based Access Control
* Token-Based Authorization

All authentication is performed by Microsoft Entra ID.

No passwords are stored inside the application.

---

# Validation Checklist

| Validation Item                | Status |
| ------------------------------ | ------ |
| App Registration Created       | ✅      |
| Enterprise Application Created | ✅      |
| Redirect URI Configured        | ✅      |
| Client Secret Created          | ✅      |
| App Roles Created              | ✅      |
| User Assignments Completed     | ✅      |
| OIDC Authentication Working    | ✅      |
| OAuth Authorization Working    | ✅      |
| Microsoft Graph Integrated     | ✅      |
| Role-Based UI Working          | ✅      |
| Claims Viewer Working          | ✅      |
| Token Viewer Working           | ✅      |

---

# Screenshots

```text
Screenshots/
│
├── Login-Page.png
├── App-Registration.png
├── App-Roles.png
├── Enterprise-Application.png
├── User-Assignments.png
├── Employee-Dashboard.png
├── HR-Dashboard.png
├── Admin-Dashboard.png
├── Claims-Viewer.png
├── Token-Viewer.png
├── Graph-Profile.png
└── SignIn-Logs.png
```

---

# Skills Demonstrated

* Microsoft Entra ID
* OpenID Connect
* OAuth 2.0
* Application Registration
* Enterprise Applications
* Service Principals
* Application Roles
* RBAC
* Microsoft Graph
* Claims-Based Authorization
* Token-Based Authentication
* Identity Governance

---

# Key Learning Outcomes

Through this project I gained hands-on experience in:

* Configuring App Registrations
* Managing Enterprise Applications
* Understanding Service Principals
* Implementing OpenID Connect Authentication
* Implementing OAuth 2.0 Authorization
* Creating Application Roles
* Assigning Users to Roles
* Consuming Microsoft Graph APIs
* Inspecting ID Tokens and Access Tokens
* Implementing Role-Based Access Control

---

# Portfolio Summary

This project demonstrates a complete enterprise authentication and authorization solution using Microsoft Entra ID. The implementation integrates OpenID Connect, OAuth 2.0, Microsoft Graph, Application Roles, and Role-Based Access Control to secure a custom web application while eliminating local credential management.
