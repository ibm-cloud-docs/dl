---

copyright:
  years: 2020, 2022
lastupdated: "2021-08-18"

keywords: direct link

subcollection: dl

---

{{site.data.keyword.attribute-definition-list}}

# Planning considerations when using AS prepends with VPC connections
{: #as-prepends-routes}

Currently, VPC networking doesn't consider the AS path length when selecting the best route for network traffic. Therefore, AS prepends configured on direct links have no effect when VPCs are directly connected. However, you can use a transit gateway between the direct link and VPC in certain topologies to achieve the same outcome.
{: shortdesc}

## Examples
{: #as-prepend-examples}

The following deployment topologies illustrate various AS Prepend scenarios when connecting to VPCs.  

1. VPC chooses a route regardless of the AS path length.

   ![AS prepends have no effect on the routing between VPCs and Direct Link gateways](/images/asprepends_2.png){: caption="Figure 4. AS prepends have no effect on the routing between VPCs and Direct Link gateways." caption-side="bottom"}
   
1. VPC routes to the transit gateway and the transit gateway considers the AS path length when choosing the route to on-premises.

   ![AS prepends are considered during route determination](/images/asprepends_1.png){: caption="Figure 5. AS prepends are considered during route determination." caption-side="bottom"}

1. The local transit gateway is preferred over the global transit gateway.

   ![AS prepends will not be considered during route determination](/images/asprepends_3.png){: caption="Figure 6. AS prepends will not be considered during route determination." caption-side="bottom"}
   
1. The local transit gateway is preferred over the global transit gateway. However, the AS path is considered to get to the on-premises.

   ![AS prepends are considered during route determination](/images/asprepends_4.png){: caption="Figure 7. AS prepends are considered during route determination." caption-side="bottom"}

## Related links
{: #as-prepends-related-links}

* [Using AS prepends to manage route priorities](/docs/dl?topic=dl-dl-about#use-case-1) 
* [Influencing route preference using AS prepends](/docs/dl?topic=dl-models-for-diversity-and-redundancy-in-direct-link#dl-bgp-path-selection)
 
