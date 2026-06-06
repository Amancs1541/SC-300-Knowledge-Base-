# SC300-Lab02-Group-Based-Access-Control

# Automated Access Management using Microsoft Entra Groups and Dynamic Membership

## Project Overview

This lab demonstrates how to implement Group-Based Access Control (GBAC) using Microsoft Entra ID. The solution automates user access management through Security Groups, Microsoft 365 Groups, Dynamic Membership Rules, and Group-Based Licensing.

The goal is to reduce manual administrative effort while ensuring users automatically receive the correct access, licenses, and permissions based on their department.

---

## Business Scenario

ABC Technologies is growing rapidly and managing user access manually has become inefficient.

As an Identity Administrator, I was tasked with implementing an automated access management solution that:

- Automatically assigns users to groups based on department
- Reduces manual administration
- Enables group-based licensing
- Supports application access management
- Aligns with Zero Trust principles

---

## Objectives

- Create Security Groups for departments
- Create Microsoft 365 Collaboration Groups
- Configure Dynamic User Groups
- Configure Dynamic Device Groups
- Implement Group-Based Licensing
- Assign Enterprise Application Access through groups
- Validate Dynamic Membership functionality
- Review Audit Logs for governance and monitoring

---

## Technologies Used

- Microsoft Entra ID
- Microsoft 365
- Dynamic Membership Rules
- Security Groups
- Microsoft 365 Groups
- Group-Based Licensing
- Enterprise Applications
- Audit Logs

---

## Lab Architecture

```text
ABC Technologies
│
├── IT Department
│   ├── John IT
│   └── Sarah IT
│
├── HR Department
│   ├── Mike HR
│   └── Emma HR
│
└── Finance Department
    ├── David Finance
    └── Lisa Finance

            ↓

Dynamic Groups

├── DG_IT
├── DG_HR
├── DG_FINANCE

            ↓

Access & Licensing

├── Microsoft 365 License
├── SharePoint Access
├── Teams Access
└── Enterprise Applications
```

---

## Security Groups Created

| Group Name | Type |
|------------|--------|
| SG_IT | Security Group |
| SG_HR | Security Group |
| SG_FINANCE | Security Group |

### Purpose

Department-based access control and permission assignment.

---

## Microsoft 365 Groups Created

| Group Name |
|------------|
| M365_IT |
| M365_HR |
| M365_FINANCE |

### Purpose

- Microsoft Teams Collaboration
- Outlook Shared Mailbox
- SharePoint Team Sites

---

## Dynamic User Groups

### IT Department

```text
(user.department -eq "IT")
```

### HR Department

```text
(user.department -eq "HR")
```

### Finance Department

```text
(user.department -eq "Finance")
```

### Outcome

Users are automatically added or removed from groups whenever their department attribute changes.

---

## Dynamic Device Group

### Rule

```text
(device.deviceOSType -contains "Windows")
```

### Outcome

All Windows devices are automatically added to the device group.

---

## Group-Based Licensing

### Assigned License

- Microsoft 365 E5
  OR
- Microsoft Entra ID P2

### Benefits

- Automatic license assignment
- Reduced administrative overhead
- Consistent license management

---

## Enterprise Application Assignment

Application access was assigned through department-based groups instead of individual user assignments.

### Benefits

- Simplified access management
- Easier onboarding and offboarding
- Improved security governance

---

## Validation Performed

### Dynamic Membership Validation

Tested automatic group membership updates by changing a user's department attribute.

Result:

- User removed from previous department group
- User added to new department group automatically

### License Validation

Verified users automatically received assigned licenses through group membership.

### Application Access Validation

Confirmed users inherited application access through group assignments.

---

## Audit and Monitoring

Reviewed Microsoft Entra Audit Logs to verify:

- Group creation events
- Membership changes
- Dynamic group processing
- License assignments
- Application assignments

---

## Screenshots

### Security Groups
![Security Groups](Screenshots/security-groups.png)

### Dynamic Groups
![Dynamic Groups](Screenshots/dynamic-groups.png)

### Dynamic Membership Validation
![Membership Validation](Screenshots/membership-validation.png)

### Group-Based Licensing
![Group Licensing](Screenshots/group-licensing.png)

### Application Assignment
![Application Assignment](Screenshots/application-assignment.png)

### Audit Logs
![Audit Logs](Screenshots/audit-logs.png)

---

## Key Skills Demonstrated

- Microsoft Entra ID Administration
- Group-Based Access Control (GBAC)
- Dynamic Membership Rules
- Group-Based Licensing
- Enterprise Access Management
- Identity Governance
- User Lifecycle Automation
- Zero Trust Access Principles

---

## Learning Outcomes

Through this lab, I gained hands-on experience with:

- Automating user access management
- Implementing Dynamic Groups
- Managing licenses at scale
- Applying role-based access control
- Improving operational efficiency through automation
- Monitoring identity-related activities

---

## SC-300 Skills Covered

✔ Manage Users and Groups

✔ Configure Dynamic Membership Rules

✔ Manage Group-Based Licensing

✔ Implement Identity Governance

✔ Manage Enterprise Application Access

✔ Monitor and Audit Identity Activities

---

## Portfolio Project

**Project Name:** Automated Access Management using Microsoft Entra Groups and Dynamic Membership

This project demonstrates practical implementation of Microsoft Entra ID identity administration capabilities and aligns with the Microsoft SC-300 Identity and Access Administrator certification objectives.

---

## Author

**Name:** Your Name

**Certification Path:** Microsoft SC-300 – Identity and Access Administrator

**Portfolio Series:** Microsoft Entra ID Enterprise Identity & Governance Labs