---
title: Azure Network libraries for Java
description: Reference documentation for the Java Azure Network management libraries 
keywords: Azure, Java, SDK, API, networking, load balancing, vnet , subnet
author: rloutlaw
ms.author: routlaw
manager: douge
ms.date: 07/20/2017
ms.topic: reference
ms.prod: azure
ms.technology: azure
ms.devlang: java
ms.service: networking
---

# Azure Network libraries for Java

## Overview

Connect Azure resources, filter and balance traffic, and manage routing with [Azure Networking](/azure/networking/networking-overview).

To get started with Azure Networking, see [Create your first virtual network](/azure/virtual-network/virtual-network-get-started-vnet-subnet).

## Management API

Create and manage Azure [virtual networks](/azure/virtual-network/virtual-networks-overview) , [ExpressRoutes](/azure/expressroute/) , and [Application Gateways](/azure/application-gateway/) with the management API.

[Add a dependency](https://maven.apache.org/guides/getting-started/index.html#How_do_I_use_external_dependencies) to your Maven `pom.xml` file to use the management API in your project.  

```XML
<dependency>
    <groupId>com.azure.resourcemanager</groupId>
    <artifactId>azure-resourcemanager-network</artifactId>
    <version>2.7.0</version>
</dependency>
```   

### Example

Create a new virtual network with two subnets.

```java
Network network = azure.networks().define("mynetwork")
	.withRegion(Region.US_EAST)
	.withNewResourceGroup()
	.withAddressSpace("10.0.0.0/28")
	.withSubnet("subnet1", "10.0.0.0/29")
	.withSubnet("subnet2", "10.0.0.8/29")
	.create();
```

> [!div class="nextstepaction"]
> [Explore the Management APIs](https://aka.ms/azsdk/java/mgmt)

## Samples

[Manage virtual networks](https://github.com/Azure-Samples/network-java-manage-virtual-network)   
[Manage network interfaces](https://github.com/Azure-Samples/network-java-manage-network-interface)   
[Manage Application Gateways](https://github.com/Azure-Samples/application-gateway-java-manage-simple-application-gateways)   
[Manage internet facing load balancers](https://github.com/Azure-Samples/network-java-manage-internet-facing-load-balancers)   

Explore more [sample Java code for Azure Networking](https://azure.microsoft.com/resources/samples/?platform=java&term=network) you can use in your apps.
