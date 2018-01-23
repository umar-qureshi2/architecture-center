---
title: Azure subscriptions in the enterprise
description: Guidance for Azure subscription design in the enterprise, as part of a cloud adoption strategy
author: alexbuckgit
---

# Azure subscriptions in the enterprise

## Overview

Organizations that are beginning to adopt Azure can use a standard [pay-as-you-go](https://azure.microsoft.com/en-in/offers/ms-azr-0003p/) subscription offer with no upfront commitment. However, larger organizations require a more structured approach to governance, balancing security and compliance with the need for agility. These organizations can add (TBD: an Enterprise Enrollment / a Server and Cloud Enrollment) to a [Microsoft Enterprise Agreement](https://www.microsoft.com/en-us/Licensing/licensing-programs/enterprise.aspx). This enrollment provides centralized administration via an Enterprise Portal, in addition to providing the best pricing, cloud-optimized licensing options, and simplified license management for Microsoft server and cloud technologies.

Any Microsoft customer with a Microsoft Enterprise Agreement can [add Azure to their agreement](https://azure.microsoft.com/en-us/pricing/enterprise-agreement/) by making an upfront monetary commitment to Azure.  That commitment is met over the course of the year as Azure services are consumed. This guide focuses on Enterprise customers that have made an Azure commitment via a corporate procurement process.

## Azure Hierarchy

An organization can design its Azure hierarchy to reflect the organization's operating model with respect to account billing, resource access, and organizational structure. The following enrollment approach includes:

![Enterprise hierarchy overview][enterprise-hierarchy-overview]

	1. **Enterprise Agreement:** Assign administrative roles for an organization's enterprise enrollment.
	2. **Subscriptions:** Once the roles are defined,  design your subscription model.
	3. **Resource Groups:** Create resource groups to logically group related resources (for example, by function, geography, or workload).
	4. **Naming Standards and Tags:** Categorize Azure resources to assist in security auditing, chargeback, and showback.
	5. **Resource Policies & Locks:** Regulate the management of your organization's Azure resources.
    6. **Role-based access Control (RBAC):** Assign permissions to allow management of and access to Azure resources.

## Enterprise agreements

With a Microsoft Enterprise Agreement and an associated enrollment, an organization can define an organizational hierarchy that provides granular administration and governance of Azure resources, by defining a hierarchy of departments, accounts, and subscriptions. The design of this hierarchy has important implications for controlling access and tracking costs for Azure resources, as well as affecting billing and reporting. 

![Enterprise roles][enterprise-roles]

## Enterprise roles (TODO)

- Enterprise administrator
- Department administrator
- Account owner
- Service administrator

## Portals (TODO)

- Enterprise portal
- Account portal
 
## Onboarding (TODO)


## TBD: Open Questions

- Where are the original source diagrams / PPTs?
- Most EA Portal collateral refers to an "Enterprise Enrollment" rather than a "Server and Cloud Enrollment". Why is this?

## TBD: Related topics

- [Azure licensing](https://www.microsoft.com/en-us/Licensing/product-licensing/azure.aspx)
- [Microsoft Enterprise Agreements](https://www.microsoft.com/en-us/licensing/licensing-programs/enterprise.aspx)
- [VIDEO: Enterprise Agreement - Server and Cloud Enrollment](https://www.microsoft.com/en-us/videoplayer/embed/eed0fe74-a5a5-4617-8c2c-6bb78e966a52)
- [Subscription governance](https://docs.microsoft.com/en-us/azure/azure-resource-manager/resource-manager-subscription-governance)
- Azure Stack
- [Azure Government Onboarding Guides](https://blogs.msdn.microsoft.com/azuregov/2016/05/18/new-azure-government-onboarding-guides/)



<!-- links -->
[enterprise-hierarchy-overview]: ../../images/enterprise-hierarchy-overview.png
[enterprise-roles]: ../../images/enterprise-roles.png
