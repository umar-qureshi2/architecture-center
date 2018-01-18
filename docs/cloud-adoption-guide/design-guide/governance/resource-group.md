---
title: Azure resource group design guide
description: Guidance for Azure resource group design as part of a cloud adoption strategy
author: petertay
---

# Azure resource group design guide

In Azure, a [resource group](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-overview#resource-groups) is a logical container in which resources are grouped. Each resource deployed in Azure must be deployed into a resource group. Each resource can only be deployed into a single resource group. 

## Who



## Design considerations

- All resources in a resource group should share the same lifecycle. That is, your practice should be to deploy, update, and delete resources with the same lifecycle as a group. For example, a web application's compute and application resources are typically deployed as a single unit. However, a database shared with other web applications would most likely be managed in a different lifecycle, and should be in its own resource group.
- A resource group can contain resources that reside in different regions.
- All the resources in a resource group must exist in the  a subscription: a resource group cannot span subscriptions; once you assign a resource to a resource group, you can move it out, but it can't span multiple subscriptions.
- A resource can interact with resources in other resource groups. This interaction is common when the two resources are related but do not share the same lifecycle (for example, web apps connecting to a database).
- A resource group can be used to scope access control for administrative actions. You can apply RBAC permissions at the subscription level or at the resource group level. Anything assigned at the subscription level will be inherited at the resource group level.

## Best practices

- The resource group design should follow Agile IT workload designs which include:  Web tier, application tier, data tier, management tier.
- Assign permissions at the resource group level as opposed to assigning them at the subscription level.
- Use tagging within your resource groups to ensure categorization of resources for billing and security purposes.
- Use a  cohesive and consistent naming standard of your security groups across your subscriptions.
- When creating resource groups, ensure that specific tiers (web, app, data, management) of the workload are assigned to the same region. 