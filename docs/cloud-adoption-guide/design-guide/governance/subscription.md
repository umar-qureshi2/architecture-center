---
title: Azure subscription design guide
description: Guidance for Azure subscription design as part of a cloud adoption strategy
author: alexbuckgit
---

# Azure subscription design guide

## Overview

An Azure subscription is an agreement with Microsoft that provides access to Microsoft's Platform-as-a-Service (PaaS) and Infrastructure-as-a-Service (IaaS) offerings. Subscriptions grant users access to available Azure services and to the Azure management portal. Subscriptions are the first thing a user establishes when starting to use Azure. 

Subscriptions provide a logical boundary of administration, scale, and billing for users who are consuming Azure services. Subscriptions help you organize access to cloud service resources, and also help you control how resource usage is reported, billed, and paid for. A subscription is a top-level billing unit, and each subscription can have a different billing and payment setup, so you can have different subscriptions and different plans by department, project, regional office, and so on. Every Azure resource belongs to an Azure subscription.

## Administration and access control

Initially, Azure provided the Azure Service Model (ASM) for management of cloud resources (also known as the Classic model). In the Classic model, access controls for a subscription were minimal, and access to a subscription in the Classic model implied access to all the resources in the portal. This lack of fine-grained control led to the proliferation of subscriptions to provide a reasonable level of access control for an Azure enrollment.

In 2014, Azure introduced the Azure Resource Management (ARM) model. ARM provides Role-Based Access Control (RBAC), which enables fine-grained control for assigning administrative privileges to Azure resources. In this model, the subscription is no longer required to serve as the primary security boundary. As a result, the proliferation of subscriptions that was common in the Classic model is no longer necessary. In general, security considerations should be managed through RBAC and policy, and billing considerations should be managed via resource groups and tagging.

> NOTE: Because of its more robust security and billing capabilities, the ARM model should be used for all new Azure deployments. This guidance focuses solely on deploying and managing Azure resources via the ARM model.

For more information, see the following:
- [Introduction to Azure security](/azure/security/azure-security)
- [Manage administrator roles](/azure/billing/billing-add-change-azure-subscription-administrator)
- [Manage access to Azure resources with Azure Active Directory](/azure/active-directory/manage-access-to-azure-resources)
- [Understanding resource access in Azure](/azure/active-directory/active-directory-understanding-resource-access)
- [Get started with Role-Based Access Control in the Azure portal](/azure/active-directory/role-based-access-control-what-is)

## Scale and subscription limits

A subscriptions are a logical limit of scale by which resources can be allocated. These limits include quotas of various Azure resource types. Organizations often have multiple multiple Azure subscriptions in order to avoid these limits. Planning for scalability is an important part of your Azure subscription strategy.  

For more information, see [Azure subscription limits](/azure/azure-subscription-service-limits).

## Ownership and administration

The user who signs up for an Azure subscription is the Account Administrator (AA). The AA is authorized to access the Account Center and perform various management tasks, such as creating new subscriptions, canceling subscriptions, changing the billing for a subscription, and reassigning the Service Administrator. Conceptually, the AA is the billing owner of the subscription. In RBAC, the AA isn't assigned a role.

Each subscription also has a Service Administrator (SA) who can add, remove, and modify Azure resources in that subscription by using the Azure portal. The default Service Administrator of a new subscription is the Account Administrator, but the AA can change the SA in the Azure Account Center.

Each Azure subscription is associated with one (AAD) tenant. Users, groups, and applications from that directory are assigned to RBAC roles with permissions to manage resources in the Azure subscription. The scope of a role assignment can be a subscription, a resource group, or a single resource. A role assigned at a parent scope also grants access to the children contained within it.

For more information, see:
- [Manage administrator roles](/azure/billing/billing-add-change-azure-subscription-administrator)
- [Transfer ownership of an Azure subscription to another account](/azure/billing/billing-subscription-transfer)
- [Create an Azure Active Directory tenant](https://docs.microsoft.com/en-us/azure/active-directory/develop/active-directory-howto-tenant)

## Managing multiple subscriptions

Many organizations using Azure will have multiple subscriptions for a variety of reasons. While each additional Azure subscription does not incur a direct cost, it can increase the complexity of managing your Azure resources.

Many of your early decisions in architecting and planning your Azure environment and related subscriptions can affect future decisions and designs as your cloud environment grows. Get participation and input from several groups within your organization, including IT leadership and those responsible for networking, security, and identity within your organization.

Consider the following when planning your subscription model:
- Segregation of users for security or compliance reasons.
- Large-scale consumption or administrative isolation for a specific application.
- Different configurations of offers and plans for various user groups or organizations.
- Separate billing and usage monitoring for user groups or organizations.
- Co-administrators from business units, departments, or other organizations.

You should consider creating an additional subscription in the following cases:
- You anticipate that the resources in a subscription will reach the defined [Azure subscription limits](/azure/azure-subscription-service-limits).
- You may wish to deploy production environments in a different subscription than your dev/test environments, to lessen the possibilities that your production environments will reach the defined subscription limits.
- There are trust or authority issues with the owners of your organization's existing subscriptions.
- Rigid financial or geopolitical controls may require separate financial arrangements for different subscriptions. For example, a large organization might have multiple subsidiaries or need to handle the accounting and billing of subscriptions in multiple countries differently.

## Billing

Subscriptions determine how resource usage is reported and billed. Each subscription can be configured separately for billing and payment. Additionally, Azure Resource Manager provides the ability to assign resource tags to provide additional information for granular chargeback and showback scenarios; this can be done based on either a resource group or resource.

## Enterprises and governance

Organizations who have an Enterprise Agreement with Microsoft can manage multiple subscriptions through the Enterprise Portal. Azure enrollment hierarchies define how services are structured within an Enterprise Agreement. The Enterprise Portal allows customers to divide access to Azure resources associated with an Enterprise Agreement based on flexible hierarchies customizable to an organization's unique needs. The hierarchy pattern should match an organization's management and geographic structure so that the associated billing and resource access can be accurately tracked.

For more information, see:
- [Governance in Azure](/azure/security/governance-in-azure#subscription-controls)
- [Azure Enterprise Enrollment - prescriptive subscription governance](/azure/azure-resource-manager/resource-manager-subscription-governance)
- [Onboarding Guide to the Microsoft Azure Enterprise Portal](https://eaportalonboardingvideos.blob.core.windows.net/onboardingvideos/AzureDirectEACustomerOnboardingGuide_En.pdf)
- **ADD: Detailed EA guidance**
 
## Azure Management Groups

Azure Management Groups were introduced in 2018. Management groups allow all organizations with multiple subscriptions to group subscriptions together for simplified management of access, policy, costs, billing, and compliance across your subscriptions. Organizations can create a hierarchy of management groups that aligns to their preferred subscription management model.

For more information, see:
- [Azure Management Groups](/azure/billing/billing-enterprise-mgmt-group-overview)
- [Azure Policy](/azure/azure-policy/azure-policy-introduction)

## Offer types

An Azure offer is the type of Azure subscription you have. Each offer has different terms and some have special benefits. Azure provides a number of different offer types, such as Pay-As-You-Go, Enterprise Agreements, Visual Studio, and Dev/Test offers. You should evaluate the [available offers](https://azure.microsoft.com/en-us/support/legal/offer-details/) based on your organization's needs.

For more information, see:
- [Change your subscription to a different offer](/azure/billing/billing-how-to-switch-azure-offer)

## Subscriptions and tenants

As stated previously, each Azure subscription is associated with a single Azure Active Directory (AAD) tenant. Most of an organization's subscriptions will use the organization's primary AAD tenant. A few subscriptions may use a different tenant (e.g., development subscriptions with specific testing requirements). These tenants may be federated with the primary AAD tenant.  

For more information, see:
- [Subscriptions, licenses, accounts, and tenants for Microsoft’s cloud offerings](https://technet.microsoft.com/en-us/library/mt765146.aspx)

## TO BE ADDED:

- [Subscription level budgets via ARM APIs](https://azure.microsoft.com/en-us/blog/subscription-budgets-api-preview/)

- More detailed information on Azure Management Groups

- Opportunistic design guidelines
- Bottom-up design guidelines
- Top-down design guidelines

## Out of scope

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
