---
title: Background - cloud adoption decision domains
description: describes the decision domains for enterprise cloud adoption
author: petertay
---

# Background: Cloud adoption decision domains

This guide breaks enterprise cloud adoption into six decision domains:

1. identity: services that Azure trusts to authenticate user identity when providing access to resources (Microsoft accounts & Azure AD accounts)
    - federation/synchronization of existing on-prem domain
2. governance: features, tools, and process to control access to Azure resources, ensuring enterprise IP and costs are protected in the cloud just as they are on-prem, includes:
    - subscriptions:
    - resource groups: 
    - policy: tools to describe the function of resources ("No VM can have a NIC with a public IP address")
    - role based access control: tools to manage authorized access to resources ("The foo role allows VMs to be created but not deleted")
3. security: tools, features, and practices to protect resources, data, network from unauthorized access
    - compliance: tools and processes to verify that policy is applied correctly
4. architecture: there will be consistent network edge between on-prem and cloud (ER, site to site VPN, etc) but there are many different ways to implement cloud architecture depending on all the above factors
5. operations and management: using logged metrics and alerts to determine resource health
have to decide whether to have on-prem/cloud monitoring side-by-side, integrate on-prem monitoring with cloud monitoring (custom portals), etc, includes billing and chargeback: 
    - naming standards and tags
6. people: many roles on-prem are different in the cloud, planning is required to transition people's skillsets from on-prem to the cloud

# Next steps

Read the [enterprise identity explainer]() to learn how digital identity in the cloud. Then, read the 