---

copyright:
  years: 2022, 2026
lastupdated: "2022-4-29"

keywords: direct link

subcollection: dl

---

{{site.data.keyword.attribute-definition-list}}

# Filtering routes by using Transit Gateway prefix filtering
{: #prefix-filtering}

If you use IBM Cloud Transit Gateway with Direct Link, you can filter direct link routes by using the Transit Gateway prefix filtering capability. For example, if a direct link is connected to a transit gateway, place the filters on the transit gateway/direct link connection as shown. This feature allows you to control what prefixes are learned by the transit gateway. It is also advantageous if you have dozens of on-prem prefixes, but want the VPC connection to be able to talk to only one prefix, or a select few. 

The prefix filter will only filter prefixes into the transit gateway. There is no prefix filter to block prefixes that are learned by the transit gateway out to networks that are connected to it. This means that the direct link sees all the prefixes from all the networks that participate in the transit gateway. 

![Filtering routes by using Transit Gateway prefix filtering](/images/prefix-filter-transit-gateway.png){: caption="Filtering routes using Transit Gateway prefix filtering" caption-side="bottom"}
