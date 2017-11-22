---
title: Cloud adoption strategies overview
description: overview of the general strategies for enterprise cloud adoption
author: petertay
---

# Cloud adoption strategies

What are the major areas that require design decisions?

- governance: ensuring enterprises IP and costs are protected in the cloud just as they are on-prem
    - roles
    - security
    - monitoring
    - compliance
- employee skillsets: many roles on-prem are different in the cloud, planning is required to transition people's skillsets from on-prem to the cloud
- billing and chargeback: on-prem, procurement process ensured IT costs and plans met; in the cloud, provisioning is typically done by DevOps; different ways to organize enterprise cloud reporting structure to support billing and chargeback
- identity: typically have on identity management system on-prem, will have to integrate with multiple identity systems across multiple cloud providers
- architecture: there will be consistent network edge between on-prem and cloud (ER, site to site VPN, etc) but there are many different ways to implement cloud architecture depending on all the above factors
- operations and management: have to decide whether to have on-prem/cloud monitoring side-by-side, integrate on-prem monitoring with cloud monitoring (custom portals), etc.