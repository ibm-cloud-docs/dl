---

copyright:
  years: 2020
lastupdated: "2020-05-27"

keywords: hybrid, solutions, features, benefits, port speed, cross-connect, use cases, latency, routing, options, colocation, interconnectivity

subcollection: dl

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:DomainName: data-hd-keyref="DomainName"}
{:note: .note}
{:important: .important}
{:new_window: target="_blank"}
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

# About {{site.data.keyword.dl_full_notm}} (2.0)
{: #dl-about}

{{site.data.keyword.dl_full}} offerings provide connectivity from an external source into a customer's {{site.data.keyword.cloud_notm}} private network. {{site.data.keyword.dl_short}} can be viewed as an alternative to a traditional site-to-site VPN solution, which is designed for customers that need more consistent, higher-throughput connectivity between a remote network and their {{site.data.keyword.cloud_notm}} environments.
{:shortdesc}

## {{site.data.keyword.dl_short}} offerings
{: #overview-of-direct-link-offerings}

Currrently, two types of connections are available:
{:shortdesc}

* **{{site.data.keyword.dl_short}} Dedicated** - Allows customers to terminate a single-tenant, fiber-based cross-connect into the {{site.data.keyword.cloud_notm}} network. This offering can be used by customers with colocation premises that are next to {{site.data.keyword.cloud_notm}} PoPs and data centers, as well as network service providers that deliver circuits to customer on-premises or other data centers.

   The {{site.data.keyword.dl_full_notm}} service is a routed, OSI Layer-3 service. It offers a direct connection to the {{site.data.keyword.cloud_notm}} private network backbone, with low latency and speeds up to 10 Gbps.

  For increased flexibility in creating this Layer-3 connectivity, {{site.data.keyword.dl_full_notm}} enables customers to use:

   * Dual IP for remote hosts
   * NAT
   * Tunneling for BYOIP

* **{{site.data.keyword.dl_short}} Connect** - Offers private access to your IBM Cloud infrastructure and to any other clouds linked to your service provider through your local IBM Cloud data center. This option is perfect for creating multi-cloud connectivity in a single environment. IBM connects customers to the IBM Cloud private network, using a shared bandwidth topology. As with all {{site.data.keyword.dl_short}} products, you can add global routing that enables private network traffic to all IBM Cloud locations.

## Use cases
{: #use-cases}
The following use cases illustrate some common scenarios with the {{site.data.keyword.dl_full_notm}} Dedicated and Connect services.

### {{site.data.keyword.dl_short}} Dedicated use cases
{: #use-cases-dedicated}
These use cases are best for working with hybrid workloads, cross-provider workloads, large or frequent data transfers, private workloads, and environment administration. Use these use cases:

* When you want dedicated connectivity for mission-critical workloads
* When you need dedicated, single-tenant connections between a client and IBM
* When diverse ports in a point of presence (PoP) are available, or when you require link aggregation group (LAG) support for 10 GB or greater speeds

#### Use case 1: Customer on-premises facility to {{site.data.keyword.cloud_notm}}
{: #use-cases-dedicated-1}

Use when deterministic latency is required.

![Figure 1](/images/direct-link-dedicated.png)

#### Use case 2: Customer colocation to {{site.data.keyword.cloud_notm}}
{: #use-case-dedicated-2}

Use when ultra-low latency is required.

![Figure 2](/images/dedicated-model-colo.png)

**Termination location** - {{site.data.keyword.cloud_notm}} point of presence (PoP) or Data Center (DC).

**Typical deployment time** - Averages 10-15 business days after the new circuit reaches the PoP. Deployment time can be 30 - 60 days overall, depending on your location and the requirements when you order a circuit from a service provider or carrier.

**Cross-connect details** - {{site.data.keyword.cloud_notm}} provides a Letter of Authorization (LOA) that you can use to order fiber Ethernet (single-mode fiber only, either 1Gig-LX or 10Gig-LR optics). This Ethernet runs from a customer cage or provider cage to the {{site.data.keyword.cloud_notm}} Connecting Facility Assignment (CFA) termination point, which is tied down to the cross-connect router (XCR) infrastructure. The media must be a 1310 nm wavelength optic.

**Port speed options** - Select 1 Gbps, 2 Gbps, 5 Gbps, or 10 Gbps.

**Approximate latency** - Latency is approximately 1.5 ms within the local area (data centers with the same three-letter prefix, such as DAL, AMS, MEL). See [Looking Glass](http://lg.softlayer.com/){: external} for live PoP-to-PoP (P2P) location latency measurements.

**IBM colocation services** - None.

**Redundancy** - {{site.data.keyword.cloud_notm}} doesn't provide redundancy as part of the product. To establish redundant connectivity, customer must acquire two connections on diverse cross connect routers (XCRs) and configure BGP on each {{site.data.keyword.dl_short}} connection as they prefer. Examples include: _prefer Lowest MED_, _prefer highest local-preference_, or _prefer shorter AS paths_.

**Local and global routing options** - The local routing option is the default routing option. It provides access to data centers within the same market as the {{site.data.keyword.dl_short}} PoP (denoted, for example, as DAL, AMS, or MEL). The global routing option is required as an add-on to connect your {{site.data.keyword.cloud_notm}} resources to other {{site.data.keyword.cloud_notm}} resources in data centers outside the local market. It provides a way to share workloads between {{site.data.keyword.cloud_notm}} resources (for example, Dallas to Ashburn, or Dallas to Frankfurt).

### {{site.data.keyword.dl_short}} Connect use case
{: #use-case-connect}

The Connect solution enables you to use a service provider to deliver connectivity to {{site.data.keyword.cloud_notm}} locations. This offering typically provides connectivity at a reduced cost because the physical connectivity from {{site.data.keyword.cloud_notm}} to the service provider is already in place, which is shared among other customers.

Some benefits include:

* Multi-cloud use through a single Connect port
* Latency tolerant
* Lower cost entry to {{site.data.keyword.cloud_notm}}

![Figure 3](/images/direct-link-connect.png)

**Termination location:** {{site.data.keyword.cloud_notm}} point of presence (PoP).

**Typical deployment time:** 5 - 10 days after the circuit reaches the exchange. Deployment time can be 30 - 60 days overall, depending on your location and the requirements when you order a circuit from a service provider or carrier.

**Cross-connect details:** Physical cross-connects for the secure {{site.data.keyword.dl_short}} Connect interconnect are maintained between {{site.data.keyword.cloud_notm}} and the Connect provider. You must request a "Virtual Circuit" from the Cloud Connect provider, which establishes logical connectivity to {{site.data.keyword.cloud_notm}}, after you are connected to the Cloud Connect provider.

**Port speed options:** Select 50 Mbps, 100 Mbps, 200 Mbps, 500 Mbps, 1 Gbps, 2 Gbps, or 5 Gbps.

**Approximate latency:** Latency is approximately 1.5 ms within the local area (data centers with the same three-letter prefix, such as DAL, AMS, MEL). See [Looking Glass](http://lg.softlayer.com/){: external} for live PoP-to-PoP (P2P) location latency measurements.

**IBM colocation services** - None.

**Redundancy**: {{site.data.keyword.cloud_notm}} does not provide redundancy as part of the product. To establish redundant connectivity, you must acquire two connections on diverse cross connect routers (XCRs) and configure BGP on each {{site.data.keyword.dlc_full_notm}} connection as they prefer. Examples include: _prefer Lowest MED_, _prefer highest local-preference_, or _prefer shorter AS paths_.

**Local and global routing options:** The default routing option is Local routing. It provides access to data centers within the same market as the {{site.data.keyword.dl_short}} PoP (denoted, for example, as DAL, AMS, or MEL). The global routing option is required as an add-on to connect your IBM Cloud resources to other IBM Cloud resources in data centers outside the local market. It is used to share workloads between IBM Cloud resources (for example Dallas to Ashburn, or Dallas to Frankfurt).
