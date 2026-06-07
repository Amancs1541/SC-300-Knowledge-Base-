# SC300-Lab13-Access-Reviews

## Identity Governance, Access Certification, Compliance Validation, and Automated Access Remediation using Microsoft Entra ID

---

# Project Overview

This project demonstrates the implementation of Microsoft Entra Access Reviews to govern user access across groups, enterprise applications, guest accounts, and access packages.

Access Reviews are one of the most important Identity Governance capabilities within Microsoft Entra ID because they solve the problem of **privilege creep**.

Privilege creep occurs when users accumulate access over time but that access is never removed.

Examples:

* Employee changes department
* Employee changes role
* Contractor engagement ends
* Vendor project finishes
* Guest collaboration completes

However access remains assigned.

This creates:

* Security Risks
* Compliance Violations
* Excessive Permissions
* Insider Threat Exposure

Access Reviews introduce periodic certification to ensure access remains appropriate.

---

# Business Problem

Without Access Reviews:

```text
User Gets Access
      │
      ▼
Changes Department
      │
      ▼
Manager Leaves
      │
      ▼
Nobody Reviews Access
      │
      ▼
Access Remains Forever
```

Result:

```text
Unauthorized Access

Compliance Failures

Privilege Creep
```

---

# Business Scenario

ABC Technologies maintains:

```text
Finance Group

HR Group

Payroll Application

Employee Portal

Guest Users

Contractor Accounts
```

Management requires:

* Quarterly access validation
* Manager certification
* Contractor review every 90 days
* Guest review every 30 days
* Automatic removal of unnecessary access

---

# Understanding Access Reviews

## What is an Access Review?

Access Review is a governance process that asks:

```text
Should this user still have access?
```

The reviewer must decide:

```text
Approve
or
Deny
```

If denied:

```text
Access Removed
```

---

# Access Review Architecture

```text
User Access
      │
      ▼
Access Review Created
      │
      ▼
Reviewers Assigned
      │
      ▼
Approve / Deny
      │
      ▼
Results Applied
      │
      ▼
Access Retained
or
Access Removed
```

---

# Navigate to Access Reviews

```text
Microsoft Entra Admin Center
    │
    ▼
Identity Governance
    │
    ▼
Access Reviews
```

---

# Understanding Identity Governance Menu

Many SC-300 candidates know how to click buttons but not why the menu exists.

Identity Governance is Microsoft's framework for:

```text
Who Gets Access

Why They Get Access

How Long They Keep Access

When Access Is Removed
```

Main components:

```text
Entitlement Management

Access Reviews

Lifecycle Workflows

Privileged Identity Management
```

---

# Understanding Access Reviews Menu

Inside Access Reviews you can review:

```text
Groups

Applications

Access Packages
```

Each review creates a governance workflow.

---

# Task 1 – Create Finance Security Group

Create:

```text
Finance-Sensitive-Access
```

Purpose:

Represents a business-critical group containing sensitive financial data.

Add:

```text
John
Sarah
Mike
```

---

# Why This Group Exists

Real organizations often have:

```text
Payroll Team

Finance Team

Treasury Team
```

with elevated permissions.

These memberships require periodic certification.

---

# Task 2 – Create New Access Review

Navigate:

```text
Identity Governance
→ Access Reviews
→ New Access Review
```

---

# Understanding "What to Review"

Microsoft asks:

```text
What should be reviewed?
```

Options include:

### Teams + Groups

Reviews:

```text
Security Groups

Microsoft 365 Groups

Teams Membership
```

Use Case:

```text
Finance Group Review
```

---

### Applications

Reviews:

```text
Enterprise Applications
```

Use Case:

```text
Salesforce Access Review

ServiceNow Access Review
```

---

### Access Packages

Reviews assignments created through:

```text
Entitlement Management
```

Use Case:

```text
Contractor Access Package Review
```

---

# Select

```text
Teams + Groups
```

Choose:

```text
Finance-Sensitive-Access
```

---

# Task 3 – Configure Review Scope

Microsoft asks:

```text
Who should be reviewed?
```

---

# Understanding Review Scope

### All Users

Review every member.

Example:

```text
John
Sarah
Mike
```

Recommended for compliance reviews.

---

### Guest Users Only

Review only external identities.

Example:

```text
partner@vendor.com
```

Useful for B2B governance.

---

### Inactive Users

Review only users who have not recently used access.

Example:

```text
No Sign-In
for 60 Days
```

Useful for cleanup.

---

# Select

```text
All Users
```

---

# Task 4 – Configure Reviewers

Microsoft asks:

```text
Who should decide?
```

---

# Understanding Reviewer Options

### Group Owners

Best Practice.

Why?

Group owners understand business requirements.

Example:

```text
Finance Director
```

reviews:

```text
Finance Group Members
```

---

### Managers

Manager reviews direct reports.

Example:

```text
Sarah's Manager
```

reviews:

```text
Sarah's Access
```

---

### Selected Users

Dedicated governance team.

Example:

```text
Identity Governance Team
```

---

### Self Review

Users review themselves.

Generally not recommended for high-risk access.

---

# Select

```text
Group Owner
```

---

# Task 5 – Configure Recurrence

Microsoft asks:

```text
How often should review occur?
```

---

# Understanding Recurrence

### One Time

Single review.

Use:

```text
Audit Requirement
```

---

### Weekly

High-risk environments.

---

### Monthly

Guest accounts.

---

### Quarterly

Most common enterprise setting.

---

### Annually

Low-risk systems.

---

# Select

```text
Quarterly
```

Duration:

```text
30 Days
```

Meaning:

Reviewer has 30 days to complete review.

---

# Task 6 – Configure Review Decisions

Microsoft asks:

```text
What happens if reviewer ignores request?
```

---

# Understanding Decision Settings

### No Action

Access remains.

Not recommended.

---

### Approve Automatically

Keep access.

Rarely used.

---

### Remove Access

Recommended.

Known as:

```text
Fail Secure
```

Principle.

Meaning:

If nobody approves access,
access is removed.

---

# Select

```text
Remove Access
```

---

# Task 7 – Enable Auto Apply Results

Microsoft asks:

```text
Should review results be enforced automatically?
```

---

# Without Auto Apply

Reviewer says:

```text
Remove Mike
```

but nothing happens.

Administrator must manually remove access.

---

# With Auto Apply

Reviewer says:

```text
Remove Mike
```

Microsoft Entra automatically:

```text
Removes Group Membership
```

---

# Select

```text
Automatically Apply Results
```

---

# Task 8 – Perform Review

Reviewer receives notification.

Members:

```text
John
Sarah
Mike
```

---

Decisions:

```text
John → Approve

Sarah → Approve

Mike → Deny
```

---

# What Happens Internally?

Microsoft stores:

```text
Review Decision

Reviewer

Timestamp

Justification
```

inside governance logs.

---

# Task 9 – Complete Review

Review closes.

Results applied.

Expected:

```text
Mike Removed
from Finance Group
```

---

# Validation

Verify:

```text
Group Membership Updated
```

---

# Guest User Reviews

Navigate:

```text
Access Reviews
→ New Access Review
```

Select:

```text
Guest Users Only
```

---

# Why Guest Reviews Matter

Guests are highest-risk identities.

Common issue:

```text
Vendor Leaves Project

Access Never Removed
```

---

Review Frequency:

```text
30 Days
```

Reviewer:

```text
Sponsor
```

---

# Enterprise Application Reviews

Review:

```text
Employee Portal

Salesforce

ServiceNow
```

---

Reviewer:

```text
Application Owner
```

Purpose:

Validate application assignments.

---

# Real Enterprise Example

```text
Salesforce
│
├── John
├── Sarah
└── Mike
```

Application Owner decides:

```text
John → Keep

Sarah → Keep

Mike → Remove
```

After review:

```text
Mike
No Longer Has Salesforce Access
```

---

# Access Review Lifecycle

```text
Access Granted
      │
      ▼
Review Scheduled
      │
      ▼
Reviewer Decision
      │
      ▼
Results Applied
      │
      ▼
Access Retained
or
Access Removed
```

---

# Security Benefits

Access Reviews help prevent:

```text
Privilege Creep

Dormant Accounts

Excessive Permissions

Compliance Violations

Unauthorized Access
```

---

# Key Learning Outcomes

Through this project I gained hands-on experience in:

* Identity Governance
* Access Certification
* Group Reviews
* Application Reviews
* Guest User Reviews
* Review Automation
* Auto Remediation
* Compliance Controls
* Least Privilege Enforcement

---

# Interview Question

## What is the purpose of Access Reviews?

Access Reviews provide a governance mechanism to periodically certify whether users should continue to have access to groups, applications, guest resources, and access packages. They help organizations enforce least privilege, reduce privilege creep, maintain compliance, and automatically remove unnecessary access.
