---
title: Explainer - Enterprise identity in Azure
description: Explains how user identity works in Azure
author: petertay
---

# Explainer: Enterprise identity in the cloud

One of the most fundamental concepts in computing is digital identity. Digital identity is used to control access to all types of resources - from computer systems and mobile devices to online services. 

Most modern enterprises control access to physical resources using digital identity. When an employee is hired, an administrator creates an account for the employee in an on-premises identity service - such as Active Directory. The employee uses this account and password to access many different physical resources - buildings, computers, networks. 

Things are slightly different in the Cloud: resources are "virtual" - virtual machines, virtual networks, and so on. However, these virtual resources can be integrated with the enterprise's on-premises identity services over a network gateway and employees can access them in a similar way.

Cloud computing also introduces another key difference: while procuring physical resources on-premises does not require a digital identity, procuring resources in the cloud does require a digital identity. This is because the procurement of physical resources on-premises is typically performed manually, while procurement of virtual resources is automated using a cloud management layer.

This difference brings with it another consideration - where the digital identity is stored. On-premises, digital identity is most likely stored in a database associated with the directory service, and that database exists on a physical machine owned by the enterprise. In the cloud, digital identity is stored and managed by the cloud provider, typically as a service. This is known as identity as a service (IDaaS). 

Each of the enterprise and the cloud provider maintain their own security boundary. That is, each digital identity is defined and trusted within the security boundary because each entity has enacted all the necessary security protocols to create that trust. This results in the first choice that enterprise adopting the cloud will have to make - either maintain two distinct digital identities in each trusted location, or extend the trusted security boudnary to encompass both locations.

## Identity in Azure

Azure's IDaaS offer is named Azure Active Directory (AAD). AAD is Azure's multi-tenant cloud based directory and identity management service. A tenant is simply a dedicated instance of Azure Active Directory (Azure AD) that an organization receives and owns when it signs up for a Microsoft cloud service such as Azure or Office 365.

