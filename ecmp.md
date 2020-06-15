---

copyright:
  years: 2020
lastupdated: "2020-05-15"

keywords: diversity, redundancy, schematics, deployment, configuration, global routing, ECMP, Dual XCRs, model

subcollection: dl

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
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

# Leveraging ECMP for redundant connections
{: #leverage-ecmp-for-redundant-connections}

Equal-cost multipath (ECMP) is a feature of the Border Gateway Protocol (BGP). ECMP alone is not sufficient to achieve redundancy, and the use cases in this topic explain why.
{: shortdesc}

## Use Case 1: ECMP without diversity
{: #usecase-without-diversity-ecmp}

ECMP isn’t designed for creating redundant connections but for balancing the load over two links. With ECMP on {{site.data.keyword.cloud_notm}}, both connections must terminate to the same {{site.data.keyword.cloud_notm}} cross-connect router (XCR), which makes it a single point of failure. In other words, ECMP can be provisioned as two sessions only on the same {{site.data.keyword.cloud_notm}} XCR.

ECMP for redundancy or load balancing can impact diversity at the IBM XCR. As a result, careful design is recommended for projects with Diversity or High Availability (HA) requirements.

![ECMP Dedicated model](/images/ecmp-without-diversity.png "ECMP Dedicated model"){: caption="Figure 1: ECMP provisioning" caption-side="top"}

## Use Case 2: ECMP with diversity
{: #usecase-with-diversity-ecmp}

ECMP is a feature of BGP. If you want to use ECMP and have redundancy, you must have two {{site.data.keyword.dl_short}} connections on each XCR so that you can have two ECMP sessions going simultaneously.

For HA with ECMP, it is recommended that four {{site.data.keyword.dl_short}} circuits be established, with two of them at diverse XCRs to achieve diversity.

![ECMP Dual XCR Model](/images/ecmp-with-diversity.png "ECMP Dual XCR Model"){: caption="Figure 2: ECMP with Dual XCRs" caption-side="top"}
