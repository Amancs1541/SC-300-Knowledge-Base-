# SC300-Lab12-Entitlement-Management

## Identity Governance using Microsoft Entra ID – Catalogs, Access Packages, Approval Workflows, and Access Lifecycle Management

---

# Project Overview

This project demonstrates the implementation of Microsoft Entra ID Entitlement Management to automate access requests, approvals, assignments, reviews, and expirations.

The solution enables users, contractors, vendors, and guest users to request access to resources through self-service workflows while maintaining governance, compliance, and security controls.

Instead of manually assigning groups, applications, and SharePoint permissions, Entitlement Management automates the complete access lifecycle.

---

# Business Scenario

ABC Technologies collaborates with:

* Vendors
* Contractors
* Consultants
* Business Partners
* Temporary Employees

These users require access to:

* Microsoft Teams
* SharePoint Sites
* Enterprise Applications
* Employee Portal
* Security Groups

The organization wants to:

* Eliminate manual access requests
* Implement approval workflows
* Automate onboarding
* Automate offboarding
* Enforce access expiration
* Improve governance and compliance

Microsoft Entra Entitlement Management is used to achieve these goals.

---

# Solution Architecture

```text
User
 │
 ▼
Access Package Request
 │
 ▼
Approval Workflow
 │
 ▼
Access Package Assignment
 │
 ├── Security Group
 │
 ├── Enterprise Application
 │
 └── SharePoint Site
 │
 ▼
Access Granted
 │
 ▼
Access Review
 │
 ▼
Expiration
 │
 ▼
Automatic Removal
```

---

# Understanding Entitlement Management

## What is Entitlement Management?

Entitlement Management is an Identity Governance capability within Microsoft Entra ID that automates access lifecycle management.

It provides:

* Self-Service Access Requests
* Approval Workflows
* Automatic Resource Assignment
* Access Reviews
* Access Expiration
* Automated Access Removal

---

# Core Components

## Catalog

A Catalog is a logical container that stores resources.

Resources may include:

* Security Groups
* Microsoft 365 Groups
* Enterprise Applications
* SharePoint Sites

Example:

```text
External Collaboration Catalog
```

---

## Access Package

An Access Package is a collection of resources that can be requested as a single unit.

Example:

```text
Contractor Access Package
```

Contains:

```text
Contractor Security Group
Employee Portal
Contractor SharePoint Site
```

Users request one package and receive access to all configured resources.

---

## Assignment Policy

An Assignment Policy controls:

* Who can request access
* Approval requirements
* Access duration
* Renewal settings
* Review settings

---

## Resources

Resources are the actual objects being assigned.

Examples:

```text
Security Groups
Enterprise Applications
SharePoint Sites
```

---

# Lab Objectives

* Create Catalogs
* Add Resources
* Create Access Packages
* Configure Assignment Policies
* Configure Approval Workflows
* Configure Access Reviews
* Configure Expiration Policies
* Validate Access Assignment
* Validate Access Removal

---

# Task 1 – Create Catalog

Navigate:

```text
Identity Governance
→ Entitlement Management
→ Catalogs
→ New Catalog
```

Create:

```text
External Collaboration Catalog
```

Description:

```text
Resources for Contractors and Vendors
```

---

## Validation

Verify catalog appears under Catalogs.

---

# Task 2 – Add Resources to Catalog

Add:

```text
Contractor Security Group

Employee Portal Enterprise Application

Contractor SharePoint Site
```

to:

```text
External Collaboration Catalog
```

---

## Why?

Resources cannot be included in an Access Package until they exist inside a Catalog.

---

## Validation

Verify all resources appear inside the Catalog.

---

# Task 3 – Create Access Package

Navigate:

```text
Identity Governance
→ Entitlement Management
→ Access Packages
→ New Access Package
```

Create:

```text
Contractor Access Package
```

Description:

```text
Provides access to contractor resources.
```

---

## Validation

Verify package creation.

---

# Task 4 – Add Resource Roles

Add:

### Security Group

```text
Contractor Security Group
```

Role:

```text
Member
```

---

### Enterprise Application

```text
Employee Portal
```

Role:

```text
User
```

---

### SharePoint Site

```text
Contractor SharePoint
```

Role:

```text
Member
```

---

## Validation

Verify resources appear in Access Package.

---

# Task 5 – Create Assignment Policy

Configure:

```text
External Users
```

Allowed Requestors:

```text
All Connected Organizations
```

---

## Purpose

Allows guest users and external users to request access.

---

## Validation

Verify policy creation.

---

# Task 6 – Configure Approval Workflow

Approval Required:

```text
Yes
```

Approver:

```text
Manager
```

or

```text
Identity Governance Team
```

---

## Approval Flow

```text
User Request
     │
     ▼
Manager Approval
     │
     ▼
Access Granted
```

---

## Validation

Verify approval workflow configuration.

---

# Task 7 – Configure Access Duration

Configure:

```text
90 Days
```

Purpose:

```text
Prevent Permanent Access
```

---

## Validation

Verify expiration settings.

---

# Task 8 – Configure Access Reviews

Enable:

```text
Quarterly Access Reviews
```

Reviewer:

```text
Manager
```

---

## Why?

Ensures access remains necessary.

---

## Validation

Verify review schedule.

---

# Task 9 – Request Access Package

External User:

```text
vendor@external.com
```

Requests:

```text
Contractor Access Package
```

---

## Request Flow

```text
Vendor
  │
  ▼
Request Package
  │
  ▼
Approval
  │
  ▼
Assignment
```

---

## Validation

Verify request submitted.

---

# Task 10 – Approve Request

Approver reviews request.

Approve:

```text
Contractor Access Package
```

---

## Result

Microsoft Entra automatically:

* Adds User to Group
* Assigns Enterprise Application
* Grants SharePoint Access

---

## Validation

Verify assignments.

---

# Task 11 – Verify Resource Access

Check:

```text
Contractor Security Group
```

Verify:

```text
Vendor Added
```

---

Check:

```text
Employee Portal
```

Verify:

```text
Access Granted
```

---

Check:

```text
Contractor SharePoint Site
```

Verify:

```text
Access Granted
```

---

# Task 12 – Test Access Expiration

Simulate:

```text
90 Days Expired
```

Expected:

```text
Group Membership Removed
Application Access Removed
SharePoint Access Removed
```

---

## Validation

Verify automatic removal.

---

# Access Lifecycle

```text
Request
 │
 ▼
Approval
 │
 ▼
Assignment
 │
 ▼
Usage
 │
 ▼
Review
 │
 ▼
Expiration
 │
 ▼
Removal
```

---

# Real World Use Cases

## Vendor Access

```text
Vendor
 ↓
Request Package
 ↓
Approval
 ↓
Access Granted
 ↓
Access Removed Automatically
```

---

## Contractor Access

```text
Contractor
 ↓
Request Package
 ↓
Manager Approval
 ↓
90 Day Access
```

---

## Partner Collaboration

```text
Partner User
 ↓
Access Package
 ↓
Teams
 ↓
SharePoint
 ↓
Applications
```

---

# Validation Results

| Validation Item              | Status |
| ---------------------------- | ------ |
| Catalog Created              | ✅      |
| Resources Added              | ✅      |
| Access Package Created       | ✅      |
| Assignment Policy Configured | ✅      |
| Approval Workflow Created    | ✅      |
| Access Duration Configured   | ✅      |
| Access Reviews Enabled       | ✅      |
| Request Submitted            | ✅      |
| Access Assigned              | ✅      |
| Access Expiration Tested     | ✅      |


# SC-300 Skills Covered

## Identity Governance

* Entitlement Management
* Catalogs
* Access Packages
* Assignment Policies
* Access Reviews

## Access Management

* Approval Workflows
* Self-Service Access Requests
* Resource Assignment

## External Collaboration

* Guest Users
* Vendors
* Contractors
* Partners

## Lifecycle Management

* Access Expiration
* Automatic Access Removal

---

# Key Learning Outcomes

Through this project, I gained hands-on experience in:

* Building Catalogs
* Creating Access Packages
* Implementing Approval Workflows
* Configuring Access Reviews
* Managing Access Lifecycle
* Automating Resource Assignments
* Governing Guest and Contractor Access

---

# Portfolio Project

**Project Name:** Entitlement Management and Access Package Governance using Microsoft Entra ID

This project demonstrates how Microsoft Entra Identity Governance automates access requests, approvals, assignments, reviews, and expirations through Catalogs and Access Packages, reducing administrative overhead while improving security, compliance, and governance.

---

# Author

**Aman Varma**

Microsoft SC-300 Identity and Access Administrator Journey

Microsoft Entra ID Enterprise Identity & Governance Lab Series

---

# Next Lab

```text
SC300-Lab13-Access-Reviews
```

Topics:

* Group Access Reviews
* Application Access Reviews
* Guest User Reviews
* Automatic Review Decisions
* Governance Compliance
* Periodic Access Certification
