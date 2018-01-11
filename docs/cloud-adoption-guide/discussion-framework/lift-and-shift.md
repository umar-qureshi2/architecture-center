# Architectural discussion questions: Lift-and-shift

Lift-and-shift is an approach to cloud migration where applications are not redesigned.

## Application and data migration  

**Are you aware of the Microsoft Azure Virtual Machine Readiness Assessment tool?**

This tool will automatically inspect your on-premises environment, whether physical or virtualized. The output of the tool is a high level checklist and a detailed report on steps you need to take to move your environment to the cloud. For more information, see [Azure Virtual Machine Readiness Assessment](https://azure.microsoft.com/downloads/vm-readiness-assessment/).

## Azure Design Principles with Lift and Shift   

**Have you considered your approach to governance in an Azure environment?**

Governance involves the policies and processes that control access to Azure resources. On Azure, some aspects of governance include subscription management, resource group management, and auditing. The goal of the discussion is to plan where the workloads will go. For example, create separate production and dev/test environments; use tags to organize resources; use Azure Policy to enforce rules and actions for your resources. 

- Cloud Adoption Guide: Governance [tbd]

- [Subscription Governance](/azure/azure-resource-manager/resource-manager-subscription-governance)

- [Enabling EA DevTest Subscriptions](https://channel9.msdn.com/blogs/EA.Azure.com/Enabling-and-Creating-EA-DevTest-Subscriptions-through-the-EA-Portal?term=ea%20portal%20taxonomy)
 
- [Azure subscription Limits](/azure/azure-subscription-service-limits)

- [Resource naming conventions](../../best-practices/naming-conventions)

- [Use tags to organize your Azure resources](https://docs.microsoft.com/en-us/azure/azure-resource-manager/resource-group-using-tags)

- RBAC?

- Azure Policy? [Azure Policy documentation](/azure/azure-policy/)

**How does the application communicate? Are there legacy applications that need to be taken into account that cannot be migrated?**

Determine data flows, as well as dependencies within the application.    

[Design Principles for Applications hosted in Azure](https://docs.microsoft.com/en-us/azure/architecture/resiliency/)

[WASSON: I don't understand how this link supports the discussion question]

**Have you considered the load and runtime requirements of your solution?** It is important to plan the VM size and storage appropriately, to ensure that performance is not compromised once the solution has been migrated to Azure. Understand the VM sizes in terms of memory, processing, and storage and disk throughput. 

- [Sizes for Windows virtual machines in Azure](/azure/virtual-machines/windows/sizes)

- [Azure Storage scalability and performance targets](/azure/storage/common/storage-scalability-targets)

- [Microsoft Azure Storage performance and scalability checklist](/azure/storage/common/storage-performance-checklist)

> [Azure Site Recovery Deployment Planner for VMware to Azure](/azure/site-recovery/site-recovery-deployment-planner)
>
> [Azure Site Recovery Deployment Planner for Hyper-V to Azure](/azure/site-recovery/site-recovery-hyper-v-deployment-planner)

[WASSON - How do the last 2 support lift and shift?]

**Have you defined your networking requirements?**

The goal is to understand the network capacity to transfer data and also to secure the application across tiers. What is needed to transfer your data from on-premises into Azure? Have you thought about how you will segregate your workloads across subnets or Virtual Networks?

- [Azure networking limits](/azure/azure-subscription-service-limits#networking-limits)

- [Virtual network peering](https://docs.microsoft.com/en-us/azure/virtual-network/virtual-network-peering-overview)

- [Connect an on-premises network to Azure](../../reference-architectures/hybrid-networking/index.md)

## App & Data Migration 

* **What are the current set of dependencies that your current and legacy applications have?  Do you plan to extend your current authorization and authentication for applications or do you plan to create a hosting domain to insulate your internal Active Directory? &nbsp; &nbsp;**

The goal is to understand whether there is an on-premises environment and considerations made for the moving of the application to a new environment.  Which Azure services are used within the solution?  Are there any third party services used within the solution?  Does the solution talk to any on-premises components? Are the applications currently virtualized in VMWare and moving to Azure? Understanding of the planning that must occur if Azure Site Recovery will be used.    

[Minimize and understand service dependencies](Reference - Minimize and understand service dependencies)

[https://docs.microsoft.com/en-us/azure/site-recovery/site-recovery-azure-to-azure-prereq](https://docs.microsoft.com/en-us/azure/site-recovery/site-recovery-azure-to-azure-prereq)

[https://azure.microsoft.com/en-us/resources/videos/asrhowto-video2-migrate-virtual-machines-to-azure/](https://azure.microsoft.com/en-us/resources/videos/asrhowto-video2-migrate-virtual-machines-to-azure/)

[https://blogs.technet.microsoft.com/hybridcloud/2016/03/03/move-vmware-aws-hyper-v-and-physical-servers-to-azure-with-azure-site-recovery/](https://blogs.technet.microsoft.com/hybridcloud/2016/03/03/move-vmware-aws-hyper-v-and-physical-servers-to-azure-with-azure-site-recovery/)

[https://docs.microsoft.com/en-us/azure/site-recovery/vmware-walkthrough-overview](https://docs.microsoft.com/en-us/azure/site-recovery/vmware-walkthrough-overview)

[https://blogs.msdn.microsoft.com/zxue/2016/07/30/tips-and-tricks-on-doing-lift-and-shift-on-prem-systems-to-azure/](https://blogs.msdn.microsoft.com/zxue/2016/07/30/tips-and-tricks-on-doing-lift-and-shift-on-prem-systems-to-azure/)

* **Have you considered the feasibility of your internet connection, in line with the volume of data to be uploaded?**

Establish if there is a sufficiently fast connection to the internet and if there is an opportunity to move unstructured data into Azure    

[https://docs.microsoft.com/en-us/azure/storage/common/storage-import-export-service](https://docs.microsoft.com/en-us/azure/storage/common/storage-import-export-service)

[https://docs.microsoft.com/en-us/azure/storage/common/storage-import-export-using-the-rest-api](https://docs.microsoft.com/en-us/azure/storage/common/storage-import-export-using-the-rest-api)

* **Are you aware of the options available to migrate your data to Azure?**

Establish which options in moving the data to Azure will align best with your scenario and solution.    
    
- [Moving data to and from Azure Storage](/azure/storage/common/storage-moving-data)

- [Use the Microsoft Azure Import/Export service to transfer data to Azure Storage](/azure/storage/common/storage-import-export-service)


* **The data that you want to move into Azure how much of it is data that is intended to be archived or actual live data you plan to use on a daily basis?**

Determine whether the data needs to be moved for daily use or if the data is intended for archive    

[https://docs.microsoft.com/en-us/azure/backup/backup-introduction-to-azure-backup](https://docs.microsoft.com/en-us/azure/backup/backup-introduction-to-azure-backup)

## Linux Lift and Shift into Azure   

* **Do you have any Open Source workloads deployed on Linux that you plan to migrate to Azure and which distributions do you currently run in production**

Understand what OSS workloads that are currently running and the file systems that are currently running.    
[https://docs.microsoft.com/en-us/azure/site-recovery/site-recovery-support-matrix-to-azure](https://docs.microsoft.com/en-us/azure/site-recovery/site-recovery-support-matrix-to-azure)

## Distributed Architecture  

* **Is your application located in one central datacenter or is it spread across a multisite topology? Does this include multiple cloud providers? &nbsp;**

Is part of the application on-premises, or an alternate cloud provider, or third party? Ensure that you are aware of the risk of upstream or downstream dependency failures.    

[https://docs.microsoft.com/en-us/azure/site-recovery/site-recovery-migrate-aws-to-azure](https://docs.microsoft.com/en-us/azure/site-recovery/site-recovery-migrate-aws-to-azure)

[Host applications in multiple datacenters](https://docs.microsoft.com/en-gb/azure/best-practices-availability-checklist)

[Azure Paired Regions](https://docs.microsoft.com/en-gb/azure/best-practices-availability-paired-regions)

[Multiple datacenter regions / Azure Traffic Manager](https://docs.microsoft.com/en-gb/azure/resiliency/resiliency-disaster-recovery-azure-applications)

[Recovery from a region-wide service disruption](https://docs.microsoft.com/en-gb/azure/resiliency/resiliency-technical-guidance-recovery-loss-azure-region)

## High Availability and Business Continuity / Disaster Recovery  

* **Do you have Availability Requirements defined for the workload? How much downtime is acceptable? Have you defined a Recovery Time OBjective (RTO) and Recovery Point Objective (RPO)?**

It is critical that there are defind Resiliency (High Availability &amp; Disaster Recovery) metrics like RPO/RTO/SLA. Without these metrics it will be hard to design an application to hit business needs.    

[Designing resilient applications for Azure](https://docs.microsoft.com/en-us/azure/architecture/resiliency/index#defining-your-resiliency-requirements)

* **Is there a defined SLA for the workload?**

It is important to understand how this impacts the SLA that you provide your end-users. You should define a target SLA for each workload. An SLA makes it possible to evaluate whether the architecture meets the business requirements.  Ensure that you calculate Composite SLA (SLA of multiple Azure and other dependent services that makes up the workload) and see if that meets the business SLA requirements.  You can then cross compare your SLAs with Microsoft Azure's to determine the neccessary requirements needed.    

[Defining Resiliency Requirements](https://docs.microsoft.com/en-us/azure/architecture/resiliency/index#defining-your-resiliency-requirements)

[Azure SLAs](https://azure.microsoft.com/en-us/support/legal/sla/)

* **Have you performed Failure Mode Analysis (FMA)?**

FMA is to identify possible points of failures and define how the applications will respond to those failures.    

[Failure Mode Analysis](https://docs.microsoft.com/en-us/azure/architecture/resiliency/failure-mode-analysis)

* **Do you require a level of high availability for your Open Source Application systems when they are migrated to Azure? Do you require your Linux system to be a failover cluster?**

Understand if the Open Source System requires high availability as part of the application design.    
    

* **Does your MySQL database have any high availability requirements?**

Be aware of the associated guidance for MySQL on Azure.    

http://download.microsoft.com/download/6/1/C/61C0E37C-F252-4B33-9557-42B90BA3E472/MySQL_HADR_solution_in_Azure.pdf](http://download.microsoft.com/download/6/1/C/61C0E37C-F252-4B33-9557-42B90BA3E472/MySQL_HADR_solution_in_Azure.pdf)

## Monitoring & Management

* **How is the health and performance of the application measured and monitored? What KPIs are reviewed by the operations team? &nbsp;**

When developing a monitoring strategy and implementation for a system, the first step is determining the Key Performance Indicators used to measure the health, behavior and performance of the system. Without having clear and quantified targets in mind, making informed engineering decisions is effectively impossible, and leads to circular, anecdotal discussions of &quot;the system feels slow&quot; &nbsp;    

[Reference - Monitoring and diagnostics guidance](https://docs.microsoft.com/en-gb/azure/best-practices-monitoring)
>
[https://docs.microsoft.com/en-us/azure/backup/backup-azure-configure-reports](https://docs.microsoft.com/en-us/azure/backup/backup-azure-configure-reports)

[https://blogs.technet.microsoft.com/msoms/2016/07/27/introducing-oms-network-performance-monitor/](https://blogs.technet.microsoft.com/msoms/2016/07/27/introducing-oms-network-performance-monitor/)

* **If you are offering an SLA, do you have any methods of monitoring the SLA that you are providing?**

Many commercial systems that support paying customers make guarantees about the performance of the system in the form of SLAs. Essentially, SLAs state that the system can handle a defined volume of work within an agreed time frame and without losing critical information. SLA monitoring is concerned with ensuring that the system can meet measurable SLAs. &nbsp;    

[SLA Monitoring](https://docs.microsoft.com/en-gb/azure/best-practices-monitoring#sla-monitoring)

* **What is the resource utilization across deployed resources? How much headroom (capacity) is there across the deployed resources? &nbsp;**

Usage monitoring can help to determine which features may benefit from functional partitioning or re-architecture. Additionally, it may help to serve which components should be retired from the solution. &nbsp; It could also be used to Detect (possibly indirectly) user satisfaction with the performance or functionality of the system. For example, if a large number of customers in an e-commerce system regularly abandon their shopping carts, this might be due to a problem with the checkout functionality. &nbsp;    

[Usage Monitoring](https://docs.microsoft.com/en-gb/azure/best-practices-monitoring#usage-monitoring)

* **How many operations are executed across various tiers? Per second/hour/day? Peak load? Are you monitoring the performance of your application as it scales and is placed under more and more stress/load? &nbsp;**

As the system is placed under more and more stress (by increasing the volume of users), the size of the datasets that these users access grows and the possibility of failure of one or more components becomes more likely. Frequently, component failure is preceded by a decrease in performance. If you&#39;re able detect such a decrease, you can take proactive steps to remedy the situation. &nbsp;    

[Performance Monitoring](https://docs.microsoft.com/en-gb/azure/best-practices-monitoring#performance-monitoring)

* **How many errors (user-visible) are produced in the system? Per second/hour/day? If needed, can a root-cause be defined? Do you actively check if the system is functioning as expected? Are you currently performing health monitoring? &nbsp;**

An operator should be alerted quickly (within a matter of seconds) if any part of the system is deemed to be unhealthy. The operator should be able to ascertain which parts of the system are functioning normally, and which parts are experiencing problems. &nbsp;    
git
[Health Monitoring](https://docs.microsoft.com/en-gb/azure/best-practices-monitoring#health-monitoring)
>
[Overview of Azure Monitor](https://docs.microsoft.com/en-us/azure/monitoring-and-diagnostics/monitoring-overview)

* **How many active, unique users does your application support (mobile, web, etc.)? &nbsp;**

    Understand the personas that are using the application and when peak usage occurs  

* **Are you aware of managed disks, and how they can provide High Availability compared with user managed disks?**

    Explain the benefit of Managed Disks as well as how they are supported in ASR during lift and shift.    
    
    [https://azure.microsoft.com/en-us/blog/managed-disks-with-azure-site-recovery/](https://azure.microsoft.com/en-us/blog/managed-disks-with-azure-site-recovery/)

## Performance & Scalability  

* **How many users does your application need to support? (total and concurrently active; how are they geographically distributed) Have you designed for scaling within your solution? (e.g. Stateless where appropriate, auto-detection of new instances) &nbsp;**

    Determine whether the solution is being tested beyond the predicted peak load. Additionally, this will determine whether their solution has been configured for scaling or not, and whether it is architected to avoid platform limits.    
    
    [Scalability checklist](https://docs.microsoft.com/en-us/azure/best-practices-scalability-checklist)

* **What are the per-operation latency targets, and acceptable latency range? How many operations/messages per second?**

    Reduce chatty interactions between components and services. Avoid designing interactions in which an application is required to make multiple calls to a service (each of which returns a small amount of data), rather than a single call that can return all of the data. Where possible, combine several related operations into a single request when the call is to a service or component that has noticeable latency. This makes it easier to monitor performance and optimize complex operations. For example, use stored procedures in databases to encapsulate complex logic, and reduce the number of round trips and resource locking.    
    
    [Scalability checklist - Reduce chatty interactions](https://docs.microsoft.com/en-us/azure/best-practices-scalability-checklist)

* **What, if any, seasonality is there to the solution? &nbsp;**

    Azure Advisor is a personalized cloud consultant that helps you follow best practices to optimize your Azure deployments. It analyzes your resource configuration and usage telemetry and recommends solutions that can help you improve the cost effectiveness, performance, high availability and security of your Azure resources.    
    
    [Introduction to Azure Advisor](https://docs.microsoft.com/en-us/azure/advisor/advisor-overview)

* **What are the operational constraints and requirements for the system? Are there compliance, location (required geography), regulatory (HIPAA, FEDRAMP, etc.) or sovereignty requirements?**

    Microsoft Trust Center provides you with a wealth of information about how Microsoft Cloud Services are secured, how Microsoft ensures privacy of your data, as well as information about Compliance and more.    
    
    [Microsoft Trust Center](https://docs.microsoft.com/en-us/azure/security/security-microsoft-trust-center)

## Security  

* **Do you have any requirements for encryption?**

    Understand if the current workload has or will require encryption.    
    
    [https://docs.microsoft.com/en-us/azure/storage/common/storage-service-encryption-customer-managed-keys](https://docs.microsoft.com/en-us/azure/storage/common/storage-service-encryption-customer-managed-keys)
    
    [https://azure.microsoft.com/en-us/documentation/articles/security-get-started-overview/](https://azure.microsoft.com/en-us/documentation/articles/security-get-started-overview/)

* **Who currently requires access to the application during and after the migration?**

    Define the security requirements and if there are new security requirements once the solution has moved onto Azure.    
    
    [https://docs.microsoft.com/en-us/azure/azure-resource-manager/resource-group-lock-resources](https://docs.microsoft.com/en-us/azure/azure-resource-manager/resource-group-lock-resources)
    
    [https://docs.microsoft.com/en-us/azure/backup/backup-rbac-rs-vault](https://docs.microsoft.com/en-us/azure/backup/backup-rbac-rs-vault)