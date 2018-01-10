---
title: Azure resource group design guide
description: Guidance for Azure resource group design as part of a cloud adoption strategy
author: petertay
---

# Azure resource group design guide

 https://docs.microsoft.com/en-us/azure/azure-resource-manager/resource-group-overview#resource-groups
- describe relationship between:
    - Tenant/Enterprise agreement
    - Subscription
    - resource group
    - RBAC Roles for applications, resources, and people
    - similar to subscriptions, can apply consistent policy for all resources in a resource group
        - can implement different policies for different groups (ex. devs in germany only allowed to create resources in Black Forest)
        - when DevOps requests resources, they get a resource group with appropriate roles and policy, ensures only allowed resources are created in the resource group
    - operations and management
        - send notifications for operations on resource groups, such as adding or deleting resources
- don't want to be able to let opeators create resoruces that can be orphaned (ie. stuff that is not connected to any other netowork ; is inacessable)
- resource groups provide functionality to manage multiple resources as a single unit
    - can set RBAC policy by resource group instead of by individual resource
    - can delete all resources in a group by deleting the resource group
    - can lock resources at the subscription or resource group level
        - prevents accidental deletion or modification of any resource 

- resource groups used to group together resources; can be used to group by:
    - application/project for lifecycle management
        - for example, use resource group to contain resources for an n-tier app
        - group together resources used for PoC work and delete the group with a single operation
        - can be used to create environments such as PoC, non-prod dev, prod
        - can be used to segment enterprise's customer resources to provide a type of multitenacy
    - function for durable infrastructure such as shared security services
        - for example, group together VMs running AD or other management services, or, VMs used as workstations accessed via RDP
        - once configured, apply locks to prevent accidental modification or deletion
    - DevOps function
        - if using multiple environments (PoC, non-prod dev, prod), use infrastructure as code to create resources in a single resource group, then tear them down and stand them up in the new environment
        - for repeatable deployment in different environments

- Resource group guidance relevant to all strategies:
    - governance
        - compliance:
            - resource groups do not provide any implicit compliance tools for things like ensuring that user data is encrypted, etc. See the security guidelines for specific Azure resources and services for more information on securing your assets in Azure.
    - billing and chargeback
        - it is currently not possible to manage billing and chargeback using resource groups. Resource groups are not surfaced in current billing reports.

- Opportunistic design guidelines:
    - architecture 
        - use resource groups primarily to manage resource lifecycle
        - since there's only one 'PoC' environment, map it to a single resource group
        - if multiple teams are using the same resource group, use a naming convention or tagging to partition resources by team/project
        - might need to switch to manage environments by subsciption if limit of 800 resources per resource group reached
        - DevOps:
            - use ARM templates to manage resource deployment to tear down and stand up projects
                - allows the process of deploying "project" infrastructure to be standardized
            - configure existing on-prem CI/CD pipelines to deploy to resource group
            - 
    - governance
        - roles:
            - utilize built-in roles as much as possible. Creating custom roles for specific tasks related to a project can lead to management overhead.
        - policy:
            - utilize built-in policy as much as possible. 
        - security:
            - Permissions set by role apply to all resources in the resource group. Because there will be a small number of resource groups and potentially multiple projects per resource group, those with the "owner" role will have permission to add, modify, or delete any resource in the resource group as well as add and remove user access to the resource group. Users with the "contributor" role will be able to add, modify, or delete any resource in the resource group. So if there are multiple projects per resource group, it's possible that users with the "contributor" role from one project can modify or delete resources that belong to a different project. 
    - people:
        - decide who in your current organization will be responsible for the "owner" role on the resource group. The "owner" should be someone in your organization that is familiar with the provisioning of hardware resources and networking resources. This role closely aligns with tradition IT manager roles, therefore someone from your existing IT organization may be suited for this role. However, because this is a small scale adoption, a senior developer may assume this role.
        - decide who in your current organization will be added to the "contributor" role. Developers, operations, build engineers will require "contributor" roles so they can provision infrastructure and platform resources, configure them, and deploy code artifacts.
        - decide who in your current organization will be responsible for security and compliance auditing. Again because this is a small scale adoption effort, a member of the development team with experience in security 
    - operations and management:
        - configure alerts to:
        - ?
    - path forward:
        - resources can be moved between resource groups and between subscriptions so it's possible to migrate projects to different environments in the future

- bottom-up design guidelines
    - architecture
        - due to the larger number of projects, you may decide to use resource groups to manage projects.
        - this will result in more management overhead because:
            - you will need either a manual or automated process to provision new resource groups for each project
            - you will need to set permissions (users/roles) on each resource group individually
        - it's better than a single resource group for all projects because less likely to run up against 800 resources per resource group limit
    - should be using subscriptions to manage environments, so use resource groups to manage projects
    - map resource group to:
        - durable infrastructure (ie. IaaS ad services) and use policy/locking to prevent undesired modification or deletion
        - projects, use roles/policy/locking to manage access to the project's resources 
    - audit ? at the resource group level
    - configure alerts to:
        - ?
    - relationship between CI/CD pipeline and resource groups:
        - ?

    - policy
        - if something related to config ruels, should have a policy for that
        - rules should be independent from who is accessing the resources
        - who can access
        - what is the shape
        - "only mike can create large vms" not a policy, it's access control
            - intersection between rbac, scope, policy allows us to do this
            - ideally should express the intent "make can create small vms but not others"
        - "everything in my company must not have public ip" that's a security policy on the resource itself
        - create a policy "only large vms 
- tag using cost center
    - when provision RG people have own tools to deploy RGs with tags etc.
    - 