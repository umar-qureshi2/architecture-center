---
title: Innovation enablement cloud adoption pattern
description: Describes the adoption strategy that enables enterprises to take advantage of cloud services to add innovation to existing applications and services
author: petertay
---

# Bottom-up adoption pattern

What do we want to call this pattern?
- bottom-up pattern (developer driven)
- innovation enablement

# what are the characteristics of the "bottom up" cloud adoption pattern?

- individual dev teams want to use cloud features but enterprise not committed to full cloud migration at this point; not fully committed to migrating entire enterprise to cloud, but want to take advantage of cloud services to add innovation to existing applications and services
    - for example, stand up big data/ML service, integrate with existing on-prem or public-facing application or service
    - for example, collect IoT data from already deployed devices/sensors
- will want to have pathway from PoC -> dev -> dev non-prod (test) -> prod
- may or may not integrate solutions with applications and services in multiple clouds?
- governance
    - roles: okay with using built-in roles to manage resource access?  
        - or use ARM policy?
        - okay to create custom roles specific to cloud with no counterpart on-prem?
    - compliance: may work with customer data or MBI/HBI data, so compliance bar is higher?        
        - how is compliance audited? cloud-provided scanning and reporting tools are good enough, or, require custom scanning tools?
    - security: okay with securing on-prem and cloud edge with site-to-site VPN and NSGs, or require ER?
        - cloud presence large enough to require shared security services (hub)?
        - secrets stored in keyvault, password-protected source control, somewhere else?
        - access logging to central location? or?
    - monitoring: okay with just using the monitoring tools provided by cloud? (don't need to integrate on-prem or multi-cloud monitoring)
- employee skillsets
    - larger team with members from multiple groups across the enterprise
        - possibly mapped by department/application -> consumed cloud service?
    - need to plan for skills migration from on-prem to cloud in a staged fashion
    - team may manage more than one cloud environment, may want to "abstract" job functions for personel interoperability between clouds?
    - staged plan for cloud training or revamping of HR skillset 
- billing and chargeback
    - okay with using tagging and/or naming conventions for managing resource spend?
- architectures
    - need multiple dev environments (segmented by subscription?): PoC -> dev -> dev non-prod (test) -> prod
    - may want to migrate more on-prem to cloud, so may want to consider shared security stack now instead of later?
    - applications and services managed by resource group or subscription?
    - use common architectures such as n-tier, microservices, PaaS, etc.?
    - if using multiple dev environments, require a DevOps pipeline with deployment pointing to PoC or dev or dev non-prod or prod
- identity
    - will need to manage customer identity
    - will need to federate identity from on-prem to cloud
    - might be using SaaS such as Office 365, but don't need to integrate tenant
- operations
    - who performs data backup/restore for each cloud environment segment? 
    - support is handled on a case-by-case basis?
        - centralized support organization that interacts with cloud support?
    - who gets called if cloud alert happens?

# what are the considerations for using this adoption pattern?

Main consideration: decisions made early on in the strategy may have to be mitigated later during large scale adoption

- governance
    - roles: if starting with minimal set of roles, will have to transition those roles to finer granularity as adoption increases
    - compliance: depending on what's going in the cloud, 
