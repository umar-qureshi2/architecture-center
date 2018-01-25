---
title: Explainer - Enterprise identity in Azure
description: Explains how user identity works in Azure
author: petertay
---
<!-->
prerequisites: understand how Azure internals work, should understand how resources are allocated before understanding how resource allocation is restricted
goal: provide enough background to assist reader in understanding RBAC and policy
<-->

# Explainer: Access control management for resources in Azure

In the [how does Azure work? explainer](azure-explainer.md), you learned that Azure is a collection of servers and networking hardware running virtualized hardware and software on behalf of  users. You also learned that some of these servers run a distributed orchestration application to manage the creation, modification, and deletion of Azure resources.

Azure doesn't allow just anyone to request a resource be created, modified, or deleted - it requires that users authenticate their digital identity and then determines if it is allowed to perform the request on the authenticated user's behalf. 

Azure includes a service that authenticates digital identity named **Azure Active Directory** (Azure AD). Azure AD offers identity as a service (IDaaS) with users ssgmented into **tenants**. A tenant is simply a secure, dedicated instance of Azure AD. 

In order to create a tenant, Azure requires a **privileged account**. This privieged account is associated with either an Azure account or an enterprise agreement. Both of these are billing constructs and are not stored in Azure AD. That is, one or more pivileged accounts own the Azure AD tenant.

Once the tenant has been created, a **tenant identifier** is created in Azure AD. A priviliged account can then create and add users to the new Azure AD tenant. 

THese users can then send requests to Azure to create, modify, or delete resources, and Azure uses Azure AD to authenticate the user. If the request was to create a resource, Azure creates the resource and saves a unique identifier associated with the user along with the tenant ID in an internal database. This is how Azure knows which tenant owns which resource and which user requested 

Most enterprises already have at least one identity management service - typicaly Active Directory Domain Services (AD DS). Azure AD is capable of synchronizing or federating user identity from AD DS, so enterprises do not need to manage identity seperately in the two environments.

## Next steps

Learn more about privileged accounts in Azure and the best practices for managing them. 

