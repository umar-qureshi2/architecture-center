---
layout: LandingPage
---

# Azure Cloud Adoption Guide

The cloud presents a fundamental shift in the way that enterprises procure and utilize technology resources. In the past, enterprises assumed ownership and responsibility of all levels of technology from infrastructure to software. Now, the cloud offers the potential to transform the way enterprises utilize technology by provisioning and consuming resources as needed.

While the cloud offers nearly unlimited flexibility in terms of design choices, enterprises seek proven and consistent methodology for the adoption of cloud technologies. And, each enterprise has different goals and timelines for cloud adoption, making a a one-size-fits-all approach to adoption nearly impossible.

This guide approaches enterprise cloud adoption from the perspective of in order to adopt the cloud and achieve the organization's goals in the cloud, a 

Stages of cloud adoption: 
1) Adopt
    - org maturity: Foundational learning about the cloud/Azure (minimum amount of knowledge to deploy ad-hoc to Azure)
2) Modernize
    - org maturity: enumerate, stack rank, and select on-premises workloads for migration (lift and shit etc.)
3) Optimize
    - org maturity: understand cloud features that lead to efficient use of resources (autoscaling, instance reservation, etc.)
4) Innovate
    - org maturity: native cloud development; set up devops; have multiple environments (sandbox, dev, pre-prod, prod)
5) Operate
6) Secure
7) Govern
<!--- TODO: add content to describe intended audience for this guide --->

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
6. people: these are the stakeholders in adopting the cloud; 

## Next Steps

Learn more about the [cloud adoption decision domains](/adoption-overview/overview.md) - identity, governance, security, architecture, operations and management, and people.