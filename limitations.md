---

copyright:
  years: 2018, 2020
lastupdated: "2020-03-18"

keywords: vpc, limitations, restrictions

subcollection: vpc


---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}

# Service limitations
{: #limitations}

Limitations might change as capabilities are added, so feel free to check back from time to time.
{:shortdesc}

## General restrictions
{: #general-restrictions}

The following features are not supported, including all properties associated with these features:

* The following concepts are not supported:
  * IPV6
  * Multiple IP addresses on the same network interface

* Virtual server instance name change: If you update the name of a virtual server, the name change may not appear consistently in different areas of the {{site.data.keyword.cloud}} console. For example, the virtual server name change might not be reflected in the {{site.data.keyword.cloud_notm}} console, or on the billing invoice, yet it appears correctly in the user's list of running instances.

* POWER-based instances are only available in the Dallas region.

* Direct Link on Classic access to VPC is supported through [Setting up access to classic infrastructure](/docs/vpc?topic=vpc-setting-up-access-to-classic-infrastructure) only. Direct Link (release 2.0) does not have this limitation. 

## Virtual private cloud restrictions
{: #virtual-private-cloud-restrictions}

* An {{site.data.keyword.vpc_short}} cannot be peered with other VPCs natively. It is possible to connect VPCs utilizing either Transit Gateway, VPN Gateways or Floating IPs. 
    - With both VPN Gateways and Floating IPs, there is no automatic route advertisement between the two VPCs. Static routes must be used in each VPC to enable layer 3 connectivity between the two VPCs. See [How to use a VPN Gateway to connect two VPCs](/docs/vpc-on-classic-network?topic=vpc-on-classic-network---using-vpn-with-your-vpc#vpn-example) for how you can achieve VPC-to-VPC connectivity using this method. 
    - With Transit Gateway, it advertises the root subnets of each VPC allowing trafific to be routed without the use of static routes. For more information see [Getting started with IBM Cloud Transit Gateway](/docs/transit-gateway?topic=transit-gateway-getting-started)

## Network restrictions
{: #network-restrictions}

* Multi-zone regions: 
  * A security group can be configured in a single zone only. 
  * A security group can’t reference another security group in a different zone in the same region.

* Bring your own subnet: Address prefixes must be within one of the "private" address ranges defined in RFC1918.

* Multiple Virtual Network Interface Controllers: Only one Virtual Network Interface Controller is allowed for each virtual server instance. Currently, only the primary Virtual Network Interface Controller (VNIC) Ethernet 0 (eth0) works for a virtual server.

* VPN: A VPN gateway serves only subnets that are in the zone in which the VPN is created. For more information, see [Using VPN](/docs/vpc?topic=vpc-using-vpn#vpn-limitations).

## Compute restrictions
{: #compute-restrictions}

* Every x86-based profile has a network performance value of 2 Gbps per vCPU, with a cap of 80 Gbps.
* Every POWER-based profile has a network performance value of 3 Gbps per vCPU, with a cap of 100 Gbps.
* Each x86-based network interface has a network performance cap of 16 Gbps. <!-- You might need to attach multiple network interfaces to your virtual server instance to optimize network performance. -->
* Each POWER-based network interface has a network performance cap of 25 Gbps.
* Start/Stop actions are not registered under virtual server instance activity in the UI.
* Activity Tracker logs (request logs and resource lifecycle event logs) are not available.
* Updating the profile of a created instance is not supported.
* Live migration is not supported.

* We have temporarily suspended API support for creating new instances from an existing boot volume. For more information, see the [API change log](/docs/vpc?topic=vpc-api-change-log).

## Storage restrictions
{: #storage-restrictions}

* Customer-managed encryption for secondary volumes is not supported.

## API considerations
{: #api-considerations}

* For API limitations and considerations, see [API application migration considerations](/docs/vpc?topic=vpc-api-integration-migration). 

