

## Topics not yet covered (TODO: Review)

- Subscription model for Cloud Solution Providers
- Licenses
- Cost, billing, invoicing, and resource tagging
- Policy
- Other subscriptions and tenants (O365, Dynamics, InTune) 
- Naming conventions


## Subscriptions

- [Subscription level budgets via ARM APIs](https://azure.microsoft.com/en-us/blog/subscription-budgets-api-preview/)

- Subscriptions in the Classic (ASM) deployment model
- Privileged Access Management / "Tier 0" model


## Azure Management Groups

_In private preview as of January 2018. According to existing documentation, Management Groups are read-only in the portal, and must still be defined and managed via the EA portal._ 

[Azure Management Groups](/azure/billing/billing-enterprise-mgmt-group-overview) (introduced in 2018) allow all organizations with multiple subscriptions to group subscriptions together for simplified management of access, [policy](/azure/azure-policy/azure-policy-introduction)), costs, billing, and compliance across your subscriptions. Organizations can create a hierarchy of management groups that aligns to their preferred subscription management model.
