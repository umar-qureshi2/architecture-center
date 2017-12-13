---
title: Azure subscription design guide
description: Guidance for Azure subscription design as part of a cloud adoption strategy
author: abuck
---

# Azure subscription design guide

## Overview

An Azure subscription is an agreement with Microsoft that provides access to Microsoft's Platform-as-a-Service (PaaS) and Infrastructure-as-a-Service (IaaS) offerings. 

Subscriptions help you organize access to cloud service resources. They also help you control how resource usage is reported, billed, and paid for. Each subscription can have a different billing and payment setup, so you can have different subscriptions and different plans by department, project, regional office, and so on. Every Azure resource belongs to an Azure subscription.

## Security and Role-Based Access Control (RBAC)

Initially, Azure provided the Azure Service Model (ASM) for management of cloud resources (also known as the Classic model). In the Classic model, access controls for a subscription were minimal, and access to a subscription in the Classic model implied access to all the resources in the portal. This lack of fine-grained control led to the proliferation of subscriptions to provide a level of reasonable access control for an Azure enrollment.

Azure introduced the the Azure Resource Management (ARM) model in 2014. ARM provides Role-Based Access Control (RBAC), which enables fine-grained access management for Azure resources. In this model, the subscription is no longer required to serve as the primary security boundary. As a result, the proliferation of subscriptions that was common in the Classic model is no longer necessary. In general, security considerations should be managed through RBAC and policy, and billing considerations should be managed via resource groups and tagging.

Because of its more robust security and billing capabilities, the ARM model is recommended for all new Azure deployments use the ARM model, while provides a more granular Role-Based Access Control (RBAC) model for assigning administrative privileges at the resource level. This guidance focuses on deploying Azure resources via the ARM model.

For more information, see the following:
- [Manage administrator roles](https://docs.microsoft.com/en-us/azure/billing/billing-add-change-azure-subscription-administrator)
- [Manage access to Azure resources with Azure Active Directory](https://docs.microsoft.com/en-us/azure/active-directory/manage-access-to-azure-resources)
- [Understanding resource access in Azure](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-understanding-resource-access)
- [Get started with Role-Based Access Control in the Azure portal](https://docs.microsoft.com/en-us/azure/active-directory/role-based-access-control-what-is)

## Ownership and administration

The owner of an Azure account is the Account Administrator (AA). Each subscription has a Service Administrator (SA) who can add, remove, and modify Azure resources in that subscription by using the Azure portal. The default Service Administrator of a new subscription is the Account Administrator, but the AA can change the SA in the Azure Accounts Center.

The Account Administrator is the person who signed up for or purchased an Azure subscription, and is authorized to create subscriptions, cancel subscriptions, change the billing for a subscription, and assign the Service Administrator role.

Each Azure subscription is associated with one (AAD) tenant. Users, groups, and applications from that directory are assigned to RBAC roles with permissions to manage resources in the Azure subscription. The scope of a role assignment can be a subscription, a resource group, or a single resource. A role assigned at a parent scope also grants access to the children contained within it.

For more information, see:
- [Transfer ownership of an Azure subscription to another account](https://docs.microsoft.com/en-us/azure/billing/billing-subscription-transfer)

## Managing Multiple Subscriptions

Most organizations using Azure will have multiple subscriptions for a variety of reasons. While each additional Azure subscription does not incur a direct cost, it can increase the complexity of managing your Azure resources. You should consider creating an additional subscription in the following cases:
- You anticipate that the resources in a subscription will reach the defined [Azure subscription limits](https://docs.microsoft.com/en-us/azure/azure-subscription-service-limits).
- You may wish to deploy production environments in a different subscription than your dev/test environments, to lessen the possibilities that your production environments will reach the defined subscription limits.
- There are trust or authority issues with the owners of your organization's existing subscriptions.
- Rigid financial or geopolitical controls may require separate financial arrangements for different subscriptions. For example, a large organization might have multiple subsidiaries or need to handle the accounting and billing of subscriptions in multiple countries differently.

## Subscription controls and governance

Subscriptions determine how resource usage is reported and billed. Each subscription can be configured separately for  billing and payment. 

Organizations who have an Enterprise Agreement with Microsoft can manage multiple subscriptions through the Enterprise Portal. Azure enrollment hierarchies define how services are structured within an Enterprise Agreement. The Enterprise Portal allows customers to divide access to Azure resources associated with an Enterprise Agreement based on flexible hierarchies customizable to an organization's unique needs. The hierarchy pattern should match an organization's management and geographic structure so that the associated billing and resource access can be accurately tracked.

For more information, see:
- [Governance in Azure](https://docs.microsoft.com/en-us/azure/security/governance-in-azure#subscription-controls).
- [Azure Enterprise Enrollment - prescriptive subscription governance](https://docs.microsoft.com/en-us/azure/azure-resource-manager/resource-manager-subscription-governance)

## Azure Management Groups

Azure Management Groups were introduced in 2018. Management groups allow all organizations with multiple descriptions to group subscriptions together to simplify management of access, policy, costs, billing, and compliance across your subscriptions. Organizations can create a hierarchy of management groups that aligns to their preferred subscription management model.

For more information, see:
- [Azure Management Groups](https://docs.microsoft.com/en-us/azure/billing/billing-enterprise-mgmt-group-overview)
- [Azure Policy](https://docs.microsoft.com/en-us/azure/azure-policy/azure-policy-introduction)

## Offer types

An Azure offer is the type of Azure subscription you have. Each offer has different terms and some have special benefits. Azure provides a number of different offer types, such as Pay-As-You-Go, Enterprise Agreements, Visual Studio, and Dev/Test offers. You should evaluate the [available offers](https://azure.microsoft.com/en-us/support/legal/offer-details/) based on your organization's needs.

For more information, see:
- [Change your subscription to a different offer]O(https://docs.microsoft.com/en-us/azure/billing/billing-how-to-switch-azure-offer)

## Subscriptions and tenants

Each Azure subscription is associated with one Azure Active Directory (AAD) tenant. Most of an organization's subscriptions will use the organization's primary AAD tenant. A few subscriptions may use a different tenant (e.g., development subscriptions with specific testing requirements). These tenants may be federated to the primary AAD tenant.  

For more information, see:
- [Subscriptions, licenses, accounts, and tenants for Microsoft’s cloud offerings](https://technet.microsoft.com/en-us/library/mt765146.aspx)

## TO BE ADDED:
- Opportunistic design guidelines
- Bottom-up design guidelines
- Top-down design guidelines

## Out-of-scope

- Azure Service Manager / "Classic" deployment model
- Privileged Access Management / "Tier 0" model

## Related topics

- Subscription model for Cloud Solution Providers
- Licenses
- Cost, billing, invoicing, and resource tagging
- Policy
- Identity/AAD
- Other subscriptions and tenants (O365, Dynamics, InTune) 
- Naming conventions
