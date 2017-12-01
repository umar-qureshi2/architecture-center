---
title: Azure resource group design guide
description: Guidance for Azure resource group design as part of a cloud adoption strategy
author: petertay
---

# Azure resource group design guide

 https://docs.microsoft.com/en-us/azure/azure-resource-manager/resource-group-overview#resource-groups
- describe relationship between:
    - Enterprise agreement
    - Subscription
    - resource group
    - RBAC Roles for applications, resources, and people
    - similar to subscriptions, can apply consistent policy for all resources in a resource group
        - can implement different policies for different groups (ex. devs in germany only allowed to create resources in Black Forest)
        - when DevOps requests resources, they get a resource group with appropriate roles and policy, ensures only allowed resources are created in the resource group
    - can lock resources at the subscription or resource group level
        - prevents accidental deletion or modification of any resource 
    - can send notifications for many 

- resource groups provide functionality to manage multiple resources concurrently
    - can set RBAC policy by resource group instead of by individual resource
    - can delete all resources in a group by deleting the resource group

- resource groups used to group together resources; can be used to group by:
    - application/project for lifecycle management
        - for example, use resource group to contain resources for an n-tier app
        - group together resources used for PoC work and delete the group with a single operation
        - can be used to create environments such as PoC, non-prod dev, prod
        - can be used to segment enterprise's customer resources to provide a type of multitenacy
    - function for durable infrastructure such as shared security services
        - for example, group together VMs running AD or other management services
        - once configured, apply locks to prevent accidental modification or deletion
    - DevOps function
        - if using multiple environments (PoC, non-prod dev, prod), use infrastructure as code to create resources in a single resource group, then tear them down and stand them up in the new environment
        - for repeatable deployment in different environments

- Opportunistic design guidelines:
    - use resource groups primarliy to manage resource lifecycle
    - map resource groups to environments
        - per team?
        - if multiple teams are using the same resource group, use a naming convention or tagging to partition resources by team
        - might need to switch to managine environments by subsciption if limit of 800 resources per resource group reached
        - use ARM templates to manage resource deployment to tear down and stand up projects
    - use locks to prevent resource modification or deletion at the management plane level
    - path forward:
        - resources can be moved between resource groups and between subscriptions so it's possible to migrate projects to different environments in the future

- bottom-up design guidelines
    - should be using subscirptions to manage environments, so use resource groups to manage projects
    - map resource group to:
        - durable infrastructure (ie. IaaS ad services) and use policy/locking to prevent undesired modification or deletion
        - projects, use roles/policy/locking to manage access to the project's resources 