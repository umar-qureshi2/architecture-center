---
title: Explainer - How does Azure Resource Manager work?
description: Explanation of the internal functioning of Azure Resource Manager
author: petertay
---

<!-->
prerequisite: understanding of how resources are allocated in Azure (ARM has an API for provisioning resources )
<-->
# Explainer: How does Azure Resource Manager work?

In the [how does Azure work?](azure-explainer.md) explainer, you learned that the internal architecture of Azure includes a front end that hosts all of the distributed applications that manage Azure services.

The Azure front end includes a service called Azure Resource Manager. Azure Resource Manager is responsible for the lifecycle of resources hosted in Azure from creation to deletion. There are many ways to interact with Azure Resource Manager - using Powershell, a command line interface, SDKs - but each of these is simply a wrapper on top of a RESTful API hosted by Azure Resource Manager.

The RESTful API provided by Azure Resource Manager is a consistent interface over a set of resource providers. Resource providers are simply a service running in Azure that includes all the functionality necessary to provision, manage, and delete a resource in Azure.  

A customer can use any of these to request a resource in a region, and Azure Resource Manager is responsible for locating capacity in the specified region. The request is sent to the fabric controller in the rack, and the fabric controller allocates the resources. The fabric controller then sends the status of the request back Azure Resource Manager, which responds to the customers request with success or failure along with other useful information. The resource is then available for use.