---
title: Explainer - How does Azure work?
description: Explanation of the internal functioning of Azure works
author: petertay
---

# Explainer: How does Azure work?

Azure is Microsoft's public cloud platform. Azure offers a large collection of services including platform as a service (PaaS), infrastructure as a service (IaaS), database as a service (DBaaS), and many others. But what exactly is Azure, and how does it work?

Azure, as with all other cloud platforms, relies on a technology known as virtualization. The term virtualization refers to the fact that most computer hardware can be emulated in software. This is because fundamentally, most computer hardware is simply a set of instructions and memory permanently or semi-permanently encoded in silicon. With the aid of an emulation layer that knows how to map software instructions to hardware instructions, virtual hardware can execute in software just as though it were the actual hardware itself.

Put simply, the cloud is a set of hardware computers in a datacenter that are executing virtualized hardware on behalf of customers. So how does the cloud manage creating, starting, stopping, and deleting millions of pieces of virtualized hardware on behalf of millions of customers, all at the same time?

To understand this, we need to look at the architecture of the hardware in the datacenter.  Within each datacenter is a collection of servers sitting in server racks. Each server rack contains many server "blades" as well as a top-of-rack (TOR) network switch providing network connectivity and a power distribution unit (PDU) providing power. 

Within each rack, most of the servers are designated to run these virtualized hardware instances on behalf of the user. However, a small number of the servers run cloud management software known as a "fabric controller". The fabric controller is responsible for many things, including allocating services, monitoring health of the server and the services running on it, and healing servers when they fail.

Each fabric controller is connected to another set of servers running cloud orchestration software, typically known as a "front end". This front end hosts all the web services, APIs, billing, and all other functions the cloud performs. The front end includes databases for everything from user identity all the way down to where individual resources are allocated. 

To understand how the front end works, let's take a look at Azure. The Azure front end includes a service known as Azure Resource Manager. Azure Resource Manager is responsible for the entire resource lifecycle from creation to deletion. There are many ways to interact with Azure Resource Manager - using Powershell, a command line interface, SDKs - but each of these is simply a wrapper on top of the restful API hosted by Azure Resource Manager. 

A customer can use any of these to request a resource in a region, and Azure Resource Manager find a rack within that region that can satisfy the request. The request is sent to the fabric controller in the rack, and the fabric controller allocates the resources. The fabric controller then sends the status of the request back Azure Resource Manager, which responds to the customers request with success or failure along with other useful information. The resource is then available for use.