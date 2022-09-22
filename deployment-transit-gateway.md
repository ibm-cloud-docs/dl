---

copyright:
  years: 2020, 2022
lastupdated: "2022-09-21"

keywords: direct link

subcollection: dl

---

{{site.data.keyword.attribute-definition-list}}

### As traffic travels from a VPC to on-premises, will AS prepends work?
{: #as-prepends-routes}

Currently, VPC networking doesn't consider the AS path length when selecting the best route for network traffic and therefore, AS prepends configured on direct links have no effect when VPCs are directly connected. However, you can use a transit gateway between the direct link and VPC in some topologies to achieve the desired effect.
{: shortdesc}

Examples:

1. VPC chooses a route regardless of the AS path length.

   ![AS prepends have no effect on the routing between VPCs and Direct Link gateways](/images/asprepends_2.png){: caption="Figure 1. AS prepends have no effect on the routing between VPCs and Direct Link gateways." caption-side="bottom"}
   
1. VPC routes to the transit gateway and the transit gateway considers the AS path length when choosing the route to on-premises.

   ![AS prepends are considered during route determination](/images/asprepends_1.png){: caption="Figure 2. AS prepends are considered during route determination." caption-side="bottom"}

1. The local transit gateway is preferred over the global transit gateway.

   ![AS prepend expected "not" to be considered](/images/asprepends_3.png){: caption="Figure 3. AS prepend expected "not" to be considered." caption-side="bottom"}
   
1. The local transit gateway is preferred over the global transit gateway. However, the AS path is considered to get to the on-premises.

   ![AS prepend expected to be considered](/images/asprepends_4.png){: caption="Figure 4. AS prepend expected to be considered." caption-side="bottom"}