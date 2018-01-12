# Architectural discussion questions: Lift-and-shift

Lift-and-shift is an approach to cloud migration where applications are not redesigned for the cloud. Instead, the application is moved to VMs running in Azure with minimal changes.

## Requirements

**Do you have availability requirements defined for the workload? How much downtime is acceptable? Have you defined a Recovery Time Objective (RTO) and Recovery Point Objective (RPO)?**

It is critical that there are defind resiliency (High Availability &amp; Disaster Recovery) metrics like RPO/RTO/SLA. Without these metrics it will be hard to design an application to hit business needs.    
    
**Is there a defined SLA for the workload?**

It is important to understand how this impacts the SLA that you provide your  end-users. You should define a target SLA for each workload. An SLA makes it possible to evaluate whether the architecture meets the business requirements.  Calculate the composite SLA of Azure and other dependent services that make up the workload, to ensure they meet your target SLA. 

**What are the operational constraints and requirements for the system? Are there compliance, location (required geography), regulatory (HIPAA, FEDRAMP, etc.) or sovereignty requirements?**

Microsoft Trust Center provides you with a wealth of information about how Microsoft Cloud Services are secured, how Microsoft ensures privacy of your data, as well as information about Compliance and more.    

## Assessment 

**Are you aware of the Microsoft Azure Virtual Machine Readiness Assessment tool?**

This tool will automatically inspect your on-premises environment, whether physical or virtualized. The output of the tool is a high level checklist and a detailed report on steps you need to take to move your environment to the cloud. For more information, see [Azure Virtual Machine Readiness Assessment](https://azure.microsoft.com/downloads/vm-readiness-assessment/).    

## Capacity planning

**How many active, unique users does your application support (mobile, web, etc.)? &nbsp;**

Understand the personas that are using the application and when peak usage occurs  

**Have you considered the load and runtime requirements of your solution?**

It is important to plan the VM size and storage appropriately, to ensure that performance is not compromised once the solution has been migrated to Azure. Understand the VM sizes in terms of memory, processing, and storage and disk throughput.     
    

**Have you defined your networking requirements? What is needed to transfer your data from on-premises into Azure? Additionally, have you thought about how you will segregate your workloads across subnets or Virtual Networks?**

Understand the network capacity to transfer data and also to secure the application across tiers. What is needed to transfer your data from on-premises into Azure? Have you thought about how you will segregate your workloads across subnets or Virtual Networks?    
   

**How many users does your application need to support? (total and concurrently active; how are they geographically distributed) Have you designed for scaling within your solution? (e.g. Stateless where appropriate, auto-detection of new instances) &nbsp;**

Determine whether the solution is being tested beyond the predicted peak load. Additionally, this will determine whether their solution has been configured for scaling or not, and whether it is architected to avoid platform limits. 

## Deployment considerations

**Have you considered your approach to governance in an Azure environment?**

Governance involves the policies and processes that control access to Azure resources. On Azure, some aspects of governance include subscription management, resource group management, and auditing. The goal of the discussion is to plan where the workloads will go. For example, create separate production and dev/test environments; use tags to organize resources; use Azure Policy to enforce rules and actions for your resources.

## Application migration

**How does the application communicate? Are there legacy applications that need to be taken into account that cannot be migrated?**

Determine data flows, as well as dependencies within the application.    
    
**What are the current set of dependencies that your current and legacy applications have?  Do you plan to extend your current authorization and authentication for applications or do you plan to create a hosting domain to insulate your internal Active Directory?**

The goal is to understand whether there is an on-premises environment and considerations made for the moving of the application to a new environment.  Which Azure services are used within the solution?  Are there any third party services used within the solution?  Does the solution talk to any on-premises components? Are the applications currently virtualized in VMWare and moving to Azure? Understanding of the planning that must occur if Azure Site Recovery will be used.    
    
**Do you have any Open Source workloads deployed on Linux that you plan to migrate to Azure and which distributions do you currently run in production**

Understand what OSS workloads that are currently running and the file systems that are currently running.

**Is your application located in one central datacenter or is it spread across a multisite topology? Does this include multiple cloud providers?**

Is part of the application on-premises, or an alternate cloud provider, or third party? Ensure that you are aware of the risk of upstream or downstream dependency failures.

**Will you use Azure Site Recovery to migrate existing VMs or servers to Azure?**

tbd

## Data migration

**Are you aware of the options available to migrate your data to Azure?**

Establish which options in moving the data to Azure will align best with your scenario and solution.    

**The data that you want to move into Azure how much of it is data that is intended to be archived or actual live data you plan to use on a daily basis?**

Determine whether the data needs to be moved for daily use or if the data is intended for archive.

**Have you considered the feasibility of your internet connection, in line with the volume of data to be uploaded?**

Establish if there is a sufficiently fast connection to the internet and if there is an opportunity to move unstructured data into Azure. 


## Monitoring

**How is the health and performance of the application measured and monitored? What KPIs are reviewed by the operations team?**

When developing a monitoring strategy and implementation for a system, the first step is determining the Key Performance Indicators used to measure the health, behavior and performance of the system. Without having clear and quantified targets in mind, making informed engineering decisions is effectively impossible, and leads to circular, anecdotal discussions of "the system feels slow."    
    
**If you are offering an SLA, do you have any methods of monitoring the SLA that you are providing?**

Many commercial systems that support paying customers make guarantees about the performance of the system in the form of SLAs. Essentially, SLAs state that the system can handle a defined volume of work within an agreed time frame and without losing critical information. SLA monitoring is concerned with ensuring that the system can meet measurable SLAs.     
    
**What is the resource utilization across deployed resources? How much headroom (capacity) is there across the deployed resources? &nbsp;**

Usage monitoring can help to determine which features may benefit from functional partitioning or re-architecture. Additionally, it may help to serve which components should be retired from the solution. It could also be used to detect (possibly indirectly) user satisfaction with the performance or functionality of the system. For example, if a large number of customers in an e-commerce system regularly abandon their shopping carts, this might be due to a problem with the checkout functionality.

**How many errors (user-visible) are produced in the system? Per second/hour/day? If needed, can a root-cause be defined? Do you actively check if the system is functioning as expected? Are you currently performing health monitoring? &nbsp;**

An operator should be alerted quickly (within a matter of seconds) if any part of the system is deemed to be unhealthy. The operator should be able to ascertain which parts of the system are functioning normally, and which parts are experiencing problems. 

**How many operations are executed across various tiers? Per second/hour/day? Peak load? Are you monitoring the performance of your application as it scales and is placed under more and more stress/load? &nbsp;**

As the system is placed under more and more stress (by increasing the volume of users), the size of the datasets that these users access grows and the possibility of failure of one or more components becomes more likely. Frequently, component failure is preceded by a decrease in performance. If you're able detect such a decrease, you can take proactive steps to remedy the situation. 

## Availability and resiliency planning

**Have you performed Failure Mode Analysis (FMA)?**

FMA is to identify possible points of failures and define how the applications will respond to those failures.    
    
**Do you require a level of high availability for your Open Source Application systems when they are migrated to Azure? Do you require your Linux system to be a failover cluster?**

Understand if the Open Source System requires high availability as part of the application design.    
    
**Does your MySQL database have any high availability requirements?**

Be aware of the associated guidance for MySQL on Azure.    

**Are you aware of managed disks, and how they can provide High Availability compared with user managed disks?**

Understand the benefit of Managed Disks as well as how they are supported in ASR during lift and shift.    
    
## Security  

**Do you have any requirements for encryption?**

Understand if the current workload has or will require encryption.    
    
**Who currently requires access to the application during and after the migration?**

Define the security requirements and if there are new security requirements once the solution has moved onto Azure.    

<!-- uncategorized -->

## ???

**What are the per-operation latency targets, and acceptable latency range? How many operations/messages per second?**

Reduce chatty interactions between components and services. Avoid designing interactions in which an application is required to make multiple calls to a service (each of which returns a small amount of data), rather than a single call that can return all of the data. Where possible, combine several related operations into a single request when the call is to a service or component that has noticeable latency. This makes it easier to monitor performance and optimize complex operations. For example, use stored procedures in databases to encapsulate complex logic, and reduce the number of round trips and resource locking.    

[REVIEWER: This sounds more like app modernization than lift-and-shift]
    
**What, if any, seasonality is there to the solution?**

Azure Advisor is a personalized cloud consultant that helps you follow best practices to optimize your Azure deployments. It analyzes your resource configuration and usage telemetry and recommends solutions that can help you improve the cost effectiveness, performance, high availability and security of your Azure resources.

[REVIEWER: I don't understand the connection between seasonality and Azure Advisor]
