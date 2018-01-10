---
title: Opportunistic cloud adoption pattern
description: Describes the adoption strategy that allows developers to experiment in the cloud with minimal governance
author: petertay
---

# Opportunistic cloud adoption pattern

- what are the characteristics of the "opportunistic" cloud adoption pattern?
    - not fully committed to migrating entire enterprise to cloud
    - creating a standalone cloud environment with low goverance requirements for proof of concept work
    - may or may not want to promote workloads from PoC to a production environment once proven
    - may or may not be experimenting with multiple clouds
    - governance
        - roles: okay with using built-in roles to manage resource access?  
            - or use ARM policy?
            - okay to create custom roles specific to cloud with no counterpart on-prem?
        - compliance: not allowed to work with customer data or MBI/HBI data, so compliance bar is lower?        
            - how is compliance audited? cloud-provided scanning and reporting tools are good enough?
        - security: okay with securing on-prem and cloud edge with site-to-site VPN and NSGs?
            - secrets stored in keyvault, password-protected source control, somewhere else?
            - access logging to central location? or?
        - monitoring: okay with just using the monitoring tools provided by cloud? (don't need to integrate on-prem or multi-cloud monitoring)
    - employee skillsets
        - managed by a small on-prem team
        - no need to plan for large scale skills migration from on-prem to cloud
        - team may manage more than one cloud environment, but don't need to worry about "abstracting" job functions for personel interoperability
        - no plan for cloud training or revamping of HR skillset 
    - billing and chargeback
        - okay with using tagging and/or naming conventions for managing resource spend?
    - architectures
        - cloud environment is made up of single subscription-based self contained projects
            - segmented by subnet, VNet, resource group, subscription?
        - can use whatever architecture is best for the PoC, or, can be used for learning
        - does each dev org own their own cloud environment segment (subnet, VNet, etc)
        - may or may not have a DevOps pipeline from on-prem to cloud
        - manage cloud network segmentation using subnets? VNets?
    - identity
        - might be using SaaS such as Office 365, but don't need to integrate tenant
        - may need to federate identity from on-prem to cloud for experimentation
    - operations
        - who performs data backup/restore for each cloud environment segment? 
        - support is handled on a case-by-case basis?
            - individual team members contact cloud support directly?
            - dev org does their own support for their cloud environment segment? (cloud dev team does their own VM patching/hardening, investigates and fixes network issues, etc)?
        - who gets called if cloud alert happens?