---

copyright:
  years: 2017, 2018, 2019
lastupdated: "2019-12-15"

keywords: limitations, VRF, account-to-account, VPN, BGP, fees, contract, Exchange, Connect, Dedicated, Hosting

subcollection: dl

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:DomainName: data-hd-keyref="DomainName"}
{:note: .note}
{:important: .important}
{:deprecated: .deprecated}
{:external: target="_blank" .external}
{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:term: .term}  
{:generic: data-hd-programlang="generic"}
{:download: .download}  

# Known limitations
{: #known-limitations}

Known limitations are as follows:

 * Each IBM Cloud Direct Link connection requires a unique order. If you require multiple connections, open an IBM Cloud Direct Link order for each connection.
 * IBM Cloud Direct Link requires BGP to establish the routes to a customer's remote network.
 * Each IBM Cloud Direct Link service is not redundant. Diversity can be supplied by IBM for multiple direct links, however, customers need to build redundancy in their own BGP schemes.
 * If you want to connect to the classic infrastructure, be aware that IP subnet overlaps may exist and require exception approval. For more information, see [Configuring BPG](/docs/direct-link?topic=direct-link-configure-ibm-cloud-direct-link#configuring-bgp).
 * The IBM Cloud services network is not accessible directly from your remote networks.
 * IBM Cloud does not permit customers to back haul traffic between their remote sites across the IBM Cloud backbone. The IBM Cloud Direct Link product is meant to let your remote networks communicate privately with your IBM Cloud infrastructure.
 * IBM Cloud Direct Link requires you to use a VRF (Virtual Routing and Forwarding) instance.
 * VRF is not fully compatible with the IBM Cloud SSL and IPSec VPN services.
 * Changes to the IBM Cloud Direct Link services must be made between 8AM and 5PM, US Central time zone.
 * The IBM Cloud fees for Direct Link Dedicated cover the cost of port termination on the IBM Cloud infrastructure. Customers are responsible for any fees that are associated with reaching the PoP from a remote network and any cross-connects needed within the PoP facility. IBM Cloud does not order a cross-connect on any customer's behalf.
 * IBM Cloud does not colocate any customer equipment in our network PoPs. Customers must work with their provider to determine whether they need to colocate any equipment in the facility where the IBM Cloud network PoP exists.
