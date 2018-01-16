---
title: Explainer - Enterprise identity in Azure
description: Explains how user identity works in Azure
author: petertay
---

# Explainer: Enterprise identity in the cloud

One of the most fundamental concepts in computing is digital identity. Digital identity is used to control access to all types of resources - from computer systems and mobile devices to online services. 

Most modern enterprises control access to physical resources using digital identity. When an employee is hired, an administrator creates an account for the employee in an on-premises identity service - such as Active Directory. The employee uses this account and password to access many different physical resources - buildings, computers, networks. This digital identity is typically used for everything from logging into their local desktop to accessing services on the corporate network.

Things are slightly different in the Cloud: resources are "virtual" - virtual machines, virtual networks, and so on. These resources behave much the same way as resources on-premises, but they exist exclusively in the cloud datacenter. These resources are deployed using a management layer implemented by the cloud provider. This management layer provides services for the management - including creation and deletion - of these resources. Access to the management layer itself is managed through a cloud identity service.  

This means that in the cloud there are two layers of digital identity. First, digital identity used to access the cloud management layer, and second, digital identity used to access virtual machines and other services in the cloud. And, if an enterprise does not extend their network security boundary to encompass their virtual networks in the cloud, the on-premises digital identity management system makes three seperate layers of digital identity.

Ideally, the best approach to managing digital identity uses the same digital identity management system for all three layers. This approach is accomplished by either synchronizing or federating the on-premises digital identity management system with the cloud digital identity service. 

## Identity in Azure

Azure's cloud identity service is named Azure Active Directory (AAD). AAD is Azure's multi-tenant cloud based directory and identity management service. AAD is Identity as a Service (IDaaS) and user accounts from on-premises Active Directory Domain Services (AD DS) can be synchronized or federated for use with Azure Resource Manager.

## Next steps

Read the [digital identity design guide]() to learn more about about the design decisions to consider when adopting Azure AD. 

