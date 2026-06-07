# 🔐 SC300-Lab10-App-Registrations-Service-Principals

# Application Identity Management using Microsoft Entra ID

## Deep Dive into App Registrations, Enterprise Applications, Service Principals, OAuth 2.0, OpenID Connect, Microsoft Graph and Application Governance

---

# Executive Summary

Microsoft Entra ID manages two primary identity types:

1. Human Identities
2. Workload Identities

Human identities represent users, administrators, guests, and groups.

Workload identities represent:

* Applications
* Services
* Automation Accounts
* Azure Functions
* Logic Apps
* DevOps Pipelines
* Service Principals
* Managed Identities

This lab focuses on the lifecycle, authentication, authorization, governance, and monitoring of workload identities.

The objective is to understand how modern applications authenticate against Microsoft Entra ID, obtain tokens, access APIs, and interact with enterprise resources using industry-standard protocols such as OAuth 2.0, OpenID Connect, and SAML.

---

# Business Scenario

ABC Technologies has developed an internal application called Employee Portal.

The application provides:

* Employee profile lookup
* Organizational hierarchy information
* Group membership information
* Microsoft 365 integration
* Teams integration
* SharePoint integration

The organization requires:

* Centralized authentication
* Single Sign-On
* MFA enforcement
* Conditional Access enforcement
* API authorization
* Secure token issuance

Instead of implementing custom authentication, the application is integrated with Microsoft Entra ID.

---

# Enterprise Identity Architecture

```text
User
 │
 ▼
Employee Portal
 │
 ▼
Microsoft Entra ID
 │
 ├── Authentication
 ├── Conditional Access
 ├── Identity Protection
 ├── MFA
 └── Token Issuance
 │
 ▼
Microsoft Graph
 │
 ├── Users
 ├── Groups
 ├── Teams
 ├── Devices
 ├── Mailboxes
 └── SharePoint
 │
 ▼
Application Response
```

---

# Understanding Application Identity

Most administrators understand user identities.

Example:

```text
John Smith
Sarah Wilson
Mike Johnson
```

Each user possesses:

* Object ID
* User Principal Name
* Authentication Methods
* Group Membership
* Permissions

Applications require equivalent identity constructs.

Example:

```text
Employee Portal
Payroll Application
HR Management System
Automation Service
```

Applications require:

* Authentication
* Authorization
* Permissions
* Auditing
* Governance

Microsoft Entra implements this through Application Objects and Service Principals.

---

# Application Object (App Registration)

## Technical Definition

An Application Object is the global definition of an application within Microsoft Entra ID.

It represents the application's identity blueprint.

The Application Object contains metadata describing:

* Authentication requirements
* Redirect URIs
* API permissions
* Certificates
* Client secrets
* Token configuration
* Branding
* Exposed APIs

The Application Object does not perform authentication itself.

It defines how authentication should occur.

---

# Internal Architecture

When an application is registered, Microsoft Entra creates:

```text
Application Object
```

Stored in:

```text
App Registrations
```

The Application Object becomes the authoritative definition of the application.

---

# Application Object Attributes

## Application (Client) ID

Globally unique identifier assigned to the application.

Example:

```text
7f52d7cf-xxxx-xxxx-xxxx-xxxxxxxxxxxx
```

Purpose:

* OAuth client identification
* Token requests
* Application authentication

---

## Tenant ID

Identifies the Microsoft Entra tenant.

Example:

```text
ABC Technologies Tenant
```

Used during authentication and authorization processes.

---

## Object ID

Unique identifier of the Application Object itself.

Used internally by Microsoft Entra.

---

# What Can Be Managed in App Registration?

App Registration is primarily developer-focused.

Administrators and developers configure:

## Authentication

Configure:

* Web Applications
* Single Page Applications
* Mobile Applications
* Desktop Applications

Authentication Settings:

* Redirect URIs
* Logout URLs
* Front Channel Logout
* Implicit Grant Settings

---

## Credentials

Application credentials include:

### Client Secrets

Shared secret used for confidential client authentication.

### Certificates

X.509 certificates used instead of shared secrets.

Enterprise best practice favors certificates due to stronger security posture.

---

## Token Configuration

Administrators can customize token contents.

Examples:

* Email Claims
* Group Claims
* Role Claims
* Custom Claims

These claims are inserted into:

* ID Tokens
* Access Tokens

---

## API Permissions

Applications can request permissions to:

* Microsoft Graph
* SharePoint APIs
* Custom APIs

Permission types include:

### Delegated Permissions

User context required.

### Application Permissions

No user context required.

---

## Expose APIs

Applications may act as resource servers.

Developers can expose:

* OAuth Scopes
* Application Roles

Other applications can consume these APIs securely.

---

# Service Principal

## Technical Definition

A Service Principal is the security identity of an application inside a tenant.

Where the Application Object represents the blueprint, the Service Principal represents the operational identity.

---

# Relationship Between Application Object and Service Principal

```text
Application Object
(Global Definition)

        │

        ▼

Service Principal
(Tenant Instance)

        │

        ▼

Authentication

Authorization

Access Management

Monitoring
```

The Service Principal is what actually participates in authentication and authorization operations.

---

# Why Service Principals Exist

Microsoft Entra is multi-tenant.

A single SaaS application such as Salesforce may be used by thousands of organizations.

The Application Object exists once.

Each tenant receives its own Service Principal.

Example:

```text
Salesforce Application Object
```

Tenant A:

```text
Salesforce Service Principal
```

Tenant B:

```text
Salesforce Service Principal
```

Tenant C:

```text
Salesforce Service Principal
```

Each tenant independently controls:

* Access
* Permissions
* Conditional Access
* Assignments

---

# Enterprise Applications

Enterprise Applications is the administrative view of Service Principals.

Location:

```text
Microsoft Entra ID
→ Enterprise Applications
```

Everything visible here is based on Service Principals.

---

# What Can Be Managed in Enterprise Applications?

Unlike App Registration, Enterprise Applications focuses on governance and access management.

## User Assignment

Assign:

* Users
* Security Groups
* Dynamic Groups

Access can be controlled at application level.

---

## Single Sign-On

Configure:

* SAML
* OpenID Connect
* Password-Based SSO
* Linked Sign-On

---

## Conditional Access Integration

Applications can be protected using:

* MFA
* Authentication Strengths
* Device Compliance
* Risk-Based Policies

---

## Provisioning

SCIM provisioning can automatically:

* Create Users
* Update Users
* Disable Users

in target SaaS applications.

---

## Monitoring

Enterprise Applications provide:

* Sign-In Logs
* Audit Logs
* Provisioning Logs
* Consent Logs

---

## Governance

Administrators can manage:

* Application Owners
* User Consent
* Admin Consent
* Access Reviews

---

# Application Lifecycle Flow

```text
Developer Creates Application
        │
        ▼
App Registration
(Application Object)
        │
        ▼
Service Principal Created
        │
        ▼
Enterprise Application
        │
        ▼
User Assignment
        │
        ▼
Authentication
        │
        ▼
Token Issuance
        │
        ▼
API Access
```
