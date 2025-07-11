---

copyright:
  years: 2020, 2025
lastupdated: "2025-06-17"

keywords: interconnectivity, direct link

subcollection: dl

---

{{site.data.keyword.attribute-definition-list}}

# About {{site.data.keyword.dl_full_notm}}
{: #dl-about}

{{site.data.keyword.dl_full}} offerings provide connectivity from an external source into a customer's {{site.data.keyword.cloud_notm}} private network. {{site.data.keyword.dl_short}} can be viewed as an alternative to a traditional site-to-site VPN solution, which is designed for customers that need more consistent, higher-throughput connectivity between a remote network and their {{site.data.keyword.cloud_notm}} environments.
{: shortdesc}

The {{site.data.keyword.dl_full_notm}} service is a routed, OSI Layer-3 service. It offers a direct connection to the {{site.data.keyword.cloud_notm}} private network backbone, with low latency and speeds up to 10 Gbps.

For increased flexibility in creating this Layer-3 connectivity, {{site.data.keyword.dl_full_notm}} enables customers to use:

* Dual IP for remote hosts
* Tunneling for BYOIP

You can also bind a direct link to transit gateways so that you have a secure connection to on-premises networks and IBM Cloud resources that are connected through the transit gateways.

## {{site.data.keyword.dl_short}} offerings
{: #overview-of-direct-link-offerings}

Currently, two types of connections are available: {{site.data.keyword.dl_short}} Dedicated and {{site.data.keyword.dl_short}} Connect.
{: shortdesc}

### {{site.data.keyword.dl_short}} Connect
{: #ibm-cloud-connect}

Provides private access to the IBM Cloud infrastructure and any other clouds that are linked to your service provider through your local IBM Cloud data center. This option is perfect for creating multi-cloud connectivity in a single environment. IBM connects customers to the IBM Cloud Private network, by using a shared bandwidth topology. As with all {{site.data.keyword.dl_short}} products, you can add global routing that enables private network traffic to all IBM Cloud locations.

### {{site.data.keyword.dl_short}} Dedicated
{: #ibm-cloud-dedicated}

Allows customers to end a single-tenant, fiber-based cross-connect into the {{site.data.keyword.cloud_notm}} network. Customers with colocation premises that are next to {{site.data.keyword.cloud_notm}} PoPs and data centers can use this offering. Network service providers that deliver circuits to customers' on-premises or other data centers can also use this offering. 

You can now enable MACsec when ordering IBM Cloud Direct Link Dedicated to secure Ethernet connections between your on-premises network and IBM Cloud. For more information, see [Planning for the Direct Link MACsec feature](/docs/dl?topic=dl-dl-planning-considerations#macsec-feature-dedicated).
{: note}

## Using AS prepends to influence route preference
{: #use-case-1}

This use case pertains to both Direct Link Connect and Direct Link Dedicated offerings.
{: note}

Adding one or more autonomous system (AS) numbers at the beginning of an AS path is called _AS prepending_. You can use this technique to make a route less preferable to the BGP router by increasing the length of the AS path. For example, you might want route redundancy, but don't want traffic going through both routes at the same time.

Assuming that all other criteria are equal, the prefix of the AS prepend matches with routes and lengthens the AS path to the destination. This action results in a less priority route compared to one without AS prepends to the same destination. Take the following use case, for example. Suppose that you want your East site to prefer Path A through IBM PoP East when traffic is sent to `10.80.0.0/28`. To de-prioritize Path B, the BGP Autonomous System Number (ASN) of `12345` is prepended to the route (`12345 12345 12345 4040 286 I`).

![Influencing route priority by using AS prepends](images/as-prepends.png){: caption="Influencing route priority using AS prepends" caption-side="bottom"}

For more information, see [Influencing route preference by using AS prepends](/docs/dl?topic=dl-models-for-diversity-and-redundancy-in-direct-link#dl-bgp-path-selection) and [Using AS prepends with VPN connections](/docs/dl?topic=dl-dl-planning-considerations&interface=ui#as-prepends-routes).

## Direct Link Connect use cases
{: #connect-use-cases}

These use cases are best for working with hybrid workloads, cross-provider workloads, large or frequent data transfers, private workloads, and environment administration. Use these use cases:

* When you want quicker connectivity for mission-critical workloads
* When you need connections between a client network and IBM Cloud at speeds of 100 Gbps or less
* When diverse ports in a point of presence (PoP) are available

### {{site.data.keyword.dl_short}} Connect use case 1: Using service provider networks to virtually reach IBM Cloud
{: #use-case-connect-2}

The {{site.data.keyword.dl_short}} Connect solution enables you to use a service provider to deliver connectivity to {{site.data.keyword.cloud_notm}} locations. This offering typically provides connectivity at a reduced cost because the physical connectivity from {{site.data.keyword.cloud_notm}} to the service provider is already in place, which is shared among other customers.

Some benefits include:

* Multi-cloud use through a single Connect port
* Latency tolerant
* Lower-cost entry to {{site.data.keyword.cloud_notm}}

![Using service provider networks to virtually reach IBM Cloud](images/direct-link-connect.png){: caption="Leveraging service provider networks to virtually reach IBM Cloud" caption-side="bottom"}

### {{site.data.keyword.dl_short}} Connect use case 2: Other Cloud Service Providers (CSPs) or enterprises
{: #connect-use-case-3}

* Multicloud use through a single Connect port
* Latency tolerant
* Multi-tenant through NNI between IBM Cloud and a service provider
* Layer 2 and Layer 3 support
* Lower cost of entry to IBM Cloud

![Other CSPs or enterprises](images/connect-use-case.png){: caption="Other CSPs or enterprises" caption-side="bottom"}

Termination location:

 :    {{site.data.keyword.cloud_notm}} point of presence (PoP).

Typical deployment time:

 :    5 - 10 days after the circuit reaches the exchange. Deployment time can be 30 - 60 days overall, depending on your location and the requirements when you order a circuit from a service provider or carrier.

Cross-connect details:

 :    Physical cross-connects for the secure {{site.data.keyword.dl_short}} Connect interconnect are maintained between {{site.data.keyword.cloud_notm}} and the service provider. Request a "Virtual Circuit" from the service provider, which establishes logical connectivity to {{site.data.keyword.cloud_notm}}, after you are connected to the service provider.

Port speed options

 :    Select 50 Mbps, 100 Mbps[^100], 200 Mbps, 500 Mbps, 1 Gbps, 2 Gbps, 5 Gbps, 10 Gbps, 25 Gbps, 40 Gbps, 50 Gbps, or 100 Gbps.

[^100]: The 100 Mbps port speed option is not available for Equinix Exchange and Connect direct links.

Approximate latency:

 :    Latency is approximately 1.5 ms within the local area (data centers with the same three-letter prefix, such as DAL, AMS, MEL). See [Looking Glass](http://lg.softlayer.com/){: external} for live PoP-to-PoP (P2P) location latency measurements.

IBM colocation services:

 :    None.

Redundancy:

 :    {{site.data.keyword.cloud_notm}} does not provide redundancy as part of the product. To establish redundant connectivity, you must acquire two connections on diverse cross-connect routers (XCRs) and configure BGP on each {{site.data.keyword.dlc_full_notm}} connection as they prefer. Examples include: _prefer Lowest MED_, _prefer highest local-preference_, or _prefer shorter AS paths_.

Local and global routing options:

 :    The default routing option is Local routing. It provides access to data centers within the same market as the {{site.data.keyword.dl_short}} PoP (denoted, for example, as DAL, AMS, or MEL). The global routing option is required as an add-on to connect your IBM Cloud resources to other IBM Cloud resources in data centers outside the local market. It is used to share workloads between IBM Cloud resources (for example, Dallas to Ashburn, or Dallas to Frankfurt).

### {{site.data.keyword.dl_short}} Connect use case 3: Location connectivity that uses Power Systems Virtual Servers and Transit Gateway
{: #connect-use-case-4}

Direct Link is a hybrid cloud connectivity service that provides secure, private, high-bandwidth connectivity between customer on-premises and IBM Cloud resources. Paired with Power Systems Virtual Servers and IBM Cloud Transit Gateway, Direct Link offers options for high-bandwidth customer demand.

For deployment topologies that use Direct Link and Power Systems Virtual Servers, see [Network architecture diagrams](/docs/power-iaas?topic=power-iaas-network-architecture-diagrams).

## {{site.data.keyword.dl_short}} Dedicated use cases
{: #use-cases-dedicated}

These use cases are best for working with hybrid workloads, cross-provider workloads, large or frequent data transfers, private workloads, and environment administration. Use these use cases:

* When you want dedicated connectivity for mission-critical workloads
* When you need dedicated, single-tenant connections between a client and IBM
* When diverse ports in a point of presence (PoP) are available

### {{site.data.keyword.dl_short}} Dedicated use case 1: Customer on-premises facility to {{site.data.keyword.cloud_notm}}
{: #use-cases-dedicated-1}

Use when deterministic latency is required.
{: important}

![Customer on-premises facility to IBM Cloud](images/direct-link-dedicated.png){: caption="Customer on-premises facility to IBM Cloud" caption-side="bottom"}

### {{site.data.keyword.dl_short}} Dedicated use case 2: Customer colocation to {{site.data.keyword.cloud_notm}}
{: #use-case-dedicated-2}

Use when ultra-low latency is required.

![Customer colocation to IBM Cloud](images/dedicated-model-colo.png){: caption="Customer colocation to IBM Cloud" caption-side="bottom"}

Termination location:

 :    {{site.data.keyword.cloud_notm}} point of presence (PoP) or Data Center (DC).

Typical deployment time:

 :    Averages 10-15 business days after the new circuit reaches the PoP. Deployment time can be 30 - 60 days overall, depending on your location and the requirements when you order a circuit from a service provider or carrier.

Cross-connect details:

 :    {{site.data.keyword.cloud_notm}} provides a Letter of Authorization (LOA) that you can use to order fiber Ethernet (single-mode fiber only, either 1Gig-LX or 10Gig-LR optics). The Ethernet runs from a customer cage or provider cage to the {{site.data.keyword.cloud_notm}} Connecting Facility Assignment (CFA) termination point, which is tied down to the cross-connect router (XCR) infrastructure. The media must be a 1310 nm wavelength optic.

Port speed options:

 :    Select 1 Gbps, 2 Gbps, or 5 Gbps.

Approximate latency:

 :    Latency is approximately 1.5 ms within the local area (data centers with the same three-letter prefix, such as DAL, AMS, MEL). See [Looking Glass](http://lg.softlayer.com/){: external} for live PoP-to-PoP (P2P) location latency measurements.

IBM colocation services:

 :    None.

Redundancy:

 :    {{site.data.keyword.cloud_notm}} doesn't provide redundancy as part of the product. To establish redundant connectivity, a customer must acquire two connections on diverse cross-connect routers (XCRs) and configure BGP on each {{site.data.keyword.dl_short}} connection as they prefer. Examples include: _prefer Lowest MED_, _prefer highest local-preference_, or _prefer shorter AS paths_.

Local and global routing options:

 :    The local routing option is the default routing option. It provides access to data centers within the same market as the {{site.data.keyword.dl_short}} PoP (denoted, for example, as DAL, AMS, or MEL). The global routing option is required as an add-on to connect your {{site.data.keyword.cloud_notm}} resources to other {{site.data.keyword.cloud_notm}} resources in data centers outside the local market. It provides a way to share workloads between {{site.data.keyword.cloud_notm}} resources (for example, Dallas to Ashburn, or Dallas to Frankfurt).
