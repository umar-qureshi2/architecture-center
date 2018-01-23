---
title: Explainer - How does Azure Resource Manager work?
description: Explanation of the internal functioning of Azure Resource Manager
author: petertay
---

# Explainer: How does Azure Resource Manager work?

In the [how does Azure work?](azure-explainer.md) explainer, you learned that the internal architecture of Azure includes a front end that hosts the management services that connect to the fabric controller software running within each server rack in each datacenter. These management services include Azure Resource Manager, the service responsible for sending resource management instructions to fabric controllers. 

Azure resource manager