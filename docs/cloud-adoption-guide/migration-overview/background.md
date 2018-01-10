---
title: Migrating from on-premises to the cloud
description: Describes operational concerns related to integrating on-premises applications and services with the cloud or migrating on-premises applications and services to the cloud
author: petertay
---

# Migrating operations from on-premises to the cloud

- Adopting the cloud requires a large number of design decisions; these design decision fall into six buckets:
1. identity: services that Azure trusts to authenticate user identity when providing access to resources (Microsoft accounts & Azure AD accounts)
2. governance: features, tools, and process to control access to Azure resources, ensuring enterprise IP and costs are protected in the cloud just as they are on-prem, includes:
    - subscriptions:
    - resource groups: 
    - naming standards and tags:
    - policy: tools to describe the function of resources ("No VM can have a NIC with a public IP address")
    - role based access control: tools to manage authorized access to resources ("The foo role allows VMs to be created but not deleted")
3. security: tools, features, and practices to protect resources, data, network from unauthorized access
    - compliance: tools and processes to verify that policy is applied correctly
4. architecture: there will be consistent network edge between on-prem and cloud (ER, site to site VPN, etc) but there are many different ways to implement cloud architecture depending on all the above factors
5. operations and management: using logged metrics and alerts to determine resource health
have to decide whether to have on-prem/cloud monitoring side-by-side, integrate on-prem monitoring with cloud monitoring (custom portals), etc, includes billing and chargeback
6. people: many roles on-prem are different in the cloud, planning is required to transition people's skillsets from on-prem to the cloud