---
title: Top-down cloud adoption pattern
description: Describes the adoption strategy that allows developers to experiment in the cloud with minimal governance
author: petertay
---

# Top down cloud adoption pattern

What do we want to call this?
    - top down (leadership driven)
    - capital expendure reduction strategy
    - enterprise cost strate

## what are the characteristics of the "top down" cloud adoption pattern?

- enterprise has decided not to invest in additional on-prem hardware and is committed to moving to cloud in short-medium term.

- governance
    - roles
        - extend existing on-prem roles to Azure  
        - use existing Azure roles and create custom roles based on need      
    - security
        - share on-prem trust with Azure
        - store MBI and HBI customer data in Azure 
        - require robust logging of all incoming and outgoing traffic
    - monitoring
        - integrate on-prem monitoring with cloud monitoring to provide all-up visibility
    - compliance
        - extend existing policy to Azure
        - create custom policy where specific to Azure
        - have unified on-prem/cloud auditing
- employee skillsets
    - will create extensive cloud training program for entire enterprise
- billing and chargeback
    - require robust EA/tenant/subscription/RG naming and tagging conventions to match enterprise departments
- identity
    - may or may not already have an Azure AD tenant because of O365, Dyn or Intune consumption
    - may manage customer accounts using multitenancy (i.e. may create a tenant for each of their own customers)
- architecture
    - will connect on-prem edge to Azure using ER (will share some address space)
    - will use shared security services, aka hub and spoke architecture
    - need to manage applications/services independently
    - will develop large scale migration plans
        - enumerate existing applications
        - identify candidates for retirement, re-hosting, replacement, rewriting
        - stack rack based on criteria
        - plan migration
        - execute migration
        - continue until all workloads migrated
- operations and management
    - will have distinct operations and management roles for security, networking, systems, and devops
    - will implement self-service functionality for provisioning, accounts, etc.