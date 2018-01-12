---
title: Explainer - Identity in Azure
description: Explains how user identity works in Azure
author: petertay
---

# Explainer: Identity in the cloud

One of the most fundamental concepts in computing is identity for access management. Identity is used to control access to all types of resources - from online services to hardware devices. Access to your mobile phone or tablet is controlled by registering your device with your mobile provider and specifying a password or personal identification number (PIN) that you use to unlock the device. Access to your email is controlled with a user name and a password.

Enterprises control access to physical resources using identity. When an employee is hired, an administrator creates an account for the employee. Employee accounts are stored in a directory service database, such as Active Directory. The employee uses their account and password to get access to many different resources - buildings, computers, networks. 

For enterprises whose business is providing online services to the public, customer user identity is typically stored in a separate database. When a customer accesses the enterprise's service, the enterprise takes the user's identity and password to authenticate that user and authorize access to the service.

Cloud computing is similar, however, there is an extra level of access control. In cloud computing, resources are not procured as they are in the on-premises environment. Rather, resources such as virtual networks and virtual machines are provisioned by a cloud management layer. The cloud computing provider maintains a database of customers and user accounts associated with those customers. When a user for a particular customer makes a request to provision a cloud resource, they provide their user name and password to the cloud management layer for authentication.

In Azure, there are two tiers of user identity - the first tier is the enterprise enrollment tier, where user identity is used to control access to an enterprise's Azure enrollment. Azure trusts Microsoft accounts and Azure Active Directory (AAD) accounts for this tier. The next tier is the 