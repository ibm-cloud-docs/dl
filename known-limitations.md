---

copyright:
  years: 2019, 2020
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

 * Each {{site.data.keyword.cloud_notm}} Direct Link connection requires a unique order. If you require multiple connections, open an {{site.data.keyword.cloud_notm}} Direct Link order for each connection.
 * {{site.data.keyword.cloud_notm}} Direct Link requires BGP to establish the routes to a customer's remote network.
 * Each {{site.data.keyword.cloud_notm}} Direct Link service is not redundant. Diversity can be supplied by IBM for multiple direct links, however, customers need to build redundancy in their own BGP schemes.
 * If you want to connect to the classic infrastructure, be aware that IP subnet overlaps may exist and require exception approval. For more information, see [Configuring BPG](/docs/direct-link?topic=direct-link-configure-ibm-cloud-direct-link#configuring-bgp).
 * The {{site.data.keyword.cloud_notm}} services network is not accessible directly from your remote networks.
 * {{site.data.keyword.cloud_notm}} does not permit customers to back haul traffic between their remote sites across the {{site.data.keyword.cloud_notm}} backbone. The {{site.data.keyword.cloud_notm}} Direct Link product is meant to let your remote networks communicate privately with your {{site.data.keyword.cloud_notm}} infrastructure.
 * {{site.data.keyword.cloud_notm}} Direct Link requires you to use a VRF (Virtual Routing and Forwarding) instance.
 * VRF is not fully compatible with the {{site.data.keyword.cloud_notm}} SSL and IPsec VPN services.
 * Changes to the {{site.data.keyword.cloud_notm}} Direct Link services must be made between 8AM and 5PM, US Central time zone.
 * The {{site.data.keyword.cloud_notm}} fees for Direct Link Dedicated cover the cost of port termination on the {{site.data.keyword.cloud_notm}} infrastructure. Customers are responsible for any fees that are associated with reaching the PoP from a remote network and any cross-connects needed within the PoP facility. {{site.data.keyword.cloud_notm}} does not order a cross-connect on any customer's behalf.
 * {{site.data.keyword.cloud_notm}} does not colocate any customer equipment in our network PoPs. Customers must work with their provider to determine whether they need to colocate any equipment in the facility where the {{site.data.keyword.cloud_notm}} network PoP exists.
