---

copyright:
  years: 2023
lastupdated: "2023-03-16"

keywords: direct link

subcollection: dl

---

{{site.data.keyword.attribute-definition-list}}

# Filtering routes using Transit Gateway prefix filtering
{: #prefix-filtering}

If you use IBM Cloud Transit Gateway with IBM Cloud Direct Link, you can filter direct link routes using the Transit Gateway prefix filtering capability. For example, if you have a direct link connected to a transit gateway, you can place the filters on the transit gateway or direct link connection as shown in Figure 1. This allows you to control what prefixes are learned by the transit gateway and is advantageous if you have dozens of on-premises prefixes, but only want the VPC connection to be able to talk to one prefix (or a select few). 

The prefix filter only filters prefixes into the transit gateway. There is no prefix filter to block prefixes learned by the transit gateway out to networks that are connected to it. This means that the direct link sees all the prefixes from all the networks participating in the transit gateway. 

![Filtering routes using Transit Gateway prefix filtering](/images/prefix-filter-transit-gateway1.svg){: caption="Figure 1. Filtering routes using Transit Gateway prefix filtering" caption-side="bottom"}

Direct Link BGP route filters work effectively with Transit Gateway prefix filters. You can use both filters at the same time. For more information about Transit Gateway prefix filters, see [Adding and deleting prefix filters](/docs/transit-gateway?topic=transit-gateway-adding-prefix-filters&interface=ui).
{: note}
