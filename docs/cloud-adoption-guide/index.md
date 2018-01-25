---
layout: LandingPage
---

# Azure Cloud Adoption Guide

The cloud presents a fundamental shift in the way that enterprises procure and utilize technology resources. In the past, enterprises assumed ownership and responsibility of all levels of technology from infrastructure to software. Now, the cloud offers the potential to transform the way enterprises utilize technology by provisioning and consuming resources as needed.

While the cloud offers nearly unlimited flexibility in terms of design choices, enterprises seek proven and consistent methodology for the adoption of cloud technologies. And, each enterprise has different goals and timelines for cloud adoption, making a a one-size-fits-all approach to adoption nearly impossible.

## Cloud adoption is an iterative process

The process of adopting cloud technologies is not a linear process. Different teams within the organization will require different approaches to adopting the cloud based on their goals, and those goals may change over time. Therefore, the process of cloud adoption is in an iterative process in which the experience and learning gained by the teams taking part in the adoption process are used as feedback to improve the adoption process for other teams in the organization as they begin their adoption process.

For example, development teams may be tasked with modernizing an on-premises application by migration parts to the cloud in one project, and tasked with developing a cloud native application in the next project.

This guide approaches enterprise cloud adoption from the perspective of organizational readiness. The guide includes education, guidance, and engineering artifacts for an enterprise to achieve the following operational stages:

1. Adopting Azure: foundational learning about the cloud/Azure (minimum amount of knowledge to deploy ad-hoc to Azure)
2. Modernizing legacy on-premises applications: enumerate, stack rank, and select on-premises workloads for migration (lift and shift etc.)
3. Optimizing migrated applications for the cloud: understand cloud features that lead to efficient use of resources (autoscaling, instance reservation, etc.)
4. Innovating in the cloud: native cloud development; set up devops; have multiple environments (sandbox, dev, pre-prod, prod)
5. Enterprise operations in the cloud

<!--- TODO: add content to describe intended audience for this guide --->

<!-- Each of the stages includes 

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
6. people: these are the stakeholders in adopting the cloud; -->

## Next Steps

If you are new to Azure, begin with the [Adopting Azure](/adoption-stage) section to learn what your organization needs to know to successfully onboard and deploy your first resources to Azure.