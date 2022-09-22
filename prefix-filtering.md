---

copyright:
  years: 2022
lastupdated: "2022-4-29"

keywords: direct link

subcollection: dl

---

{{site.data.keyword.attribute-definition-list}}

# Filtering routes using Transit Gateway prefix filtering
{: #prefix-filtering}

If you use IBM Cloud Transit Gateway with IBM Cloud Direct Link, you can filter direct link routes using the Transit Gateway prefix filtering capability. For example, if you have a direct link gateway connected to a transit gateway, place the filters on the transit gateway/direct link connection as shown. This allows you to control what prefixes are learned by the transit gateway and is advantageous if you have dozens of on-prem prefixes, but only want the VPC connection to be able to talk to one prefix, or a select few. 

The prefix filter will only filter prefixes into the transit gateway. There is no prefix filter to block prefixes learned by the transit gateway out to networks that are connected to it. This means that the direct link sees all the prefixes from all the networks participating in the transit gateway. 

![Filtering routes using Transit Gateway prefix filtering](/images/prefix-filter-transit-gateway.png){: caption="Figure 4. Filtering routes using Transit Gateway prefix filtering" caption-side="bottom"}
