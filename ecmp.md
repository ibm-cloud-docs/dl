---

copyright:
  years: 2020, 2021
lastupdated: "2021-11-02"

keywords: direct link

subcollection: dl
---

{{site.data.keyword.attribute-definition-list}}

# Leveraging ECMP for redundant connections
{: #leverage-ecmp-redundant-connections}

Equal-cost multipath (ECMP) is a feature of the Border Gateway Protocol (BGP). ECMP alone is not sufficient to achieve redundancy, and the use cases in this topic explain why.
{: shortdesc}

The direct link router does not support ECMP. However, the customer router can use ECMP to load-balance incoming traffic over multiple direct links into IBM Cloud.
{: important}

## Use Case 1: ECMP without diversity
{: #usecase-one}

ECMP isn’t designed for creating redundant connections, but for balancing the load over two links. In this ECMP example on IBM Cloud, both connections terminate to the same IBM Cloud cross-connect router (XCR), which makes it a single point of failure. 

ECMP for redundancy, or load balancing, can impact diversity at the IBM XCR. As a result, careful design is recommended for projects with diversity or High Availability (HA) requirements.

![ECMP Dedicated model](/images/ecmp-without-diversity.png "ECMP Dedicated model"){: caption="Figure 1: ECMP provisioning" caption-side="bottom"}

## Use Case 2: ECMP with diversity
{: #usecase-two}

In this example of ECMP and direct link router diversity, there are two direct links on diverse direct link routers. For HA with ECMP, it is recommended to establish BGP with at least two direct link routers to achieve diversity in the HA design.

![ECMP Dual XCR Model](/images/ecmp-with-diversity.png "ECMP Dual XCR Model"){: caption="Figure 2: ECMP with Dual XCRs" caption-side="bottom"}
