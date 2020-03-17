---

copyright:
  years: 2019, 2020
lastupdated: "2019-12-15"

keywords: hybrid, solutions, features, benefits, port speed, cross-connect, use cases, latency, routing, options, colocation

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

# About the {{site.data.keyword.cloud_notm}} Direct Link Dedicated solution
{: #dl-dedicated-solution}

You can use the {{site.data.keyword.cloud}} Direct Link Dedicated solution to terminate a single-tenant, fiber-based cross-connect into their own {{site.data.keyword.cloud_notm}} private network connection. This offering can be used by customers with colocation facilities that are next to {{site.data.keyword.cloud_notm}} PoPs and data centers. It can also be used by network service providers (NSPs) that deliver circuits to customer premises or to other data centers.
{: shortdesc}

## Use cases

These use cases are best for working with hybrid workloads, cross-provider workloads, large or frequent data transfers, private workloads, and environment administration. Use these use cases:

* When you want dedicated connectivity for mission-critical workloads
* When you need dedicated, single-tenant connections between a client and IBM
* When diverse ports in a point of presence (PoP) are available, or when you require link aggregation group (LAG) support for 10 GB or greater speeds

### Use case 1: Customer on-premises facility to {{site.data.keyword.cloud_notm}}

Use when deterministic latency is required.

![Figure 1](/images/direct-link-dedicated.png)

### Use case 2: Customer colocation to {{site.data.keyword.cloud_notm}}

Use when ultra-low latency is required.

![Figure 2](/images/dedicated-model-colo.png)

## More information

**Termination location** - 
{{site.data.keyword.cloud_notm}} point of presence (PoP) or Data Center (DC).

**Typical deployment time** - Averages 10-15 business days after the new circuit reaches the PoP. Deployment time can possibly be 30 - 60 days overall, depending on your location and requirements when you order a circuit from an NSP or carrier.

**Cross-connect details** - {site.data.keyword.cloud_notm}} provides a Letter of Authorization (LOA) that a customer uses to order fiber Ethernet (single-mode fiber only, either 1Gig-LX or 10Gig-LR optics). This Ethernet runs from a customer cage or provider cage to the {{site.data.keyword.cloud_notm}} Connecting Facility Assignment (CFA) termination point, which is tied down to the cross-connect router (XCR) infrastructure. The media must be a 1310 nm wavelength optic.

**Port speed options** - Select 1 Gbps, 2 Gbps, 5 Gbps, or 10 Gbps.

**Approximate latency** - Latency is approximately 1.5 ms within the local area (data centers with the same three-letter prefix, such as DAL, AMS, MEL). See [Looking Glass](http://lg.softlayer.com/){: external} for live PoP-to-PoP (P2P) location latency measurements.

**IBM colocation services** - None

**Redundancy** - {{site.data.keyword.cloud_notm}} doesn't provide redundancy as part of the product. To establish redundant connectivity, customer must acquire two connections on diverse cross connect routers (XCRs) and configure BGP on each Direct Link connection as they prefer. Examples include options such as: _prefer Lowest MED_, _prefer highest local-preference_, or _prefer shorter AS paths_.

**Local and global routing options** - The local routing option is the default routing option. It provides access to data centers within the same market as the Direct Link PoP (denoted, for example, as DAL, AMS, or MEL). The global routing option is required as an add-on to connect your {{site.data.keyword.cloud_notm}} resources to other {{site.data.keyword.cloud_notm}} resources in data centers outside the local market. It provides a way to share workloads between {{site.data.keyword.cloud_notm}} resources (for example, Dallas to Ashburn, or Dallas to Frankfurt).
