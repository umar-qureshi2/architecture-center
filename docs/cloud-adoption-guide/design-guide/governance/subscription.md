---
title: Azure subscription design guide
description: Guidance for Azure subscription design as part of a cloud adoption strategy
author: abuck
---

# Azure subscription design guide

## Overview

An Azure subscription is an agreement with Microsoft that provides access to Microsoft's to Microsoft's Platform-as-a-Service (PaaS) and Infrastructure-as-a-Service (IaaS) offerings. 
- Organizations often have multiple subscriptions. 

## Licenses
   - Included for PaaS offerings
   - Additional licenses may be required for IaaS

## Subscriptions and tenants

  - One tenant per subscription
  - Most organization's subscriptions will use the organization's AAD tenant.
  - A few subscriptions may use a different tenant - e.g., development subscriptions.
      - May be federated  

  **References**:
  [TECHNET: Subscriptions, licenses, accounts, and tenants for Microsoft’s cloud offerings](https://technet.microsoft.com/en-us/library/mt765146.aspx)

## Managing Multiple Subscriptions

  - When to add subscriptions
      - varies by adoption strategy
  - Hard limits per subscription
  - Do you trust the subscription owner
  - Rigid financial controls (e.g., subsidiaries; transnational boundaries)
  - Prod vs. non-prod environments
  - Historical impact of ASM vs. ARM
      - Not predominantly a security boundary
      - Billing is typically managed through resource tags
      - Security is typically managed through RBAC and policy
  
## Azure Management Groups

  - Coming in 2018
  - Allows organizations to group subscriptions together to simplify management of multiple subscriptions with the similar policies and security requirements.
  - Organization can define custom management group hierarchy
  - Policy is inherited; specific policies can be overridden

  **References:**  
  [Azure Management Groups](/azure/billing/billing-enterprise-mgmt-group-overview)


## Enterprise Agreements
  
  - Enterprise Portal
  - Primarily for tracking costs?
  - Rigid hierarchy
  -   Enterprise -> Departments -> Accounts -> Subscriptions
  - Account Portal?
  - Constraints of EA & roles
    - Enterprise admin -> Department admin -> Account owner -> Service admin
  - Ramifications of multiple EAs?
  - Relationship to Management Groups
