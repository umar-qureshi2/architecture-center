---
title: Migrating from on-premises to the cloud
description: Describes background concepts about integrating on-premises applications and services with the cloud or migrating on-premises applications and services to the cloud
author: petertay
---

# Migrating from on-premises to the cloud

- what are the similarities and differences between an on-prem environment and a cloud environment?
- what elements (i.e. networking, storage, servers, virtualization...applications, data) am I responsible for on-prem -> cloud -> SaaS?
- goverance
    - what is governance?
        - roles
        - compliance
        - security
        - monitoring
    - how are these elements currently governed on-prem?
        - networking: roles, compliance, security, monitoring
        - storage: roles, compliance, security, monitoring
        ...
        - application: roles, compliance, security, monitoring
        - data: roles, compliance, security, monitoring
    - how are these elements governed in the cloud?
        - networking: roles, compliance, security, monitoring
        ....
        - data: roles, compliance, security, monitoring
- how will my people and existing apps and services transition between these different goverance models during migration?
    - i.e. my people have to govern one way for on-prem and a different way for cloud, is there a way to handle that?
- how can I allow lower my compliance requirements to allow more developer experimentation freedom, but migrate the app to a higher compliance cloud environment for production?
    - multiple environments - PoC, non-prod dev, non-prod test, prod
- how can I effectively manage billing, limits, and chargeback in these multidimensional environments?