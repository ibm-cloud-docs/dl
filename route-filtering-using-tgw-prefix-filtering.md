---

copyright:
  years: 2023, 2024
lastupdated: "2024-07-18"

keywords: direct link

subcollection: dl

---

{{site.data.keyword.attribute-definition-list}}

# Filtering routes by using Transit Gateway prefix filtering
{: #prefix-filtering-transit}

If you use IBM Cloud Transit Gateway with IBM Cloud Direct Link, you can filter direct link routes by using the Transit Gateway prefix filtering capability. For example, if you have a direct link that is connected to a transit gateway, you can put the filters on the transit gateway or direct link connection as shown in Figure 1. This configuration allows you to control what prefixes the transit gateway learns and is advantageous if you have dozens of on-premises prefixes, but want the VPC connection only to be able to talk to one prefix (or a select few).

The prefix filter will only filter prefixes into the transit gateway. There is no prefix filter to block prefixes that are learned by the transit gateway out to networks that are connected to it. The direct link sees all the prefixes from all the networks that participate in the transit gateway.

![Filtering routes by using Transit Gateway prefix filtering](images/prefix-filter-transit-gateway1.svg){: caption="Figure 1. Filtering routes using Transit Gateway prefix filtering" caption-side="bottom"}

Direct Link BGP route filters work effectively with Transit Gateway prefix filters. You can use both filters at the same time. For more information about Transit Gateway prefix filters, see [Adding and deleting prefix filters](/docs/transit-gateway?topic=transit-gateway-adding-prefix-filters&interface=ui).
{: note}
