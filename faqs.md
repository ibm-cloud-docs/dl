---

copyright:
  years: 2019, 2020
lastupdated: "2019-12-15"

keywords: faq, faqs, questions, answer, billing, fees, point-to-point, bandwidth, charges, redundancy, global routing, diversity, IPv6, BGP, charges, jumbo frames

subcollection: dl

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:faq: data-hd-content-type='faq'}
{:support: data-reuse='support'}
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

# FAQs
{: #faqs}

You can review answers to some frequently asked questions about {{site.data.keyword.cloud}} Direct Link Dedicated "2.0".
{:shortdesc}

## How does the new Direct Link differ from Direct Link on Classic?
{: #differentiators}
{: faq}
{: support}

The new Direct Link "2.0" offering differs from the Direct Link classic infrastructure in that Direct Link "2.0" is decoupled from classic IaaS, and exists only in the local cross-connect router (XCR). This design enables native connectivity to VPC and future capabilities without being forced into the classic IaaS network.

The initial rollout of Direct Link "2.0" is in the Dallas and Washington D.C. sites. The zone-region model allows for multiple data centers to exist in a single zone.

The new Direct Link"2.0" offering allows connectivity to both Classic IaaS as well as VPCs, whereas the Classic Direct Link always connects to IaaS network and a global VRF first. Classic Direct Link can only reach Classic VPC on a limited basis, and cannot reach VPC Gen 2 at all.

For more information about the differences between the new Direct Link Dedicated "2.0" offering and the Classic version, see [How do I know which Direct Link solution to order?](/docs/direct-link?topic=direct-link-get-started-with-ibm-cloud-direct-link#get-started-solution-to-order).
{: tip}

## What is planned for Direct Link Exchange?
{: #exchange-eom}
{: faq}
{: support}

The marketplace has evolved since Direct Link Exchange was established. With data center operators now blurring the lines as Network Service Providers, IBM will be combining the Exchange offering with Connect on the new "next generation" platform to reflect both this change in the marketplace and simplify the Direct Link portfolio. Direct Link Exchange will service only the Direct Link classic infrastructure. After migrations of the partner inter-connections to the XCRs are complete, Exchange will be moved to End of Marketing (EoM).

## Will Direct Link "2.0" be available in non-MZRs, or is it only a solution for MZRs?  
{: #dl-mzr}
{: faq}
{: support}

Initial rollout plans are for the MZRs to be prioritized. Other PoPs across the portfolio will support the new Direct Link access model, enabling access to the classic infrastructure and VPC expansions as they occur.

## What other locations are in the 2020 roadmap?
{: #roadmap}
{: faq}
{: support}

Six MZRs are in plan for 1H20 (Frankfurt, Tokyo, London, and Sydney in 1H20; Toronto and Sao Paulo in 2H20.

## If Direct Link "2.0" is not available for SZRs, how do  financial services clients handle the data that they need to keep in their regions?
{: #roadmap-szrs}
{: faq}

Any existing customers on classic IaaS can remain in classic IaaS and continue to access classic IaaS data centers on Direct Link "2.0" or Direct Link on Classic. VPC connectivity is fully supported ONLY on Direct Link "2.0".

## Will Direct Link "2.0" be available in all {{site.data.keyword.cloud_notm}} data centers?
{: #dc}
{: faq}
{: support}

The plan is for Direct Link to be available in the following data centers by the end of 2020:

| Region | Zone | Data Center |
|:---|:---|:---|
| us-south | us-south-1<br />us-south-2<br />us-south-3 | DAL10<br />DAL12<br />DAL13 |
| eu-de | eu-de-1<br />eu-de-2<br />eu-de-3 | FRA02<br />FRA04<br />FRA05 |
| jp-tok | jp-tok-1<br />jp-tok-2<br />jp-tok-3 | TOK02<br />TOK04<br />TOK05 |
| eu-gb | eu-gb-1<br />eu-gb-2<br />eu-gb-3 | LON04<br />LON05<br />LON06 |
| au-syd | au-syd-1<br />au-sy-2<br />au-syd-3 | SYD01<br />SYD04<br />SYD05 |
| us-east | us-east-1<br />us-east-2<br />us-east-3 | WDC-04<br />WDC06<br />WDC07 |

## Where are the Direct Link "2.0" offerings enabled?
{: #classic-enabled-versus-dl}
{:faq}
{: support}

| MZR | Direct Link Classic | Direct Link |
|:---|:---|:---|
| us-south (Dallas) | Yes | Yes |
| us-east (Washington DC) | Yes | Yes |
| eu-de (Frankfurt) | Yes | Coming soon |
| jp-tok (Tokyo) | Yes | Coming soon |
| eu-gb (London) | Yes | Coming soon |
| au-syd (Sydney) | Yes | Coming soon |

## How do I interconnect the classic infrastructure and VPC?
{: #interconnect}
{:faq}
{: support}

You can connect the classic infrastructure and VPC with classic peering as described in (/docs/vpc-on-classic-network?topic=vpc-on-classic-setting-up-access-to-your-classic-infrastructure-from-vpc).

Classic access features of VPC are an option at VPC setup and can only be enabled at the initial VPC creation. For more information, see [Creating and managing network resources in VPC](/docs/vpc-on-classic?topic=vpc-on-classic-creating-and-managing-network-resources-in-vpc).

## Is there a way to connect Direct Link "2.0" to VPC without using the classic infrastructure?
{: #connect-wo-using-classic}
{:faq}
{: support}

Yes, this is possible on Direct Link "2.0". The VRF created is local to the XCR versus global on the classic intrastructure. Route targeting to VPC then enables Direct Link "2.0" to be used with VPC natively using the UI (and not touch the classic infrastructure).

## Are there documented limitations on Direct Link?
{: #direct-link-vpc-limitations}
{:faq}
{: support}

Yes, they are listed in Virtual Private Cloud [Quotas](/docs/vpc-on-classic?topic=vpc-on-classic-quotas) documentation.

## How do I move from Direct Link on Classic to the new Direct Link?
{: #move-classic-to-new}
{:faq}

Direct Link "2.0" has a new user interface and records system, requiring you to place a brand new Direct Link "2.0" order.

## Are there any performance impacts affected by moving from Direct Link on Classic?
{: #move-classic-to-new-performance}
{:faq}

The new Direct Link "2.0" performs better as it's not required to exist inside a customer's global VRF for classic IaaS. It is a true access platform to all of {{site.data.keyword.cloud_notm}}.

## In terms of cost, what do you pay for?
{: #cost}
{:faq}

There are two pricing plans: metered and unmetered. Metered has a port fee and bill per GB egressed across the Direct Link.
Unmetered billing has a higher port fee and no usage charges, which are ideal for customers who consistently egress traffic across their direct link.

## How does {{site.data.keyword.cloud_notm}} Direct Link work?
{: #how-does-ibm-cloud-dl-work}
{:faq}

For every Direct Link customer, the {{site.data.keyword.cloud}} team assigns a small private subnet to build a point-to-point network between the {{site.data.keyword.cloud_notm}} cross-connect router (XCR) and the customer's edge router (CER). Then, {{site.data.keyword.cloud_notm}} and the customer configure Border Gateway Protocol (BGP) to exchange routes between the environments. Finally, {{site.data.keyword.cloud_notm}} places the customer into a VRF to allow for the implementation of non-unique routes to the private address space of the customer's remote network.

## When does billing begin with Direct Link?
{: #when-does-billing-begin-with-dl}
{:faq}

The fees for Direct Link cover the cost of service termination on the {{site.data.keyword.cloud_notm}} infrastructure.

Infrastructure services are billed in advance and begin upon acceptance of a client’s order. However, due to the nature of {{site.data.keyword.cloud_notm}} Direct Link, the Direct Link service billing begins when a BGP session is established with {{site.data.keyword.cloud_notm}}, or 30 days after the service key is provided to the client.

Billing stops after (1) a customer requests a circuit to be deleted AND (2) the provider has de-provisioned the circuit.

## What extra charges will I incur from other parties with Direct Link?
{: #what-additional-charges-will-i-incur-from-other-parties-with-dl}
{:faq}

You might have extra charges from your provider. Refer to your provider for their fee information.

## How can I achieve redundancy with {{site.data.keyword.cloud_notm}} Direct Link?
{: #how-can-i-achieve-redundancy-with-ibm-cloud-dl}
{:faq}

Direct Link does not provide an inherently redundant service. Direct Link can provide diverse connections that enable customers to create redundancy via BGP. You can achieve diversity with Direct Link by connecting to more than one {{site.data.keyword.cloud_notm}} Direct Link Dedicated provider for {{site.data.keyword.cloud_notm}}.

## What is the difference between the default "local" routing and the global routing add-on for Direct Link?
{: #what-is-the-difference-between-the-default-local-routing-and-the-global-routing-add-on-for-dl}
{:faq}

The local routing option is the default routing option. If your Direct Link is connected at the local PoP, it provides access to all data centers within that same market. In some markets, local routing is applicable for stand-alone PoP locations and direct links that are terminated at the data center.  

With our standard Direct Link offering, you can send traffic between the data centers in your selected region. If you need access to other data centers outside of the specified region, you must order the global routing add-on. For example, you might use global routing to share workloads between dispersed {{site.data.keyword.cloud_notm}} resources (such as Dallas to Ashburn, or Dallas to Frankfurt).

## Why does a global routing add-on package exist for Direct Link?
{: #why-does-a-global-routing-add-on-package-exist-for-dl}
{:faq}

The global routing add-on prevents our customers from experiencing unexpected data costs when traversing outside of their data center's local market. It keeps costs lower for most of our customers, and it provides the ability for customers with a global presence to reach all regions across the globe easily. However, usually a customer requires only a local bandwidth package.

## If I am connected to a Direct Link Dedicated in a region, such as Dallas, can I access other regions in the US through Direct Link?
{: #if-i-am-connected-to-a-dl-dedicated}
{:faq}

Yes, you are able to gain access to areas outside of your local market if you choose the global routing add-on. If this option is not selected, your Direct Link traffic is limited to the local market for the PoP or DC location you selected. Refer to the [pricing document](/docs/dl?topic=dl-pricing-for-ibm-cloud-dl) for details.

## Can I connect to any available region from a given Direct Link location?
{: #can-i-connect-to-any-available-region-from-a-given-dl-location}
{:faq}

Yes, if you order Direct Link with the global routing add-on.

## Can I restrict the regions that my Direct Link can reach?
{: #can-i-restrict-the-regions-that-my-dl-can-reach}
{:faq}

No. {{site.data.keyword.cloud_notm}} offers two options: (1) a local market only, or (2) all regions, with the global routing add-on.

## Can IBM Support IPv6 over Direct Link?
{: #can-ibm-support-ipv6-over-dl}
{:faq}

Not for the BGP session. We must assign our `/30` from IPv4, and we need the same in return from the customer.

## Can IBM do IPV6 on the private network?
{: #can-ibm-do-ipv6-on-the-private-network}
{:faq}

No. IPv6 is public only.

## Does Direct Link support any type of QoS?
{: #does-dl-support-any-type-of-qos}
{:faq}

We are unable to support any QoS guarantees. QoS requires MPLS mapping between each of our service suppliers and {{site.data.keyword.cloud_notm}}. Cloud Service providers generally cannot support QoS because it must reach from end-to-end and involve every device in between. No workaround is currently available by "tunneling" or any other method.

## Does Direct Link support Jumbo frames?
{: #does-dl-support-jumbo-frames}
{:faq}

Jumbo frames (up to 9214 bytes) are supported on Dedicated and Dedicated Hosting.

## How easy is it to upgrade the bandwidth of my Direct Link connection, for example 1 - 5 GB?
{: #how-easy-is-it-to-upgrade-the-bandwidth-of-my-dl-connection}
{:faq}

Typically, we install speeds of 1 GB and lower on 1 GB optics. For speeds of 2 - 10 GB, we install 10 GB optics. Thus, the upgrade 1 - 5 GB would require new optics to be assigned or inserted. It would be a service-affecting event. If you anticipate that type of growth, it's possible to request 10 GB optical fibers to be installed at the beginning of your Direct Link deployment, or to order 2 GB initially so that the 10 GB optics are in place.

## Is ECMP the way to go for redundant Direct Link connections? What alternatives exist?
{: #is-ecmp-the-way-to-go-for-redundant-dl-connections}
{:faq}

ECMP isn’t for redundant connections, but for balancing the load over the two links. With ECMP, both connections must terminate to the same {{site.data.keyword.cloud_notm}} cross-connect router (XCR), which makes it a single point of failure. In other words, ECMP can be provisioned only as two sessions on the same {{site.data.keyword.cloud_notm}} XCR.

ECMP is a feature of BGP. If you are looking for redundancy, get two Direct Link connections, one going into each XCR. If you want to use ECMP and have redundancy, you need two Direct Link connections on each XCR so that you can have 2 ECMP sessions running simultaneously.

Alternatively, some customers set up two links into a different XCR in the same data center (for example, WDC02) and then failover as needed by using BGP configurations. This configuration is less redundant (less safe) than having Direct Link connections into two separate data centers, such as WDC02 and WDC05.

## Is there a Service Level Agreement (SLA) on the Direct Link XCR connections up to the account’s BCR connection?
{: #is-there-an-sla-on-the-diret-link-xr-connections}
{:faq}

There is no SLA on Direct Link today. Customers can achieve 99.999% effectively with two or more direct links that are properly configured for failover by using BGP, but IBM cannot control that or provide an SLA on it.
