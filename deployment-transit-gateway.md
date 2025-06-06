---

copyright:
  years: 2020, 2025
lastupdated: "2025-05-23"

keywords: direct link

subcollection: dl

---

{{site.data.keyword.attribute-definition-list}}

# Planning for deployment
{: #dl-planning-considerations}

Provides general considerations for planning your Direct Link deployment.
{: shortdesc}

## Planning for virtual connections
{: #dl-planning-virtual-connections}

Direct Link gateways allow on-premises networks to connect to networks in the IBM Cloud using virtual connections. Network traffic between virtual connections on a Direct Link gateway is not supported. However, depending on what network prefixes are advertised from the on-prem network, traffic might still flow between the virtual connections. For example, if the on-prem network advertises the default route (`0.0.0.0/0`). In this case, all traffic originating from a network that is connected through a virtual connection that does not find a route more specific than `0.0.0.0/0` is sent to the Direct Link gateway. After traffic arrives at the gateway, the traffic is forwarded by using standard routing algorithms. If another virtual connection has a route that matches the destination address of the traffic, then it is forwarded to the network on that virtual connection (instead of the less specific `0.0.0.0/0` of the on-premises network).

## Using AS prepends with VPC connections
{: #as-prepends-routes}

Currently, VPC networking doesn't consider the AS path length when selecting the best route for network traffic. However, you can use a transit gateway between the direct link and VPC in certain topologies to achieve the same outcome. Also, if prefix values are repeated across different AS prepends (of the same policy), the first instance of the prefix value sets the prefix length; the rest are ignored.

Keep in mind that AS prepends currently have no effect on the routing between VPCs and direct links.
{: important}



### Examples
{: #as-prepend-examples}

The following deployment topologies illustrate various AS Prepend scenarios when connecting to VPCs.

1. VPC chooses a route regardless of the AS path length.

   ![AS prepends have no effect on the routing between VPCs and direct links](images/asprepends_1.png){: caption="AS prepends have no effect on the routing between VPCs and direct links." caption-side="bottom"}

1. VPC routes to the transit gateway, then the transit gateway considers the AS path length when choosing the route to on-premises.

   ![AS prepends are considered during route determination](images/asprepends_2.png){: caption="AS prepends are considered during route determination." caption-side="bottom"}

1. The local transit gateway is preferred over the global transit gateway.

   ![AS prepends are not considered during route determination](images/asprepends_3.png){: caption="AS prepends will not be considered during route determination." caption-side="bottom"}

1. The local transit gateway is preferred over the global transit gateway. However, the AS path is considered to get to the on-premises.

   ![AS prepends are considered during route determination](images/asprepends_4.png){: caption="AS prepends are considered during route determination." caption-side="bottom"}

1. A direct link to VPC connection is always a higher priority than a direct link (attached to a transit gateway) connected to a VPC.

   ![Direct link directly attached to a VPC is always higher priority than a direct link (attached to a transit gateway) connected to a VPC](images/asprepends_5.png){: caption="Direct link directly attached to a VPC is always higher priority than a direct link (attached to a transit gateway) connected to a VPC." caption-side="bottom"}

### Related links
{: #as-prepends-related-links}

* [Using AS prepends to manage route priorities](/docs/dl?topic=dl-dl-about#use-case-1)
* [Influencing route preference using AS prepends](/docs/dl?topic=dl-models-for-diversity-and-redundancy-in-direct-link#dl-bgp-path-selection)
