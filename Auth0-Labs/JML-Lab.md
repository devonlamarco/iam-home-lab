# Joiner, Mover, Leaver (JML) Lifecycle Lab - Auth0

## Overview

This lab demonstrates a complete Joiner, Mover, Leaver (JML) lifecycle using Auth0.

The objective was to simulate how Identity and Access Management (IAM) teams provision, modify, and deprovision user access throughout an employee's lifecycle while enforcing Role-Based Access Control (RBAC) and least privilege principles.

---

## Objectives

- Create and manage user identities
- Implement Role-Based Access Control (RBAC)
- Assign permissions through roles
- Simulate employee role changes
- Deprovision user access
- Understand Joiner, Mover, Leaver processes

---

## Lab Environment

### Identity Platform

Auth0

### User

Sarah Johnson

### Roles

- Finance Analyst
- HR Specialist

### Permissions

#### Finance

- read:invoices
- approve:invoices

#### Human Resources

- read:employees
- update:employees

---

## Architecture

```text
API
 └─ Permissions
      └─ Roles
           └─ Users
```

Permissions were created as API scopes and assigned to roles.

Roles were then assigned to users to implement Role-Based Access Control (RBAC).

---

# Phase 1 - Joiner

A new employee was provisioned into the organization.

User:

```text
Sarah Johnson
```

The user was assigned the Finance Analyst role.

The Finance Analyst role contained permissions required to perform finance-related tasks.

### Validation

#### User Assigned Finance Analyst Role

<img width="1920" height="1032" alt="Screenshot 2026-06-16 191241" src="https://github.com/user-attachments/assets/4f504194-9667-433c-8e06-1d54b9b4bebb" />

#### Finance Analyst Permissions

<img width="1920" height="1032" alt="Screenshot 2026-06-16 191443" src="https://github.com/user-attachments/assets/e78f5cc1-319a-4c5b-96f4-aafc297d0718" />

---

# Phase 2 - Mover

The employee transferred from Finance to Human Resources.

To maintain least privilege:

- Finance access was removed
- HR access was assigned

The user was assigned the HR Specialist role.

### Validation

#### User Assigned HR Specialist Role

<img width="1920" height="1032" alt="Screenshot 2026-06-16 191323" src="https://github.com/user-attachments/assets/69996428-9163-4d76-87fb-47ed144a5b16" />

#### HR Specialist Permissions

<img width="1920" height="1032" alt="Screenshot 2026-06-16 191433" src="https://github.com/user-attachments/assets/e5b54438-eb71-40f5-bedd-2cb85c3b14c8" />

---

# Phase 3 - Leaver

The employee left the organization.

To prevent unauthorized access, the user account was blocked.

In Auth0, blocking a user prevents authentication while preserving account records for auditing purposes.

### Validation

#### User Blocked

<img width="1920" height="1032" alt="Screenshot 2026-06-16 191554" src="https://github.com/user-attachments/assets/f1596eaf-7aae-481e-ba7e-00b82edaab2a" />

---

## Validation Performed

Verified that:

- User was successfully assigned the Finance Analyst role
- Finance permissions were inherited through role assignment
- User access changed appropriately during department transfer
- Finance permissions were removed after reassignment
- HR permissions were successfully assigned
- User account was blocked during the leaver process
- Access lifecycle followed least privilege principles

---

## Key Concepts Demonstrated

### Joiner

Provisioning a new identity and assigning initial access.

### Mover

Adjusting access when responsibilities change.

### Leaver

Removing access when employment ends.

### Role-Based Access Control (RBAC)

Permissions are assigned to roles rather than directly to users.

### Least Privilege

Users receive only the access necessary to perform their job functions.

### Identity Lifecycle Management

Managing access throughout the lifecycle of an identity.

---

## Key Takeaways

This lab demonstrated a complete Joiner, Mover, Leaver lifecycle using Auth0.

By assigning roles, modifying access based on changing responsibilities, and deprovisioning the account at termination, the exercise simulated common IAM processes used by organizations to manage identity lifecycles securely and consistently.

The lab also reinforced the concepts of Role-Based Access Control (RBAC), least privilege, and access governance.
